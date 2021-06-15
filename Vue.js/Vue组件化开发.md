#  Vue组件化开发

##  组件注册

###  全局组件注册

**语法**

```javascript
Vue.component(组件名称, {
    data: 组件数据,
    template: 组件模板内容,
    methods: 组件用到的方法
});
```

```javascript
const cpn = Vue.extend({
    data: 组件数据,
    template: 组件模板内容,
    methods: 组件用到的方法
});
Vue.component(组件名称, cpn);
```

**注意事项**:blue_heart:：

data必须是一个函数

组件模板内容必须是单个根元素

组件模版内容可以是模板字符串(``)(es6语法)

**组件命名方式：**

短横线：

```javascript
Vue.component('button-counter', {
    data: function() {
        
    },
    template: 组件模板内容,
    methods: 组件用到的方法
})
```

驼峰式：

在普通标签中应用时要转化成短横线的写法

```javascript
Vue.component('ButtonCounter', {
    data: function() {
        
    },
    template: 组件模板内容,
    methods: 组件用到的方法
})
```



**按钮点击次数**

```html
		<div id="app">
			<button-counter></button-counter>
			<button-counter></button-counter>
			<button-counter></button-counter>
		</div>
```

```javascript
			Vue.component('button-counter', {
				data: function() {
					return {
						count: 0
					}
				},
				template: '<button @click="handle">点击了{{count}}次</button>',
				methods: {
					handle: function() {
						this.count++;
					}
				}
			})
			var app = new Vue({
				el: '#app',
				data: {
					
				}
			});
```

##  局部组件注册

**语法**

```javascript
var ComponentA = {/*.........*/};
var ComponentB = {/*.........*/};
var ComponentC = {/*.........*/};
var vm = new Vue({
    el: '#app',
    data: {
        
    },
    components: {
        'component-a': ComponentA,
        'component-b': ComponentB,
        'component-c': ComponentC
    }
})
```

```html
		<div id="app">
			<hello-a></hello-a>
			<hello-b></hello-b>
			<hello-c></hello-c>
		</div>
```

```javascript
			var HelloA = {
				data: function() {
					return {
						msg: 'helloa'
					}
				},
				template: '<div>{{msg}}</div>'
			};
			var HelloB = {
				data: function() {
					return {
						msg: 'hellob'
					}
				},
				template: '<div>{{msg}}</div>'
			};
			var HelloC = {
				data: function() {
					return {
						msg: 'helloc'
					}
				},
				template: '<div>{{msg}}</div>'
			};
			var app = new Vue({
				el: '#app',
				data: {
					
				},
				components: {
					'hello-a': HelloA,
					'hello-b': HelloB,
					'hello-c': HelloC
				}
			});
```

##  组件模版分离

```html
<script type="text/x-template" id="cpn">
	<div>
		<h1>1111</h1>
	</div>
</script>
```

```html
<template id="cpn">
	<div>
		<h1>1111</h1>
	</div>
</template>
```

```javascript
Vue.component('button-counter', {
	data: function() {
		return {
			count: 0
		}
	},
	template: '#cpn',
})
```

##  组件间数据交互

###  通过Props向子组件传递数据

```html
		<div id="app">
			<blog-post v-bind:key="post.id" v-for="post in posts" v-bind:test-title="post.title"></blog-post>
		</div>
```

```javascript
			Vue.component('blog-post', {
				props: ['testTitle'],
				template: '<h2>{{ testTitle }}</h2>'
			});
			//props: {
			//	testTitle: {
            //        type: Array,
            //        default: function() {
            //            return [];
            //        },
            //        require:true
            //    }
			//}
			var app = new Vue({
				el: '#app',
				data: {
					posts: [{
						id: 0,
						title: '123'
					},{
						id: 1,
						title: '456'
					},{
						id: 2,
						title: '789'
					}]
				}
			})
```

**props命名规则**

在props中使用驼峰式命名，在模板中要使用短横线的形式。

###  子组件向父组件传递数据

**子组件通过自定义事件向父组件传递信息**

```html
<div id="app">
			<span :style="{fontSize: fontSize + 'px'}">父组件的内容</span>
			<min-font @enlarge-text="handle()" :style="{fontSize: fontSize + 'px'}"></min-font>
		</div>
		<script type="text/javascript">
			Vue.component('min-font',{
				template: `<button @click="$emit('enlarge-text')">字体变大</button>`
			});
			var app = new Vue({
				el: '#app',
				data: {
					fontSize: 10
				},
				methods: {
					handle: function() {
						this.fontSize += 5;
					}
				}
			});
		</script>
```

