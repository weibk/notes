#  jQuery 效果

##  jQuery 隐藏/显示

###  jQuery  hide() 和 show()

**语法**

```javascript
$(selector).hide(speed,callback);
$(selector).show(speed,callback);
//可选参数speed，规定显示或隐藏的速度，可取'slow'、'fast'或具体毫秒数
//可选参数callback，是显示或隐藏完成后执行的回调函数
```

**实例**

```css
		#app {
			width: 200px;
			height: 200px;
			background-color: pink;
		}
```

```html
		<div id="app">
			<button type="button">按钮</button>
			<p>content</p>
		</div>
		<button id="btn2">按钮</button>
```

```javascript
			$(function() {
				var flag = false;
				$('#btn1').click(function() {
					$('#app').hide(1000,'linear',function() {
						alert('隐藏成功');
						flag = true;
					})
				});
				$('#btn2').click(function() {
					if(flag){
						$('#app').show(1000,'linear',function() {
							alert('显示成功');
						})
					}
				})
			})

```

###  jQuery toggle()

通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：

**语法**

```javascript
$(selector).toggle(speed,callback);
```

**实例**

```html
		<div id="app">
			<button id="btn1">按钮</button>
			<p>content</p>
		</div>
		<button id="btn2">按钮</button>
```

```javascript
			$(function() {
				$('#btn2').click(function() {
					$('#app').toggle(1000,'linear',function() {
						alert('切换成功');
					})
				})
			})

```

##  jQuery 淡入淡出

###  jQuery fadeIn()

jQuery fadeIn() 方法用于淡入隐藏元素。

**语法**

```javascript
$(selector).fadeIn(speed,callback);
//可选参数speed，规定显示或隐藏的速度，可取'slow'、'fast'或具体毫秒数
//可选参数callback，是显示或隐藏完成后执行的回调函数
```

**实例**

```css
		div {
			width: 100px;
			height: 100px;
			display: none;
		}
		#box1 {
			background-color: pink;
		}
		#box2 {
			background-color: hotpink;
		}
		#box3 {
			background-color: deeppink;
		}
```

```html
		<button id="btn">按钮</button>
		<div id="box1"></div>
		<div id="box2"></div>
		<div id="box3"></div>
```

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#box1').fadeIn('fast');
					$('#box2').fadeIn('slow');
					$('#box3').fadeIn(2000);
				})
			})
```

###  jQuery fadeOut()

jQuery fadeOut() 方法用于淡出可见元素。

**语法**

```javascript
$(selector).fadeOut(speed,callback);
```

**实例**

```javascript
		<button id="btn">淡入</button>
		<button id="btn1">淡出</button>
		<div id="box1"></div>
		<div id="box2"></div>
		<div id="box3"></div>
```

```javascript
			$(function() {
				$('#btn1').click(function() {
					$('#box1').fadeOut('fast');
					$('#box2').fadeOut('slow');
					$('#box3').fadeOut(2000);
				})
			})
```

###  jQuery fadeToggle()

jQuery fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。

如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果。

如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果。

**语法**

```javascript
$(selector).fadeToggle(speed,opacity,callback);
```

必需的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。

可选的 callback 参数是该函数完成后所执行的函数名称。

**实例**

```css
		div {
			width: 100px;
			height: 100px;
			margin-bottom: 20px;
		}
		#box1 {
			background-color: red;
		}
		#box2 {
			background-color: green;
		}
		#box3 {
			background-color: blue;
		}
```

```html
		<button>淡入/淡出</button>
		<div id="box1"></div>
		<div id="box2"></div>
		<div id="box3"></div>
```

```javascript
			$(function() {
				$('button').click(function() {
					$('#box1').fadeToggle('fast');
					$('#box2').fadeToggle('slow');
					$('#box3').fadeToggle(2000);
				})
			})
```

###  jQuery fadeTo()

jQuery fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。

**语法**

```javascript
$(selector).fadeTo(speed,opacity,callback);
//必需的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。无默认值
//fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。
//可选的 callback 参数是该函数完成后所执行的函数名称。
```

**实例**

```css
		div {
			width: 100px;
			height: 100px;
			margin-bottom: 20px;
		}
		#box1 {
			background-color: red;
		}
		#box2 {
			background-color: green;
		}
		#box3 {
			background-color: blue;
		}
```

```html
		<button id="btn3">颜色变淡</button>
		<div id="box1"></div>
		<div id="box2"></div>
		<div id="box3"></div>
```

```javascript
			$(function() {
				$('#btn3').click(function() {
					$('#box1').fadeTo('fast',0.25);
					$('#box2').fadeTo('slow',0.5);
					$('#box3').fadeTo(2000,0.75);
				})
			})
