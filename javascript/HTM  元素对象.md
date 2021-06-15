#  HTM  元素对象

##  常用的属性和方法

###  属性

####  element.accessKey

可设置或返回访问单选按钮的快捷键。

```html
<script>
function accesskey(){
  document.getElementById('runoob').accessKey="r"
  document.getElementById('g').accessKey="g"
}
</script>
</head>
<body onload="accesskey()">
    
<a id="runoob" href="//www.runoob.com/">菜鸟教程</a><br>
<a id="g" href="//www.google.com/">Google</a>
<p><b>注：</b>使用Alt + <i> accesskey </i>访问具有指定访问键的元素。</p>
 
</body>
```

####  element.attributes

返回指定节点属性的集合。

```html
<p id="p1" class="ps"></p>
<script type="text/javascript">
	var para = document.querySelector('p');
	console.log(para.attributes.length);
</script>
```

####  element.childNodes

返回指定节点的所有子节点的集合，会把空格看作文本节点。

####  element.children

返回指定节点的所有子元素节点的集合。

####  element.classList

返回指定节点的类名的集合。

该属性用于在元素中添加，移除及切换 CSS 类。

classList 属性是只读的，但你可以使用 add() 和 remove() 方法修改它。

```html
		<p class="p1 ps active current" id="pp"></p>
		<script type="text/javascript">
			var pp = document.querySelector('#pp');
			pp.classList.add('ppp');
			pp.classList.remove('ps');
			console.log(pp.classList)
		</script>
```

**add(class1,class2,class3.....)**

向元素添加一个或多个类名，如果指定类名已存在，则不会添加

**contains(class)**

返回布尔值，判断类名是否存在。

若存在，返回true，

若不存在，返回false。

**remove(class1,class2....)**

移除元素中一个或多个类名，

移除不存在的类名，不会报错。

**toggle(class,true[false])**

在元素中切换类名。

第一个参数为要在元素中移除的类名，并返回 false。
如果该类名不存在则会在元素中添加类名，并返回 true。

第二个是可选参数，是个布尔值用于设置元素是否强制添加或移除类，不管该类名是否存在。

移除一个 class: *element*.classList.toggle("classToRemove", false);
添加一个 class: *element*.classList.toggle("classToAdd", true);

**item(index)**

返回元素中索引值对应的类名，索引值从0开始。

如果索引值在区间范围外，则返回null。

####  element.className

返回或设置元素的类名，设置类名会覆盖原有的类名。

####  *element*.clientHeight

在页面上返回内容的可视高度（不包括边框，边距或滚动条）

####  *element*.clientWidth

在页面上返回内容的可视宽度（不包括边框，边距或滚动条）

####  element.contentEditable

用于设置或返回元素的内容是否可编辑。

true:内容可编辑

false:内容不可编辑

```html
		<div>hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh</div>
		<script type="text/javascript">
			var div = document.querySelector('div');
			div.contentEditable = true;
		</script>
```

####  element.dir

设置或返回元素的文字方向。

rtl:从右向左   

ltr：从左向右

####  element.firstChild

返回被选节点的第一个子节点。

####  element.firstElementChild

返回被选节点的第一个元素子节点。

####  element.lastChild

返回被选节点的最后一个子节点。

####  element.lastElementChild

返回被选节点的最后一个元素子节点。

####  element.id

设置或者返回元素的 id。

####  element.innerHtml

设置或者返回元素的内容。

####  element.isContentEditable

判断元素内容是否可编辑

可编辑返回true，否则返回false

####  element.lang

设置或返回元素的语言。

####  element.nextElementSibling

返回指定元素之后的下一个兄弟元素

#### element.previousElementSibling

返回指定元素之后的上一个兄弟元素

####  element.nodeName

nodeName 属性可依据节点的类型返回其名称。

如果节点是一个元素节点 , nodeName 属性将返回标签名。

如果节点是一个属性节点， nodeName 属性将返回属性名。

其他节点类型, nodeName 属性将返根据不同的节点类型返回不同的节点名称。

