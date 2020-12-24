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

#### 概要

```js
array.forEach(f)
array.forEach(f,o)
```

#### 参数

f

为array的每一个元素调用的函数

o

调用f时可选的this值

#### 返回值

该方法无返回值

#### 描述

forEach()按照序号从小到大遍历array，并对每一个元素调用一次f。对于序号i，调用f时带有三个参数：

f(array[i],i,array)

f的任何返回值都会忽略。注意forEach()没有返回值。特别注意，它不会返回array。

#### 数组方法的细节

下述细节适用于forEach()方法，也适用于相关方法：map()、filter()、every()和some()。

所有这些方法都接受函数作为第一个参数，并接受可选的第二个参数。如果指定了第二个参数o，则调用函数时，就好像该函数是o的方法一样。也就是说，在函数体内，this值等于o。如果没有指定第二个参数，则就像函数一样调用该函数（而不像方法），this值在非严格模式下是全局对象，在严格模式下则为null。

所有这些方法都会在遍历时就记录array的长度。如果调用函数在新元素追加到array中，这些新添加的元素不会遍历到。如果调用的函数修改了未遍历到的已存在元素，则调用时会传递修改后的值。

当作用于稀疏数组时，这些方法不会在实际上不存在元素的序号上调用函数。

#### 示例

```
var a=[1,2,3]
a.forEach(function(x,i,a){a[i]++}) //a现在是[2,3,4]
```



### indexOf()

在数组中查找匹配元素

#### 概要

```js
array.indexof(value)
array.indexof(value,start)
```

#### 参数

value

要在array中查找的值

start

开始查找的可选数组序号。如果省略，则为0

#### 返回值

一个大于等于start的最小序号值，该序号值出的array元素与value全相等。如果不存在匹配元素时，则返回-1。

#### 描述

该方法在array中查找等于value的元素，并返回找到的第一个元素的序号。查找的起始位置是start指定的数组序号，如果没有指定，则从0开始，然后一个接一个地查找，查找到匹配的元素或检查完所有元素为止。判断是否相等使用的是'==='操作符。返回值是找到的第一个匹配元素的序号，如果没找到匹配的，则返回-1。

#### 示例

```js
['a','b','c'].indexOf('b')    //=>1
['a','b','c'].indexOf('d')    //=>-1
['a','b','c'].indexOf('a',1)    //=>-1
```



### join()

将数组所有元素转化为字符串，并衔接起来

#### 概要

```js
array.join()
array.join(separator)
```

参数

separator

在返回的字符串中，用来分割数组的某个元素与下一个元素的可选字符或字符串。

如果省略，默认是英文逗号(,)

#### 返回值

一个字符串。将array的每一个元素转化为字符串，然后用separator字符串分隔开，最后衔接为返回的字符串。

#### 描述

join()将数组的每一个元素转换为字符串，并通过在中间插入指定的spearator字符串将他们衔接起来，最后返回衔接好的字符串。

可以进行相反的操作---将字符串分割成数组元素---使用String对象的split()方法即可

#### 示例

```
a=new Array(1,2,3,'testing');
s=a.join('+');//s是字符串'1+2+3+testing'
```



### lastIndexOf()

在数组中反向查找

#### 概要

```js
array.lastIndexOf(value)
array.lastIndexOf(value,start)
```

#### 参数

value

要在array中查找的值

start

开始查找的可选数组序号。如果省略，则从最后一个元素开始查找。

#### 返回值

一个小于等于start的最大序号值，该序号值处的array元素与value全等。如果不存在匹配元素时，则返回-1。

#### 描述

该方法在array中一个接一个地反向查找等于value的元素，并返回找到的第一个元素的序号。查找的起始位置是start指定的数组序号，如果没有指定，则从最后一个元素开始。判断是否相等使用的是‘===’操作符。返回值是找到的第一个匹配元素的序号，如果没有找到匹配的，则返回-1

### Array.length	

数组大小

#### 概要

Array.length

#### 描述

数组的length属性总是比该数组中定义的序号最大的元素的序号大一。一般来说，数组都是‘稠密’数组，拥有连续的元素，并且序号从0开始。对于这种数组，length属性表示数组中的元素个数。

使用Array()构造函数创建数组时，会初始化该数组的length属性。把新元素添加到数组中，在有必要时，会更新length属性

```js
a=new Array()    //a.length初始化为0
b=new Array(10)  //b.length初始化为10
c=new Array('one','two','three') //c.length初始化为3
c[3] = 'four' //c.length更新为4
c[10]='blastoff'  //c.length变成14
```

可以设置length的属性来改变数组的大小。如果设置的length属性小于原值，会裁减数组，末尾处的元素会丢失。如果设置的length属性大于原值，数组会变大，新添加到末尾处的元素的值为undefined。