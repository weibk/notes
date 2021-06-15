#  Vue的基本使用

```html
		<div id="app">
			<p>{{ msg }}</p>
		</div>
```

```java
			var app = new Vue({
				el:'#app',
				data:{
					msg: 'hello vue'
				}
```

##  实例参数分析

* el：元素的挂载位置(值可以是CSS选择器或者DOM元素)
* data：模型数据(值是一个对象)
##  模版语法
###  插值表达式{{  }}

* 将数据填充到HTML标签中
* 插值表达式支持基本的计算操作(算术运算，逻辑运算，字符串拼接等)

##  指令

指令的本质就是自定义属性

格式：以v- 开始

####  v-cloak

* 插值表达式存在的问题“闪动”(频繁刷新页面时会闪动插值表达式)
* 解决方法：使用v-cloak指令
* 原理：先隐藏、替换好值之后再显示最终结果

```css
		/* 提供样式 */
		[v-cloak] {
			display: none;
		}
```

```html
		<!-- 在插值表达式所在的标签中一添加v-cloak指令 -->
		<p v-cloak>{{ msg }}</p>		
```

####  v-text

更新元素的 `textContent`。如果要更新部分的 `textContent`，需要使用 `{{ Mustache }}` 插值。

```html
			<p v-text="msg">原始数据</p>
			<!-- 会替换掉原来的数据,没有闪动 -->
			<p v-cloak>原始数据{{ msg }}</p>
			<!-- 在指定的位置插值 -->
```

####  v-html

更新元素的 `innerHTML`。即可以解析html元素。

```html
<div v-html="html"></div>
```

