# PHP中数组操作函数汇总

1. array_change_key_case — 改变数组中索引的大小写（对苏子索引无效）

    array_change_key_case(array $array [, int $case]) :array

    $case 可以在这里用两个常量，**CASE_UPPER** 或 **CASE_LOWER**（默认值）。

2. array_chunk — 对数组切分割成多个

    array_chunk(array $array, int $size [, bool `$preserve_keys` = false ]) : array

    $preserve_keys 是否保留数组的键，true保留 false不保留（数字索引）

3. array_column — 返回数组指定的一列

    array_column(array $array, mixed $column_key [, mixed $index = null ]) :array

    $index为返回的数组的键，若填写$array中的键，则该键对应的值变为返回数组的键；若填写的键是不存在的，则用数字索引（若使用对象为一个对象时，会取出它的属性，且属性值要为public修饰）

4. array_combine — 创建一个数组，一个数组的值为键，另一个数组的值为值

    array_combione(array $key, array $value) :array

    若两个数组的个数不一致，会报错（warring）PHP7.2

5. array_count_values — 统计数组中所有的值

    array_count_values(array $array) :array

    返回的数组中：键为数组中的值，值为出现的次数（要求原数组值或键须为string或integer，否则报warring）

6. array_diff_assoc — 带索引检查计算数组的差集

    array_diff_assoc(array $array1, array $array2 [, ... array]) :array

    返回一个数组，该数组包括了所有在 `array1` 中但是不在任何其它参数数组中的值。

    与array_diff相比，此函数同时对索引进行了比较

7. array_diff_key — 使用键名比较计算各数组的差集

    array_diff_key(array $array1, array $array2 [, ..array]) :array

   与array_diff相比，此函数仅对索引进行了比较，不对值进行比较

8. array_diff_uassoc — 用用户自定义函数带索引检查计算数组的差集

    array_diff_assoc(array $array1, array $array2[, ...array], callable $key_compare_func) :array

    与array_diff_assoc比多了一个参数（用户的自定义函数）

9. array_diff_ukey — 用回调函数对键名比较计算数组的差集

    array_diff_ukey ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$key_compare_func` ) : array

    与array_diff_key比多了一个参数（用户的自定义函数）

10. array_diff — 计算数组的差集

     array_diff ( array `$array1` , array `$array2` [, array `$...` ] ) : array

     对比 `array1` 和其他一个或者多个数组，返回在 `array1` 中但是不在其他 array 里的值。（仅对值进行比较）

11. array_fill_keys — 使用指定的键和值填充数组

     array_fill_keys ( array `$keys` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$value` ) : array

     使用 `value` 参数的值作为值，使用 `keys` 数组的值作为键来填充一个数组。

12. array_fill — 用给定的值填充数组

     array_fill ( int `$start_index` , int `$num` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$value` ) : array

     **array_fill()** 用 `value` 参数的值将一个数组填充 `num` 个条目，键名由 `start_index` 参数指定的开始。

13. array_fillter — 用回调函数来过滤数组中的单元

     array_fillter(array $array [, callable $callback[, int $flag = 0] ] ) :array

     依次将 `array` 数组中的每个值传递到 `callback` 函数。如果 `callback` 函数返回 true，则 `array` 数组的当前值会被包含在返回的结果数组中。数组的键名保留不变。

    ```
    flag
    ```

    决定`callback`接收的参数形式:

    - **ARRAY_FILTER_USE_KEY** - `callback`接受键名作为的唯一参数
    - **ARRAY_FILTER_USE_BOTH** - `callback`同时接受键名和键值

​       (即：use_key 能在回调函数中使用数组的键，use_both能在回掉函数中使用数组的键和值)

14. array_flip — 交换数组中的键和值

     array_flip ( array `$array` ) : array

15. array_intersect_assoc — 带索引和值进行计算各数组的**交集**

     array_intersect_assoc ( array `$array1` , array `$array2` [, array `$...` ] ) : array

16. array_intersect_key — 使用键名比较计算数组的交集

17. array_intersect_uassoc — 带索引检查计算数组的交集，用回调函数比较索引

18. array_intersect_ukey — 用回调函数比较键名来计算数组的交集

19. array_intersect — 计算数组的交集

20. array_key_exists — 检查数组里是否有指定的键名或索引

     array_key_exists ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$key` , array `$array` ) : bool

     数组里有键 `key` 时，**array_key_exists()** 返回 **TRUE**。 `key` 可以是任何能作为数组索引的值。

