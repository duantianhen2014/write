# window server系统下PHP环境安装说明

## 总结

**On IIS 6**

- PHP 5.4
- VC9 [x86](http://www.microsoft.com/en-us/download/details.aspx?id=5582) or [x64](http://www.microsoft.com/en-us/download/details.aspx?id=15336)
- [WinCache 1.3 for PHP 5.4](http://go.microsoft.com/fwlink/?LinkId=259761)

**On IIS 7**

- PHP 5.5
- VC11 [x86 or x64](http://www.microsoft.com/en-us/download/details.aspx?id=30679)
- [WinCache 1.3 for PHP 5.5](http://go.microsoft.com/fwlink/?LinkId=323603)



一般在windows server 2003系统中标配IIS6，所以最高安装PHP5.4，不要忘记安装VC9库，强行安装PHP5.5及高版本，会报 `1%不是有效的win32应用程序解决`错误