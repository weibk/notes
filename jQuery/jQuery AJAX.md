#  jQuery AJAX

##  jQuery load()

jQuery load() 方法是简单但强大的 AJAX 方法。

load() 方法从服务器加载数据，并把返回的数据放入被选元素中。

**语法**

```javascript
$(selector).load(URL,data,callback);
//必需的 URL 参数规定您希望加载的 URL。
//可选的 data 参数规定与请求一同发送的查询字符串键/值对集合。
//可选的 callback 参数是 load() 方法完成后所执行的函数名称。
```

**实例**

示例文件demo_test.text的内容：

```html
<h2>jQuery AJAX 是个非常棒的功能！</h2>
<p id="p1">这是段落的一些文本。</p>
```

```html
		<div id="div1">
			使用AJAX修改内容
		</div>
		<button>修改</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('#div1').load('./demo_test.text');
				})
			})
```

也可以把 jQuery 选择器添加到 URL 参数。

下面的例子把 "demo_test.txt" 文件中 id="p1" 的元素的内容，加载到指定的` <div> `元素中：

```javascript
			$(function() {
				$('button').click(function() {
					$('#div1').load('./demo_test.text #p1');
				})
			})
```

可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：

- *responseTxt* - 包含调用成功时的结果内容
- *statusTXT* - 包含调用的状态
- *xhr* - 包含 XMLHttpRequest 对象

##  jQuery -AJAX get()和post()

### **GET 和 POST 方法的区别**：

**1、发送的数据数量**

在 GET 中，只能发送有限数量的数据，因为数据是在 URL 中发送的。

在 POST 中，可以发送大量的数据，因为数据是在正文主体中发送的。

**2、安全性**

GET 方法发送的数据不受保护，因为数据在 URL 栏中公开，这增加了漏洞和黑客攻击的风险。

POST 方法发送的数据是安全的，因为数据未在 URL 栏中公开，还可以在其中使用多种编码技术，这使其具有弹性。

**3、加入书签中**

GET 查询的结果可以加入书签中，因为它以 URL 的形式存在；而 POST 查询的结果无法加入书签中。

**4、编码**

在表单中使用 GET 方法时，数据类型中只接受 ASCII 字符。

在表单提交时，POST 方法不绑定表单数据类型，并允许二进制和 ASCII 字符。

**5、可变大小**

GET 方法中的可变大小约为 2000 个字符。

POST 方法最多允许 8 Mb 的可变大小。

**6、缓存**

GET 方法的数据是可缓存的，而 POST 方法的数据是无法缓存的。

**7、主要作用**

GET 方法主要用于获取信息。而 POST 方法主要用于更新数据。

###  $.get()

**语法**

```javascript
$.get(URL,callback);
//必需的 URL 参数规定您希望请求的 URL。
//可选的 callback 参数是请求成功后所执行的函数名。
```

**实例**

```html
		<button>发送一个 HTTP GET 请求并获取返回结果</button>
```

```javascript
			$(function() {
				$('button').click(function() {
					$.get('./demo_test.text',function(data,status) {
						alert('数据\n' +data + '\n状态\n' + status);
					});
				});
			});
```

###  $.post()

$.post() 方法通过 HTTP POST 请求向服务器提交数据。

**语法**

```javascript
$.post(URL,data,callback);
//必需的 URL 参数规定您希望请求的 URL。
//可选的 data 参数规定连同请求发送的数据。
//可选的 callback 参数是请求成功后所执行的函数名。
```

**实例**