在网站上动态渲染任意 HTML 是非常危险的，因为容易导致 [XSS 攻击](https://en.wikipedia.org/wiki/Cross-site_scripting)。只在可信内容上使用 `v-html`，**永不**用在用户提交的内容上。

####  v-pre

跳过这个元素和它的子元素的编译过程。可以用来显示原始 Mustache 标签。跳过大量没有指令的节点会加快编译。

```html
<span>{{ this will not be compiled }}</span>
```

####  v-once

只渲染元素和组件**一次**。随后的重新渲染，元素/组件及其所有的子节点将被视为静态内容并跳过。这可以用于优化更新性能。

```html
<!-- 单个元素 -->
<span v-once>This will never change: {{msg}}</span>
<!-- 有子元素 -->
<div v-once>
  <h1>comment</h1>
  <p>{{msg}}</p>
</div>
<!-- 组件 -->
<my-component v-once :comment="msg"></my-component>
<!-- `v-for` 指令-->
<ul> 
  <li v-for="i in list" v-once>{{i}}</li>
</ul>
```

v-once应用场景：如果显示的信息后续不需要再进行更改，可以使用v-once指令，提高性能。

####  v-model

​    用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。

- **限制**：
  - `<input>`
  - `<select>`
  - `<textarea>`
  - components
- **修饰符**：
  - `.lazy` - 用`change`事件取代 `input` 监听  事件
  - `.number` - 输入字符串转为有效的数字
  - `.trim` - 自动过滤用户输入的首尾空格

```html
		<input type="text" v-model="msg" />
		<h2>{{ msg }}</h2>
```

####  MVVM设计思想

M(model)(数据)

V(view)(视图)

VM(view-model)

V------>M: DOM Listeners 事件监听

M------>V: Data Bindings  数据绑定

###  事件绑定
####  v-on

```html
			<input type="button" v-on:click="num++" />
			<h2>{{ num }}</h2>
```

v-on:可以直接写成@同下:

```html
			<input type="button" @click="num++" />
			<h2>{{ num }}</h2>
```

调用函数的方法：

```html
			<input type="button" @click="add" value="btn2"/>
			<input type="button" @click="add()" value="btn3"/>
			<h2>{{ num }}</h2>
```

```javascript
			var app = new Vue({
				el:'#app',
				data:{
					msg: 'hello vue',
					num: 1
				},
				methods: {
					add: function(){
						this.num++;
					}
				}
			})
```

传参方式：普通参数和事件对象
```html
			<input type="button" @click="dec" value="btn2"/>
			<input type="button" @click="add(123,456,$event)" value="btn3"/>
			<h2>{{ num }}</h2>
```

```javascript
			var app = new Vue({
				el:'#app',
				data:{
					msg: 'hello vue',
					num: 1
				},
				methods: {
					add: function(n1,n2,event){
						this.num++;
                        console.log(n1);
                        console.log(n2);
                        console.log(event.target);                        
					},
                    dec: function(event){
                        this.num--;
                        console.log(event.target);
                    }
				}
			})
```

**事件修饰符：**

stop:阻止事件冒泡

```html
<input type="button" @click.stop="dec" value="btn2"/>
```

prevent:阻止默认行为

```html
<input type="button" @click.prevent="dec" value="btn2"/>
```

capture:添加事件监听器时使用事件捕获模式，即内部元素触发的事件先在此处理，然后才交由内部元素处理。

```html
<div v-on:click.capture="doThis">...</div>
```

self:只当`event.target`是当前元素自身时触发处理函数。

```html
<div v-on:click.self="doThat">...</div>
```

once:事件将只会触发一次。

```html
<a v-on:click.once="doThis"></a>
```

passive:不拦截默认行为。

```html
<div v-on:scroll.passive="onScroll">...</div>
```

**按键修饰符:**

在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 `v-on` 在监听键盘事件时添加按键修饰符：

```html
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">
```

你可以直接将 [`KeyboardEvent.key`](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values) 暴露的任意有效按键名转换为 kebab-case 来作为修饰符。

```html
<input v-on:keyup.page-down="onPageDown">
```

在上述示例中，处理函数只会在 `$event.key` 等于 `PageDown` 时被调用。

自定义按键修饰符

```javascript
Vue.config.keyCodes.f1 = 112;
```

###  属性绑定

####  v-bind

```html
		<div id="app">
			<a v-bind:href="url">baidu</a>
            <!--可以简写为:-->
			<a :href="url">baidu</a>
            
		</div>
```

```javascript
			var app = new Vue({
				el:'#app',
				data: {
					url: 'http://www.baidu.com'
				}
			})
```

加法器：

```html
		<div id="app">
			<span>n1:</span>
			<input type="number" v-model="n1"/>
			<span>n2:</span>
			<input type="number" v-model="n2"/>
			<button type="button" @click="add">计算</button>
			<span>计算结果:</span>
			<span>{{ result }}</span>
		</div>
```

```javascript
			var app = new Vue({
				el:'#app',
				data: {
					n1: '',
					n2: '',
					result: ''
				},
				methods: {
					add: function() {
						this.result = parseInt(this.n1) + parseInt(this.n2);
					}
				}
			})
```



###  样式绑定

class样式处理：默认的class会保留

对象语法:

```css
		.active {
			border: 2px solid aqua;
			width: 50px;
			height: 50px;
		}
		.error {
			background-color: darkblue;
		}

```



```html
		<div id="app">
			<div :class="{active: isActive,error: isError}">
				
			</div>
			<button type="button" @click="handle">btn</button>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					isActive: true,
					isError: true
				},
				methods: {
					handle: function() {
						this.isActive = !this.isActive;
						this.isError = !this.isError;
					}
				}
			})
```

数组语法

```css
		.active {
			border: 2px solid aqua;
			width: 50px;
			height: 50px;
		}
		.error {
			background-color: pink;
		}
```

```html
		<div id="app">
			<div :class="[activeClass,erroeClass]">
				测试
			</div>
			<button type="button" @click="handle1">btn</button>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					activeClass: 'active',
					erroeClass: 'error'
				},
				methods: {
					handle1: function() {
						this.activeClass = '';
						this.erroeClass = '';
					}
				}
			})
```

style样式处理：

```html
		<div id="app">
			<div :style="objStyles">
				测试
			</div>
			<button type="button" @click="handle2">btn</button>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					objStyles: {
						border: '2px solid pink',
						width: '200px',
						height: '200px'
					}
				},
				methods: {
					handle2: function() {
						this.objStyles.width = '500px';
					}
				}
			})
```

###  分支循环结构

####  分支结构

#####  v-if  v- else-if  v-else  v-show(条件渲染)

```html
		<div id="app">
			<p v-if="num > 50">num &gt; 50</p>
			<p v-else-if="num > 40">40 &lt; num &le; 50</p>
			<p v-else-if="num > 30">30 &lt; num &le; 40 </p>
			<p v-else>num &le; 30</p>
            <p v-show="num == 20">num=20</p>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					num: 21
				}
			})
```

`v-show`的原理：通过控制元素的display属性来控制元素的显示和隐藏

`v-if`控制元素是否显示到页面

如果显示和隐藏变化频繁，用`v-show`

####  循环结构

#####  v-for

````html
			<h3 :key="index" v-for="item in arr">{{ item }}</h3>
			<h3 :key="index" v-for="(item,index) in arr">{{ index }}----{{ item }}</h3>
			<h5 :key="item.id" v-for="item in arr1">
				<span>{{ item.ename }}</span>
				<span>{{ item.cname }}</span>
			</h5>
````

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					arr: [1,2,3,4,5,6,7,8,9],
                    arr1: [{
                        id: 1,
						ename: 'apple',
						cname: '苹果'
					},{
                        id: 2,                        
						ename: 'orange',
						cname: '橘子'
					},{
                        id: 3,                        
						ename: 'banana',
						cname: '香蕉'
					}]
				}
			})
