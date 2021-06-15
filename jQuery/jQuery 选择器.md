#  jQuery 选择器

##  基本选择器

| 选择器     | 描述         | 实例           | 选取                          |
| ---------- | ------------ | -------------- | ----------------------------- |
| *          | 通配符选择器 | $('*')         | 所有元素                      |
| #id        | id选择器     | $('#box')      | id="box"的元素                |
| .class     | 类选择器     | $('.intro')    | class="intro"的所有元素       |
| element    | 元素选择器   | $('p')         | 所有`<p>`元素                 |
| .class,#id | 组合选择器   | $(.intro,#box) | class="intro"或id="box"的元素 |

##  过滤选择器

| 选择器         | 实例                 | 选取                                                         |
| -------------- | -------------------- | ------------------------------------------------------------ |
| :first         | $('p:first')         | 选取属于其父元素中第一个为 `<p> `的元素(必须是所有元素中的第一个) |
| :last          | $('p:last')          | 选取属于其父元素的最后一个` <p> `的元素(必须是所有元素中的最后一个) |
| :even          | $('li:even')         | 选择下标为偶数的li元素                                       |
| :odd           | $('li:odd')          | 选择下标为奇数的li元素                                       |
| :first-of-type | $('p:first-of-type') | 选取属于其父元素中第一个`<p>`元素                            |
| :last-of-type  | $('p:last-of-type')  | 选取属于其父元素中最后一个`<p>`元素                          |
| :eq            | $('ul li:eq(4)')     | 列表中的第5个li(index值从0开始)                              |
| :gt            | $('ul li:gt(2)')     | index大于2的li元素                                           |
| :lt            | $('ul li:lt(2)')     | index小于2的li元素                                           |

##  层次选择器

| 选择器             | 实例         | 选取                                           |
| ------------------ | ------------ | ---------------------------------------------- |
| parent>child       | $('div > p') | `<div>`元素的直接子元素中的所有`<p>`元素       |
| parent descendant  | $('div p')   | `<div>`元素后代中的所有`<p>`元素               |
| element + next     | $('div + p') | 选取与每个` <div> `元素相邻的下一个` <p> `元素 |
| element ~ siblings | $('div ~ p') | 与`<div>`元素同级的所有`<p>`元素               |

##  内容过滤选择器

| 选择器          | 实例                     | 选取                                        |
| --------------- | ------------------------ | ------------------------------------------- |
| :contains(text) | $('p:contains("hello")') | 所有包含文本'hello'的`<p>`元素              |
| :empty          | $('p:empty')             | 不包含子元素或文本的所有`<p>`元素，即空元素 |
| :has(selector)  | $('div:has(p)')          | 所有包含有` <p> `元素在其内的`<div>` 元素   |
| :parent         | $('')                    | 匹配含有子元素或者文本的元素                |

##  可见性过滤选择器

| 选择器    | 实例          | 选取                |
| --------- | ------------- | ------------------- |
| :hidden   | $('p:hidden') | 所有隐藏的`<p>`元素 |
| :visiable | $('p:table')  | 所有可见的表格      |

##  属性过滤选择器

| 选择器                      | 实例                        | 选取                                                         |
| --------------------------- | --------------------------- | ------------------------------------------------------------ |
| [attribute]                 | $('[href]')                 | 所有带有 href 属性的元素                                     |
| [attribute=value]           | $('[href="default.html"]')  | 所有带有 href 属性且值等于 "default.htm" 的元素              |
| [attribute!=value]          | $('[href!="default.html"]') | 所有带有 href 属性且值不等于 "default.htm" 的元素            |
| [attribute$=value]          | $('[href$=".jpg"]')         | 所有带有 href 属性且值以 ".jpg" 结尾的元素                   |
| [attribute\|=value]         | $('[title\|="Tomorrow"]')   | 所有带有 title 属性且值等于 'Tomorrow' 或者以 'Tomorrow' 后跟连接符作为开头的字符串 |
| [attribute^=value]          | $('[title^="Tom"]')         | 所有带有 title 属性且值以 "Tom" 开头的元素                   |
| [attribute~=value]          | $('[title~="hellow"]')      | 所有带有 title 属性且值包含单词 "hello" 的元素               |
| [attribute*=value]          | $('[title*="hellow"]')      | 所有带有 title 属性且值包含字符串 "hello" 的元素             |
| [name=value] [name2=value2] | $('input[id\][name="man"]') | 带有 id 属性，并且 name 属性以 man 结尾的输入框              |

##  状态过滤选择器

| 选择器    | 实例           | 选取                   |
| --------- | :------------- | ---------------------- |
| :enabled  | $(':enabled')  | 所有启用的元素         |
| :disabled | $(':disabled') | 所有禁用的元素         |
| :selected | $(':selected') | 所有选定的下拉列表元素 |
| :checked  | $('checked')   | 所有选中的复选框选项   |

##  表单选择器

| 选择器    | 实例           | 选取                                             |
| --------- | -------------- | ------------------------------------------------ |
| :input    | $(':input')    | 所有input元素                                    |
| :text     | $(':text')     | 所有带有 type="text" 的 input 元素               |
| :password | $(':password') | 所有带有 type="password" 的 input 元素           |
| :radio    | $(':radio')    | 所有带有 type="radio" 的 input 元素              |
| :checkbox | $(':checkbox') | 所有带有 type="checkbox" 的 input 元素           |
| :submit   | $(':submit')   | 所有带有 type="submit" 的 input 元素             |
| :button   | $(':button')   | 所有带有 type="button" 的 input 元素和button元素 |
| :reset    | $(':reset')    | 所有带有 type="reset" 的 input 元素              |
| :image    | $(':image')    | 所有带有 type="image" 的 input 元素              |
| :file     | $(':file')     | 所有带有 type="file" 的 input 元素               |

