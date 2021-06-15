#  JavaScript HTML  DOM  Eventlistener

##  addEventListener()方法

addEventListener() 方法用于向指定元素添加事件句柄。

addEventListener() 方法添加的事件句柄不会覆盖已存在的事件句柄。

可以向一个元素添加多个事件句柄。

可以向同个元素添加多个同类型的事件句柄，如：两个 "click" 事件。

可以向任何 DOM 对象添加事件监听，不仅仅是 HTML 元素。如： window 对象。

addEventListener() 方法可以更简单的控制事件（冒泡与捕获）。

当使用 addEventListener() 方法时, JavaScript 从 HTML 标记中分离开来，可读性更强， 在没有控制HTML标记时也可以添加事件监听。

可以使用 removeEventListener() 方法来移除事件的监听。

**语法**

```javascript
element.addEventListener(event,function,useCapture);
```

第一个参数是事件的类型 (如 "click" 或 "mousedown").

第二个参数是事件触发后调用的函数。

第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的。

true:使用捕获传递，false:使用冒泡传递，默认为false，冒泡传递

**注意：**不要使用 "on" 前缀。 例如，使用 "click" ,而不是使用 "onclick"。

###  向元素添加事件句柄

**实例**

```javascript
element.addEventListener('click',function(){
    alert('hello word');
});
```

也可以使用函数名，来引用外部函数：

```javascript
element.addEventListener('click',myFunction);
function myFunction(){
    alert('hello world');
}
```

###  向同一个元素添加多个事件句柄

addEventListener() 方法允许向同一个元素添加多个事件，且不会覆盖已存在的事件：

**实例**

```javascript
element.addEventListener('click',myFunction);
element.addEventListener('click',mySecondFunction);
```

向同一个元素添加不同类型的事件：

```javascript
element.addEventListener('mouseover',myFunction);
element.addEventListener('click',mySecondFunction);
element.addEventListener('mouseout',myThirdFunction);
```

###  向Window对象添加事件句柄

addEventListener() 方法允许你在 HTML DOM 对象添加事件监听， HTML DOM 对象如： HTML 元素, HTML 文档, window 对象。或者其他支出的事件对象如: xmlHttpRequest 对象。

**实例**

```javascript
Window.addEventListener('resize',myFunction);
```

###  传递参数

当传递参数值时，使用"匿名函数"调用带参数的函数：

**实例**

```javascript
var p1 = 5;
var p2 = 7;
document.getElementById("myBtn").addEventListener("click", function() {
    myFunction(p1, p2);
});
function myFunction(a, b) {
    var result = a * b;
    document.getElementById("demo").innerHTML = result;
}
```

###  事件冒泡和事件捕获

事件传递有两种方式：冒泡与捕获。

事件传递定义了元素事件触发的顺序。 如果你将`<p> `元素插入到`` <div>`` 元素中，用户点击` <p> `元素, 哪个元素的 "click" 事件先被触发呢？

在 *冒泡* 中，内部元素的事件会先被触发，然后再触发外部元素，即：`` <p>`` 元素的点击事件先触发，然后会触发 `<div>` 元素的点击事件。

在 *捕获* 中，外部元素的事件会先被触发，然后才会触发内部元素的事件，即：` <div> `元素的点击事件先触发 ，然后再触发` <p> `元素的点击事件。

###  removeEventlistener()

removeEventListener() 方法移除由 addEventListener() 方法添加的事件句柄:

```javascript
element.removeEventLitener(event,function);
```

###  跨浏览器

```javascript
var x = document.getElementById("myBtn");
if (x.addEventListener) {                    // 所有主流浏览器，除了 IE 8 及更早版本
    x.addEventListener("click", myFunction);
} else if (x.attachEvent) {                  // IE 8 及更早版本
    x.attachEvent("onclick", myFunction);
}
```

