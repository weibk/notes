#  数组(Array)

------

##  创建数组

字面量创建数组：

```javascript
var fruits = ['apple','banana'];
console.log(fruits.length);//2
```

利用new关键字通过Array对象创建数组：

```javascript
var fruits = new Array(['apple','banana']);
console.log(fruits.length);//2
```

通过索引访问数组：

```javascript
var fruits = ['apple','banana'];
var first = fruits[0];
console.log(first);//apple
var last = fruits[1];
console.log(last);//banana
```
##   数组属性

###  arr.length

`length`是`Array`的实例属性。返回或设置一个数组中元素的个数。该值是一个无符号 32-bit 整数，并且总是大于数组最高项的下标。

```javascript
const fruits = ['apple','banana','orange'];
console.log(fruits.length);//3
```

你可以设置 `length` 属性的值来截断任何数组。当通过改变`length`属性值来扩展数组时，实际元素的数目将会增加。例如：将一个拥有 2 个元素的数组的 `length` 属性值设为 3 时，那么这个数组将会包含3个元素，并且，第三个元素的值将会是 `undefined` 。

###  arr.constructor

所有的数组实例都继承了这个属性，它的值就是 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)，表明了所有的数组都是由 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array) 构造出来的。
##  常用的数组方法

###  Array.from()

`Array.from()` 方法从一个类似数组或可迭代对象创建一个新的，浅拷贝的数组实例。

```javascript
console.log(Array.from('foo'));
//Array ["f","o","o"]
console.log(Array.from([1,2,3], x => x*2));
//Array [2,4,6]
```

**语法：**

```javascript
Array.from(arrayLike[, mapFn[, thisArg]])
```

**参数：**

`arrayLike`
想要转换成数组的伪数组对象或可迭代对象。

`mapFn` (可选)
如果指定了该参数，新数组中的每个元素会执行该回调函数。

`thisArg` (可选)
可选参数，执行回调函数 mapFn 时 this 对象。

**返回值：**一个新的数组实例

###  Array.isArray()

**Array.isArray()** 用于确定传递的值是否是一个 `Array`。

```java
Array.isArray([1, 2, 3]);  
// true
Array.isArray({foo: 123}); 
// false
Array.isArray("foobar");   
// false
Array.isArray(undefined);  
// false
```

**语法**

```javascript
Array.isArray(obj)
```

**参数**

`obj`
需要检测的值。

**返回值**

如果值是 `Array`则返回true，否则为false。

###  Array.of()

**Array.of()** 方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。

**Array.of()** 和 **Array** 构造函数之间的区别在于处理整数参数：**Array.of(7)**创建一个具有单个元素 **7** 的数组，而 **`Array(7)`** 创建一个长度为7的空数组（**注意：**这是指一个有7个空位(empty)的数组，而不是由7个`undefined`组成的数组）。

```javascript
Array.of(7);//[7]
Array.of(1,2,3);//[1,2,3]
Array(7);//[ , , , , , , ]
Array(1,2,3);//[1,2,3]
```

**语法**

```javascript
Array.of(element0[, element1[, ...[, elementN]]])
```

**参数**

`elementN`

任意个参数，将按顺序成为返回数组中的元素。

**返回值**

新的`Array`实例。

##  修改器方法

下面这些方法会改变调用它们的对象自身的值。

###  删除元素Array.prototype.pop()

`pop()`删除数组的最后一个元素，并返回这个元素。

```javascript
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];
console.log(plants.pop());
//  "tomato"
console.log(plants);
// Array ["broccoli", "cauliflower", "cabbage", "kale"]
plants.pop();
console.log(plants);
// ["broccoli", "cauliflower", "cabbage"]
```

**语法**