21. array_key_first — 获得数组的第一个键名或索引

     array_key_first ( array `$array` ) : mixed

22. array_key_last — 获得数组的最后一个键名或索引

     array_key_last ( array `$array` ) : mixed

23. array_keys — 返回数组中部分的或所有的键名

     array_keys ( array `$array` [, mixed `$search_value` = null [, bool `$strict` = false ]] ) : array

     **array_keys()** 返回 `input` 数组中的数字或者字符串的键名。

     如果指定了可选参数 `search_value`，则只返回该值的键名。否则 `input` 数组中的所有键名都会被返回。

    ```
    strict
    ```

    判断在搜索的时候是否该使用严格的比较（===）。

24. array_map — 为数组的每个元素应用回调函数

     array_map(callable $callback, array $array1 [, ...array]) :array

     **array_map()**：返回数组，是为 `array1` 每个元素应用 `callback`函数之后的数组。 `callback` 函数形参的数量和传给 **array_map()** 数组数量，两者必须一样。

25. array_merge_recursive — 递归地合并一个或多个数组

     array_merge_recursive(array $array1, [, ...array]) :array

     **array_merge_recursive()** 将一个或多个数组的单元合并起来，一个数组中的值**附加**在前一个数组的后面。返回作为结果的数组。

    如果输入的数组中有相同的字符串键名，则这些值会被合并到一个数组中去，这将递归下去，因此如果一个值本身是一个数组，本函数将按照相应的条目把它合并为另一个数组。需要注意的是，如果数组具有相同的数值键名，后一个值将不会覆盖原来的值，而是附加到后面。

    (键相同的均不会覆盖)

26. array_merge — 合并一个或多个数组

     array_merge ( array `$array1` [, array `$...` ] ) : array

     **array_merge()** 将一个或多个数组的单元合并起来，一个数组中的值附加在前一个数组的后面。返回作为结果的数组。

    如果输入的数组中有相同的字符串键名，则该键名后面的值将覆盖前一个值。然而，如果数组包含数字键名，后面的值将*不会*覆盖原来的值，而是附加到后面。

    如果只给了一个数组并且该数组是数字索引的，则键名会以连续方式重新索引。

