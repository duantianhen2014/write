# PHP的Ctype常用函数

1. [ctype_alnum](http://php.net/manual/zh/function.ctype-alnum.php) — 做字母和数字字符检测

    ctype_alnum ( string `$text` ) : bool

    检查提供的[string](http://php.net/manual/zh/language.types.string.php),`text` 是否全部为字母和(或)数字字符。

2. [ctype_alpha](http://php.net/manual/zh/function.ctype-alpha.php) — 做纯字符检测

    ctype_alpha ( string `$text` ) : bool

    查看提供的[string](http://php.net/manual/zh/language.types.string.php)，`text`里面的所有字符是否只包含字符。 在标准的 *C* 语言环境下，字母仅仅是指 *[A-Za-z]* ， **ctype_alpha()** 等同于*(ctype_upper($text) || ctype_lower($text))* 如果 `text` 是简单的单个字符串还好，但是在其他语言中有些字母被认为既不是大写也不是小写。

   ### 注释

   > **Note**:
   >
   > 如果给出一个 -128 到 255 之间(含)的整数, 将会被解释为该值对应的ASCII字符 (负值将加上 256 以支持扩展ASCII字符). 其它整数将会被解释为该值对应的十进制字符串.

3. [ctype_cntrl](http://php.net/manual/zh/function.ctype-cntrl.php) — 做控制字符检测

    ctype_cntrl ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是控制字符。 控制字符就是例如：换行、缩进、空格。

4. [ctype_digit](http://php.net/manual/zh/function.ctype-digit.php) — 做纯数字检测

    ctype_digit ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是数字。

    如果 `text` 字符串是一个十进制数字，就返回 **TRUE** ；反之就返回 **FALSE** 。

    注释

   > **Note**:
   >
   > 这个函数的参数要求是一个 [string](http://php.net/manual/zh/language.types.string.php) 这一点是非常有用的，因此当你传入一个 [integer](http://php.net/manual/zh/language.types.integer.php) 的参数也许不能得到期望的结果。然后，同样需要注意HTML表单将会返回数字字符串而不是一个整型。 看下手册的 [types](http://php.net/manual/zh/language.types.php) 章节。

   > **Note**:
   >
   > 如果给出一个 -128 到 255 之间(含)的整数, 将会被解释为该值对应的ASCII字符 (负值将加上 256 以支持扩展ASCII字符). 其它整数将会被解释为该值对应的十进制字符串.

5. [ctype_graph](http://php.net/manual/zh/function.ctype-graph.php) — 做可打印字符串检测，空格除外

    ctype_graph ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符输出都是可见的。

    如果 `text` 里面的每个字符都是输出可见的（没有空白），就返回 **TRUE** ；反之就返回 **FALSE** 。

6. [ctype_lower](http://php.net/manual/zh/function.ctype-lower.php) — 做小写字符检测

    ctype_lower ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是小写字母。

    如果在当前的语言环境下 `text` 里面的每个字符都是小写字母，就返回 **TRUE** ；反之就返回 **FALSE** 。

7. [ctype_print](http://php.net/manual/zh/function.ctype-print.php) — 做可打印字符检测

    ctype_print ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是可以打印出来。

    如果在当前的语言环境下 `text` 里面的每个字符都能被实际输出（包括空白），就返回 **TRUE** ；如果 `text` 里面包含控制字符或者那些根本不会有任何输出的字符串，就返回 **FALSE** 。

8. [ctype_punct](http://php.net/manual/zh/function.ctype-punct.php) — 检测可打印的字符是不是不包含空白、数字和字母

    ctype_punct ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是标点符号。

    如果在 `text` 里面的每个字符都是能打印的，但不是字母、数字，也不是空白，那么就返回 **TRUE** ；反之则返回 **FALSE** 。

9. [ctype_space](http://php.net/manual/zh/function.ctype-space.php) — 做空白字符检测

    ctype_space ( string `$text` ) : bool

    检查提供的 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是否包含空白。

    如果 `text` 里面的每个字符最终被实际输出的时候都是某种形式的空白，就返回 **TRUE** ；否则返回 **FALSE** 。 除了空白字符，还包括缩进，垂直制表符，换行符，回车和换页字符。

10. [ctype_upper](http://php.net/manual/zh/function.ctype-upper.php) — 做大写字母检测

     ctype_upper ( string `$text` ) : bool

     检查 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是大写字母。

     在当前语言环境下，如果 `text` 里面的每个字符都是大写字母，就返回 **TRUE**。

11. [ctype_xdigit](http://php.net/manual/zh/function.ctype-xdigit.php) — 检测字符串是否只包含十六进制字符

     ctype_xdigit ( string `$text` ) : bool

     检查 [string](http://php.net/manual/zh/language.types.string.php) 和 `text` 里面的字符是不是都是十六进制字符串。

     如果 `text` 里面的每个字符都是十六进制字符。也就是只能包含十进制的树枝和 *[A-Fa-f]* 的字母。否则，返回 **FALSE** 。