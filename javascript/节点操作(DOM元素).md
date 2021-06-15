#  节点操作(DOM元素)

##  创建并添加新的节点

###  1.创建节点

**创建元素节点:**

```javascript
var para = document.createElement('p');
//创建一个<p>元素
```

**创建文本节点:**

```javascript
var textnode = document.createTextNode('这是一个新段落');
//创建一个文本节点
```

###  2.添加节点

**appendChild()**

**语法**

```javascript
Node.appendChild(newchild);
```

该方法可向节点的子节点列表的末尾添加新的子节点。

**提示：**如果文档树中已经存在了 newchild，它将从文档树中删除，然后重新插入它的新位置。如果 newchild 是 DocumentFragment 节点，则不会直接插入它，而是把它的子节点按序插入当前节点的 childNodes[] 数组的末尾。

```javascript
para.appendChild(textnode);
//将文本节点添加到<p>元素中
var element = document.getElementById("div1");
element.appendChild(para);
//在一个已存在的元素中添加<p>元素
```

**insertBefore()**

**语法**

```javascript
Node.insertBefore(newchild,existingchild);
```

该方法可在已有的子节点前插入一个新的子节点。

##  移出除存在的元素

```html
<div id="div1">
	<p id="p1">这是一个段落。</p>
	<p id="p2">这是另外一个段落。</p>
</div>
```

```javascript
var parent = document.querySelector("#div1");
var child = document.querySelector("#p1");
parent.removeChild(child);
```

如果只知道要删除的元素，而不知道其父元素，可以通过下面的方法删除：

```javascript
child.parentNode.removeChild(child);
//查找其父元素再删除
```

##  替换节点

**replaceChild()**

```javascript
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);
//创建新节点
parent.replaceChild(para, child);
//替换
```





