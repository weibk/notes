#  JSON 数组

##  数组作为JSON对象

```javascript
[ "Google", "Runoob", "Taobao" ]
```

JSON 数组在中括号中书写。

JSON 中数组值必须是合法的 JSON 数据类型（字符串, 数字, 对象, 数组, 布尔值或 null）。

JavaScript 中，数组值可以是以上的 JSON 数据类型，也可以是 JavaScript 的表达式，包括函数，日期，及 *undefined*。

##  JSON 对象中的数组

对象属性的值可以是一个数组：

```javascript
{
"name":"网站",
"num":3,
"sites":[ "Google", "Runoob", "Taobao" ]
}
```

**访问对象中的数组**

```javascript
console.log(myObj.sites[0]);//Google
```

##  循环数组

```javascript
for(i in myObj.sites) {
    console.log(myObj.sites[i]);//Google   Runoob   Taobao
}
```

##  嵌套JSON对象中的数组

JSON 对象中数组可以包含另外一个数组，或者另外一个 JSON 对象：

```javascript
myObj = {
    "name":"网站",
    "num":3,
    "sites": [
        { "name":"Google", "info":[ "Android", "Google 搜索", "Google 翻译" ] },
        { "name":"Runoob", "info":[ "菜鸟教程", "菜鸟工具", "菜鸟微信" ] },
        { "name":"Taobao", "info":[ "淘宝", "网购" ] }
    ]
}
```

使用for-in访问每个数组

```javascript
			for(var i in myObj.sites) {
				console.log(myObj.sites[i].name);
				for(var j in myObj.sites[i].info) {
					console.log(myObj.sites[i].info[j]);
				}
			}
```

##  修改数组的值

可以使用索引值来修改数组值：

```javascript
myObj.sistes[0].info[0] = "glasses"
```

##  删除数组元素

```javascript
delete myObj.sites[0];
//删除数值的元素，数组的大小不变，
```

**delete 运算符并不是彻底删除元素，而是删除它的值，但仍会保留空间。**

**如何彻底删除数组中的元素**

使用数组的splice()方法