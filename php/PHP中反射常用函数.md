# PHP中反射常用函数

PHP 5 具有完整的反射 API，添加了对类、接口、函数、方法和扩展进行*反向工程*的能力。 此外，反射 API 提供了方法来取出函数、类和方法中的文档注释。

请注意部分内部 API 丢失了反射扩展工作所需的代码。 例如，一个内置的 PHP 类可能丢失了反射属性的数据。这些少数的情况被认为是错误，不过， 正因为如此，它们应该被发现和修复。

**Example #1 Shell 里的一个反射例子（一个终端）**

```php
$ php --rf strlen
$ php --rc finfo
$ php --re json
$ php --ri dom
```



- ReflectionClass



  — ReflectionClass 类  **ReflectionClass** 类报告了一个类的有关信息。

  - [ReflectionClass::__construct](http://php.net/manual/zh/reflectionclass.construct.php) — 初始化 ReflectionClass 类

  - [ReflectionClass::export](http://php.net/manual/zh/reflectionclass.export.php) — 导出一个类

  - [ReflectionClass::getConstant](http://php.net/manual/zh/reflectionclass.getconstant.php) — 获取定义过的一个常量

  - [ReflectionClass::getConstants](http://php.net/manual/zh/reflectionclass.getconstants.php) — 获取一组常量

  - [ReflectionClass::getConstructor](http://php.net/manual/zh/reflectionclass.getconstructor.php) — 获取类的构造函数

  - [ReflectionClass::getDefaultProperties](http://php.net/manual/zh/reflectionclass.getdefaultproperties.php) — 获取默认属性

  - [ReflectionClass::getDocComment](http://php.net/manual/zh/reflectionclass.getdoccomment.php) — 获取文档注释

  - [ReflectionClass::getEndLine](http://php.net/manual/zh/reflectionclass.getendline.php) — 获取最后一行的行数

  - [ReflectionClass::getExtension](http://php.net/manual/zh/reflectionclass.getextension.php) — 根据已定义的类获取所在扩展的 ReflectionExtension 对象

  - [ReflectionClass::getExtensionName](http://php.net/manual/zh/reflectionclass.getextensionname.php) — 获取定义的类所在的扩展的名称

  - [ReflectionClass::getFileName](http://php.net/manual/zh/reflectionclass.getfilename.php) — 获取定义类的文件名

  - [ReflectionClass::getInterfaceNames](http://php.net/manual/zh/reflectionclass.getinterfacenames.php) — 获取接口（interface）名称

  - [ReflectionClass::getInterfaces](http://php.net/manual/zh/reflectionclass.getinterfaces.php) — 获取接口

  - [ReflectionClass::getMethod](http://php.net/manual/zh/reflectionclass.getmethod.php) — 获取一个类方法的 ReflectionMethod。

  - [ReflectionClass::getMethods](http://php.net/manual/zh/reflectionclass.getmethods.php) — 获取方法的数组

  - [ReflectionClass::getModifiers](http://php.net/manual/zh/reflectionclass.getmodifiers.php) — 获取类的修饰符

  - [ReflectionClass::getName](http://php.net/manual/zh/reflectionclass.getname.php) — 获取类名

  - [ReflectionClass::getNamespaceName](http://php.net/manual/zh/reflectionclass.getnamespacename.php) — 获取命名空间的名称

  - [ReflectionClass::getParentClass](http://php.net/manual/zh/reflectionclass.getparentclass.php) — 获取父类

  - [ReflectionClass::getProperties](http://php.net/manual/zh/reflectionclass.getproperties.php) — 获取一组属性

  - [ReflectionClass::getProperty](http://php.net/manual/zh/reflectionclass.getproperty.php) — 获取类的一个属性的 ReflectionProperty

  - [ReflectionClass::getReflectionConstant](http://php.net/manual/zh/reflectionclass.getreflectionconstant.php) — Gets a ReflectionClassConstant for a class's constant

  - [ReflectionClass::getReflectionConstants](http://php.net/manual/zh/reflectionclass.getreflectionconstants.php) — Gets class constants

  - [ReflectionClass::getShortName](http://php.net/manual/zh/reflectionclass.getshortname.php) — 获取短名

  - [ReflectionClass::getStartLine](http://php.net/manual/zh/reflectionclass.getstartline.php) — 获取起始行号

  - [ReflectionClass::getStaticProperties](http://php.net/manual/zh/reflectionclass.getstaticproperties.php) — 获取静态（static）属性

  - [ReflectionClass::getStaticPropertyValue](http://php.net/manual/zh/reflectionclass.getstaticpropertyvalue.php) — 获取静态（static）属性的值

  - [ReflectionClass::getTraitAliases](http://php.net/manual/zh/reflectionclass.gettraitaliases.php) — 返回 trait 别名的一个数组

  - [ReflectionClass::getTraitNames](http://php.net/manual/zh/reflectionclass.gettraitnames.php) — 返回这个类所使用 traits 的名称的数组

  - [ReflectionClass::getTraits](http://php.net/manual/zh/reflectionclass.gettraits.php) — 返回这个类所使用的 traits 数组

  - [ReflectionClass::hasConstant](http://php.net/manual/zh/reflectionclass.hasconstant.php) — 检查常量是否已经定义

  - [ReflectionClass::hasMethod](http://php.net/manual/zh/reflectionclass.hasmethod.php) — 检查方法是否已定义

  - [ReflectionClass::hasProperty](http://php.net/manual/zh/reflectionclass.hasproperty.php) — 检查属性是否已定义

  - [ReflectionClass::implementsInterface](http://php.net/manual/zh/reflectionclass.implementsinterface.php) — 接口的实现

  - [ReflectionClass::inNamespace](http://php.net/manual/zh/reflectionclass.innamespace.php) — 检查是否位于命名空间中

  - [ReflectionClass::isAbstract](http://php.net/manual/zh/reflectionclass.isabstract.php) — 检查类是否是抽象类（abstract）

  - [ReflectionClass::isAnonymous](http://php.net/manual/zh/reflectionclass.isanonymous.php) — 检查类是否是匿名类

  - [ReflectionClass::isCloneable](http://php.net/manual/zh/reflectionclass.iscloneable.php) — 返回了一个类是否可复制

  - [ReflectionClass::isFinal](http://php.net/manual/zh/reflectionclass.isfinal.php) — 检查类是否声明为 final

  - [ReflectionClass::isInstance](http://php.net/manual/zh/reflectionclass.isinstance.php) — 检查类的实例

  - [ReflectionClass::isInstantiable](http://php.net/manual/zh/reflectionclass.isinstantiable.php) — 检查类是否可实例化

  - [ReflectionClass::isInterface](http://php.net/manual/zh/reflectionclass.isinterface.php) — 检查类是否是一个接口（interface）

  - [ReflectionClass::isInternal](http://php.net/manual/zh/reflectionclass.isinternal.php) — 检查类是否由扩展或核心在内部定义

  - [ReflectionClass::isIterable](http://php.net/manual/zh/reflectionclass.isiterable.php) — Check whether this class is iterable

  - [ReflectionClass::isIterateable](http://php.net/manual/zh/reflectionclass.isiterateable.php) — 检查是否可迭代（iterateable）

  - [ReflectionClass::isSubclassOf](http://php.net/manual/zh/reflectionclass.issubclassof.php) — 检查是否为一个子类

  - [ReflectionClass::isTrait](http://php.net/manual/zh/reflectionclass.istrait.php) — 返回了是否为一个 trait

  - [ReflectionClass::isUserDefined](http://php.net/manual/zh/reflectionclass.isuserdefined.php) — 检查是否由用户定义的

  - [ReflectionClass::newInstance](http://php.net/manual/zh/reflectionclass.newinstance.php) — 从指定的参数创建一个新的类实例

  - [ReflectionClass::newInstanceArgs](http://php.net/manual/zh/reflectionclass.newinstanceargs.php) — 从给出的参数创建一个新的类实例。

  - [ReflectionClass::newInstanceWithoutConstructor](http://php.net/manual/zh/reflectionclass.newinstancewithoutconstructor.php) — 创建一个新的类实例而不调用它的构造函数

  - [ReflectionClass::setStaticPropertyValue](http://php.net/manual/zh/reflectionclass.setstaticpropertyvalue.php) — 设置静态属性的值

  - [ReflectionClass::__toString](http://php.net/manual/zh/reflectionclass.tostring.php) — 返回 ReflectionClass 对象字符串的表示形式。

- ReflectionClassConstant

   

  — The ReflectionClassConstant class

  - [ReflectionClassConstant::__construct](http://php.net/manual/zh/reflectionclassconstant.construct.php) — Constructs a ReflectionClassConstant

  - [ReflectionClassConstant::export](http://php.net/manual/zh/reflectionclassconstant.export.php) — Export

  - [ReflectionClassConstant::getDeclaringClass](http://php.net/manual/zh/reflectionclassconstant.getdeclaringclass.php) — Gets declaring class

  - [ReflectionClassConstant::getDocComment](http://php.net/manual/zh/reflectionclassconstant.getdoccomment.php) — Gets doc comments

  - [ReflectionClassConstant::getModifiers](http://php.net/manual/zh/reflectionclassconstant.getmodifiers.php) — Gets the class constant modifiers

  - [ReflectionClassConstant::getName](http://php.net/manual/zh/reflectionclassconstant.getname.php) — Get name of the constant

  - [ReflectionClassConstant::getValue](http://php.net/manual/zh/reflectionclassconstant.getvalue.php) — Gets value

  - [ReflectionClassConstant::isPrivate](http://php.net/manual/zh/reflectionclassconstant.isprivate.php) — Checks if class constant is private

  - [ReflectionClassConstant::isProtected](http://php.net/manual/zh/reflectionclassconstant.isprotected.php) — Checks if class constant is protected

  - [ReflectionClassConstant::isPublic](http://php.net/manual/zh/reflectionclassconstant.ispublic.php) — Checks if class constant is public

  - [ReflectionClassConstant::__toString](http://php.net/manual/zh/reflectionclassconstant.tostring.php) — Returns the string representation of the ReflectionClassConstant object

- ReflectionZendExtension

   

  — ReflectionZendExtension 类

  - [ReflectionZendExtension::__clone](http://php.net/manual/zh/reflectionzendextension.clone.php) — Clone handler

  - [ReflectionZendExtension::__construct](http://php.net/manual/zh/reflectionzendextension.construct.php) — Constructor

  - [ReflectionZendExtension::export](http://php.net/manual/zh/reflectionzendextension.export.php) — Export

  - [ReflectionZendExtension::getAuthor](http://php.net/manual/zh/reflectionzendextension.getauthor.php) — Gets author

  - [ReflectionZendExtension::getCopyright](http://php.net/manual/zh/reflectionzendextension.getcopyright.php) — Gets copyright

  - [ReflectionZendExtension::getName](http://php.net/manual/zh/reflectionzendextension.getname.php) — Gets name

  - [ReflectionZendExtension::getURL](http://php.net/manual/zh/reflectionzendextension.geturl.php) — Gets URL

  - [ReflectionZendExtension::getVersion](http://php.net/manual/zh/reflectionzendextension.getversion.php) — Gets version

  - [ReflectionZendExtension::__toString](http://php.net/manual/zh/reflectionzendextension.tostring.php) — To string handler

- ReflectionExtension

   

  — ReflectionExtension 类

  - [ReflectionExtension::__clone](http://php.net/manual/zh/reflectionextension.clone.php) — Clones

  - [ReflectionExtension::__construct](http://php.net/manual/zh/reflectionextension.construct.php) — Constructs a ReflectionExtension

  - [ReflectionExtension::export](http://php.net/manual/zh/reflectionextension.export.php) — Export

  - [ReflectionExtension::getClasses](http://php.net/manual/zh/reflectionextension.getclasses.php) — Gets classes

  - [ReflectionExtension::getClassNames](http://php.net/manual/zh/reflectionextension.getclassnames.php) — 获取类名称

  - [ReflectionExtension::getConstants](http://php.net/manual/zh/reflectionextension.getconstants.php) — 获取常量

  - [ReflectionExtension::getDependencies](http://php.net/manual/zh/reflectionextension.getdependencies.php) — 获取依赖

  - [ReflectionExtension::getFunctions](http://php.net/manual/zh/reflectionextension.getfunctions.php) — 获取扩展中的函数

  - [ReflectionExtension::getINIEntries](http://php.net/manual/zh/reflectionextension.getinientries.php) — 获取ini配置

  - [ReflectionExtension::getName](http://php.net/manual/zh/reflectionextension.getname.php) — 获取扩展名称

  - [ReflectionExtension::getVersion](http://php.net/manual/zh/reflectionextension.getversion.php) — 获取扩展版本号

  - [ReflectionExtension::info](http://php.net/manual/zh/reflectionextension.info.php) — 输出扩展信息

  - [ReflectionExtension::isPersistent](http://php.net/manual/zh/reflectionextension.ispersistent.php) — 返回扩展是否持久化载入

  - [ReflectionExtension::isTemporary](http://php.net/manual/zh/reflectionextension.istemporary.php) — 返回扩展是否是临时载入

  - [ReflectionExtension::__toString](http://php.net/manual/zh/reflectionextension.tostring.php) — To string

- ReflectionFunction

   

  — ReflectionFunction 类

  - [ReflectionFunction::__construct](http://php.net/manual/zh/reflectionfunction.construct.php) — Constructs a ReflectionFunction object

  - [ReflectionFunction::export](http://php.net/manual/zh/reflectionfunction.export.php) — Exports function

  - [ReflectionFunction::getClosure](http://php.net/manual/zh/reflectionfunction.getclosure.php) — Returns a dynamically created closure for the function

  - [ReflectionFunction::invoke](http://php.net/manual/zh/reflectionfunction.invoke.php) — Invokes function

  - [ReflectionFunction::invokeArgs](http://php.net/manual/zh/reflectionfunction.invokeargs.php) — Invokes function args

  - [ReflectionFunction::isDisabled](http://php.net/manual/zh/reflectionfunction.isdisabled.php) — Checks if function is disabled

  - [ReflectionFunction::__toString](http://php.net/manual/zh/reflectionfunction.tostring.php) — To string

- ReflectionFunctionAbstract

   

  — ReflectionFunctionAbstract 类

  - [ReflectionFunctionAbstract::__clone](http://php.net/manual/zh/reflectionfunctionabstract.clone.php) — 复制函数

  - [ReflectionFunctionAbstract::getClosureScopeClass](http://php.net/manual/zh/reflectionfunctionabstract.getclosurescopeclass.php) — Returns the scope associated to the closure

  - [ReflectionFunctionAbstract::getClosureThis](http://php.net/manual/zh/reflectionfunctionabstract.getclosurethis.php) — 返回本身的匿名函数

  - [ReflectionFunctionAbstract::getDocComment](http://php.net/manual/zh/reflectionfunctionabstract.getdoccomment.php) — 获取注释内容

  - [ReflectionFunctionAbstract::getEndLine](http://php.net/manual/zh/reflectionfunctionabstract.getendline.php) — 获取结束行号

  - [ReflectionFunctionAbstract::getExtension](http://php.net/manual/zh/reflectionfunctionabstract.getextension.php) — 获取扩展信息

  - [ReflectionFunctionAbstract::getExtensionName](http://php.net/manual/zh/reflectionfunctionabstract.getextensionname.php) — 获取扩展名称

  - [ReflectionFunctionAbstract::getFileName](http://php.net/manual/zh/reflectionfunctionabstract.getfilename.php) — 获取文件名称

  - [ReflectionFunctionAbstract::getName](http://php.net/manual/zh/reflectionfunctionabstract.getname.php) — 获取函数名称

  - [ReflectionFunctionAbstract::getNamespaceName](http://php.net/manual/zh/reflectionfunctionabstract.getnamespacename.php) — 获取命名空间

  - [ReflectionFunctionAbstract::getNumberOfParameters](http://php.net/manual/zh/reflectionfunctionabstract.getnumberofparameters.php) — 获取参数数目

  - [ReflectionFunctionAbstract::getNumberOfRequiredParameters](http://php.net/manual/zh/reflectionfunctionabstract.getnumberofrequiredparameters.php) — 获取必须输入参数个数

  - [ReflectionFunctionAbstract::getParameters](http://php.net/manual/zh/reflectionfunctionabstract.getparameters.php) — 获取参数

  - [ReflectionFunctionAbstract::getReturnType](http://php.net/manual/zh/reflectionfunctionabstract.getreturntype.php) — Gets the specified return type of a function

  - [ReflectionFunctionAbstract::getShortName](http://php.net/manual/zh/reflectionfunctionabstract.getshortname.php) — 获取函数短名称

  - [ReflectionFunctionAbstract::getStartLine](http://php.net/manual/zh/reflectionfunctionabstract.getstartline.php) — 获取开始行号

  - [ReflectionFunctionAbstract::getStaticVariables](http://php.net/manual/zh/reflectionfunctionabstract.getstaticvariables.php) — 获取静态变量

  - [ReflectionFunctionAbstract::hasReturnType](http://php.net/manual/zh/reflectionfunctionabstract.hasreturntype.php) — Checks if the function has a specified return type

  - [ReflectionFunctionAbstract::inNamespace](http://php.net/manual/zh/reflectionfunctionabstract.innamespace.php) — 检查是否处于命名空间

  - [ReflectionFunctionAbstract::isClosure](http://php.net/manual/zh/reflectionfunctionabstract.isclosure.php) — 检查是否是匿名函数

  - [ReflectionFunctionAbstract::isDeprecated](http://php.net/manual/zh/reflectionfunctionabstract.isdeprecated.php) — 检查是否已经弃用

  - [ReflectionFunctionAbstract::isGenerator](http://php.net/manual/zh/reflectionfunctionabstract.isgenerator.php) — 判断函数是否是一个生成器函数

  - [ReflectionFunctionAbstract::isInternal](http://php.net/manual/zh/reflectionfunctionabstract.isinternal.php) — 判断函数是否是内置函数

  - [ReflectionFunctionAbstract::isUserDefined](http://php.net/manual/zh/reflectionfunctionabstract.isuserdefined.php) — 检查是否是用户定义

  - [ReflectionFunctionAbstract::isVariadic](http://php.net/manual/zh/reflectionfunctionabstract.isvariadic.php) — Checks if the function is variadic

  - [ReflectionFunctionAbstract::returnsReference](http://php.net/manual/zh/reflectionfunctionabstract.returnsreference.php) — 检查是否返回参考信息

  - [ReflectionFunctionAbstract::__toString](http://php.net/manual/zh/reflectionfunctionabstract.tostring.php) — 字符串化

- ReflectionMethod

   

  — ReflectionMethod 类

  - [ReflectionMethod::__construct](http://php.net/manual/zh/reflectionmethod.construct.php) — ReflectionMethod 的构造函数

  - [ReflectionMethod::export](http://php.net/manual/zh/reflectionmethod.export.php) — 输出一个回调方法

  - [ReflectionMethod::getClosure](http://php.net/manual/zh/reflectionmethod.getclosure.php) — 返回一个动态建立的方法调用接口，译者注：可以使用这个返回值直接调用非公开方法。

  - [ReflectionMethod::getDeclaringClass](http://php.net/manual/zh/reflectionmethod.getdeclaringclass.php) — 获取反射函数调用参数的类表达

  - [ReflectionMethod::getModifiers](http://php.net/manual/zh/reflectionmethod.getmodifiers.php) — 获取方法的修饰符

  - [ReflectionMethod::getPrototype](http://php.net/manual/zh/reflectionmethod.getprototype.php) — 返回方法原型 (如果存在)

  - [ReflectionMethod::invoke](http://php.net/manual/zh/reflectionmethod.invoke.php) — Invoke

  - [ReflectionMethod::invokeArgs](http://php.net/manual/zh/reflectionmethod.invokeargs.php) — 带参数执行

  - [ReflectionMethod::isAbstract](http://php.net/manual/zh/reflectionmethod.isabstract.php) — 判断方法是否是抽象方法

  - [ReflectionMethod::isConstructor](http://php.net/manual/zh/reflectionmethod.isconstructor.php) — 判断方法是否是构造方法

  - [ReflectionMethod::isDestructor](http://php.net/manual/zh/reflectionmethod.isdestructor.php) — 判断方法是否是析构方法

  - [ReflectionMethod::isFinal](http://php.net/manual/zh/reflectionmethod.isfinal.php) — 判断方法是否定义 final

  - [ReflectionMethod::isPrivate](http://php.net/manual/zh/reflectionmethod.isprivate.php) — 判断方法是否是私有方法

  - [ReflectionMethod::isProtected](http://php.net/manual/zh/reflectionmethod.isprotected.php) — 判断方法是否是保护方法 (protected)

  - [ReflectionMethod::isPublic](http://php.net/manual/zh/reflectionmethod.ispublic.php) — 判断方法是否是公开方法

  - [ReflectionMethod::isStatic](http://php.net/manual/zh/reflectionmethod.isstatic.php) — 判断方法是否是静态方法

  - [ReflectionMethod::setAccessible](http://php.net/manual/zh/reflectionmethod.setaccessible.php) — 设置方法是否访问

  - [ReflectionMethod::__toString](http://php.net/manual/zh/reflectionmethod.tostring.php) — 返回反射方法对象的字符串表达

- ReflectionObject

   

  — ReflectionObject 类

  - [ReflectionObject::__construct](http://php.net/manual/zh/reflectionobject.construct.php) — Constructs a ReflectionObject

  - [ReflectionObject::export](http://php.net/manual/zh/reflectionobject.export.php) — Export

- ReflectionParameter

   

  — ReflectionParameter 类

  - [ReflectionParameter::allowsNull](http://php.net/manual/zh/reflectionparameter.allowsnull.php) — Checks if null is allowed

  - [ReflectionParameter::canBePassedByValue](http://php.net/manual/zh/reflectionparameter.canbepassedbyvalue.php) — Returns whether this parameter can be passed by value

  - [ReflectionParameter::__clone](http://php.net/manual/zh/reflectionparameter.clone.php) — Clone

  - [ReflectionParameter::__construct](http://php.net/manual/zh/reflectionparameter.construct.php) — Construct

  - [ReflectionParameter::export](http://php.net/manual/zh/reflectionparameter.export.php) — Exports

  - [ReflectionParameter::getClass](http://php.net/manual/zh/reflectionparameter.getclass.php) — 获得类型提示类。

  - [ReflectionParameter::getDeclaringClass](http://php.net/manual/zh/reflectionparameter.getdeclaringclass.php) — Gets declaring class

  - [ReflectionParameter::getDeclaringFunction](http://php.net/manual/zh/reflectionparameter.getdeclaringfunction.php) — Gets declaring function

  - [ReflectionParameter::getDefaultValue](http://php.net/manual/zh/reflectionparameter.getdefaultvalue.php) — Gets default parameter value

  - [ReflectionParameter::getDefaultValueConstantName](http://php.net/manual/zh/reflectionparameter.getdefaultvalueconstantname.php) — Returns the default value's constant name if default value is constant or null

  - [ReflectionParameter::getName](http://php.net/manual/zh/reflectionparameter.getname.php) — Gets parameter name

  - [ReflectionParameter::getPosition](http://php.net/manual/zh/reflectionparameter.getposition.php) — Gets parameter position

  - [ReflectionParameter::getType](http://php.net/manual/zh/reflectionparameter.gettype.php) — Gets a parameter's type

  - [ReflectionParameter::hasType](http://php.net/manual/zh/reflectionparameter.hastype.php) — Checks if parameter has a type

  - [ReflectionParameter::isArray](http://php.net/manual/zh/reflectionparameter.isarray.php) — Checks if parameter expects an array

  - [ReflectionParameter::isCallable](http://php.net/manual/zh/reflectionparameter.iscallable.php) — Returns whether parameter MUST be callable

  - [ReflectionParameter::isDefaultValueAvailable](http://php.net/manual/zh/reflectionparameter.isdefaultvalueavailable.php) — 检查是否有默认值。

  - [ReflectionParameter::isDefaultValueConstant](http://php.net/manual/zh/reflectionparameter.isdefaultvalueconstant.php) — Returns whether the default value of this parameter is a constant

  - [ReflectionParameter::isOptional](http://php.net/manual/zh/reflectionparameter.isoptional.php) — Checks if optional

  - [ReflectionParameter::isPassedByReference](http://php.net/manual/zh/reflectionparameter.ispassedbyreference.php) — Checks if passed by reference

  - [ReflectionParameter::isVariadic](http://php.net/manual/zh/reflectionparameter.isvariadic.php) — Checks if the parameter is variadic

  - [ReflectionParameter::__toString](http://php.net/manual/zh/reflectionparameter.tostring.php) — To string

- ReflectionProperty

   

  — ReflectionProperty 类

  - [ReflectionProperty::__clone](http://php.net/manual/zh/reflectionproperty.clone.php) — Clone

  - [ReflectionProperty::__construct](http://php.net/manual/zh/reflectionproperty.construct.php) — Construct a ReflectionProperty object

  - [ReflectionProperty::export](http://php.net/manual/zh/reflectionproperty.export.php) — Export

  - [ReflectionProperty::getDeclaringClass](http://php.net/manual/zh/reflectionproperty.getdeclaringclass.php) — Gets declaring class

  - [ReflectionProperty::getDocComment](http://php.net/manual/zh/reflectionproperty.getdoccomment.php) — Gets the property doc comment

  - [ReflectionProperty::getModifiers](http://php.net/manual/zh/reflectionproperty.getmodifiers.php) — Gets the property modifiers

  - [ReflectionProperty::getName](http://php.net/manual/zh/reflectionproperty.getname.php) — Gets property name

  - [ReflectionProperty::getValue](http://php.net/manual/zh/reflectionproperty.getvalue.php) — Gets value

  - [ReflectionProperty::isDefault](http://php.net/manual/zh/reflectionproperty.isdefault.php) — Checks if property is a default property

  - [ReflectionProperty::isPrivate](http://php.net/manual/zh/reflectionproperty.isprivate.php) — Checks if property is private

  - [ReflectionProperty::isProtected](http://php.net/manual/zh/reflectionproperty.isprotected.php) — Checks if property is protected

  - [ReflectionProperty::isPublic](http://php.net/manual/zh/reflectionproperty.ispublic.php) — Checks if property is public

  - [ReflectionProperty::isStatic](http://php.net/manual/zh/reflectionproperty.isstatic.php) — Checks if property is static

  - [ReflectionProperty::setAccessible](http://php.net/manual/zh/reflectionproperty.setaccessible.php) — Set property accessibility

  - [ReflectionProperty::setValue](http://php.net/manual/zh/reflectionproperty.setvalue.php) — Set property value

  - [ReflectionProperty::__toString](http://php.net/manual/zh/reflectionproperty.tostring.php) — To string

- ReflectionType

   

  — The ReflectionType class

  - [ReflectionType::allowsNull](http://php.net/manual/zh/reflectiontype.allowsnull.php) — Checks if null is allowed

  - [ReflectionType::isBuiltin](http://php.net/manual/zh/reflectiontype.isbuiltin.php) — Checks if it is a built-in type

  - [ReflectionType::__toString](http://php.net/manual/zh/reflectiontype.tostring.php) — To string

- ReflectionGenerator

   

  — 生成器反射类

  - [ReflectionGenerator::__construct](http://php.net/manual/zh/reflectiongenerator.construct.php) — Constructs a ReflectionGenerator object

  - [ReflectionGenerator::getExecutingFile](http://php.net/manual/zh/reflectiongenerator.getexecutingfile.php) — Gets the file name of the currently executing generator

  - [ReflectionGenerator::getExecutingGenerator](http://php.net/manual/zh/reflectiongenerator.getexecutinggenerator.php) — Gets the executing Generator object

  - [ReflectionGenerator::getExecutingLine](http://php.net/manual/zh/reflectiongenerator.getexecutingline.php) — Gets the currently executing line of the generator

  - [ReflectionGenerator::getFunction](http://php.net/manual/zh/reflectiongenerator.getfunction.php) — Gets the function name of the generator

  - [ReflectionGenerator::getThis](http://php.net/manual/zh/reflectiongenerator.getthis.php) — Gets the $this value of the generator

  - [ReflectionGenerator::getTrace](http://php.net/manual/zh/reflectiongenerator.gettrace.php) — Gets the trace of the executing generator

- Reflector

   

  — Reflector 接口

  - [Reflector::export](http://php.net/manual/zh/reflector.export.php) — Exports

  - [Reflector::__toString](http://php.net/manual/zh/reflector.tostring.php) — 转化成字符串

- [ReflectionException](http://php.net/manual/zh/class.reflectionexception.php) — ReflectionException 类