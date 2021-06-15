#  String

##  String.fromCharCode()

**一系列 UTF-16 代码单元的数字。范围介于 `0` 到 `65535`（`0xFFFF`）之间。大于 `0xFFFF` 的数字将被截断。不进行有效性检查。**

```javascript
console.log(String.fromCharCode(88,90,33,22));//XZ!
```

##  charAt()

**charAt()** 方法从一个字符串中返回指定索引对应的字符。

**语法**

```javascript
str.charAt(index);
```

**参数**

index：介于0 和字符串和字符串长度减1之间的整数(0 ~ str.length-1)

**返回值**

指定索引对应的字符。

##   charCodeAt()

方法返回 `0` 到 `65535` 之间的整数，表示给定索引处的 UTF-16 代码单元

**语法**

```javascript
str.charCodeAt(index);
```

**参数**

index：介于0 和字符串和字符串长度减1之间的整数(0 ~ str.length-1)

**返回值**

指定 `index` 处字符的 UTF-16 代码单元值的一个数字；如果 `index` 超出范围，`charCodeAt()` 返回 [`NaN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/NaN)。

##  字符串拼接concat()

```javascript
var str1 = 'aaa';
var str2 = 'bbb';
var str3 = 'ccc';
console.log(str1.concat(str2));//'aaabbb'
console.log(str2.concat(str1));//'bbbaaa'
console.log(str1.concat(str2,str3));//'aaabbbccc'
str1.concat();//没有参数的时候返回原字符串，相当于复制操作
```

##  字符串截取

###  slice()

**语法**

```javascript
str.slice(startIndex,endIndex);
```

**参数**

`startIndex`:截取的起始索引，截取的字符串包括该索引。

`endIndex`:截取的结束索引，截取的字符串不包括该索引。

参数可以为负值。

**返回值**

返回截取到的字符串。

###  substring()

**语法**

```javascript
str.substring(startIndex,endIndex);
```

**参数**

`startIndex`:截取的起始索引，截取的字符串包括该索引。

`endIndex`:截取的结束索引，截取的字符串不包括该索引。

当参数为负值时，等同于0。

**返回值**

返回截取到的字符串。

###  substr()

**语法**

```javascript
str.substring(startIndex,length);
```

**参数**

`startIndex`:截取的起始索引，截取的字符串包括该索引。当参数为负值时，从后面开始计算。

`length`:截取字符串的长度。可选，如果省略，截取开始索引之后的所有。

**返回值**

返回截取到的字符串。

##  字符串访问方法

###  indexOf()

`indexOf()` 方法返回调用它的 `String`对象中第一次出现的指定值的索引，从 `fromIndex` 处进行搜索。如果未找到该值，则返回 -1。

**语法**

```javascript
str.indexOf(searchValue[,fromIndex]);
```

**参数**

* `searchValue`

要被查找的字符串值。

如果没有提供确切地提供字符串，[searchValue 会被强制设置为 `"undefined"`](https://tc39.github.io/ecma262/#sec-tostring)， 然后在当前字符串中查找这个值。

举个例子：`'undefined'.indexOf()` 将会返回0，因为 `undefined` 在位置0处被找到，但是 `'undefine'.indexOf()` 将会返回 -1 ，因为字符串 `'undefined'` 未被找到。

* `fromIndex` 可选

数字表示开始查找的位置。可以是任意整数，默认值为 `0`。

如果 `fromIndex` 的值小于 `0`，或者大于 `str.length` ，那么查找分别从 `0` 和`str.length` 开始。（译者注： `fromIndex` 的值小于 `0`，等同于为空情况； `fromIndex` 的值大于或等于 `str.length` ，那么结果会直接返回 `-1` 。）

举个例子，`'hello world'.indexOf('o', -5)` 返回 `4` ，因为它是从位置`0`处开始查找，然后 `o` 在位置`4`处被找到。另一方面，`'hello world'.indexOf('o', 11)` （或 `fromIndex` 填入任何大于`11`的值）将会返回 `-1` ，因为开始查找的位置`11`处，已经是这个字符串的结尾了。

**返回值**

查找的字符串 `searchValue` 的第一次出现的索引，如果没有找到，则返回 `-1`。

若被查找的字符串 `searchValue` 是一个空字符串，将会产生“奇怪”的结果。如果 `fromIndex` 值为空，或者 `fromIndex` 值小于被查找的字符串的长度，返回值和以下的 `fromIndex` 值一样：

###  includes()

**`includes()`** 方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false。

**语法**

```javascript
str.includes(searchValue[,startIndex]);
```

**参数**

`searchString`

要在此字符串中搜索的字符串。

`position` 可选

从当前字符串的哪个索引位置开始搜寻子字符串，默认值为 `0`。

**返回值**

如果当前字符串包含被搜寻的字符串，就返回 **`true`**；否则返回 **`false`**。

###  lastIndexOf()

**`lastIndexOf()`** 方法返回调用[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String) 对象的指定值最后一次出现的索引，在一个字符串中的指定位置 `fromIndex`处从后向前搜索。如果没找到这个特定值则返回-1 。

该方法将从尾到头地检索字符串 *str*，看它是否含有子串 *searchValue*。开始检索的位置在字符串的 *fromIndex* 处或字符串的结尾（没有指定 *fromIndex* 时）。如果找到一个 *searchValue*，则返回 *searchValue* 的第一个字符在 *str* 中的位置。*str*中的字符位置是从 0 开始的。

**语法**

```javascript
str.lastIndexOf(searchValue[,fromIndex]);
```

**参数**

`searchValue`

一个字符串，表示被查找的值。如果`searchValue`是空字符串，则返回`fromIndex`。

`fromIndex`可选

待匹配字符串searchValue的开头一位字符从 str的第fromIndex位开始向左回向查找。`fromIndex`默认值是 `+Infinity`。如果 `fromIndex >= str.length` ，则会搜索整个字符串。如果 `fromIndex < 0` ，则等同于 `fromIndex == 0`。

**返回值**

返回指定值最后一次出现的索引(该索引仍是以从左至右0开始记数的)，如果没找到则返回-1。