#  JSON 对象

##  对象语法

**实例**

```javascript
{ "name":"runoob", "alexa":10000, "site":null }
```

JSON 对象使用在大括号`{}`中书写。

对象可以包含多个 **key/value（键/值）**对。

key 必须是字符串，value 可以是合法的 JSON 数据类型（字符串, 数字, 对象, 数组, 布尔值或 null）。

key 和 value 中使用冒号`:`分割。

每个 key/value 对使用逗号`,`分割。

##  访问对象值

1. 可以使用点号来访问：

```javascript
var myObj, x;
myObj = { "name":"runoob", "alexa":10000, "site":null };
x = myObj.name;
```

2. 也可以使用`[]`来访问对象的值：

```javascript
var myObj, x;
myObj = { "name":"runoob", "alexa":10000, "site":null };
x = myObj["name"];
```

##  循环对象

使用for-in循环对象的属性：

```javascript
var myObj = { "name":"runoob", "alexa":10000, "site":null };
for (x in myObj) {
    console.log(x);//name    alexa   site
}
```

循环对象属性的同时，访问属性的值：

```javascript
var myObj = { "name":"runoob", "alexa":10000, "site":null };
for (x in myObj) {
    console.log(myObj[x]);//runoob    10000   null
}
```

##  嵌套JSON对象

JSON对象中可以嵌套另一个JSON对象：

```javascript
myObj = {
    "name":"runoob",
    "alexa":10000,
    "sites": {
        "site1":"www.runoob.com",
        "site2":"m.runoob.com",
        "site3":"c.runoob.com"
    }
}
```

可以使用点号(.)或者中括号([])来访问嵌套的 JSON 对象。

```javascript
console.log(myObj.sites.site1);//www.runoob
//或者
console.log(myObj.sites["site1"]);//www.runoob
```

##  修改值

```javascript
myObj.sites.site1 = "www.goole.com";
//或者
myObj.sites["site1"] = "www.goole.com";
```

##  删除对象属性

```javascript
delete myObj.sites.site1;
//或者
delete myObj.sites["site1"];
```

