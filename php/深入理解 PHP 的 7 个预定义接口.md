# 深入理解 PHP 的 7 个预定义接口

### 深入理解预定义接口

> 场景：平常工作中写的都是业务模块，很少会去实现这样的接口，但是在框架里面用的倒是很多。

#### 1. Traversable（遍历）接口

> 该接口不能被类直接实现，如果直接写了一个普通类实现了该遍历接口，是会直接报致命的错误，提示使用Iterator（迭代器接口）或者IteratorAggregate（聚合迭代器接口）来实现，这两个接口后面会介绍；所有通常情况下，我们只是会用来判断该类是否可以使用foreach来进行遍历；

```
<?php
    class Test implements Traversable
    {
    }
    上面这个是错误示范，该代码会提示这样的错误：
    Fatal error: Class Test must implement interface Traversable as part of either Iterator or 
    IteratorAggregate in Unknown on line 0
    上面的大致意思是说如要实现这个接口，必须同Iterator或者IteratorAggregate来实现

    正确的做法：
    当我们要判断一个类是否可以使用foreach来进行遍历，只需要判断是否是traversable的实例

    class Test
    {
    }
    $test = new Test;
    var_dump($test instanceOf Traversable);
```

#### 2. Iterator（迭代器）接口

> 迭代器接口其实实现的原理就是类似指针的移动，当我们写一个类的时候，通过实现对应的5个方法：key（），current（），next（），rewind（），valid（），就可以实现数据的迭代移动，具体看以下代码

```php
<?php
class Test implements Iterator
    {
        public $key;
        protected $val = [
            'one',
            'two',
            'three',
        ];

        public function key()
        {
            return $this->key;
        }

        public function current()
        {
            return $this->val[$this->key];
        }

        public function next()
        {
            ++$this->key;
        }

        public function rewind()
        {
            $this->key = 0;
        }

        public function valid()
        {
            return isset($this->val[$this->key]);
        }
    }

    $test = new Test;

    $test->rewind();

    while($test->valid()) {
        echo $test->key . ':' . $test->current() . PHP_EOL;
        $test->next();
    }
```

#### 3. IteratorAggregate（聚合迭代器）接口

> 聚合迭代器和迭代器的原理是一样的，只不过聚合迭代器已经实现了迭代器原理，你只需要实现一个getIterator（）方法来实现迭代，具体看以下代码

```php
<?php
    class Test implements IteratorAggregate
    {
        public $one = 1;
        public $two = 2;
        public $three = 3;

        public function __construct()
        {
            $this->four = 4;
        }

        public function getIterator()
        {
            return new ArrayIterator($this);
        }
    }

    $test = (new Test())->getIterator();
    $test->rewind();
    while($test->valid()) {
        echo $test->key() . ' : '  .  $test->current() . PHP_EOL;
        $test->next();
    }

	从上面的代码，我们可以看到我们将Test类的对象传进去当做迭代器，通过while循环的话，我们必须通过调用getIterator（）方法获取到迭代器对象，然后直接进行迭代输出，而不需要去实现相关的key()等方法。
    当然这个时候，我们肯定想知道是否可以直接从foreach进行迭代循环出去呢？那么我们来打印一下结果
  $test = new Test;
  var_dump($test instanceOf Traversable);

    结果是输出bool true，所以我们接下来是直接用foreach来实现一下。

  $test = new Test;
  foreach($test as $key => $value) {
     echo $key . ' : ' . $value  .  PHP_EOL;
  }
  class Test implements IteratorAggregate
  {
    public $data;

    public function __construct()
    {
        $this->data = ['one' =>  1 , 'two' => 2];
    }

    public function getIterator()
    {
        return new ArrayIterator($this->data);
    }
  }

  同理实现的方式跟对对象进行迭代是一样的。
```

#### 4. ArrayAccess（数组式访问）访问

> 通常情况下，我们会看到this['name']这样的用法，但是我们知道，$this是一个对象，是如何使用数组方式访问的？答案就是实现了数据组访问接口ArrayAccess，具体代码如下

```php
<?php
	class Test implements ArrayAccess
    {
        public $container;

        public function __construct()
        {
            $this->container = [
                'one' => 1,
                'two' => 2,
                'three'  => 3,
            ];
        }

        public function offsetExists($offset) 
        {
            return isset($this->container[$offset]);
        }

        public function offsetGet($offset)
        {
            return isset($this->container[$offset]) ? $this->container[$offset] : null;
        }

        public function offsetSet($offset, $value)
        {
            if (is_null($offset)) {
                $this->container[] = $value;
            } else {
                $this->container[$offset] = $value;
            }
        }

        public function offsetUnset($offset)
        {
            unset($this->container[$offset]);
        }
    }
   $test = new Test;
   var_dump(isset($test['one']));
   var_dump($test['two']);
   unset($test['two']);
   var_dump(isset($test['two']));
   $test['two'] = 22;
   var_dump($test['two']);
   $test[] = 4;
   var_dump($test);
   var_dump($test[0]);

	当然我们也有经典的一个做法就是把对象的属性当做数组来访问

   class Test implements ArrayAccess
   {
        public $name;

        public function __construct()
        {
            $this->name = 'gabe';  
        }

        public function offsetExists($offset)
        {
            return isset($this->$offset);
        }

        public function offsetGet($offset)
        {
            return isset($this->$offset) ? $this->$offset : null;
        }

        public function offsetSet($offset, $value)
        {
            $this->$offset = $value;
        }

        public function offsetUnset($offset)
        {
            unset($this->$offset);
        }
   }

  $test = new Test;
  var_dump(isset($test['name']));
  var_dump($test['name']);
  var_dump($test['age']);
  $test[1] = '22';
  var_dump($test);
  unset($test['name']);
  var_dump(isset($test['name']));
  var_dump($test);
  $test[] = 'hello world';
  var_dump($test);
```