从数组中删除的元素(当数组为空时返回[`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined))。

**描述**

`pop` 方法从一个数组中删除并返回最后一个元素。

`pop` 方法有意具有通用性。该方法和 [`call()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call) 或 [`apply()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) 一起使用时，可应用在类似数组的对象上。`pop`方法根据 `length`属性来确定最后一个元素的位置。如果不包含`length`属性或`length`属性不能被转成一个数值，会将`length`置为0，并返回`undefined`。

如果你在一个空数组上调用 pop()，它返回  [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。

###  添加元素Array.prototype.push()

**`push()`**方法将一个或多个元素添加到数组的末尾，并返回该数组新的长度。

```javascript
const animals = ['pigs', 'goats', 'sheep'];
const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]
animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```

**语法**

```javascript
arr.push(element1, ..., elementN)
```

**参数**

`elementN`
被添加到数组末尾的元素。

**返回值**

当调用该方法时，新的 `length` 属性值将被返回。

###  Array.prototype.unshift()

`unshift()`方法将一个或多个元素添加到数组的**开头**，并返回该数组的**新长度(该**方法修改原有数组**)**。

```javascript
const array1 = [1, 2, 3];
console.log(array1.unshift(4, 5));
// 返回新数组的长度 5
console.log(array1);
// Array [4, 5, 1, 2, 3]
```

**语法**

```javascript
arr.unshift(element1,.....,elementN)
```

**参数列表**

`elementN`

要添加到数组开头的元素或多个元素。

 **返回值**

当一个对象调用该方法时，返回其 [`length`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/length) 属性值。

###  反转数组Array.prototype.reverse()

`reverse()` 方法将数组中元素的位置颠倒，并返回该数组。数组的第一个元素会变成最后一个，数组的最后一个元素变成第一个。该方法会改变原数组。

```javascript
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]
const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]
console.log('array1:', array1);
// "array1:" Array ["three", "two", "one"]
```

**语法**

```javascript
arr.reverse()
```

**返回值**

颠倒后的数组。

###  删除元素Array.prototype.shift()

**`shift()` **方法从数组中删除**第一个**元素，并返回该元素的值。此方法更改数组的长度。

```javascript
const array1 = [1, 2, 3];
const firstElement = array1.shift();
console.log(array1);
// expected output: Array [2, 3]
console.log(firstElement);
// expected output: 1
```
**语法**

```javascript
arr.shift()
```

**返回值**

从数组中删除的元素; 如果数组为空则返回[`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined) 。 

###  数组排序Array.prototype.sort()

