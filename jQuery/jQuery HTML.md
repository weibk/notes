#  jQuery HTML

##  jQuery 获取内容和属性

jQuery 中非常重要的部分，就是操作 DOM 的能力。

jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。

###  获得内容 text()、html()、val()

三个简单实用的用于 DOM 操作的 jQuery 方法：

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标记）
- val() - 设置或返回表单字段的值

**实例**

text()和html()

```javascript
			$(function() {
				console.log($('p').text());//这是段落中的粗体文本
				console.log($('p').html());//这是段落中的<b>粗体</b>文本
			})
//html()可以解析元素内容中包含的html元素，相当于innerhtml
```

val()

```html
		<input type="text" name="" id="" value="菜鸟教程" />
```

```javascript
			$(function() {
				console.log($('input').val());//菜鸟教程
			})
```

###  获取属性   attr()、prop()

对于 HTML 元素本身就带有的固有属性，在处理时，使用 **prop** 方法。

对于 HTML 元素我们自己自定义的 DOM 属性，在处理时，使用 **attr** 方法。

```html
		<a href="https://www.baidu.com/" target="_blank" action="delete">百度</a>
```

```javascript
			$(function() {
				console.log($('a').prop('href'));//https://www.baidu.com/
				console.log($('a').prop('target'));//_blank
				console.log($('a').prop('action'));//undefined
				console.log($('a').attr('action'));//delete
			})
```

##  jQuery 设置内容和属性

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标记）
- val() - 设置或返回表单字段的值

###  通过 text()、html() 以及 val() 方法来设置内容：

```html
		<input type="text" id="text1" value="" />
		<p id="text2"></p>
		<p id="text3"></p>
		<button id="btn1">设置text</button>
		<button id="btn2">设置html</button>
		<button id="btn3">设置val</button>
```

```javascript
			$(function() {
				$('#btn1').click(function() {
					$('#text2').text('<b>hello world</b>');
				});
				$('#btn2').click(function() {
					$('#text3').html('<b>hello world</b>');
				});
				$('#btn3').click(function() {
					$('#text1').val('菜鸟教程');
				});
			})
//text()不能解析html元素
```

###  text()、html() 以及 val() 的回调函数

上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

下面的例子演示带有回调函数的 text() 和 html()：

```html
		<p id="text2">这是一个有 <b>粗体</b> 字的段落。</p>
		<p id="text3">这是一个有 <b>粗体</b> 字的段落。</p>
		<button id="btn1">设置text</button>
		<button id="btn2">设置html</button>
```

```javascript
			$(function() {
				$("#btn1").click(function() {
					$("#text2").text(function(i, origText) {
						return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")";
					});
				})
				$("#btn2").click(function() {
					$("#text3").html(function(i, origText) {
						return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")";
					});
				});
			})
```

###  设置属性 attr()

```html
		<a href="">百度</a>
		<button>设置连接地址</button>
```

```javascript
			$(function() {
					$('button').click(function() {
						$('a').attr('href','https://www.baidu.com/');
					})
			})

```

##  jQuery 添加元素

用于添加新内容的四个 jQuery 方法：

- append() - 在被选元素的结尾插入内容
- prepend() - 在被选元素的开头插入内容
- after() - 在被选元素之后插入内容
- before() - 在被选元素之前插入内容

**注：**其中append和prepend是在元素的内部嵌入，after和before是下元素的外部嵌入。

**插入文本**

```html
		<p>
			<span>本来存在的span</span>
		</p>
```

```javascript
			$('p').append('通过append追加的内容');
			$('p').prepend('通过prepend追加的内容');
			$('p').after('通过after追加的内容');
			$('p').before('通过before追加的内容');
```

```html
		通过before追加的内容
		<p>
			通过prepend追加的内容<span>本来存在的span</span>通过append追加的内容
		</p>
		通过after追加的内容
```

###  添加若干新元素

```html
<p>这是一个段落。</p>
<button onclick="appendText()">追加文本</button>
```

```javascript
function appendText(){
	var txt1="<p>文本-1。</p>";              // 使用 HTML 标签创建文本
	var txt2=$("<p></p>").text("文本-2。");  // 使用 jQuery 创建文本
	var txt3=document.createElement("p");
	txt3.innerHTML="文本-3。";               // 使用 DOM 创建文本 text with DOM
	$("body").append(txt1,txt2,txt3);        // 追加新元素
}
```

