# PHP异常处理

### 一、异常与错误的区别

	###### PHP中的异常：

程序在运行中出现不符合预期的情况，允许发生（你也不想让他出现不正常的情况）但他是一种不正常的情况，按照我们的正常逻辑本不该出的错误，但仍然会出现的错误，属于逻辑和业务流程的错误，而不是编译或者语法上的错误。

###### PHP中的错误：

属于php脚本自身的问题，大部分情况是由错误的语法，服务器环境导致，使得编译器无法通过检查，甚至无法运行的情况。warning、notice都是错误，只是他们的级别不同而已，并且错误是**不能被try-catch捕获**的。

### 二、PHP中ERROR的级别

[参考文章](http://www.cnblogs.com/zyf-zhaoyafei/p/3649434.html)

1. `    Fatal Error:致命错误（脚本终止运行）`
2. `        E_ERROR         // 致命的运行错误，错误无法恢复，暂停执行脚本`
3. `        E_CORE_ERROR    // PHP启动时初始化过程中的致命错误`
4. `        E_COMPILE_ERROR // 编译时致命性错，就像由Zend脚本引擎生成了一个E_ERROR`
5. `        E_USER_ERROR    // 自定义错误消息。像用PHP函数trigger_error（错误类型设置为：E_USER_ERROR）`
6. ``
7. `    Parse Error：编译时解析错误，语法错误（脚本终止运行）`
8. `        E_PARSE  //编译时的语法解析错误`
9. ``
10. `    Warning Error：警告错误（仅给出提示信息，脚本不终止运行）`
11. `        E_WARNING         // 运行时警告 (非致命错误)。`
12. `        E_CORE_WARNING    // PHP初始化启动过程中发生的警告 (非致命错误) 。`
13. `        E_COMPILE_WARNING // 编译警告`
14. `        E_USER_WARNING    // 用户产生的警告信息`
15. ``
16. `    Notice Error：通知错误（仅给出通知信息，脚本不终止运行）`
17. `        E_NOTICE      // 运行时通知。表示脚本遇到可能会表现为错误的情况.`
18. `        E_USER_NOTICE // 用户产生的通知信息。`

　　由此可知有5类是产生ERROR级别的错误，这种错误直接导致PHP程序退出。可以定义成：

```php
ERROR = E_ERROR | E_CORE_ERROR |  E_COMPILE_ERROR | E_USER_ERROR | E_PARSE
```



框架中都会涉及三个函数：register_shutdown_function，set_error_handler，set_exception_handler