```

##  jQuery 滑动

通过 jQuery，您可以在元素上创建滑动效果。

jQuery 拥有以下滑动方法：

- slideDown()
- slideUp()
- slideToggle()

###  jQuery slideDown()

jQuery slideDown() 方法用于向下滑动元素。

**语法**

```javascript
$(selector).slideDown(speed,callback);
//可选参数speed，规定效果的时长，可取以下值：'slow'  'fast' 毫秒数
//可选参数callback，定义滑动完成后执行的回调函数
```

**实例**

```css
		#app {
			width: 300px;
			height: 300px;
			margin: 20px auto;
		}
		#btn,
		#slide {
			width: 100%;
			background-color: aqua;
		}
		#btn {
			height: 50px;
		}
		#slide {
			height: 250px;
			display: none;
		}
```

```html
		<div id="app">
			<button id="btn">点我滑下面板</button>
			<div id="slide"></div>
		</div>
```

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#slide').slideDown('slow');
				})
			})
```

###  jQuery slideUp()

jQuery slideUp() 方法用于向上滑动元素。

**语法**

```javascript
$(selector).slideUp(speed,callback);
//可选参数speed，规定效果的时长，可取以下值：'slow'  'fast' 毫秒数
//可选参数callback，定义滑动完成后执行的回调函数
```

**实例**

```css
		#app {
			width: 300px;
			height: 300px;
			margin: 20px auto;
		}
		#btn,
		#btn2 {
			width: 100%;
			background-color: aqua;
		}
		#btn,
		#btn2 {
			height: 50px;
		}
		#slide {
			width: 100%;
			height: 200px;
			background-color: pink;
			display: none;
		}
```

```html
		<div id="app">
			<button id="btn">点我滑下面板</button>
			<div id="slide"></div>
			<button id="btn2">点我收起面板</button>
		</div>
```

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#slide').slideDown('slow');
				});
				$('#btn2').click(function() {
					$('#slide').slideUp('slow');
				});
			})
```

###  jQuery slideToggle()

jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们。

如果元素向上滑动，则 slideToggle() 可向下滑动它们。

**语法**

```javascript
$(selector).slideToggle(speed,callback);
```

**实例**

```html
		<div id="app">
			<button id="btn">点我滑下或收起面板</button>
			<div id="slide"></div>
		</div>
```

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#slide').slideToggle('slow');
				});
			})
```

##  jQuery 动画

jQuery animate() 方法用于创建自定义动画。

**语法**

```javascript
$(selector).animate({params},speed,callback);
//必需的 params 参数定义形成动画的 CSS 属性。
//可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。默认为'fast'
//可选的 callback 参数是动画完成后所执行的函数名称。
```

**实例**

```css
		#app {
			position: relative;
			width: 150px;
			height: 150px;
			background-color: #FF69B4;
		}
```

```html
		<button id="btn">移动盒子</button>
		<div id="app"></div>
```

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#app').animate({
						left: '200px'
					},2000);
				});
			})
```

**生成动画中可同时操作多个属性**

```javascript
		$(function() {
				$('#btn').click(function() {
					$('#app').animate({
						left: '200px',
						width: '300px',
						height: '300px'
					},2000);
				 });
			})
```

**使用相对值**

```javascript
			$(function() {
				$('#btn').click(function() {
					$('#app').animate({
						left: '200px',
						width: '+=50px',
						height: '+=50px'
					},1000);
				});
			})
```

 **使用预定义的值**

您甚至可以把属性的动画值设置为 "show"、"hide" 或 "toggle"：

```javascript
			$(function() {
				    $('#btn').click(function() {
				    	$('#app').animate({
				    		width: 'toggle'
				    	},2000);
				    });
			})
```

**使用队列功能**

```javascript
			$(function() {
				    $('#btn').click(function() {
				    	$('#app').animate({
							height: '300px',
							opacity: '0.5',
				    	},'slow');
						$('#app').animate({
							width: '300px',
							opacity: '0.8',
						},'fast');
						$('#app').animate({
							height: '150px',
							opacity: '0.6',
						},'slow');
						$('#app').animate({
							width: '150px',
							opacity: '0.9',
						},2000);
				    });
			})
```

##  jQuery 停止动画

```javascript
$(selector).stop(stopAll,goToEnd);
//可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
//可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。
//因此，默认地，stop() 会清除在被选元素上指定的当前动画。
```

**实例**

```html
		<button id="btn2">停止动画</button>
		<button id="btn">移动盒子</button>
		<div id="app"></div>
```

```javascript
			$(function() {
				    $('#btn').click(function() {
				    	$('#app').animate({
							height: '300px',
							opacity: '0.5',
				    	},'slow');
						$('#app').animate({
							width: '300px',
							opacity: '0.8',
						},'fast');
						$('#app').animate({
							height: '150px',
							opacity: '0.6',
						},1000);
						$('#app').animate({
							width: '150px',
							opacity: '0.9',
						},2000);
				    });
					$('#btn2').click(function() {
						$('#app').stop();
					})
			 })
```

##  jQuery 链

通过 jQuery，可以把动作/方法链接在一起。

Chaining 允许我们在一条语句中运行多个 jQuery 方法（在相同的元素上）。

**实例**

```javascript
$('#p1').css("color","red").slideUp(2000).slideUp(2000);
//'p1'元素熟悉吗会变为红色，然后向上滑动，再向下滑动
```

