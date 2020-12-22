## 属性

### length

一个可读/写的整数，用来指明数组中的元素个数。当数组中的元素不连续时，length等于数组中最后一个元素的序号加一。改变length值会裁剪或扩充数组。

## 方法

### contact()

把元素衔接到数组中

#### 概要

`array.contact(value,...)`

#### 参数

`value,...`

任意个要衔接到array中的值

#### 返回值

一个新的数组，包含array的元素，以及衔接的新元素

#### 描述

concat()会将参数衔接到array中得到一个新数组并返回。它不会修改array。如果传给concat()的某个参数本身就是一个数组，则会将该数组的元素衔接到array中，而不是数组本身

#### 示例

```js
var a=[1,2,3];
a.contact(4,5);  //返回[1,2,3,4,5]
a.contact([4,5]) //返回[1,2,3,4,5]
a.contact([4,5],[6,7])  //返回[1,2,3,4,5,6,7]
a.contact(4,[5,[6,7]])  //返回[1,2,3,4,5,[6,7]]
```

### every()

测试断言函数是否对每个数组元素都为真

#### 概要

`array.every(predicate)`

`array.every(predicate,0)`

#### 参数

`predicate`

用来测试数组元素的断言函数

`o`

调用predicate时可选的this值

#### 返回值

如果对array的每一个元素调用predicate时都返回真值，则返回true。如果有任何一个元素调用predicate时返回假值，则返回false。

#### 描述

every()方法用来测试数组的所有元素是否都满足某些条件。他会按照序号从小到大的顺序遍历array中的元素，并对每个元素调用指定的predicate函数。如果predicate返回false（或者任何可以转化为false的值），则every()会停止遍历，并立刻返回false。如果predicate的每一个次调用都返回true，则every()返回true。当遍历的数组为空时，every()返回true。

对数组的每一个序号i，调用predicate时带有三个参数：

`predicate(array[i],i,array)`

predicate的返回值会当做布尔值解析。true和所有真值表示该数组元素通过了测试或者说满足该函数所描述的条件。如果返回值为false或假值，则表示数组元素没有通过测试。

#### 示例

```js
[1,2,3].every(function(x){return x<5;}) //=>true，所有元素都<5
[1,2,3].every(function(x){return x<3;}) //=>flase，不是所有元素都<3
[].every(function(x){return false;})    //=>true，[]总是返回true
```



### filter()

返回满足断言函数的数组元素

#### 概要

```js
every.filter(predicate)
every.filter(predicate,o)
```

#### 参数

`predicate`

用来判断array中的元素是否需要包含在返回数组中的调用函数。

`o`

调用predicate时可选的this值

#### 返回值

一个新数组，只包含那些让predicate返回真值的数组元素

#### 描述

filter()会创建一个新数组，包含那些让predicate函数返回真值的array的元素，filter方法不会修改array本身（注意predicate函数有可能会修改）

fileter()按照序号从小到大遍历array，对每个元素仅调用一次predicate，对于序号i，调用predicate时带有三个参数：

`predicate(array[i],i,array)`

如果predicate返回真值，则array中序号为i的元素会追加到新创建的数组中。一旦filter()测试完array中的每一个元素，他会返回新创建的数组

#### 示例

```js
[1,2,3].filter(function(x){return x>1;}) //=>[2,3]
```



### forEach()

为数组的每一个元素调用指定函数

### indexOf()

在数组中查找匹配元素

### join()

将数组所有元素转化为字符串，并衔接起来

### lastIndexOf()

在数组中反向查找