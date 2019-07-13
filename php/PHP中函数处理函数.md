# PHP中函数处理函数

1. [call_user_func_array](http://php.net/manual/zh/function.call-user-func-array.php) — 调用回调函数，并把一个数组参数作为回调函数的参数

    call_user_func_array ( [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` , array `$param_arr` ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    把第一个参数作为回调函数（`callback`）调用，把参数数组作（`param_arr`）为回调函数的的参数传入。

   ```
   callback
   ```

   被调用的回调函数。

   ```
   param_arr
   ```

   要被传入回调函数的数组，这个数组得是索引数组。

   **eg：**

   ```php
   <?PHP
       function foobar($arg, $arg2) {
           echo __FUNCTION__, " got $arg and $arg2\n";
       }
       class foo {
           function bar($arg, $arg2) {
               echo __METHOD__, " got $arg and $arg2\n";
           }
       }
   
   
       // Call the foobar() function with 2 arguments
       call_user_func_array("foobar", array("one", "two"));
   
       // Call the $foo->bar() method with 2 arguments
       $foo = new foo;
       call_user_func_array(array($foo, "bar"), array("three", "four"));
   ```

2. [call_user_func](http://php.net/manual/zh/function.call-user-func.php) — 把第一个参数作为回调函数调用

    call_user_func ( [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$parameter` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    第一个参数 `callback` 是被调用的回调函数，其余参数是回调函数的参数。

3. [create_function](http://php.net/manual/zh/function.create-function.php) — Create an anonymous (lambda-style) function

4. [forward_static_call_array](http://php.net/manual/zh/function.forward-static-call-array.php) — Call a static method and pass the arguments as array

    forward_static_call_array ( [callable](http://php.net/manual/zh/language.types.callable.php) `$function` , array `$parameters` ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

5. [forward_static_call](http://php.net/manual/zh/function.forward-static-call.php) — Call a static method

    forward_static_call ( [callable](http://php.net/manual/zh/language.types.callable.php) `$function` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$parameter` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ]] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

6. [func_get_arg](http://php.net/manual/zh/function.func-get-arg.php) — 返回参数列表的某一项

    func_get_arg ( int `$arg_num` ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    从用户自定义函数的参数列表中获取某个指定的参数。

   该函数可以配合 [func_get_args()](http://php.net/manual/zh/function.func-get-args.php) 和 [func_num_args()](http://php.net/manual/zh/function.func-num-args.php) 一起使用，从而使得用户自定义函数可以接受自定义个数的参数列表。

   ```
   arg_num
   ```

   参数的偏移量。函数的参数是从0开始计数的。

7. [func_get_args](http://php.net/manual/zh/function.func-get-args.php) — 返回一个包含函数参数列表的数组

    func_get_args ( void ) : array

    获取函数参数列表的数组。

   该函数可以配合 [func_get_arg()](http://php.net/manual/zh/function.func-get-arg.php) 和 [func_num_args()](http://php.net/manual/zh/function.func-num-args.php) 一起使用，从而使得用户自定义函数可以接受自定义个数的参数列表。

8. [func_num_args](http://php.net/manual/zh/function.func-num-args.php) — Returns the number of arguments passed to the function

    func_num_args ( void ) : int

9. [function_exists](http://php.net/manual/zh/function.function-exists.php) — 如果给定的函数已经被定义就返回 TRUE

    function_exists ( string `$function_name` ) : bool

    在已经定义的函数列表（包括系统自带的函数和用户自定义的函数）中查找 `function_name`。

   ```
   function_name
   ```

   函数名，必须为一个字符串。

10. [get_defined_functions](http://php.net/manual/zh/function.get-defined-functions.php) — 返回所有已定义函数的数组

     get_defined_functions ([ bool `$exclude_disabled` = **FALSE** ] ) : array

     获取所有已定义函数的数组。

    ```
    exclude_disabled
    ```

    禁用的函数是否应该在返回的数据里排除。



    返回数组，包含了所有已定义的函数，包括内置(internal) 和用户定义的函数。 可通过$arr["internal"]来访问系统内置函数， 通过$arr["user"]来访问用户自定义函数 (参见示例)。

11. [register_shutdown_function](http://php.net/manual/zh/function.register-shutdown-function.php) — 注册一个会在php中止时执行的函数

     register_shutdown_function ( [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$parameter` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ]] ) : void

     注册一个 `callback` ，它会在脚本执行完成或者 [exit()](http://php.net/manual/zh/function.exit.php) 后被调用。

    可以多次调用 **register_shutdown_function()** ，这些被注册的回调会按照他们注册时的顺序被依次调用。 如果你在注册的方法内部调用 [exit()](http://php.net/manual/zh/function.exit.php)， 那么所有处理会被中止，并且其他注册的中止回调也不会再被调用。

12. [register_tick_function](http://php.net/manual/zh/function.register-tick-function.php) — Register a function for execution on each tick

     register_tick_function ( [callable](http://php.net/manual/zh/language.types.callable.php) `$function` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$arg` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ]] ) : bool

     Registers the given `function` to be executed when a [tick](http://php.net/manual/zh/control-structures.declare.php#control-structures.declare.ticks) is called.

13. [unregister_tick_function](http://php.net/manual/zh/function.unregister-tick-function.php) — De-register a function for execution on each tick

     unregister_tick_function ( string `$function_name` ) : void

     De-registers the function named by `function_name` so it is no longer executed when a [tick](http://php.net/manual/zh/control-structures.declare.php) is called.

    **eg：**

    ```php
    <?php
    	declare(ticks = 1000);
        $startTime = microtime(true);
        $tick = true;
        $closure = function () use ($startTime, &$tick) {
            if (((microtime(true) - $startTime) > 5) && $tick) {
                $tick = false;
                throw new \Exception('Time to run code left');
            }
        };
    
        try {
                    register_tick_function($closure);
                    //do your code
                    $result = 1;
                    return $result;
                } catch (\Exception $e) {
                    throw $e;
                } finally {
                    unregister_tick_function($closure);
        }
    ```