`sort()`方法用[原地算法](https://en.wikipedia.org/wiki/In-place_algorithm)对数组的元素进行排序，并返回数组。默认排序顺序是在将元素转换为字符串，然后比较它们的UTF-16代码单元值序列时构建的

由于它取决于具体实现，因此无法保证排序的时间和空间复杂性。

```javascript
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// Array ["Dec", "Feb", "Jan", "March"]
const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// Array [1, 100000, 21, 30, 4]
```

**语法**

```javascript
arr.sort([compareFunction])
```

**参数**

compareFunction` (可选)

用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序。  

 `firstEl`  第一个用于比较的元素。

 `secondEl`  第二个用于比较的元素。  

**返回值**

排序后的数组。请注意，数组已原地排序，并且不进行复制。

比较函数：

sort内部:

```javascript
function sort(arr,fun) {
    for(var i = 0;i < arr.length - 1;i++) {
        for(var j = 0;j < arr.length -1 - i;j++) {
            if(fun(arr[j],arr[j + 1]) > 0) {
                [arr[j],arr[j + 1]] = [arr[j + 1],arr[j]];
            }
        }
    }
}
```

```javascript
function compare(a, b) {
			  if (a < b ) {           // 按某种排序标准进行比较, a 小于 b
			    return -1;
			  }
			  if (a > b ) {
			    return 1;
			  }
			  // a must be equal to b
			  return 0;
			}
			var arr = [1, 3, 4, 60, 7, 35];
			arr.sort(compare);
			console.log(arr);//[1,3,4,7,35,68]
```

要比较数字而非字符串，比较函数可以简单的以 a 减 b，如下的函数将会将数组升序排列:

```javascript
			function compareNumbers(a, b) {//数字按升序排列
			  return a - b;
			}
			function compareNumbers1(a, b) {//数字按降序排列
			  return b - a;
			}
			var arr = [2,1,3,6,88,77,96];
			var arr1 = [3,6,5,4,9,88,77];
			var arr2 = [3,6,5,4,9,88,77];
			arr.sort(compareNumbers);
			arr1.sort((a,b) => a-b);
			arr2.sort(compareNumbers1);
			console.log(arr);
			console.log(arr1);
			console.log(arr2);
```

对象可以按照某个属性排序：

```javascript
			var items = [{
				uname: 'zhangsan',
				age: 18
			},{
				uname: 'lisi',
				age: 17
			},{
				uname: 'wangwu',
				age: 19
			},{
				uname: 'xiaoming',
				age: 20
			},{
				uname: 'xiaohong',
				age: 25
			}];
			items.sort((a,b) => a.age - b.age);
			console.log(items);
```

###  Array.prototype.splice()

`splice()`方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。

**语法**

```javascript
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

**参数**

`start`

指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；如果是负值，则表示从数组末位开始的第几位（从-1计数，这意味着-n是倒数第n个元素并且等价于`array.length-n`）；如果负数的绝对值大于数组的长度，则表示开始位置为第0位。

`deleteCount` (可选)

整数，表示要移除的数组元素的个数。

如果 `deleteCount` 被省略了，或者它的值大于等于`array.length - start`(也就是说，如果它大于或者等于`start`之后的所有元素的数量)，那么`start`之后数组的所有元素都会被删除。

如果 `deleteCount` 是 0 或者负数，则不移除元素。这种情况下，至少应添加一个新元素。

`item1,item2,.....` (可选)

要添加进数组的元素,从`start` 位置开始。如果不指定，则 `splice()` 将只删除数组元素。

**返回值**

由被删除的元素组成的一个数组。如果只删除了一个元素，则返回只包含一个元素的数组。如果没有删除元素，则返回空数组。

```javascript
			var arr = [1,2,3,4,5,6,7,8,9];
			var arr1 = arr.splice(1,2,10);//从索引1开始删除两个元素，添加一个元素10
			console.log(arr);//[1,10,4,5,6,7,8,9]
			console.log(arr1);//[2,3]
```



##  访问方法

###  Array.prototype.concat()

`concat()`方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

```javascript
var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
```

**参数**

`valueN`

数组和/或值，将被合并到一个新的数组中。如果省略了所有 `valueN` 参数，则 `concat` 会返回调用此方法的现存数组的一个浅拷贝。

```javascript
		var num1 = [1,2,3];
		var num2 = [4,5,6];
		var num3 = [7,8,9];
		var newArr = num1.concat(num2,num3);
		console.log(newArr);//[1,2,3,4,5,6,7,8,9]
```

```javascript
		var num1 = [1,2,3];
		var num2 = [4,5,6];
		var newArr = num1.concat(99,num2);
		console.log(newArr);//[1,2,3,99,4,5,6]
```

```javascript
		var num1 = [[2]];
		var num2 = [4,[5,6]];
		var num3 = [[7,8],9];
		var newArr = num1.concat(num2,num3);
		console.log(newArr);//[[2],4,[5,6],[7,8],9]
```

###  Array.prototype.join()

`join()`方法将一个数组(或一个类数组对象)的所有元素连接成一个字符串并返回这个字符串，如果数组只有一个项目，那么将返回该项目而不使用分隔符。

```javascript
const elements = ['Fire', 'Air', 'Water'];
console.log(elements.join());
//Fire,Air,Water
console.log(elements.join(''));
//FireAirWater
console.log(elements.join('-'));
//Fire-Air-Water
```

**语法**

```javascript
arr.join([separator])
```

**参数**

`separator`

指定一个字符串来分隔数组的每个元素。如果需要，将分隔符转换为字符串。如果缺省该值，数组元素用逗号（`,`）分隔。如果`separator`是空字符串(`""`)，则所有元素之间都没有任何字符。

**返回值**

一个所有数组元素连接的字符串。如果 `arr.length` 为0，则返回空字符串。

:heavy_exclamation_mark:如果一个元素为`undefined`或`null`，则会被转化为空字符串.

###  Array.prototype.slice()

`slice()`方法返回一个新的数组对象，这一对象是一个由`begin`和`end`决定的原数组的**浅拷贝**(包括`begin`，不包括`end`)。原始数组不会改变。

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]
console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]
console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck","elephant"]
```

**语法**

`begin`

提取起始处的索引（从 `0` 开始），从该索引开始提取原数组元素。

如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，`slice(-2)` 表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。

如果省略 `begin`，则 `slice` 从索引 `0` 开始。

如果 `begin` 大于原数组的长度，则会返回空数组。

`end`

提取终止处的索引（从 `0` 开始），在该索引处结束提取原数组元素。`slice` 会提取原数组中索引从 `begin` 到 `end` 的所有元素（包含 `begin`，但不包含 `end`）。

`slice(1,4)` 会提取原数组中从第二个元素开始一直到第四个元素的所有元素 （索引为 1, 2, 3的元素）。

如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 `slice(-2,-1)` 表示抽取了原数组中的倒数第二个元素到最后一个元素（不包含最后一个元素，也就是只有倒数第二个元素）。

如果 `end` 被省略，则 `slice` 会一直提取到原数组末尾。

如果 `end` 大于数组的长度，`slice` 也会一直提取到原数组末尾。

**返回值**

一个含有被提取元素的新数组。

**描述**

`slice` 不会修改原数组，只会返回一个浅复制了原数组中的元素的一个新数组。原数组的元素会按照下述规则拷贝：

- 如果该元素是个对象引用 （不是实际的对象），`slice` 会拷贝这个对象引用到新的数组里。两个对象引用都引用了同一个对象。如果被引用的对象发生改变，则新的和原来的数组中的这个元素也会发生改变。

- 对于字符串、数字及布尔值来说（不是 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)、[`Number`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number) 或者 [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Boolean) 对象），`slice` 会拷贝这些值到新的数组里。在别的数组里修改这些字符串或数字或是布尔值，将不会影响另一个数组。

如果向两个数组任一中添加了新元素，则另一个不会受到影响。

###  Array.prototype.toString()

`toString()`返回一个字符串，表示指定的数组及其元素。

```javascript
const array1 = [1, 2, 'a', '1a'];
console.log(array1.toString());
// expected output: "1,2,a,1a"
```

**语法**

```javascript
arr.toString()
```

**返回值**

一个表示指定的数组机器元素的字符串。

###  Array.prototype.indexOf()

`indexOf()`方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。

```javascript
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];
console.log(beasts.indexOf('bison'));
// expected output: 1
// start from index 2
console.log(beasts.indexOf('bison', 2));
// expected output: 4
console.log(beasts.indexOf('giraffe'));
// expected output: -1 
```

**语法**

```javascript
arr.indexOf(searchElement[, fromIndex])
```

**参数**

`searchElement`

要查找的元素。

`fromIndex`

开始查找的位置。如果该索引值大于或等于数组长度，意味着不会在数组里查找，返回-1。如果参数中提供的索引值是一个负值，则将其作为数组末尾的一个抵消，即-1表示从最后一个元素开始查找，-2表示从倒数第二个元素开始查找 ，以此类推。  注意：如果参数中提供的索引值是一个负值，并不改变其查找顺序，查找顺序仍然是从前向后查询数组。如果抵消后的索引值仍小于0，则整个数组都将会被查询。其默认值为0.

###  Array.prototype.lastIndexOf()

`lastIndexOf`方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 `fromIndex` 处开始。

```javascript
const animals = ['Dodo', 'Tiger', 'Penguin', 'Dodo'];
console.log(animals.lastIndexOf('Dodo'));
// expected output: 3
console.log(animals.lastIndexOf('Tiger'));
// expected output: 1
```

**语法**

```java
arr.lastIndexOf(searchElement[, fromIndex])
```

**参数**

`searchElement`

要查找的元素。

`fromIndex`

从此位置开始逆向查找。默认为数组的长度减 1(`arr.length - 1`)，即整个数组都被查找。如果该值大于或等于数组的长度，则整个数组会被查找。如果为负值，将其视为从数组末尾向前的偏移。即使该值为负，数组仍然会被从后向前查找。如果该值为负时，其绝对值大于数组长度，则方法返回 -1，即数组不会被查找。

**返回值**

数组中该元素最后一次出现的索引，如未找到返回-1。

##  迭代方法

在下面的众多遍历方法中，有很多方法都需要指定一个回调函数作为参数。在每一个数组元素都分别执行完回调函数之前，数组的length属性会被缓存在某个地方，所以，如果你在回调函数中为当前数组添加了新的元素，那么那些新添加的元素是不会被遍历到的。此外，如果在回调函数中对当前数组进行了其它修改，比如改变某个元素的值或者删掉某个元素，那么随后的遍历操作可能会受到未预期的影响。总之，不要尝试在遍历过程中对原数组进行任何修改，虽然规范对这样的操作进行了详细的定义，但为了可读性和可维护性，请不要这样做。

###  Array.prototype,forEach()

`forEach()`方法对数组的每个元素执行一次给定的函数。

```javascript
const array1 = ['a', 'b', 'c'];
array1.forEach(element => console.log(element));
//a
//b
//c
```

**语法**

```javascript
arr.forEach(callback(currentValue [, index [, array]])[, thisArg])
```

**参数**

`callback`

​	为数组中每个元素执行的函数，该函数接受一至三个参数。

​	`currentValue`

​		数组中正在处理的当前元素。

​	`index`(可选)

​		数组中正在处理的当前元素的索引。

​	`array`(可选)

​		`forEach()` 正在操作的数组本身

`thisArg`(可选)

​	可选参数。当执行回调函数`callback`时，用作`this`的值。

###  Array.prototype.every()

`every()`方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。

**注意**：若收到一个空数组，此方法在一切情况下都会返回 `true`。

```javascript
const isBelowThreshold = (currentValue) => currentValue < 40;
const array1 = [1, 30, 39, 29, 10, 13];
console.log(array1.every(isBelowThreshold));
// expected output: true
```

**语法**

> ```javascript
> arr.every(callback(element[, index[, array]])[, thisArg])
> ```

**参数**

`callback`

​	为数组中每个元素执行的函数，该函数接受一至三个参数。

​	`element`

​		数组中正在处理的元素。

​	`index`(可选)

​		数组中正在处理的当前元素的索引。

​	`array`(可选)

​		调用`array` 的当前数组。

`thisArg`(可选)

​	可选参数。当执行回调函数`callback`时，使用的`this`值。

**返回值**

如果回调函数的每一次返回都为 [truthy](https://developer.mozilla.org/zh-CN/docs/Glossary/Truthy) 值，返回 **`true`** ，否则返回 **`false`**。

###  Array.prototype.some()

`some()`方法测试数组中是不是至少有1个元素通过了被提供的函数测试。它返回的是一个Boolean类型的值。

```javascript
const array = [1, 2, 3, 4, 5];
// checks whether an element is even
const even = (element) => element % 2 === 0;
console.log(array.some(even));
// expected output: true
```

**语法**

> ```javascript
> arr.some(callback(element[, index[, array]])[, thisArg])
> ```

**参数**

`callback`

​	为数组中每个元素执行的函数，该函数接受一至三个参数。

​	`element`

​		数组中正在处理的元素。

​	`index`(可选)

​		数组中正在处理的当前元素的索引。

​	`array`(可选)

​		调用`some()` 的当前数组。

`thisArg`(可选)

​	可选参数。当执行回调函数`callback`时，使用的`this`值。

**返回值**

数组中有至少一个元素通过回调函数的测试就会返回**`true`**；所有元素都没有通过回调函数的测试返回值才会为false。

###  Array.prototypr.filter()

`filter()`方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。 

```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

