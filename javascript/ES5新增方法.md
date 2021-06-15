#  ES5新增方法

##  数组方法

###  forEach():

array.forEach(function(currentValue,index,arr){})

```javascript
			var arr = [1,2,3,4,5,6];
			var sum = 0;
			arr.forEach(function(value,index,arr){scr
    			console.log('当前项'+value);
    			console.log('当前项索引'+index);
    			console.log('数组本身'+arr);
    			sum + = value;
			)}
```

###  filter():

通过检查指定数组中符合条件的元素来创建一个新数组，主要用于数组的筛选，它直接返回一个新数组

array.filter(function(currentValue,index,arr){})

```javascript
			var arr1 = arr.filter(function(value,index,arr){
				return value % 2 == 0;
			});
			console.log(arr1);
```

###  some():

用于检测数组中的元素是否满足指定条件，即查找数组中是否有满足条件的元素

* 它的返回值是布尔值，如果查到元素则返回true，否则返回false
* 如果找到第一个满足条件的元素，则种植循环，不再继续查找

array.some(function(currentValue,index,arr){})

```javascript
			var flag = arr.some(function(value,index,arr){
				return value % 2 == 0;
			});
			console.log(flag);
```

###  map()

###  every()

##  字符串方法

###  trim():

会从一个字符串的两端删除空白字符

str.trim()

trim()方法不会影响字符串本身，它返回的是一个新字符串

```js
			var str1 = str.trim();
			console.log(str1);
```

##  对象方法

###  Object.keys():

用于获取对象自身的所有属性，返回一个属性名组成的数组

Object.keys(obj)

```javascript
			var obj1 = {
                id: 1,
                pname: '小米',
                price: 3000,
                num: 2000
            };
			var arr = Object.keys(obj1);
			console.log(arr);
```

###  Obiect.defineProperty()

定义新属性或修改原有的属性

Object.defineproperty(obj,prop,descripyor)

* obj:必须，目标对象
* prop:必须，需定义或修改的属性的名字
* descriptor:必须，目标属性所拥有的特性

:blue_heart:参数descriptor的说明：以对象的形式书写

* value:设置属性的值，默认为undefined
* writable:值是否可以重写，true|false 默认为false
* enumerable:目标属性是否可以被枚举，true|false 默认为false
* configurable:目标属性是否可以被删除或者是否可以再次修改特性，true|false 默认为false

```javascript
				id: 1,
			    pname: '小米',
			    price: 3000,
			    num: 2000
			};
			Object.defineProperty(obj,'color',{
				value: red,
				writable: false,//值是否可以被重写(修改)
				enumerable: false,//属性是否可以被枚举(被遍历)
				configurable: false//属性是否可以被删除或者是否可以再次修改特性
			});
```