```

**遍历对象：**

```html
			<h6 v-for="(value,key,index) in obj">
				{{ index }}--{{ key }}--{{ value }}
			</h6>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					obj: {
						sid: '20171514116',
						sname: '魏家剑',
						sex: '男',
						age: 18
					}
				}
			})
```

tab切换

```css
			.tab ul {
				overflow: hidden;
				margin: 0;
				padding: 0;
			}
			
			.tab ul li {
				box-sizing: border-box;
				list-style: none;
				border-right: 2px solid pink;
				border-top: 2px solid pink;
				float: left;
				width: 100px;
				height: 45px;
				text-align: center;
				line-height: 45px;
				font-size: 25px;
				cursor: pointer;
			}
			
			.tab ul li:first-child {
				border-left: 2px solid pink;
			}
			
			.tab ul li.active {
				background-color: aqua;
			}
			.tab div {
				box-sizing: content-box;
				width: 600px;
				border: 2px solid pink;
				border-top: 0px;
				display: none;
			}
			
			.tab div img {
				width: 100%;
			}
			
			.tab div.current {
				display: block;
			}
```

```html
		<div id="app">
			<div class="tab">
				<ul>	
					<li @click="tabChange(index)" :class="currentIndex==index?'active':''" :key="item.id" v-for="(item,index) in list">{{ item.title }}</li>
				</ul>
				<div :class="currentIndex==index?'current':''" :key="item.id" v-for="(item,index) in list">
					<img :src="item.path" alt="">
				</div>
			</div>
		</div>

```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					currentIndex: 0,
					list: [{
						id: 1,
						title: '01',
						path: './img/03.jpg'
					},{
						id: 2,
						title: '02',
						path: './img/04.jpg'
					},{
						id: 3,
						title: '03',
						path: './img/07.jpg'
					}]
				},
				methods: {
					tabChange: function(index) {
						this.currentIndex = index;
					}
				}
			})

```

**声明式编程：**

模版的结构和最终的显示效果基本一致。

##  Vue的常用特性

###  表单操作(单行文本，单选，多选框，下拉选框，多行文本)

```html
		<div id="app">
			<form action="" method="post">
				<div>
					<span>姓名：</span>
					<span>
						<input type="text" v-model="uname" />
					</span>
				</div>
				<div>
					<span>性别：</span>
					<input type="radio" name="" id="male" value="1" v-model="gender"/>
					<label for="male">男</label>
					<input type="radio" name="" id="female" value="2" v-model="gender"/>
					<label for="female">女</label>
				</div>
				<div>
					<span>爱好：</span>
					<input type="checkbox" name="" value="ball" v-model="hobby"/>
					<label for="ball">篮球</label>
					<input type="checkbox" name="" value="sing" v-model="hobby"/>
					<label for="sing">唱歌</label>
					<input type="checkbox" name="" value="code" v-model="hobby"/>
					<label for="code">写代码</label>
				</div>
				<div>
					<span>职业：</span>
					<select name="" v-model="occupation" ><!-- multiple="true" -->
						<option value ="0">---请选择职业---</option>
						<option value ="1">教师</option>
						<option value ="2">软件工程师</option>
						<option value ="3">web工程师</option>
						<option value ="4">律师</option>
					</select>
				</div>
				<div>
					<span>个人简介：</span>
					<textarea rows="10" cols="20" v-model="desc">
						
					</textarea>
				</div>
				<input type="submit" value="提交" @click.prevent="handle"/>
			</form>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					uname: 'lisi',
					gender: 1,
					hobby: [],
					occupation: 0,
					desc: ''
				},
				methods: {
					handle: function() {
						console.log(this.uname);
						console.log(this.gender);
						console.log(this.hobby);
						console.log(this.occupation);
						console.log(this.desc);
					}
				}
			})
```