##  父子组件的访问方式

###  父组件访问子组件($children或$refs)

```html
		<div id="app">
			<cpn></cpn>
			<button @click="btnClick">按钮</button>
		</div>
		<template id="cpn">
			<h2>子组件的内容</h2>
		</template>
		<script type="text/javascript">
			const app = new Vue({
				el: '#app',
				methods: {
					btnClick() {
						console.log(this.$children[0]);
					}
				},
				components: {
					cpn: {
						template: '#cpn',
						methods: {
							
						}
					}
				}
			})
		</script>
```

![](C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CVue.js%5Cimages%5C$children%20Or%20$refs.png)

```html
		<div id="app">
			<cpn ref="cpn1"></cpn>
			<button @click="btnClick">按钮</button>
		</div>
		<template id="cpn">
			<h2>子组件的内容</h2>
		</template>
		<script src="../js/vue.js" type="text/javascript" charset="utf-8"></script>
		<script type="text/javascript">
			const app = new Vue({
				el: '#app',
				methods: {
					btnClick() {
						console.log(this.$refs.cpn1)
					}
				},
				components: {
					cpn: {
						template: '#cpn',
						methods: {
							
						}
					}
				}
			})
		</script>
```

###  子组件访问父组件($parent)

```html
		<div id="app">
			<cpn></cpn>
		</div>
		<template id="cpn">
			<div>
				<h2>子组件的内容</h2>
				<button @click="btnClick">子组件中的按钮</button>
			</div>
		</template>
		<script type="text/javascript">
			const app = new Vue({
				el: '#app',
				data: {
					message: 'abcdefg'
				},
				components: {
					cpn: {
						template: '#cpn',
						methods: {
							btnClick() {
								console.log(this.$parent);
							}
						}
					}
				}
			})
		</script>
```

![](C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CVue.js%5Cimages%5C$parent.png)

###  访问根组件($root)

```html
			<div>
				<h2>子组件的内容</h2>
				<button @click="btnClick">子组件中的按钮</button>
			</div>
		</template>
		<script type="text/javascript">
			const app = new Vue({
				el: '#app',
				data: {
					message: 'abcdefg'
				},
				components: {
					cpn: {
						template: '#cpn',
						methods: {
							btnClick() {
								console.log(this.$root);
							}
						}
					}
				}
			})
		</script>
```

##  插槽(slot)

当组件渲染的时候，`<slot></slot>` 将会被替换为“slot中的内容”。插槽内可以包含任何模板代码，包括 HTML、甚至其它的组件：

```html
		<div id="app">
			<my-cpn>
				slot中的内容
			</my-cpn>
		</div>
		<template id="my-cpn">
			<div>
				<h2>子组件标题</h2>
				<slot></slot>
			</div>
		</template>
		<script src="../js/vue.js" type="text/javascript" charset="utf-8"></script>
		<script type="text/javascript">
			const app = new Vue({
				el: '#app',
				components: {
					'my-cpn': {
						template: '#my-cpn'
					}
					
				}
			})
		</script>
```

如果组件的 `template` 中**没有**包含一个 `<slot>` 元素，则该组件起始标签和结束标签之间的任何内容都会被抛弃。

###  后备内容(默认内容)

有时为一个插槽设置具体的后备 (也就是默认的) 内容是很有用的，它只会在没有提供内容的时候被渲染。当提供内容的时候默认内容会被替代。

```html
		<div id="app">
			<my-cpn></my-cpn>
		</div>
		<template id="my-cpn">
			<div>
				<h2>子组件标题</h2>
				<slot>默认内容</slot>
			</div>
		</template>
```

###  具名插槽

有时我们需要多个插槽。例如对于一个带有如下模板的 `<base-layout>` 组件：

```html
<div class="container">
  <header>
    <!-- 我们希望把页头放这里 -->
  </header>
  <main>
    <!-- 我们希望把主要内容放这里 -->
  </main>
  <footer>
    <!-- 我们希望把页脚放这里 -->
  </footer>
</div>
```

对于这样的情况，`<slot>` 元素有一个特殊的 attribute：`name`。这个 attribute 可以用来定义额外的插槽：

```html
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```

一个不带 `name` 的 `<slot>` 出口会带有隐含的名字“default”。

在向具名插槽提供内容的时候，我们可以在一个 `<template>` 元素上使用 `v-slot` 指令，并以 `v-slot` 的参数的形式提供其名称：

```html
<base-layout>
  <template v-slot:header>
    <h1>Here might be a page title</h1>
  </template>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```

