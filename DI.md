# IoC & Dependency Injection

*”控制反转”（Inversion ofControl，IoC）*

实现DI的三种方式：

 * 构造器注入 （**Constructor Injection**）
 * 设值注入 （**Setter Injection**）
 * 接口注入 （**Interface Injection**）

对于不使用DI的可以使用 **服务定位器** （**Service Locator**）,ServiceLocator最大的优点可能在于实现起来非常简单，如果您开发的应用没有复杂到需要采用一个IOC框架的程度，也许您可以试着采用它。 



老马[经典的文章](http://www.martinfowler.com/articles/injection.html)