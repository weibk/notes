#  JSON语法

##  JSON 语法规则

JSON 语法是 JavaScript 对象表示语法的子集。

- 数据在名称/值对中
- 数据由逗号分隔
- 大括号 **{}** 保存对象
- 中括号 **[]** 保存数组，数组可以包含多个对象

##  JSON 名称/值对

JSON数据的书写格式是：

```javascript
key : value
```

名称/值对包括字段名称(在双引号中)，后面写一个冒号，然后是值：

```javascript
"name" : "菜鸟教程"
```

等价于这条JavaScript语句：

```javascript
name = "菜鸟教程"
```

##  JSON 值

JSON 值可以是：

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在中括号中）
- 对象（在大括号中）
- null

##  JSON 数字

JSON数字可以是整型或者浮点型：

```javascript
{ "age" : 30 }
```

##  JSON 对象

JSON对象在大括号`{}`中书写：

```javascript
{key1 : value1, key2 : value2, ..... keyN : valueN}
```

对象可以包含多个名称/值对：

```javascript
{ "name" : "菜鸟教程" , "url" : "www.runoob.com" }
```

相当于这条JavaScript语句：

```javascript
name = "菜鸟教程"
url = "www.runoob.com"
```

##  JSON 数组

JSON 数组在中括号 `[] `中书写：

数组可包含多个对象：

```javascript
[
    { key1 : value1-1 , key2:value1-2 }, 
    { key1 : value2-1 , key2:value2-2 }, 
    { key1 : value3-1 , key2:value3-2 }, 
    ...
    { keyN : valueN-1 , keyN:valueN-2 }, 
]
```

```javascript
{
    "sites": [
        { "name":"菜鸟教程" , "url":"www.runoob.com" }, 
        { "name":"google" , "url":"www.google.com" }, 
        { "name":"微博" , "url":"www.weibo.com" }
    ]
}
```

##  JSON 布尔值

```javascript
{ "flag" : true }
{ "flag1" : false }
```

##  JSON null

```javascript
{ "runoob" : null }
```

##  JSON  使用  JavaScript  语法

因为 JSON 使用 JavaScript 语法，所以无需额外的软件就能处理 JavaScript 中的 JSON。

通过 JavaScript，您可以创建一个对象数组，并像这样进行赋值：

```javascript
var sites = [
    { "name":"runoob" , "url":"www.runoob.com" }, 
    { "name":"google" , "url":"www.google.com" }, 
    { "name":"微博" , "url":"www.weibo.com" }
];
```

**访问**

```javascript
sites[0].name;//runoob
```

**修改**

```javascript
sites[0].name = "菜鸟教程"；
```