现在 `<template>` 元素中的所有内容都将会被传入相应的插槽。任何没有被包裹在带有 `v-slot` 的 `<template>` 中的内容都会被视为默认插槽的内容。

然而，如果你希望更明确一些，仍然可以在一个 `<template>` 中包裹默认插槽的内容：

```html
<base-layout>
  <template v-slot:header>
    <h1>Here might be a page title</h1>
  </template>

  <template v-slot:default>
    <p>A paragraph for the main content.</p>
    <p>And another one.</p>
  </template>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```

注意 **`v-slot` 只能添加在 `<template>` 上** (只有[一种例外情况](#独占默认插槽的缩写语法))。

####  具名插槽缩写

```html
<base-layout>
  <template #header>
    <h1>Here might be a page title</h1>
  </template>

  <template #default>
    <p>A paragraph for the main content.</p>
    <p>And another one.</p>
  </template>

  <template #footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```

###  作用域插槽

有时让插槽内容能够访问子组件中才有的数据是很有用的。例如，设想一个带有如下模板的 `<current-user>` 组件：

```html
<span>
  <slot name="cpn">{{ user.lastName }}</slot>
</span>
```

我们可能想换掉备用内容，用名而非姓来显示。如下：

```html
<current-user>
  <template v-slot:cpn>
    {{ user.firstName }}
  </template>
</current-user>
```

然而上述代码不会正常工作，因为只有 `<current-user>` 组件可以访问到 `user` 而我们提供的内容是在父级渲染的。

为了让 `user` 在父级的插槽内容中可用，我们可以将 `user` 作为 `<slot>` 元素的一个 attribute 绑定上去：

```html
<span>
  <slot name="cpn" v-bind:user="user">
    {{ user.lastName }}
  </slot>
</span>
```

绑定在 `<slot>` 元素上的 attribute 被称为**插槽 prop**。现在在父级作用域中，我们可以使用带值的 `v-slot` 来定义我们提供的插槽 prop 的名字：

```html
<current-user>
  <template v-slot:default="slotProps">
    {{ slotProps.user.firstName }}
  </template>
</current-user>
```

在这个例子中，我们选择将包含所有插槽 prop 的对象命名为 `slotProps`，但你也可以使用任意你喜欢的名字。

### 独占默认插槽的缩写语法

在上述情况下，当被提供的内容*只有*默认插槽时，组件的标签才可以被当作插槽的模板来使用。这样我们就可以把 `v-slot` 直接用在组件上：

```html
<current-user v-slot:default="slotProps">
  {{ slotProps.user.firstName }}
</current-user>
```

这种写法还可以更简单。就像假定未指明的内容对应默认插槽一样，不带参数的 `v-slot` 被假定对应默认插槽：

```html
<current-user v-slot="slotProps">
  {{ slotProps.user.firstName }}
</current-user>
```

注意默认插槽的缩写语法**不能**和具名插槽混用，因为它会导致作用域不明确：

```html
<!-- 无效，会导致警告 -->
<current-user v-slot="slotProps">
  {{ slotProps.user.firstName }}
  <template v-slot:other="otherSlotProps">
    slotProps is NOT available here
  </template>
</current-user>
```

只要出现多个插槽，请始终为**所有的**插槽使用完整的基于 `<template>` 的语法：

```html
<current-user>
  <template v-slot:default="slotProps">
    {{ slotProps.user.firstName }}
  </template>

  <template v-slot:other="otherSlotProps">
    ...
  </template>
</current-user>
```

###  解构插槽Prop

作用域插槽的内部工作原理是将你的插槽内容包裹在一个拥有单个参数的函数里：

```javascript
function (slotProps) {
  // 插槽内容
}
```

这意味着 `v-slot` 的值实际上可以是任何能够作为函数定义中的参数的 JavaScript 表达式。所以在支持的环境下 ([单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)或[现代浏览器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#浏览器兼容))，你也可以使用 [ES2015 解构](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#解构对象)来传入具体的插槽 prop，如下：

```html
<current-user v-slot="{ user }">
  {{ user.firstName }}
</current-user>
```

这样可以使模板更简洁，尤其是在该插槽提供了多个 prop 的时候。它同样开启了 prop 重命名等其它可能，例如将 `user` 重命名为 `person`：

```html
<current-user v-slot="{ user: person }">
  {{ person.firstName }}
</current-user>
```

你甚至可以定义后备内容，用于插槽 prop 是 undefined 的情形：

```html
<current-user v-slot="{ user = { firstName: 'Guest' } }">
  {{ user.firstName }}
</current-user>
```