#### 5. Serializable（序列化）接口

> 通常情况下，如果我们的类中定义了魔术方法，**sleep(),**wakeup()的话，我们在进行serialize()的时候，会先调用**sleep()的魔术方法，我们通过返回一个数组，来定义对对象的哪些属性进行序列化，同理，我们在调用反序列化unserialize()方法的时候，也会先调用的**wakeup（）魔术方法，我们可以进行初始化，如对一个对象的属性进行赋值等操作；但是如果该类实现了序列化接口，我们就必须实现serialize（）方法和unserialize()方法，同时**sleep（）和** wakeup()两个魔术方法都会同时不再支持，具体代码看如下；

```php
<?php
	class Test
    {    
        public $name;
        public $age;

        public function __construct()
        {
            $this->name = 'gabe';
            $this->age = 25; 
        }    

        public function __wakeup()
        {
            var_dump(__METHOD__); 
            $this->age++;
        }   

        public function __sleep()
        {        
            var_dump(__METHOD__);
            return ['name'];    
        }
    }

    $test = new Test;
    $a = serialize($test);
    var_dump($a);
    var_dump(unserialize($a));

    //实现序列化接口，发现魔术方法失效了

   class Test implements Serializable
   {    
    public $name;
    public $age;

    public function __construct()
    {        
        $this->name = 'gabe';
        $this->age = 25;
    } 

    public function __wakeup()
    { 
        var_dump(__METHOD__);
        $this->age++;
    }

    public function __sleep()
    {
        var_dump(__METHOD__);
        return ['name'];
    }

    public function serialize()
    {
        return serialize($this->name);
    } 

    public function unserialize($serialized)
    {       
        $this->name = unserialize($serialized);
        $this->age = 1;    
    }
}
$test = new Test;
$a = serialize($test);
var_dump($a);
var_dump(unserialize($a));
```

#### 6. Closure类

> 用于代表匿名函数的类，凡是匿名函数其实返回的都是Closure闭包类的一个实例，该类中主要有两个方法，bindTo（）和bind（），通过查看源码，可以发现两个方法是殊途同归，只不过是bind()是个静态方法，具体用法看如下；

```php
<?php
    $closure = function () {
        return 'hello world';
    }

    var_dump($closure);
    var_dump($closure());
```

通过上面的例子，可以看出第一个打印出来的是Closure的一个实例，而第二个就是打印出匿名函数返回的hello world字符串；接下来是使用这个匿名类的方法，这两个方法的目的都是把匿名函数绑定一个类上使用；

##### 1. bindTo()

```php
<?php
namespace demo1;
    class Test {
        private $name = 'hello woeld';
    }

    $closure = function () {
        return $this->name;
    };

    $func = $closure->bindTo(new Test);
    $func();
    // 这个是可以访问不到私有属性的，会报出无法访问私有属性
    // 下面这个是正确的做法
    $func = $closure->bindTo(new Test, Test::class);
    $func();

namespace demo2;
    class Test
    {
        private static $name = 'hello world';
    }

    $closure = function () {
        return self::$name;
    };
    $func = $closure->bindTo(null, Test::class);
    $func();
```

##### 2. bind()

```php
<?php
	namespace demo1;
    class Test 
    {
        private  $name = 'hello world';
    }

    $func = \Closure::bind(function() {
        return $this->name;
    }, new Test, Test::class);

    $func();

    namespace demo2;
    class Test 
    {
        private static  $name = 'hello world';
    }

    $func = \Closure::bind(function() {
        return self::$name;
    }, null, Test::class);

    $func()
```

#### 7. Generator（生成器）

> Generator实现了Iterator，但是他无法被继承，同时也生成实例。既然实现了Iterator，所以正如上文所介绍，他也就有了和Iterator相同的功能:rewind->valid->current->key->next...，Generator的语法主要来自于关键字yield。yield就好比一次循环的中转站，记录本次的活动轨迹，返回一个Generator的实例。Generator的优点在于，当我们要使用到大数据的遍历，或者说大文件的读写，而我们的内存不够的情况下，能够极大的减少我们对于内存的消耗，因为传统的遍历会返回所有的数据，这个数据存在内存上，而yield只会返回当前的值，不过当我们在使用yield时，其实其中会有一个处理记忆体的过程，所以实际上这是一个用时间换空间的办法。

```php
<?php
	$start_time = microtime(true);
    function xrange(int $num){
        for($i = 0; $i < $num; $i++) { 
            yield $i;    
        }
    }
    $generator = xrange(100000);
    foreach ($generator as $key => $value) { 
        echo $key . ': ' . $value . PHP_EOL;
    }
    echo 'memory: ' . memory_get_usage() . ' time: '. (microtime(true) - $start_time);
```

> 输出：memory: 388904 time: 0.12135100364685

```php
<?php
	$start_time = microtime(true);
    function xrange(int $num){
        $arr = [];    
        for($i = 0; $i < $num; $i++) { 
            array_push($arr, $i);
        } 
        return $arr;
    }
    $arr = xrange(100000);
    foreach ($arr as $key => $value) {
        echo $key . ': ' . $value . PHP_EOL;
    }
    echo 'memory: ' . memory_get_usage() . ' time: '. (microtime(true) - $start_time);
```

> 输出：memory: 6680312 time: 0.10804104804993