**返回值为大写**

| 属性                   | 含义                                             |
| ---------------------- | ------------------------------------------------ |
| element.offsetHeight   | 返回任何一个元素的高度包括边框和填充，但不是边距 |
| *element*.offsetWidth  | 返回元素的宽度，包括边框和填充，但不是边距       |
| *element*.offsetLeft   | 返回当前元素的相对水平偏移位置的偏移容器         |
| *element*.offsetParent | 返回元素的偏移容器                               |
| *element*.offsetTop    | 返回当前元素的相对垂直偏移位置的偏移容器         |

####  element.parentNode

返回指定节点的父节点。

| 属性                   | 含义                                                   |
| ---------------------- | ------------------------------------------------------ |
| *element*.scrollHeight | 返回整个元素的高度（包括带滚动条的隐蔽的地方）         |
| *element*.scrollLeft   | 返回当前视图中的实际元素的左边缘和左边缘之间的距离     |
| *element*.scrollTop    | 返回当前视图中的实际元素的顶部边缘和顶部边缘之间的距离 |
| *element*.scrollWidth  | 返回元素的整个宽度（包括带滚动条的隐蔽的地方）         |

####  element.tagName

 属性返回元素的标签名。

HTML 返回 tagName 属性的值是大写的。

####  element.contentText

设置或者返回指定节点的文本内容。

####  element.title

设置或返回元素的title属性

###  方法

####  node.cloneNode()

cloneNode() 方法可创建指定的节点的精确拷贝。

cloneNode() 方法 拷贝所有属性和值。

该方法将复制并返回调用它的节点的副本。如果传递给它的参数是 true，它还将递归复制当前节点的所有子孙节点。否则，它只复制当前节点。

**语法**

```javascript
node.cloneNode(false);//浅拷贝，复制当前节点
node.cloneNode(true);//深拷贝，复制当前节点并递归复制所有子节点
```

####  element.compareDocumentPosition()

该方法按照文档顺序，比较当前节点与指定节点的文档位置。

**返回值**

| 返回值 | 含义                                           |
| ------ | ---------------------------------------------- |
| 1      | 没有关系，这两个节点不属于同一个文档。         |
| 2      | 第一节点（P1）位于第二个节点后（P2）。         |
| 4      | 第一节点（P1）定位在第二节点（P2）前。         |
| 8      | 第一节点（P1）位于第二节点内（P2）。           |
| 16     | 第二节点（P2）位于第一节点内（P1）。           |
| 32     | 没有关系的，或是两个节点在同一元素的两个属性。 |

####  element.focus()

用于为元素设置焦点（如果可以设置）。

使用 blur() 方法来移除元素焦点。

####  getAttribute()

获取指定元素的属性值。

```javascript
element.getAttribute(attributename);
```

####  element.setAttribute()

创建或改变指定元素的某个属性。

####  element.removeAttribute()

从指定元素中删除指定属性。

####  element.hasAttribute()

用于判断是否有指定的属性存在，如果存在返回 true，否则返回 false。

**语法**

```javascript
element.hasAttribute(attribute);
```

####  element.hasAttributes()

如果节点有属性返回 true，否则返回false。

```javascript
element.hasAttributes();
//无参数
```

####  element.hasChildNodes()

判断指定节点是否有子节点。

```javascript
element.hasChildNodes();
//如果有子节点返回true，如果没有子节点返回false
```

####  element.hasFocus()

检测文档或元素是否获得焦点。

####  element.isEqualNode()

检查两个元素是否相等。

isEqualNode() 方法用于检查两个节点是否相等。

如果满足下列条件两个节点就相等并返回true：

- 有相同节点类型
- 相同的节点名，节点值，本地名，命名空间URI和前缀。
- 他们与所有的后代都有相同的子节点
- 有相同的属性和属性值(属性没有相同的排序方式)

####  element.isSameNode()

检查两个节点是否为同一节点。

如果是同一个节点返回true，否则返回false。

####  node.normalize()

合并相邻的文本节点并删除空的文本节点。