27. array_multisort — 对多个数组或多维数组进行排序

     array_multisort ( array `&$array1` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$array1_sort_order` = SORT_ASC [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$array1_sort_flags` = SORT_REGULAR [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ]]] ) : bool

     **array_multisort()** 可以用来一次对多个数组进行排序，或者根据某一维或多维对多维数组进行排序。

    关联（[string](http://php.net/manual/zh/language.types.string.php)）键名保持不变，但数字键名会被重新索引。

    [即：根据对第一个array1的进行排序，对应着索引去排列后面的多个数组参数，**数组数量不相同时会报错**]

28. array_pad — 以指定长度将一个值填充进数组

     array_pad ( array `$array` , int `$size` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$value` ) : array

     **array_pad()** 返回 `array` 的一个拷贝，并用 `value` 将其填补到 `size` 指定的长度。如果 `size` 为正，则填补到数组的右侧，如果为负则从左侧开始填补。如果 `size` 的绝对值小于或等于 `array` 数组的长度则没有任何填补。有可能一次最多填补 1048576 个单元。

29. array_pop — 弹出数组最后一个单元（出栈）

     array_pop ( array `&$array` ) : mixed

     **array_pop()** 弹出并返回 `array` 数组的最后一个单元，并将数组 `array` 的长度减一。

     返回值是弹出的那个元素

    > **Note**: 使用此函数后会重置（[reset()](http://php.net/manual/zh/function.reset.php)）[array](http://php.net/manual/zh/language.types.array.php) 指针。

30. array_product — 计算数组中所有值的乘积

     array_producr(array $array) :number

     **array_product()** 以整数或浮点数返回一个数组中所有值的乘积。

31. array_push — 将一个或多个单元压入数组的末尾（入栈）

     array_push ( array `&$array` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$value1` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : int

     **array_push()** 将 `array` 当成一个栈，并将传入的变量压入 `array` 的末尾。`array` 的长度将根据入栈变量的数目增加。和如下效果相同：

    ```php
    <?php
    $array[] = $var;
    ?>
    ```

    并对每个传入的值重复以上动作。

    > **Note**: 如果用 **array_push()** 来给数组增加一个单元，还不如用 *$array[] =* ，因为这样没有调用函数的额外负担。

    > **Note**: 如果第一个参数不是数组，**array_push()** 将发出一条警告。这和 *$var[]* 的行为不同，后者会新建一个数组。

32. array_rand — 从数组中随机取出一个或多个单元

     array_rand ( array `$array` [, int `$num` = 1 ] ) : mixed

     从数组中取出一个或多个随机的单元，并返回随机条目的一个或多个键。 它使用了伪随机数产生算法，所以不适合密码学场景，

33. array_reduce — 用回调函数迭代地将数组简化为单一的值

     array_reduce ( array `$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` [, mixed `$initial` = **NULL** ] ) : mixed

     **array_reduce()** 将回调函数 `callback` 迭代地作用到 `array` 数组中的每一个单元中，从而将数组简化为单一的值。

    ```
    array
    ```

    输入的 array。

    ```
    callback
    ```

    callback ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$carry` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$item` ) : [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed)

    - `carry`

      携带上次迭代里的值； 如果本次迭代是第一次，那么这个值是 `initial`。

    - `item`

      携带了本次迭代的值。

    ```
    initial
    ```

    如果指定了可选参数 `initial`，该参数将在处理开始前使用，或者当处理结束，数组为空时的最后一个结果。

34. array_replace_recursive — 使用传递的数组递归替换第一个数组的元素

     array_replace_recursive ( array `$array1` [, array `$...` ] ) : array

     **array_replace_recursive()** 使用后面数组元素的值替换数组 `array1` 的值。 如果一个键存在于第一个数组同时也存在于第二个数组，它的值将被第二个数组中的值替换。 如果一个键存在于第二个数组，但是不存在于第一个数组，则会在第一个数组中创建这个元素。 如果一个键仅存在于第一个数组，它将保持不变。 如果传递了多个替换数组，它们将被按顺序依次处理，后面的数组将覆盖之前的值。

    **array_replace_recursive()** 是递归的：它将遍历数组并将相同的处理应用到数组的内部值。

    如果第一个数组中的值是标量，它的值将被第二个数组中的值替换，它可能是一个标量或者数组。如果第一个数组和第二个数组中的值都是数组，**array_replace_recursive()** 函数将递归地替换它们各自的值。

35. array_replace — 使用传递的数组替换第一个数组的元素

     array_replace ( array `$array1` [, array `$...` ] ) : array

     **array_replace()** 函数使用后面数组元素相同 key 的值替换 `array1` 数组的值。如果一个键存在于第一个数组同时也存在于第二个数组，它的值将被第二个数组中的值替换。如果一个键存在于第二个数组，但是不存在于第一个数组，则会在第一个数组中创建这个元素。如果一个键仅存在于第一个数组，它将保持不变。如果传递了多个替换数组，它们将被按顺序依次处理，后面的数组将覆盖之前的值。

    **array_replace()** 是非递归的：它将第一个数组的值进行替换而不管第二个数组中是什么类型。

36. array_reverse — 返回单元顺序相反的数组

     array_reverse ( array `$array` [, bool `$preserve_keys` = **FALSE** ] ) : array

     **array_reverse()** 接受数组 `array` 作为输入并返回一个单元为相反顺序的新数组。

    ```
    preserve_keys
    ```

    如果设置为 **TRUE** 会保留数字的键。 非数字的键则不受这个设置的影响，总是会被保留。

    （层级为一个层级，二维数组无用）

37. array_search — 在数组中搜索给定的值，如果成功则返回首个相应的键名

     array_search ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$needle` , array `$haystack` [, bool `$strict` = false ] ) : mixed

     大海捞针，在大海（`haystack`）中搜索针（ `needle` 参数）。

    ```
    strict
    ```

    如果可选的第三个参数 `strict` 为 **TRUE**，则 **array_search()** 将在 `haystack` 中检查*完全相同*的元素。 这意味着同样严格比较 `haystack`里 `needle` 的 [类型](http://php.net/manual/zh/language.types.php)，并且对象需是同一个实例。

38. array_shift — 将数组开头的单元移出数组

39. array_slice — 从数组中取出一段

     array_slice ( array `$array` , int `$offset` [, int `$length` = **NULL** [, bool `$preserve_keys` = false ]] ) : array

     **array_slice()** 返回根据 `offset` 和 `length` 参数所指定的 `array` 数组中的一段序列。

    ```php
    offset
    ```

    如果 `offset` 非负，则序列将从 `array` 中的此偏移量开始。如果 `offset` 为负，则序列将从 `array` 中距离末端这么远的地方开始。

    ```php
    length
    ```

    如果给出了 `length` 并且为正，则序列中将具有这么多的单元。如果给出了 `length` 并且为负，则序列将终止在距离数组末端这么远的地方。如果省略，则序列将从 `offset` 开始一直到 `array` 的末端。

    ```php
    preserve_keys
    ```

    注意 **array_slice()** 默认会重新排序并重置数组的数字索引。你可以通过将 `preserve_keys` 设为 **TRUE** 来改变此行为。

40. array_splice — 去掉数组中的某一部分并用其它值取代

     array_splice ( array `&$input` , int `$offset` [, int `$length` = count($input) [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$replacement` = array() ]] ) : array

    把 `input` 数组中由 `offset` 和 `length` 指定的单元去掉，如果提供了 `replacement` 参数，则用其中的单元取代。

    注意 `input` 中的数字键名不被保留。

    > **Note**: 如果 `replacement` 不是数组，会被 [类型转换](http://php.net/manual/zh/language.types.array.php#language.types.array.casting) 成数组 (例如： `(array) $replacement`)。 当传入的 `replacement` 是个对象或者 **NULL**，会导致未知的行为出现。

41. array_sum — 对数组中所有值求和

42. array_udiff_assoc — 带索引检查计算数组的差集，用回调函数比较数据

     array_udiff_assoc ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : array

    此比较是通过用户提供的回调函数来进行的。如果认为第一个参数小于，等于，或大于第二个参数时必须分别返回一个小于零，等于零，或大于零的整数。

43. array_udiff_uassoc — 带索引检查计算数组的差集，用回调函数比较数据和索引

     array_udiff_uassoc ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` , [callable](http://php.net/manual/zh/language.types.callable.php)`$key_compare_func` ) : array

    **array_udiff_uassoc()** 返回一个数组，该数组包括了所有在 `array1` 中但是不在任何其它参数数组中的值。

    注意和 [array_diff()](http://php.net/manual/zh/function.array-diff.php) 与 [array_udiff()](http://php.net/manual/zh/function.array-udiff.php) 不同的是键名也用于比较。

44. array_udiff — 用回调函数比较数据来计算数组的差集

     array_udiff ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : array

     使用回调函数比较数据，计算数组的不同之处。和 [array_diff()](http://php.net/manual/zh/function.array-diff.php) 不同的是，前者使用内置函数进行数据比较。

45. array_uintersect_assoc — 带索引检查计算数组的交集，用回调函数比较数据

     array_uintersect_assoc ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : array

    此比较是通过用户提供的回调函数来进行的。如果认为第一个参数小于，等于，或大于第二个参数时必须分别返回一个小于零，等于零，或大于零的整数。

    注意和 [array_uintersect()](http://php.net/manual/zh/function.array-uintersect.php) 不同的是键名也要比较。数据是用回调函数比较的。

46. array_uintersect_uassoc — 带索引检查计算数组的交集，用单独的回调函数比较数据和索引

     array_uintersect_uassoc ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` , [callable](http://php.net/manual/zh/language.types.callable.php)`$key_compare_func` ) : array

    通过额外的索引检查、回调函数比较数据和索引来返回多个数组的交集。

47. array_uintersect — 计算数组的交集，用回调函数比较数据

     array_uintersect ( array `$array1` , array `$array2` [, array `$...` ], [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : array

     **array_uintersect()** 返回一个数组，该数组包含了所有在 `array1` 中也同时出现在所有其它参数数组中的值。数据比较是用回调函数进行的。 此比较是通过用户提供的回调函数来进行的。如果认为第一个参数小于，等于，或大于第二个参数时必须分别返回一个小于零，等于零，或大于零的整数。

48. array_unique — 移除数组中重复的值

     array_unique ( array `$array` [, int `$sort_flags` = SORT_STRING ] ) : array

    **array_unique()** 接受 `array` 作为输入并返回没有重复值的新数组。

    注意键名保留不变。**array_unique()** 先将值作为字符串排序，然后对每个值只保留第一个遇到的键名，接着忽略所有后面的键名。这并不意味着在未排序的 `array` 中同一个值的第一个出现的键名会被保留。

    > **Note**: 当且仅当 *(string) $elem1 === (string) $elem2* 时两个单元被认为相同。 例如，字符串表达一样时，会使用首个元素。

    ```
    sort_flags
    ```

    第二个可选参数`sort_flags` 可用于修改排序行为：

    排序类型标记：

    - **SORT_REGULAR** - 按照通常方法比较（不修改类型）
    - **SORT_NUMERIC** - 按照数字形式比较
    - **SORT_STRING** - 按照字符串形式比较
    - **SORT_LOCALE_STRING** - 根据当前的本地化设置，按照字符串比较。

49. array_unshift — 在数组开头插入一个或多个单元

     array_unshift ( array `&$array` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : int

    **array_unshift()** 将传入的单元插入到 `array` 数组的开头。注意单元是作为整体被插入的，因此传入单元将保持同样的顺序。所有的数值键名将修改为从零开始重新计数，所有的文字键名保持不变。

50. array_values — 返回数组中所有的值

     array_values ( array `$array` ) : array

    **array_values()** 返回 `input` 数组中所有的值并给其建立数字索引。

51. array_walk_recursive — 对数组中的每个成员**递归**地应用用户函数

     array_walk_recursive ( array `&$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$userdata` = **NULL** ] ) : bool

     将用户自定义函数 `callback` 应用到 `array` 数组中的每个单元。本函数会递归到更深层的数组中去。

    ```
    array
    ```

    输入的数组。

    ```
    callback
    ```

    典型情况下 `callback` 接受两个参数。`array` 参数的值作为第一个，键名作为第二个。

    > **Note**:
    >
    > 如果 `callback` 需要直接作用于数组中的值，则给 `callback` 的第一个参数指定为[引用](http://php.net/manual/zh/language.references.php)。这样任何对这些单元的改变也将会改变原始数组本身。

    ```
    userdata
    ```

    如果提供了可选参数 `userdata`，将被作为第三个参数传递给 `callback`。

52. array_walk — 使用用户自定义函数对数组中的每个元素做回调处理

     array_walk ( array `&$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$callback` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$userdata` = **NULL** ] ) : bool

    将用户自定义函数 `funcname` 应用到 `array` 数组中的每个单元。

    **array_walk()** 不会受到 `array` 内部数组指针的影响。**array_walk()** 会**遍历**整个数组而不管指针的位置。

    ```
    array
    ```

    输入的数组。

    ```
    callback
    ```

    典型情况下 `callback` 接受两个参数。`array` 参数的值作为第一个，键名作为第二个。

    > **Note**:
    >
    > 如果 `callback` 需要直接作用于数组中的值，则给 `callback` 的第一个参数指定为[引用](http://php.net/manual/zh/language.references.php)。这样任何对这些单元的改变也将会改变原始数组本身。

    > **Note**:
    >
    > 参数数量超过预期，传入内置函数 (例如 [strtolower()](http://php.net/manual/zh/function.strtolower.php))， 将抛出警告，所以不适合当做 `funcname`。

    只有 `array` 的值才可以被改变，用户不应在回调函数中改变该数组本身的结构。例如增加/删除单元，unset 单元等等。如果 **array_walk()**作用的数组改变了，则此函数的的行为未经定义，且不可预期。

    ```
    userdata
    ```

    如果提供了可选参数 `userdata`，将被作为第三个参数传递给 callback `funcname`。

53. compact — 建立一个数组，包括变量名和它们的值

     compact ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$varname1` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : array

    创建一个包含变量与其值的数组。

    对每个参数，**compact()** 在当前的符号表中查找该变量名并将它添加到输出的数组中，变量名成为键名而变量的内容成为该键的值。简单说，它做的事和 [extract()](http://php.net/manual/zh/function.extract.php) 正好相反。返回将所有变量添加进去后的数组。

    > **Note**:
    >
    > 在 PHP 7.3 之前版本，未设置的字符串会被静默忽略。

    - `varname1`

      **compact()** 接受可变的参数数目。每个参数可以是一个包括变量名的字符串或者是一个包含变量名的数组，该数组中还可以包含其它单元内容为变量名的数组， **compact()** 可以递归处理。

54. in_array — 检查数组中是否存在某个值

     in_array ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$needle` , array `$haystack` [, bool `$strict` = **FALSE** ] ) : bool

     大海捞针，在大海（`haystack`）中搜索针（ `needle`），如果没有设置 `strict` 则使用宽松的比较。

    ```
    strict
    ```

    如果第三个参数 `strict` 的值为 **TRUE** 则 **in_array()** 函数还会检查 `needle` 的[类型](http://php.net/manual/zh/language.types.php)是否和 `haystack` 中的相同。

55. extract — 从数组中将变量导入到当前的符号表

     extract ( array `&$array` [, int `$flags` = EXTR_OVERWRITE [, string `$prefix` = **NULL** ]] ) : int

    本函数用来将变量从数组中导入到当前的符号表中。

    检查每个键名看是否可以作为一个合法的变量名，同时也检查和符号表中已有的变量名的冲突。

    - `array`

      一个关联数组。此函数会将键名当作变量名，值作为变量的值。 对每个键／值对都会在当前的符号表中建立变量，并受到 `flags` 和 `prefix` 参数的影响。必须使用关联数组，数字索引的数组将不会产生结果，除非用了 **EXTR_PREFIX_ALL** 或者 **EXTR_PREFIX_INVALID**。

    - `flags`

      对待非法／数字和冲突的键名的方法将根据取出标记 `flags` 参数决定。可以是以下值之一：**EXTR_OVERWRITE**如果有冲突，覆盖已有的变量。**EXTR_SKIP**如果有冲突，不覆盖已有的变量。**EXTR_PREFIX_SAME**如果有冲突，在变量名前加上前缀 `prefix`。**EXTR_PREFIX_ALL**给所有变量名加上前缀 `prefix`。**EXTR_PREFIX_INVALID**仅在非法／数字的变量名前加上前缀 `prefix`。**EXTR_IF_EXISTS**仅在当前符号表中已有同名变量时，覆盖它们的值。其它的都不处理。 举个例子，以下情况非常有用：定义一些有效变量，然后从 [$_REQUEST](http://php.net/manual/zh/reserved.variables.request.php) 中仅导入这些已定义的变量。**EXTR_PREFIX_IF_EXISTS**仅在当前符号表中已有同名变量时，建立附加了前缀的变量名，其它的都不处理。**EXTR_REFS**将变量作为引用提取。这有力地表明了导入的变量仍然引用了 `array` 参数的值。可以单独使用这个标志或者在 `flags` 中用 OR 与其它任何标志结合使用。如果没有指定 `flags`，则被假定为 **EXTR_OVERWRITE**。

    - `prefix`

      注意 `prefix` 仅在 `flags` 的值是 **EXTR_PREFIX_SAME**，**EXTR_PREFIX_ALL**，**EXTR_PREFIX_INVALID** 或 **EXTR_PREFIX_IF_EXISTS** 时需要。 如果附加了前缀后的结果不是合法的变量名，将不会导入到符号表中。前缀和数组键名之间会自动加上一个下划线。

56. key — 从关联数组中取得键名

     key(array $array) :mixed

    **key()** 函数返回数组中内部指针指向的当前单元的键名。 但它不会移动指针。如果内部指针超过了元素列表尾部，或者数组是空的，**key()** 会返回 **NULL**。

57. list — 把数组中的值赋给一组变量

     list ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var1` [, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$...` ] ) : array

    像 [array()](http://php.net/manual/zh/function.array.php) 一样，这不是真正的函数，而是语言结构。 **list()** 可以在单次操作内就为一组变量赋值。

    （批量赋值）

    ```php
    <?php
        $info = array('coffee', 'brown', 'caffeine');
    	list($drink, $color, $power) = $info;
    ```

58. natcasesort — 用“自然排序”算法对数组进行不区分大小写字母的排序

     natcasesort ( array `&$array` ) : bool

     **natcasesort()** 是 [natsort()](http://php.net/manual/zh/function.natsort.php) 函数的不区分大小写字母的版本。

    本函数实现了一个和人们通常对字母数字字符串进行排序的方法一样的排序算法并保持原有键／值的关联，这被称为“自然排序”。

    成功时返回 **TRUE**， 或者在失败时返回 **FALSE**。

59. natsort — 用“自然排序”算法对数组排序

     natsort ( array `&$array` ) : bool

     本函数实现了一个和人们通常对字母数字字符串进行排序的方法一样的排序算法并保持原有键／值的关联，这被称为“自然排序”。本算法和通常的计算机字符串排序算法（用于 [sort()](http://php.net/manual/zh/function.sort.php)）的区别见下面示例。

60. range — 根据范围创建数组，包含指定的元素

     range ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$start` , [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$end` [, [number](http://php.net/manual/zh/language.pseudo-types.php#language.types.number) `$step` = 1 ] ) : array

     建立一个包含指定范围单元的数组。

    ```
    start
    ```

    序列的第一个值。

    ```
    end
    ```

    序列结束于 `end` 的值。

    ```
    step
    ```

    如果设置了步长 `step`，会被作为单元之间的步进值。`step` 应该为正值。不设置`step` 则默认为 1。

61. shuffle — 打乱数组

     shuffle ( array `&$array` ) : bool

     本函数打乱（随机排列单元的顺序）一个数组。 它使用的是伪随机数产生器，并不适合密码学的场合。

62. uasort — 使用用户自定义的比较函数对数组中的值进行排序并保持索引关联

     uasort ( array `&$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : bool

     本函数对数组排序并保持索引和单元之间的关联。

     主要用于对那些单元顺序很重要的结合数组进行排序。比较函数是用户自定义的。

63. uksort — 使用用户自定义的比较函数对数组中的键名进行排序

     uksort ( array `&$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$key_compare_func` ) : bool

     **uksort()** 函数将使用用户提供的比较函数对数组中的键名进行排序。如果要排序的数组需要用一种不寻常的标准进行排序，那么应该使用此函数。

    ```
    key_compare_func
    ```

    在第一个参数小于，等于或大于第二个参数时，该比较函数必须相应地返回一个小于，等于或大于 0 的整数。

    callback ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$a`, [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$b` ) : int

64. usort — 使用用户自定义的比较函数对数组中的值进行排序

     usort ( array `&$array` , [callable](http://php.net/manual/zh/language.types.callable.php) `$value_compare_func` ) : bool

     本函数将用用户自定义的比较函数对一个数组中的值进行排序。 如果要排序的数组需要用一种不寻常的标准进行排序，那么应该使用此函数。

65. 