##  jQuery 删除元素

如需删除元素和内容，一般可使用以下两个 jQuery 方法：

- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素。

###  jQuery remove()

jQuery remove() 方法删除被选元素及其子元素。

**实例**

```html
		<div id="app">
			<ul>
				<li>1</li>
				<li>2</li>
				<li>3</li>
			</ul>
		</div>
		<button>删除盒子</button>
```

```javascript
			$('button').click(function() {
				$('#app').remove();
			});
```

###  jQuery empty()

jQuery empty() 方法删除被选元素的子元素。

**实例**

```javascript
			$('button').click(function() {
				$('#app').empty();
			});
```

###  过滤删除

jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤。

该参数可以是任何 jQuery 选择器的语法。

下面的例子删除 class="italic" 的所有 <p> 元素：

```html
		<p class="italic">123456789</p>
		<p class="italic">123456789</p>
		<p>11111</p>
		<button>删除class="italic"</button>
```

```javascript
			$('button').click(function() {
				$('p').remove('.italic');
			});
```

##  jQuery 获取并设置CSS类

jQuery 拥有若干进行 CSS 操作的方法。我们将学习下面这些：

- addClass() - 向被选元素添加一个或多个类
- removeClass() - 从被选元素删除一个或多个类
- toggleClass() - 对被选元素进行添加/删除类的切换操作
- css() - 设置或返回样式属性

**实例样式表**

```css
.important {
        font-weight:bold;
        font-size:xx-large;
}
 
.blue {
        color:blue;
}
```

###  jQuery addClass()方法

下面的例子展示如何向不同的元素添加 class 属性。当然，在添加类时，您也可以选取多个元素：

```html
		<h1>标题1</h1>
		<h2>标题2</h2>
		<p>这是一个段落</p>
		<p>这是另一个段落</p>
		<div>
			这是一些重要的文本
		</div>
		<button>为元素添加样式</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('h1,h2,p').addClass('blue');
					$('div').addClass('important');
				})
			})
```

###  jQuery removeClass()方法

下面的例子演示如何在不同的元素中删除指定的 class 属性：

```html
		<h1 class="blue">标题1</h1>
		<h2 class="blue">标题2</h2>
		<p class="blue">这是一个段落</p>
		<p class="blue">这是另一个段落</p>
		<div class="important">
			这是一些重要的文本
		</div>
		<button>为元素删除样式</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('h1,h2,p').removeClass('blue');
					$('div').removeClass('important');
				})
			})
```

###  jQuery toggleClass()方法

下面的例子将展示如何使用 jQuery toggleClass() 方法。该方法对被选元素进行添加/删除类的切换操作：

```html
		<h1 class="blue">标题1</h1>
		<h2 class="blue">标题2</h2>
		<p class="blue">这是一个段落</p>
		<p class="blue">这是另一个段落</p>
		<div class="important">
			这是一些重要的文本
		</div>
		<button>为元素添加/删除样式</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('h1,h2,p').toggleClass('blue');
					$('div').toggleClass('important');
				})
			})
```

##  jQuery css()方法

css() 方法设置或返回被选元素的一个或多个样式属性。

###  返回css属性

```css
		div {
			width: 200px;
			height: 200px;
			background-color: #FF1493;
			color: #0000FF;
			font-size: 30px;
		}
```

```html
		<div>
			123645
		</div>
```

```javascript
			$(function() {
				console.log($('div').css('background-color'));//rgb(255, 20, 147)
				console.log($('div').css('width'));//200px
				console.log($('div').css('font-size'));//30px
			})
```

###  设置css属性

**语法**

```javascript
$(selector).css('propertyname','value');
```

**实例**

```javascript
$('div').css('width','500px');
```

###  设置多个css属性

**语法**

```javascript
$(selector).css({'propertyname':'value','propertyname2':'value2',...});
```

**实例**

```javascript
				$('div').css({'width':'500px','background-color':'red'});
```

##  jQuery 尺寸

jQuery 提供多个处理尺寸的重要方法：

- width()
- height()
- innerWidth()
- innerHeight()
- outerWidth()
- outerHeight()

![尺寸](https://i.loli.net/2021/06/15/zJo7wKqI1i3aSbM.gif)

