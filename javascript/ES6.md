#  ES6

ES的全称是**ECMAScript**，是ECMA国际标准化组织制定的**一项脚本语言的标准化规范**

##  let

新增的用于声明变量的关键字

1. let声明的变量只在所处于的块级有效一对{}代表一个块级作用域
2. 不存在变量提升，只能先声明再使用

```javascript
			var arr = [];
			for(var i = 0;i < 2;i++) {
				arr[i] = function() {
					console.log(i);
				}
			}
			arr[0]();//2
			arr[1]();//2
```

```javascript
            let arr = [];
			for(let i = 0;i < 2;i++) {
				arr[i] = function() {
					console.log(i);
				}
			}
			arr[0]();//0
			arr[1]();//1
```

##  const

作用：声明常量，常量就是值（内存地址）不能变化的量。

1. 具有块级作用域
2. 声明常量时必须赋初值
3. 声明常量后，值不能修改

##  新增语法

###  解构赋值

ES6中允许从数组中提取值，按照对应位置，对变量赋值，对象也可以实现解构。

####  数组解构

```javascript
			var arr = [1,2,3];
			let [a,b,c,d] = arr;
			console.log(a);
			console.log(b);
			console.log(c);
			console.log(d);//undefined
```

####  对象解构

```javascript
			var obj = {name: 'zhangsan',age: 18,sex: '男'};
			let {name,age,sex} = obj;
			console.log(name);
			console.log(age);
			console.log(sex);
			let {name: myName,age: myAge,sex: mySex} = obj;
			console.log(myName);
			console.log(myAge);
			console.log(mySex);
```

###  箭头函数

() => {}

const fn = () => {}

在箭头函数中 如果函数体只有一句代码并且执行结果就是函数的返回值 此时可以省略大括号

```javascript
			const sum = (num1,num2) => num1 + num2;
			const sum = (num1,num2) => {
                return num1 + num2;
            }
```

如果形参只有一个，小括号也可以省略

```javascript
			const fn = m => m+1;
```

箭头函数不绑定this、箭头函数中没有this关键字、如果在箭头函数中使用this，this指向箭头函数定义位置上下文中的this

#####  剩余参数

```javascript
			const sum = (...args) => {
				let total = 0;
				args.forEach(item => total += item);
				return total;
			}
			console.log(sum(10,20,30));//60
```

剩余参数和解构配合使用

```javascript
			let students = ['zhangsan','lisi','wangwu'];
			let [s1,...s2] = students;
			console.log(s1);
			console.log(s2);
```

##  ES6内置对象的扩展

####  Array的扩展方法

#####  扩展运算符可以将数组或对象转为用都好分隔的参数序列

```javascript
			let arr2 = [1,2,3,4];
			//...arr2   //  1,2,3,4
			console.log(...arr2);//1 2 3 4
```

#####  数组合并

```javascript
			let arr1 = [5,6,7,8];
			let arr2 = [1,2,3,4];
			let arr = [...arr2,...arr1];
			console.log(arr);//[1,2,3,4,5,6,7,8]
			let arr3 = arr2.push(...arr1);
```

#####  将类数组或可遍历对象转化成真正的数组

```javascript
			var divs = document.querySelectorAll('div');
			console.log(divs);
			var arr = [...divs];
			console.log(arr);

```

#####  Array.from()

```javascript
			console.log(Array.from('foo'));
			// expected output: Array ["f", "o", "o"]

			console.log(Array.from([1, 2, 3], x => x*3));
			// expected output: Array [2, 4, 6]　
```

#####  find()

用于找出**第一个符合条件**的数组成员，如果没有找到返回undefined

```javascript
			arr.find(callback[, thisArg])
```

```javascript
			const array1 = [5, 12, 8, 130, 44];
			const found = array1.find(element => element > 10);
			console.log(found);
			// expected output: 12
```

#####  findIndex()

用于找出**第一个符合条件**的数组成员的**位置(索引)**，如果没有找到返回**-1**

```javascript
			arr.findIndex(callback[, thisArg])
```

```javascript
			const array1 = [5, 12, 8, 130, 44];
			const isLargeNumber = (element) => element > 13;
			console.log(array1.findIndex(isLargeNumber));
			// expected output: 3
```

#####  includes()

用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回false。

```javascript
arr.includes(valueToFind[, fromIndex])
//fromIndex:从哪个位置开始查找，默认为0
```

```javascript
			const array1 = [1, 2, 3];
			console.log(array1.includes(2));
			// expected output: true
			const pets = ['cat', 'dog', 'bat'];
			console.log(pets.includes('cat'));
			// expected output: true
			console.log(pets.includes('at'));
			// expected output: false
```

#####  模版字符串

ES6新增的创建字符串的方式，使用反引号定义

```javascript
			let uname = `zhangsan`;
```

模版字符串中可以解析变量

```javascript
			let uname = `zhangsan`;
			let sayHello = `hello,my name is ${uname}`;
			console.log(sayHello);//hello,my name is zhangsan 
```

模版字符串中可以换行

```javascript
			let result = {
				uname: "zhangsan",
				age: 18
			}
			let html = `
				<div>
					<span>${result.uname}</span>
					<span>${result.age}</span>
				</div>
			`;
			console.log(html);
```

模版字符串中可以调用函数

```javascript
				return '我是fnn';
			}
			
			let html = `
				"hello,${fnn()}"
			`;
			console.log(html);
```

#####  String的扩展方法

startsWith(): 表示参数字符串是否在原字符串的头部，返回布尔值。

startsWith(): 表示参数字符串是否在原字符串的头部，返回布尔值。

```javascript
			let str = 'hello,world!';
			str.startsWith('hello');//true
			str.endsWith('!');//true
```

repeat(): 将原字符串重复n次，返回一个新字符串，默认1次

```javascript
			console.log('y'.repeat(3));/yyy 
```

#####  Set 数据结构

ES6提供了新的数据结构Set，它类似于数组，但是**成员的值都是唯一的**，没有重复的值。

```javascript
			const s1 = new Set([1,2,3,4,4,5,5,5,6]);
			console.log(s1);//[1,2,3,4,5,6]
			console.log(s1.size);//6
			const s2 = new Set(['a','b','c','c']);
			console.log(s2);//['a','b','c']
```

实例方法

add(value):添加某个值，返回set结构本身

```javascript
			const s = new Set();
			let a = s.add(1).add(2);
			console.log(a);[1,2]
```

delete(value):删除某个值，返回一个布尔值，表示是否删除成功

```javascript
			const s = new Set([1,2,3,4,5]);
			let a = s.delete(3);
			console.log(a);//true
			console.log(s);//[1,2,4,5]
```

has(value):返回一个布尔值，表示该值是否为Set成员

```javascript
			const s = new Set([1,2,3,4,5]);
			let a = s.has(3);
			let b = s.has(6);
			console.log(a);//true
			console.log(b);//false
```

clear():清除所有成员，没有返回值

```javascript
			const s = new Set([1,2,3,4,5]);
			s.clear();
			console.log(s);
```

遍历

```javascript
			const s = new Set([1,2,3,4,5]);
			s.forEach(value => console.log(value));
```

