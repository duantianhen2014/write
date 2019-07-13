# PHP中variable handling函数

1. [boolval](http://php.net/manual/zh/function.boolval.php) — 获取变量的布尔值

    boolval ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : boolean

    返回`var`变量的布尔值 . 标量类型会被转化成布尔类型.

2. [debug_zval_dump](http://php.net/manual/zh/function.debug-zval-dump.php) — Dumps a string representation of an internal zend value to output

    debug_zval_dump ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$variable` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : void

    Dumps a string representation of an internal zend value to output.

   （打印出变量的zval机构）

3. [doubleval](http://php.net/manual/zh/function.doubleval.php) — floatval 的别名

4. [empty](http://php.net/manual/zh/function.empty.php) — 检查一个变量是否为空

    empty ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

    判断一个变量是否被认为是空的。当一个变量并不存在，或者它的值等同于**FALSE**，那么它会被认为不存在。如果变量不存在的话，**empty()**并不会产生警告。

   > **Note**:
   >
   > 在 PHP 5.5 之前，**empty()** 仅支持变量；任何其他东西将会导致一个解析错误。换言之，下列代码不会生效： **empty(trim($name))**。 作为替代，应该使用**trim($name) == false**.

   没有警告会产生，哪怕变量并不存在。 这意味着 **empty()** 本质上与 **!isset($var) || $var == false** 等价。

5. [floatval](http://php.net/manual/zh/function.floatval.php) — 获取变量的浮点值

    floatval ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : float

    返回变量 `var` 的 [float](http://php.net/manual/zh/language.types.float.php) 数值。

   `var` 可以是任何标量类型。你不能将 **floatval()** 用于数组或对象。

6. [get_defined_vars](http://php.net/manual/zh/function.get-defined-vars.php) — 返回由所有已定义变量所组成的数组

    get_defined_vars ( void ) : array

    此函数返回一个包含所有已定义变量列表的多维数组，这些变量包括环境变量、服务器变量和用户定义的变量。

7. [get_resource_type](http://php.net/manual/zh/function.get-resource-type.php) — 返回资源（resource）类型

    get_resource_type ( resource `$handle` ) : string

    此函数返回一个字符串，用于表示传递给它的 [resource](http://php.net/manual/zh/language.types.resource.php) 的类型。如果参数不是合法的 [resource](http://php.net/manual/zh/language.types.resource.php)，将产生错误。

8. [gettype](http://php.net/manual/zh/function.gettype.php) — 获取变量的类型  （推荐使用is_*函数进行检测）

9. [import_request_variables](http://php.net/manual/zh/function.import-request-variables.php) — 将 GET／POST／Cookie 变量导入到全局作用域中 (PHP 4 >= 4.1.0, PHP 5 < 5.4.0)  **Deprecated**

10. [intval](http://php.net/manual/zh/function.intval.php) — 获取变量的整数值

     intval ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` [, int `$base` = 10 ] ) : int

     通过使用指定的进制 `base` 转换（默认是十进制），返回变量 `var` 的 [integer](http://php.net/manual/zh/language.types.integer.php) 数值。 **intval()** 不能用于 object，否则会产生 **E_NOTICE** 错误并返回 1。

11. [is_array](http://php.net/manual/zh/function.is-array.php) — 检测变量是否是数组

     is_array ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是 [array](http://php.net/manual/zh/language.types.array.php)，则返回 **TRUE**，否则返回 **FALSE**。

12. [is_bool](http://php.net/manual/zh/function.is-bool.php) — 检测变量是否是布尔型

     is_bool ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是 [boolean](http://php.net/manual/zh/language.types.boolean.php) 则返回 **TRUE**。

13. [is_callable](http://php.net/manual/zh/function.is-callable.php) — 检测参数是否为合法的可调用结构

     is_callable ( [callable](http://php.net/manual/zh/language.types.callable.php) `$name` [, bool `$syntax_only` = false [, string `&$callable_name` ]] ) : bool

     验证变量的内容能否作为函数调用。 这可以检查包含有效函数名的变量，或者一个数组，包含了正确编码的对象以及函数名。

    ```
    name
    ```

    要检查的回调函数。

    ```
    syntax_only
    ```

    如果设置为 **TRUE**，这个函数仅仅验证 `name` 可能是函数或方法。 它仅仅拒绝非字符，或者未包含能用于回调函数的有效结构。有效的应该包含两个元素，第一个是一个对象或者字符，第二个元素是个字符。

    ```
    callable_name
    ```

    接受“可调用的名称”。下面的例子是“someClass::someMethod”。 注意，尽管 someClass::SomeMethod() 的含义是可调用的静态方法，但例子的情况并不是这样的。

14. [is_countable](http://php.net/manual/zh/function.is-countable.php) — Verify that the contents of a variable is a countable value

     is_countable ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     Verify that the contents of a variable is an [array](http://php.net/manual/zh/language.types.array.php) or an object implementing [Countable](http://php.net/manual/zh/class.countable.php)

15. [is_double](http://php.net/manual/zh/function.is-double.php) — is_float 的别名

16. [is_float](http://php.net/manual/zh/function.is-float.php) — 检测变量是否是浮点型

     is_float ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是 [float](http://php.net/manual/zh/language.types.float.php) 则返回 **TRUE**，否则返回 **FALSE**。

    > **Note**:
    >
    > 若想测试一个变量是否是数字或数字字符串（如表单输入，它们通常为字符串），必须使用 [is_numeric()](http://php.net/manual/zh/function.is-numeric.php)。

17. [is_int](http://php.net/manual/zh/function.is-int.php) — 检测变量是否是整数

     is_int ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是 [integer](http://php.net/manual/zh/language.types.integer.php) 则返回 **TRUE**，否则返回 **FALSE**。

18. [is_integer](http://php.net/manual/zh/function.is-integer.php) — is_int 的别名

19. [is_iterable](http://php.net/manual/zh/function.is-iterable.php) — Verify that the contents of a variable is an iterable value

     is_iterable ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     Verify that the contents of a variable is accepted by the [iterable](http://php.net/manual/zh/language.types.iterable.php) pseudo-type, i.e. that it is either an [array](http://php.net/manual/zh/language.types.array.php) or an object implementing **Traversable**

20. [is_long](http://php.net/manual/zh/function.is-long.php) — is_int 的别名

21. [is_null](http://php.net/manual/zh/function.is-null.php) — 检测变量是否为 NULL

     is_null ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是 [null](http://php.net/manual/zh/language.types.null.php) 则返回 **TRUE**，否则返回 **FALSE**。

    查看 [**NULL**](http://php.net/manual/zh/language.types.null.php#language.types.null.syntax) 类型获知变量什么时候被认为是 **NULL**，而什么时候不是。

    参见 [**NULL**](http://php.net/manual/zh/language.types.null.php#language.types.null.syntax)、[is_bool()](http://php.net/manual/zh/function.is-bool.php)、[is_numeric()](http://php.net/manual/zh/function.is-numeric.php)、[is_float()](http://php.net/manual/zh/function.is-float.php)、[is_int()](http://php.net/manual/zh/function.is-int.php)、[is_string()](http://php.net/manual/zh/function.is-string.php)、[is_object()](http://php.net/manual/zh/function.is-object.php)、[is_array()](http://php.net/manual/zh/function.is-array.php)、[is_integer()](http://php.net/manual/zh/function.is-integer.php) 和 [is_real()](http://php.net/manual/zh/function.is-real.php)。

22. [is_numeric](http://php.net/manual/zh/function.is-numeric.php) — 检测变量是否为数字或数字字符串

     is_numeric ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是数字和数字字符串则返回 **TRUE**，否则返回 **FALSE**。

23. [is_object](http://php.net/manual/zh/function.is-object.php) — 检测变量是否是一个对象

     is_object ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果 `var` 是一个 [object](http://php.net/manual/zh/language.types.object.php) 则返回 **TRUE**，否则返回 **FALSE**。

24. [is_real](http://php.net/manual/zh/function.is-real.php) — is_float 的别名

25. [is_resource](http://php.net/manual/zh/function.is-resource.php) — 检测变量是否为资源类型

     is_resource ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果给出的参数 `var` 是 [resource](http://php.net/manual/zh/language.types.resource.php) 类型，**is_resource()** 返回 **TRUE**，否则返回 **FALSE**。

26. [is_scalar](http://php.net/manual/zh/function.is-scalar.php) — 检测变量是否是一个标量

     is_scalar ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

     如果给出的变量参数 `var` 是一个标量，**is_scalar()** 返回 **TRUE**，否则返回 **FALSE**。

    标量变量是指那些包含了 [integer](http://php.net/manual/zh/language.types.integer.php)、[float](http://php.net/manual/zh/language.types.float.php)、[string](http://php.net/manual/zh/language.types.string.php) 或 [boolean](http://php.net/manual/zh/language.types.boolean.php)的变量，而 [array](http://php.net/manual/zh/language.types.array.php)、[object](http://php.net/manual/zh/language.types.object.php) 和 [resource](http://php.net/manual/zh/language.types.resource.php) 则不是标量。

27. [is_string](http://php.net/manual/zh/function.is-string.php) — 检测变量是否是字符串

     is_string ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

28. [isset](http://php.net/manual/zh/function.isset.php) — 检测变量是否已设置并且非 NULL

     isset ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : bool

     检测变量是否设置，并且不是 **NULL**。

    如果已经使用 [unset()](http://php.net/manual/zh/function.unset.php) 释放了一个变量之后，它将不再是 **isset()**。若使用 **isset()** 测试一个被设置成 **NULL** 的变量，将返回 **FALSE**。同时要注意的是 null 字符（*"\0"*）并不等同于 PHP 的 **NULL** 常量。

    如果一次传入多个参数，那么 **isset()** 只有在全部参数都以被设置时返回 **TRUE** 计算过程从左至右，中途遇到没有设置的变量时就会立即停止。

29. [print_r](http://php.net/manual/zh/function.print-r.php) — 以易于理解的格式打印变量。

     print_r ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$expression` [, bool `$return` = **FALSE** ] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

     **print_r()** 以人类易读的格式显示一个变量的信息。

    **print_r()**、 [var_dump()](http://php.net/manual/zh/function.var-dump.php)、 [var_export()](http://php.net/manual/zh/function.var-export.php) 都会显示对象 protected 和 private 的属性。 Class 的静态属性（static） 则不会显示。

30. [serialize](http://php.net/manual/zh/function.serialize.php) — 产生一个可存储的值的表示

     serialize ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$value` ) : string

     **serialize()** 返回字符串，此字符串包含了表示 `value` 的字节流，可以存储于任何地方。

    这有利于存储或传递 PHP 的值，同时不丢失其类型和结构。

    想要将已序列化的字符串变回 PHP 的值，可使用 [unserialize()](http://php.net/manual/zh/function.unserialize.php)。**serialize()** 可处理除了 [resource](http://php.net/manual/zh/language.types.resource.php) 之外的任何类型。甚至可以 **serialize()** 那些包含了指向其自身引用的数组。你正 **serialize()** 的数组／对象中的引用也将被存储。

    当序列化对象时，PHP 将试图在序列动作之前调用该对象的成员函数 **__sleep()**。这样就允许对象在被序列化之前做任何清除操作。类似的，当使用 [unserialize()](http://php.net/manual/zh/function.unserialize.php) 恢复对象时， 将调用 **__wakeup()** 成员函数。

    > **Note**:
    >
    > 在 PHP 3 中，对象属性将被序列化，但是方法则会丢失。PHP 4 打破了此限制，可以同时存储属性和方法。请参见[类与对象](http://php.net/manual/zh/language.oop5.php)中的[序列化对象](http://php.net/manual/zh/language.oop5.serialization.php)部分获取更多信息。

31. [settype](http://php.net/manual/zh/function.settype.php) — 设置变量的类型

     settype ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `&$var` , string `$type` ) : bool

     将变量 `var` 的类型设置成 `type`。

    ```
    var
    ```

    要转换的变量。

    ```
    type
    ```

    `type` 的可能值为：

    - “boolean” （或为“bool”，从 PHP 4.2.0 起）
    - “integer” （或为“int”，从 PHP 4.2.0 起）
    - “float” （只在 PHP 4.2.0 之后可以使用，对于旧版本中使用的“double”现已停用）
    - "string"
    - "array"
    - "object"
    - “null” （从 PHP 4.2.0 起）

32. [strval](http://php.net/manual/zh/function.strval.php) — 获取变量的字符串值

     strval ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : string

     返回 `var` 的 [string](http://php.net/manual/zh/language.types.string.php) 值。 参见 [string](http://php.net/manual/zh/language.types.string.php) 文档获取更多关于字符串转换的信息。

    `var` 可以是任何标量类型。不能将 **strval()** 用于数组或对象。

    参见 [floatval()](http://php.net/manual/zh/function.floatval.php)、[intval()](http://php.net/manual/zh/function.intval.php)、[settype()](http://php.net/manual/zh/function.settype.php) 和[类型戏法](http://php.net/manual/zh/language.types.type-juggling.php)。

33. [unserialize](http://php.net/manual/zh/function.unserialize.php) — 从已存储的表示中创建 PHP 的值

     unserialize ( string `$str` ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    **unserialize()** 对单一的已序列化的变量进行操作，将其转换回 PHP 的值。

    - `str`

      序列化后的字符串。若被解序列化的变量是一个对象，在成功地重新构造对象之后，PHP 会自动地试图去调用 [__wakeup()](http://php.net/manual/zh/language.oop5.magic.php#object.wakeup) 成员函数（如果存在的话）。**Note**: **unserialize_callback_func 指令** 如果在解序列化的时候需要实例化一个未定义类，则可以设置回调函数以供调用（以免得到的是不完整的 [object](http://php.net/manual/zh/language.types.object.php)“__PHP_Incomplete_Class”）。可通过 php.ini、[ini_set()](http://php.net/manual/zh/function.ini-set.php) 或 .htaccess 定义‘unserialize_callback_func’。每次实例化一个未定义类时它都会被调用。若要禁止这个特性，只需置空此设定。

    ### 返回值

    返回的是转换之后的值，可为 [integer](http://php.net/manual/zh/language.types.integer.php)、[float](http://php.net/manual/zh/language.types.float.php)、[string](http://php.net/manual/zh/language.types.string.php)、[array](http://php.net/manual/zh/language.types.array.php) 或 [object](http://php.net/manual/zh/language.types.object.php)。

    如果传递的字符串不可解序列化，则返回 **FALSE**，并产生一个 **E_NOTICE**。

34. [unset](http://php.net/manual/zh/function.unset.php) — 释放给定的变量

     unset ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : void

     **unset()** 销毁指定的变量。

    **unset()** 在函数中的行为会依赖于想要销毁的变量的类型而有所不同。

    如果在函数中 **unset()** 一个全局变量，则只是局部变量被销毁，而在调用环境中的变量将保持调用 **unset()** 之前一样的值。

35. [var_dump](http://php.net/manual/zh/function.var-dump.php) — 打印变量的相关信息

     var_dump ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$expression` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : void

     此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。

36. [var_export](http://php.net/manual/zh/function.var-export.php) — 输出或返回一个变量的字符串表示

     var_export ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$expression` [, bool `$return` ] ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    此函数返回关于传递给该函数的变量的结构信息，它和 [var_dump()](http://php.net/manual/zh/function.var-dump.php) 类似，不同的是其返回的表示是合法的 PHP 代码。

    您可以通过将函数的第二个参数设置为 **TRUE**，从而返回变量的表示。