####  表单域修饰符

#####  number：转化为数值

```html
<input v-model.number="age" type="number">
```

#####  trim：去掉开始和结尾的空格

```html
<input v-model.number="age" type="number">
```

#####  lazy：将input(内容变化触发)事件切换为change(失去焦点触发)事件

```html
<input v-model.lazy="text" type="text">
```

###  自定义指令

自动获取焦点

```html
	<div id="app">
		<input type="text" name="" id="" value="" v-focus />
	</div>
```

```javascript
			//注册一个自定义的v-focus指令
			Vue.directive('focus',{
                //当被绑定的元素插入到 DOM 中时……
				inserted: function(el) {
                    //聚焦元素
					el.focus();
				}
			});
			var app = new Vue({
				el: '#app',
				data: {
					
				},
				methods: {
					
				}
			})
```

定义局部指令

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					
				},
				methods: {
					
				},
				directives: {
					focus: {
						inserted: function(el) {
							el.focus();
						}
					}
				}
			})
```

带参数的自定义指令

```javascript
			Vue.directive('color',{
				bind: function(el,binding) {
					console.log(binding);
					el.style.backgroundColor = binding.value.color;
				}
			});
			var app = new Vue({
				el: '#app',
				data: {
					msg: {
						color: 'pink'
					}
				},
				methods: {
					
				}
			})
```

###  计算属性(computed)

反转字符串

```html
		<div id="app">
			<div>{{ msg }}</div>
			<div>{{ reverseStr }}</div>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					msg: 'abcdefg'
				},
				methods: {
					
				},
				computed: {
					reverseStr: function() {
						return this.msg.split('').reverse().join('');
					}
				}
			})
```

计算属性(`computed`)和方法(`methods`)的区别：

`computed`是基于它们的依赖进行缓存的，只要数据不更改，只计算一次，之后的调用都用第一次的结果。

方法不存在缓存。

**计算属性的set和get**

计算属性一般没有set方法，只有get方法，是只读属性

```javascript
var app = new Vue({
				el: '#app',
				data: {
					firstName: 'Tom',
                    lastName: 'Jerry'
				},
				methods: {
					
				},
				computed: {
					fullname: {
                        set: function() {
                            
                        },
                        get: function() {
                            return this.firstName + this.lastName;
                        }
                    }
				}
			})
```

省略set方法后可以写成

```javascript
var app = new Vue({
	el: '#app',
	data: {
		firstName: 'Tom',
        lastName: 'Jerry'
		},
	methods: {
					
	},
	computed: {
		fullname: function() {
            return this.firstName + this.lastName;
        }
	}
})
```

###  过滤器

**作用：**  

格式化数据，比如将字符串格式化为首字母大写，将日期格式化为指定格式等。

**自定义过滤器**

```javascript
			Vue.filter('过滤器名称', function(value){
                //过滤器业务逻辑
            })
```

**过滤器使用**

```html
			<div>{{ msg | upper }}</div>
			<div>{{ msg | upper | lower }}</div>
			<div v-bind:id="id | formatID"></div>
```

首字母大写

```html
		<div id="app">
			<input type="text" v-model="msg"/>
			<div>{{ msg | upper }}</div>
			<div>{{ msg | upper | lower }}</div>
			<div :id="msg | upper">111</div>
		</div>
```

```javascript
			Vue.filter('upper', function(val){
				return val.charAt(0).toUpperCase() + val.slice(1);
			});
			Vue.filter('lower', function(val){
				return val.charAt(0).toLowerCase() + val.slice(1);
			});
			var app = new Vue({
				el: '#app',
				data: {
					msg: ''
				},
				methods: {
					
				}
			})
