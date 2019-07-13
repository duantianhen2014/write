## 基于TDD进行开发

TDD：Test-Driven Development

**在使用 TDD 进行开发时，请牢记以下三项法则：**

1. 在编写失败的测试之前，不要编写任何业务代码；
2. 只要有一个单元测试失败了，就不要再写测试代码。无法通过编译也是一种失败情况；
3. 业务代码恰好能够让当前失败的测试成功通过即可，不要多写；



**如果开发中创建了资源路由，之前使用此路由的需要进行修改，否则会显示Route [threads] not defined.**

```php
{{ route('threads') }}		=>		{{ route('threads.index') }}
```



章节易混点汇总：

* 第一节：

  我们的数据库发生了变化，需要重新运行迁移：

  ```php
  $ php artisan migrate:refresh
  ```

  数据填充：

  进入 `tinker` 环境：

  ```php
  $ php artisan tinker
  ```

  执行以下语句，填充假数据：

  ```php
  >>> factory('App\Reply',50)->create();
  ```

* 第六节：

  create()		方法得到一个模型实例，并保存到数据库中；

  make()		方法得到一个模型实例（不保存）；

  raw()		方法是得到一个模型实例转化后的数组。

  创建一个用户并登陆

  ```php
  //以下两个方法均可
  $this->be($user = factory('App\User')->create());
  $this->actingAs(factory('App\User')->create());
  ```

* 第七节：

  创建辅助函数（composer.json）：

  ```json
  "autoload-dev": {
      "psr-4": {
          "Tests\\": "tests/"
      },
      "files":["tests/utilities/functions.php"]  -->这里增加一行
  },
  ```

  controller中middle白名单、黑名单

  ```php
  //白
  $this->middleware('auth')->only(['index', 'show']);
  ```

  ```php
  //黑
  $this->middleware('auth')->except(['index', 'show']);
  ```

* 第十一节：

  改变Route中默认获取的key：

  ```php
  Route::get('threads/{channel}', 'ThreadsController@index');
  /**
  我们知道，以上的路由符合 Laravel 的 隐性路由模型绑定 原则。但是 {channel} 路由片段默认对应的是 id 字段，而我们需要对应的是 slug 字段。所以我们需要重写模型默认的RouteKeyName
  */
  class Channel extends Model
  {
      public function getRouteKeyName()
      {
          return 'slug';
      }
  }
  ```

* 第十四节

  视图数据共享：

  此时会发现我们所有的测试都报错了，这是因为我们在使用了 [视图共享数据](https://learnku.com/docs/laravel/5.5/views#sharing-data-with-all-views) :
  *forum\app\Providers\AppServiceProvider.php*

  ```php
  public function boot()
  {
      Carbon::setLocale('zh');
      \View::share('channels',\App\Channel::all());
  }
  ```

  而 `boot()` 方法会在应用启动的最开始时就加载，在测试场景中，运行测试时，测试数据库中是不存在数据表的，所以就抛出了异常。我们改为使用 [视图合成器](https://learnku.com/docs/laravel/5.5/views#b492db) ：

  > 视图合成器是在**渲染视图时调用**的回调或者类方法。如果你每次渲染视图时都要绑定视图的数据，视图合成器可以帮你将这些逻辑整理到特定的位置。

  ```php
  public function boot()
  {
      Carbon::setLocale('zh');
      \View::composer('*', function($view)
      {
      	$view->with('channels', Channel::all());
      });
  }
  ```

* 第十五节：

  注：这里我们使用了 Laravel [本地作用域 ](https://learnku.com/docs/laravel/5.5/eloquent#local-scopes)。本地作用域允许我们定义通用的约束集合以便在应用中复用。要定义这样的一个作用域，只需简单在对应 Eloquent 模型方法前加上一个 scope 前缀，作用域总是返回 [查询构建器](https://learnku.com/docs/laravel/5.5/queries)。一旦定义了作用域，则可以在查询模型时调用作用域方法。在进行方法调用时不需要加上 scope 前缀。如以上代码中的 filter () 。

  *ThreadsController.php*

  ```php
  use App\Filters\ThreadsFilters;
  .
  .
  public function index(Channel $channel,ThreadsFilters $filters)
  {
      if ($channel->exists) {
          $threads = $channel->threads()->latest();
      } else {
          $threads = Thread::latest();
      }
  
      $threads = $threads->filter($filters)->get();
  
      return view('threads.index',compact('threads'));
  }
  ```

  *forum\app\Thread.php*

  ```php
  public function scopeFilter($query,$filters)
  {
      return $filters->apply($query);
  }
  ```

  *ThreadsFilters*

  ```php
  <?php
  
  namespace App\Filters;
  
  use App\User;
  use Illuminate\Http\Request;
  
  class ThreadsFilters
  {
      protected $request;
  
      public function __construct(Request $request)
      {
          $this->request = $request;
      }
  
      public function apply($builder)
      {
          if(! $username = $this->request->by) return $builder;
  
          $user = User::where('name',$username)->firstOrfail();
  
          return $builder->where('user_id',$user->id);
      }
  }
  ```

* 第十六节：

  ```php
  <div class="col-md-4">
      <div class="panel panel-default">
           <div class="panel-body">
               <p>
                   <a href="#">{{ $thread->creator->name }}</a> 发布于 {{ $thread->created_at->diffForHumans() }}, 当前共有 {{ $thread->replies()->count() }} 个回复。
               </p>
           </div>
      </div>
  </div>
  ```

  注意 `$thread->replies()` 跟 `$thread->replies` 的区别：`$thread->replies()` 返回的是一个 `hasMany` 对象，而 `$thread->replies` 返回的是一个 `Collection` 集合。

  全局作用域：

  ```php
      protected static function boot()
      {
          parent::boot();
  		//为话题数据添加reply_count字段，数据为replied的count
          static::addGlobalScope('replyCount',function ($builder){
             $builder->withCount('replies');
          });
      }
  ```

* 第十七节：

  在builder Query清除order_by条件

  ```php
  public function popularity()
  {
      $this->builder->getQuery()->orders = [];
  
      return $this->builder->orderBy('replies_count','desc');
  }
  ```

* 第十八节：

  在迁移文件中对字段进行唯一索引：

  ```php
  public function up()
      {
          Schema::create('favorites', function (Blueprint $table) {
              $table->increments('id');
              $table->unsignedInteger('user_id');
              $table->unsignedInteger('favorited_id');
              $table->string('favorited_type', 50);
              $table->timestamps();
  
              $table->unique(['user_id', 'favorited_id', 'favorited_type']);
          });
      }
  ```

  在model中进行检测：

  ```php
  public function favorite()
  {
      $attributes = [
          'user_id'   => auth()->id(),
      ];
      if(! $this->favorites()->where($attributes)->exists()){
          return $this->favorites()->create($attributes);
      }
  }
  
  public function favorites()
  {
      return $this->morphMany(Favorite::class, 'favorited');
  }
  ```
