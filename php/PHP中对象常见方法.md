# PHP中对象常见方法

1. [__autoload](http://php.net/manual/zh/function.autoload.php) — 尝试加载未定义的类		Warning  This feature has been **DEPRECATED**

2. [call_user_method_array](http://php.net/manual/zh/function.call-user-method-array.php) — 以参数列表的数组，调用用户方法        Warning  This feature has been **DEPRECATED**

3. [call_user_method](http://php.net/manual/zh/function.call-user-method.php) — 对特定对象调用用户方法        Warning  This feature has been **DEPRECATED**

4. [class_alias](http://php.net/manual/zh/function.class-alias.php) — 为一个类创建别名

   class_alias ( string `$original` , string `$alias` [, bool `$autoload` = **TRUE** ] ) : bool

   ```
   original
   ```

   原有的类。

   ```
   alias
   ```

   类的别名。

   ```
   autoload
   ```

   如果原始类没有加载，是否使用自动加载（autoload）。

   **eg：**class_alias('foo', 'bar');

5. [class_exists](http://php.net/manual/zh/function.class-exists.php) — 检查类是否已定义

    class_exists ( string `$class_name` [, bool `$autoload` = true ] ) : bool

   ```
   class_name
   ```

   类名。名字的匹配是不分区大小写的。

   ```
   autoload
   ```

   是否默认调用 [__autoload](http://php.net/manual/zh/language.oop5.autoload.php)。

6. [get_called_class](http://php.net/manual/zh/function.get-called-class.php) — 后期静态绑定（"Late Static Binding"）类的名称

    get_called_class ( void ) : string

7. [get_class_methods](http://php.net/manual/zh/function.get-class-methods.php) — 返回由类的方法名组成的数组

    get_class_methods ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$class_name` ) : array

8. [get_class_vars](http://php.net/manual/zh/function.get-class-vars.php) — 返回由类的默认属性组成的数组

    get_class_vars ( string `$class_name` ) : array

9. [get_class](http://php.net/manual/zh/function.get-class.php) — 返回对象的类名

    返回对象实例 `object` 所属类的名字。

   ### 返回值

    返回对象实例 `object` 所属类的名字。 如果 `object` 不是一个对象则返回 **FALSE**。

    如果在一个类里，省略了参数 `object`， 则返回当前所在类的名称。

    如果 `object` 是命名空间中某个类的实例，（即：$baz = new \Foo\Bar\Baz;）则会返回带上命名空间的类名。



    如果用其他类型调用 **get_class()**，而不是一个对象的话，就会产生 **E_WARNING** 级别的错误。

10. [get_declared_classes](http://php.net/manual/zh/function.get-declared-classes.php) — 返回由已定义类的名字所组成的数组

     get_declared_classes ( void ) : array

     返回由当前脚本中已定义类的名字组成的数组。

11. [get_declared_interfaces](http://php.net/manual/zh/function.get-declared-interfaces.php) — 返回一个数组包含所有已声明的接口

     get_declared_interfaces ( void ) : array

     本函数返回一个数组，其内容是当前脚本中所有已声明的接口的名字。

12. [get_declared_traits](http://php.net/manual/zh/function.get-declared-traits.php) — 返回所有已定义的 traits 的数组

     get_declared_traits ( void ) : array

     返回一个数组，其值包含了所有已定义的 traits 的名称。 在失败的情况下返回 **NULL**。

13. [get_object_vars](http://php.net/manual/zh/function.get-object-vars.php) — 返回由对象属性组成的关联数组

     get_object_vars ( object `$obj` ) : array

     返回由 `obj` 指定的对象中定义的属性组成的关联数组。

    > **Note**:
    >
    > 在 PHP 4.2.0 之前的版本中，如果在 `obj` 对象实例中声明的变量没有被赋值，则它们将不会在返回的数组中。而在 PHP 4.2.0 之后，这些变量作为键名将被赋予 **NULL** 值。

14. [get_parent_class](http://php.net/manual/zh/function.get-parent-class.php) — 返回对象或类的父类名

     get_parent_class ([ [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$obj` ] ) : string

     如果 `obj` 是对象，则返回对象实例 `obj` 所属类的父类名。

    如果 `obj` 是字符串，则返回以此字符串为名的类的父类名。此功能是在 PHP 4.0.5 中增加的。

    > **Note**:
    >
    > 自 PHP 5 起，如果在对象的方法内调用，则 `obj` 为可选项。

15. [interface_exists](http://php.net/manual/zh/function.interface-exists.php) — 检查接口是否已被定义

     interface_exists ( string `$interface_name` [, bool `$autoload` = true ] ) : bool

     本函数在由 `interface_name` 给出的接口已定义时返回 **TRUE**，否则返回 **FALSE**。

16. [is_a](http://php.net/manual/zh/function.is-a.php) — 如果对象属于该类或该类是此对象的父类则返回 TRUE

     is_a ( object `$object` , string `$class_name` [, bool `$allow_string` = **FALSE** ] ) : bool

     如果 `object` 是该类或该类是此对象的父类。

17. [is_subclass_of](http://php.net/manual/zh/function.is-subclass-of.php) — 如果此对象是该类的子类，则返回 TRUE

     is_subclass_of ( object `$object` , string `$class_name` ) : bool

     如果对象 `object` 所属类是类 `class_name` 的子类，则返回 **TRUE**，否则返回 **FALSE**。

    > **Note**:
    >
    > 自 PHP 5.0.3 起也可以用一个字符串来指定 `object` 参数（类名）。

18. [method_exists](http://php.net/manual/zh/function.method-exists.php) — 检查类的方法是否存在

     method_exists ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$object` , string `$method_name` ) : bool

     检查类的方法是否存在于指定的 `object`中。

19. [property_exists](http://php.net/manual/zh/function.property-exists.php) — 检查对象或类是否具有该属性

     property_exists ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$class` , string `$property` ) : bool

     本函数检查给出的 `property` 是否存在于指定的类中（以及是否能在当前范围内访问）。

20. [trait_exists](http://php.net/manual/zh/function.trait-exists.php) — 检查指定的 trait 是否存在

     trait_exists ( string `$traitname` [, bool `$autoload` ] ) : bool