```

定义局部过滤器

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					
				},
				methods: {
					
				},
				filters: {
                    upper: function(val){
                        return val.charAt(0).toUpperCase() + val.slice(1);
                    }
                }
			})
```

带参数的过滤器，格式化日期

```html
		<div id="app">
			<div>{{ date | format('yyyy-MM-dd') }}</div>
		</div>
```

```javascript
			Vue.filter('format', function(val,arg1){
				if(arg1 == 'yyyy-MM-dd'){
					var ret = '';
					ret += val.getFullYear() + '-' +  (val.getMonth() + 1) + '-' + val.getDate();
					return ret;
				}
			});
			var app = new Vue({
				el: '#app',
				data: {
					date: new Date()
				},
				methods: {
					
				}
			})
```



###  侦听器

**侦听器应用场景：**

数据变化时执行异步或开销较大的操作。

**侦听器的用法：**

```html
		<div id="app">
			<div>
				<span>名：</span>
				<span>
					<input type="text" v-model="firstName"/>
				</span>
			</div>
			<div>
				<span>姓：</span>
				<span>
					<input type="text" v-model="lastName"/>
				</span>
			</div>
			<div>{{ fullName }}</div>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					firstName: 'Jim',
					lastName: 'Green',
					fullName: 'Jim Green'
				},
				watch: {
					firstName: function(val) {
						this.fullName = val + ' ' + this.lastName;
					},
					lastName: function(val) {
						this.fullName = this.firstName + ' ' + val;
					}
				}
			})
```

验证用户名是否可用：

```html
		<div id="app">
			<div>
				<span>用户名：</span>
				<span>
					<input type="text" v-model.lazy="uname"/>
				</span>
				<span>{{ tip }}</span>
			</div>
		</div>
```

```javascript
			var app = new Vue({
				el: '#app',
				data: {
					uname: '',
					tip: ''
				},
				methods:{
					checkName: function(uname) {
						var that = this;
						setTimeout(function() {
							if(uname == 'admin'){
								that.tip = '用户名已存在';
							}else{
								that.tip = '用户名可用';
							}
						},2000)
					}
				},
				watch: {
					uname: function(val){
						this.checkName(val);
						this.tip = '正在验证';
					}
				}
			})
```

###  生命周期

**beforeCreate:** 在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用。

 **created:**在实例创建完成后被立即调用。在这一步，实例已完成以下的配置：数据观测 (data observer)，property 和方法的运算，watch/event 事件回调。然而，挂载阶段还没开始，`$el` property 目前尚不可用。

**beforeMount:**在挂载开始之前被调用：相关的 `render` 函数首次被调用。(**该钩子在服务器端渲染期间不被调用。**)

**mounted:**实例被挂载后调用，这时 `el` 被新创建的 `vm.$el` 替换了。如果根实例挂载到了一个文档内的元素上，当 `mounted` 被调用时 `vm.$el` 也在文档内。(**该钩子在服务器端渲染期间不被调用。**)

**beforeupdate:**数据更新时调用，发生在虚拟 DOM 打补丁之前。这里适合在更新之前访问现有的 DOM，比如手动移除已添加的事件监听器。(**该钩子在服务器端渲染期间不被调用。**)

**update:**由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。()

当这个钩子被调用时，组件 DOM 已经更新，所以你现在可以执行依赖于 DOM 的操作。然而在大多数情况下，你应该避免在此期间更改状态。如果要相应状态改变，通常最好使用[计算属性](https://cn.vuejs.org/v2/api/#computed)或 [watcher](https://cn.vuejs.org/v2/api/#watch) 取而代之。(**该钩子在服务器端渲染期间不被调用。**)

**activated:**被 keep-alive 缓存的组件激活时调用。(**该钩子在服务器端渲染期间不被调用。**)

**deactivate:**被 keep-alive 缓存的组件停用时调用。(**该钩子在服务器端渲染期间不被调用。**)

**beforeDestroy:**实例销毁之前调用。在这一步，实例仍然完全可用。(**该钩子在服务器端渲染期间不被调用。**)

**destroyed:**实例销毁后调用。该钩子被调用后，对应 Vue 实例的所有指令都被解绑，所有的事件监听器被移除，所有的子实例也都被销毁。(**该钩子在服务器端渲染期间不被调用。**)