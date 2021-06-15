#  JSON.parse()

JSON 通常用于与服务端交换数据。

在接收服务器数据时一般是字符串。

我们可以使用 JSON.parse() 方法将数据转换为 JavaScript 对象。

**语法**

```javascript
JSON.parse(text[,reviver]);
```

**参数说明**

* text：必需，一个有效的JSON字符串。
* reviver：可选，一个转换结果的函数，将为对象的每个成员点用此函数。

##  JSON 解析实例

例如我们从服务器接收了以下数据：

```javascript
{ "name":"runoob", "alexa":10000, "site":"www.runoob.com" }
```

我们使用 JSON.parse() 方法处理以上数据，将其转换为 JavaScript 对象：

```javascript
var obj = JSON.parse('{ "name":"runoob", "alexa":10000, "site":"www.runoob.com" }');
```

解析完成后，我们就可以在网页上使用 JSON 数据了：

```javascript
document.getElementById("demo").innerHTML = obj.name + "：" + obj.site;
```

##  解析函数

```javascript
var text = '{ "name":"Runoob", "alexa":"function () {return 10000;}", "site":"www.runoob.com"}';
var obj = JSON.parse(text);
obj.alexa = eval("(" + obj.alexa + ")");
 
document.getElementById("demo").innerHTML = obj.name + " Alexa 排名：" + obj.alexa();
```

对于服务器返回的JSON字符串，如果 jQuery 异步请求没做类型说明，或者以字符串方式接受，那么需要做一次对象化处理，方式不是太麻烦，就是将该字符串放于 eval()中执行一次。这种方式也适合以普通 javascipt 方式获取 json 对象，以下举例说明：

```
var u = eval('('+user+')');
```

为什么要 eval 这里要添加 **('('+user+')')** 呢？

原因在于：eval 本身的问题。 由于 json 是以 **{}** 的方式来开始以及结束的，在 js 中，它会被当成一个语句块来处理，所以必须强制性的将它转换成一种表达式。

加上圆括号的目的是迫使 eval 函数在处理 JavaScript 代码的时候强制将括号内的表达式（expression）转化为对象，而不是作为语句（statement）来执行。举一个例子，例如对象字面量 {}，如若不加外层的括号，那么 eval 会将大括号识别为 javascript 代码块的开始和结束标记，那么{}将会被认为是执行了一句空语句。所以下面两个执行结果是不同的：

```javascript
alert(eval("{}"); // return undefined
alert(eval("({})");// return object[Object]
```