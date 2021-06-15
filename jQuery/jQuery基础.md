#  jQuery基础

##  简介

jQuery是一个JavaScript函数库。

jQuery是一个轻量级的"写的少，做的多"的JavaScript库。

jQuery库包含以下功能：

- HTML 元素选取
- HTML 元素操作
- CSS 操作
- HTML 事件函数
- JavaScript 特效和动画
- HTML DOM 遍历和修改
- AJAX
- Utilities

**提示：** 除此之外，Jquery还提供了大量的插件。

##  jQuery语法

jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： **$(selector).action()**

- 美元符号定义 jQuery
- 选择符（selector）"查询"和"查找" HTML 元素
- jQuery 的 action() 执行对元素的操作

实例:

- $(this).hide() - 隐藏当前元素
- $("p").hide() - 隐藏所有 `<p>` 元素
- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
- $("#test").hide() - 隐藏 id="test" 的元素

###  文档就绪事件

```javascript
$(document).ready(function(){
    //jQuery代码
})
```

这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。

**提示：**简洁写法（与以上写法效果相同）:

```javascript
$(function(){
    //jQuery代码
})
```

##  jQuery选择器

jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 [CSS 选择器](https://www.runoob.com/cssref/css-selectors.html)，除此之外，它还有一些自定义的选择器。

jQuery 中所有选择器都以美元符号开头：$()。

###  元素选择器

jQuery元素选择器基于元素名选取元素。

```javascript
$('p')  //选取页面中所有的<p>元素
```

**实例**

点击按钮隐藏所有`<p>`元素。

```html
		<p>123456789</p>
		<p>123456789</p>
		<p>123456789</p>
		<p>123456789</p>
		<button type="button">btn</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('p').hide();
				})
			})
```

###  id选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

```javascript
$('#t1')   //选取id为t1的元素
```

**实例**

点击按钮隐藏有id="t1"属性的元素。

```html
		<p>123456789</p>
		<p id="t1">12345678910</p>
		<p>123456789</p>
		<p>123456789</p>
		<button type="button">btn</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('#t1').hide();
				})
			})
```

###  class选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

```javascript
$('.t1')   //选取class为t1的元素
```

**实例**

点击按钮后所有带有 class="test" 属性的元素都隐藏：
```html
		<p>123456789</p>
		<p class="t1">12345678910</p>
		<p>123456789</p>
		<p>123456789</p>
		<button type="button">btn</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('.class').hide();
				})
			})
```

###   其它选择器

| 语法                     | 描述                                             |
| ------------------------ | ------------------------------------------------ |
| $('*')                   | 选取所有元素                                     |
| $(this)                  | 选取当前的HTML元素                               |
| $('p.intro')             | 选取class为intro的<p>元素                        |
| $('p:first')             | 选取第一个<p>元素                                |
| $('ul li:first')         | 选取第一个<ul>元素的第一个<li>元素               |
| $('ul li:first-child')   | 选取每个<ul>元素的第一个<li>元素                 |
| $('[href]')              | 选取带有 href 属性的元素                         |
| $('a[target="_blank"]')  | 选取所有target属性值等于'_blank'的<a>元素        |
| $('a[target!="_blank"]') | 选取所有target属性值不等于'_blank'的<a>元素      |
| $(':button')             | 选取所有type="button"的<input>元素和<button>元素 |
| $('tr:even')             | 选取偶数位置的<tr>元素                           |
| $('tr:odd')              | 选取奇数位置的<tr>元素                           |

##  jQuery事件

页面对不同访问者的响应叫做事件。

事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。

实例：

- 在元素上移动鼠标。
- 选取单选按钮
- 点击元素

在事件中经常使用术语"触发"（或"激发"）例如： "当您按下按键时触发 keypress 事件"。

常见 DOM 事件：

| 鼠标事件                           | 键盘事件 | 表单事件 | 文档/窗口事件 |
| ---------------------------------- | -------- | -------- | ------------- |
| click(点击触发)                    | keypress | submit   | load          |
| dbclick(双击触发)                  | keydown  | change   | resize        |
| mouseenter(鼠标指针穿过元素时触发) | keyup    | focus    | scroll        |
| mouseleava(鼠标指针离开元素时触发) |          | blur     | unload        |
| hover                              |          |          |               |
| mousedown                          |          |          |               |
| mouseup                            |          |          |               |

###  jQuery 事件方法语法

在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。

页面中指定一个点击事件：

```javascript
$('p').click();
```

下一步是定义什么时间触发事件。您可以通过一个事件函数实现：

```javascript
$('p').click(function() {
    //动作触发后执行的方法
});
```