**语法**

> ```javascript
> var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
> ```

**参数**

`callback`

用来测试数组的每个元素的函数。返回 `true` 表示该元素通过测试，保留该元素，`false` 则不保留。它接受以下三个参数：

`element`  

数组中当前正在处理的元素。  

`index`可选  

正在处理的元素在数组中的索引。  

`array`可选  

调用了 `filter` 的数组本身。  

`thisArg`(可选)

执行 `callback` 时，用于 `this` 的值。

**返回值**

一个新的、由通过测试的元素组成的数组，如果没有任何数组元素通过测试，则返回空数组。

###  Array.prototype.map()

`map()`方法创建一个新数组，其结果是该数组中的每个元素是调用一次提供的函数后的返回值。

```javascript
const array1 = [1, 4, 9, 16];
// pass a function to map
const map1 = array1.map(x => x * 2);
console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

**语法**

> ```javascript
> var new_array = arr.map(function callback(currentValue[, index[, array]]) {
>  // Return element for new_array 
> }[, thisArg])
> ```

**参数**

`callback`

生成新数组元素的函数，使用三个参数：  

`currentValue`  

​	`callback` 数组中正在处理的当前元素。  

`index`可选  

​	`callback` 数组中正在处理的当前元素的索引。  

`array`可选  

​	`map` 方法调用的数组。  

`thisArg`可选

​	执行 `callback` 函数时值被用作`this`。

**返回值**

一个由原数组每个元素执行回调函数的结果组成的新数组。