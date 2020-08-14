## PHP版本升级坑

PHP7 => PHP7.2

#### count函数

count(): Parameter must be an array or an object that implements Countable

或count()中变量如果不可Countable，直接报错

 兼容：count((array) $a); 采用类型限制