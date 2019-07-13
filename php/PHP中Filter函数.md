# PHP中Filter函数

#### 过滤器函数

1. [filter_has_var](http://php.net/manual/zh/function.filter-has-var.php) — 检测是否存在指定类型的变量

    filter_has_var ( int `$type` , string `$variable_name` ) : bool

   ```
   type
   ```

   **INPUT_GET**、 **INPUT_POST**、 **INPUT_COOKIE**、 **INPUT_SERVER**、 **INPUT_ENV** 里的其中一个。

   ```
   variable_name
   ```

   要检查的变量名。

   **eg：**

   ```php
   <?php
       $_GET['test'] = 1;
   	echo filter_has_var(INPUT_GET, 'test') ? 'Yes' : 'No';
   ```

2. [filter_id](http://php.net/manual/zh/function.filter-id.php) — 返回与某个特定名称的过滤器相关联的id

    filter_id ( string `$filtername` ) : int

   ```
   filtername
   ```

   待获取的过滤器名称

   如果获取成功则返回过滤器id，如果过滤器不存在则返回 **FALSE** 。

3. [filter_input_array](http://php.net/manual/zh/function.filter-input-array.php) — 获取一系列外部变量，并且可以通过过滤器处理它们

    filter_input_array ( int `$type` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$definition` [, bool `$add_empty` = true ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    这个函数当需要获取很多变量却不想重复调用[filter_input()](http://php.net/manual/zh/function.filter-input.php)时很有用。

   ```
   type
   ```

   **INPUT_GET**, **INPUT_POST**, **INPUT_COOKIE**, **INPUT_SERVER**, or **INPUT_ENV**之一。

   ```
   definition
   ```

   一个定义参数的数组。一个有效的键必须是一个包含变量名的[string](http://php.net/manual/zh/language.types.string.php)，一个有效的值要么是一个[filter type](http://php.net/manual/zh/filter.filters.php)，或者是一个[array](http://php.net/manual/zh/language.types.array.php) 指明了过滤器、标示和选项。如果值是一个数组，那么它的有效的键可以是 *filter*， 用于指明 [filter type](http://php.net/manual/zh/filter.filters.php)，*flags* 用于指明任何想要用于过滤器的标示，或者 *options* 用于指明任何想要用于过滤器的选项。 参考下面的例子来更好的理解这段说明。

   这个参数也可以是一个[filter constant](http://php.net/manual/zh/filter.constants.php)的整数。那么数组中的所有变量都会被这个过滤器所过滤。

   ```
   add_empty
   ```

   在返回值中添加 **NULL** 作为不存在的键。

   如果成功的话返回一个所请求的变量的数组，如果失败的话返回 **FALSE** 。对于数组的值，如果过滤失败则返回 **FALSE** ，如果`variable_name` 不存在的话则返回 **NULL** 。 如果标示 **FILTER_NULL_ON_FAILURE** 被使用了，那么当变量不存在时返回 **FALSE** ，当过滤失败时返回 **NULL** 。

4. [filter_input](http://php.net/manual/zh/function.filter-input.php) — 通过名称获取特定的外部变量，并且可以通过过滤器处理它

    filter_input ( int `$type` , string `$variable_name` [, int `$filter` = FILTER_DEFAULT [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$options` ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

   ```
   type
   ```

   **INPUT_GET**, **INPUT_POST**, **INPUT_COOKIE**, **INPUT_SERVER**或 **INPUT_ENV**之一。

   ```
   variable_name
   ```

   待获取的变量名。

   ```
   filter
   ```

   The ID of the filter to apply. The [Types of filters](http://php.net/manual/zh/filter.filters.php) manual page lists the available filters.

   If omitted, **FILTER_DEFAULT** will be used, which is equivalent to [**FILTER_UNSAFE_RAW**](http://php.net/manual/zh/filter.filters.sanitize.php). This will result in no filtering taking place by default.

   ```
   options
   ```

   一个选项的关联数组，或者按位区分的标示。如果过滤器接受选项，可以通过数组的 "flags" 位去提供这些标示。

   如果成功的话返回所请求的变量。如果过滤失败则返回 **FALSE** ，如果`variable_name` 不存在的话则返回 **NULL** 。 如果标示 **FILTER_NULL_ON_FAILURE** 被使用了，那么当变量不存在时返回 **FALSE** ，当过滤失败时返回 **NULL** 。

5. [filter_list](http://php.net/manual/zh/function.filter-list.php) — 返回所支持的过滤器列表

    filter_list ( void ) : array

    返回一个所支持的过滤器的名称的列表，如果没有这样子的过滤器的话则返回空数组。这个数组的索引不是过滤器id， 你可以通过 [filter_id()](http://php.net/manual/zh/function.filter-id.php) 去根据名称获取它们。

6. [filter_var_array](http://php.net/manual/zh/function.filter-var-array.php) — 获取多个变量并且过滤它们

    filter_var_array ( array `$data` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$definition` [, bool `$add_empty` = true ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    不需要重复调用 [filter_var()](http://php.net/manual/zh/function.filter-var.php) 就能获取多个变量。

   ```
   data
   ```

   数组，键为字符串，值为待过滤的数据。

   ```
   definition
   ```

   一个定义参数的数组。一个有效的键必须是一个包含变量名的[string](http://php.net/manual/zh/language.types.string.php)，一个有效的值要么是一个[filter type](http://php.net/manual/zh/filter.filters.php)，或者是一个[array](http://php.net/manual/zh/language.types.array.php) 指明了过滤器、标示和选项。如果值是一个数组，那么它的有效的键可以是 *filter*， 用于指明 [filter type](http://php.net/manual/zh/filter.filters.php)，*flags* 用于指明任何想要用于过滤器的标示，或者 *options* 用于指明任何想要用于过滤器的选项。 参考下面的例子来更好的理解这段说明。

   这个参数也可以是一个[filter constant](http://php.net/manual/zh/filter.constants.php)的整数。那么数组中的所有值都会被这个过滤器所过滤。

   ```
   add_empty
   ```

   在返回值中添加 **NULL** 作为不存在的键。

7. [filter_var](http://php.net/manual/zh/function.filter-var.php) — 使用特定的过滤器过滤一个变量

    filter_var ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$variable` [, int `$filter` = FILTER_DEFAULT [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$options` ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

   ```
   variable
   ```

   待过滤的变量。注意：标量的值在过滤前，会被[转换成字符串](http://php.net/manual/zh/language.types.string.php#language.types.string.casting)。

   ```
   filter
   ```

   The ID of the filter to apply. The [Types of filters](http://php.net/manual/zh/filter.filters.php) manual page lists the available filters.

   If omitted, **FILTER_DEFAULT** will be used, which is equivalent to [**FILTER_UNSAFE_RAW**](http://php.net/manual/zh/filter.filters.sanitize.php). This will result in no filtering taking place by default.

   ```
   options
   ```

   一个选项的关联数组，或者按位区分的标示。如果过滤器接受选项，可以通过数组的 "flags" 位去提供这些标示。 对于回调型的过滤器，应该传入 [callable](http://php.net/manual/zh/language.types.callable.php)。这个回调函数必须接受一个参数，即待过滤的值，并且 返回一个在过滤/净化后的值。