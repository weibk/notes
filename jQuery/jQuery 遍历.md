# jQuery 遍历 

##  jQuery 遍历-祖先

祖先是父、祖父或曾祖父等等。

通过 jQuery，您能够向上遍历 DOM 树，以查找元素的祖先。

这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：

- parent()
- parents()
- parentsUntil()

###  jQuery parent()方法

parent() 方法返回被选元素的直接父元素。

该方法只会向上一级对 DOM 树进行遍历。

###  jQuery parents()方法

parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。

您也可以使用可选参数来过滤对祖先元素的搜索。

下面的例子返回所有 `<span> `元素的所有祖先，并且它是 `<ul> `元素：

```javascript
$(document).ready(function(){
  $("span").parents("ul");
});
```

###  jQuery parentsUntil()方法

parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

```javascript
$(document).ready(function(){
  $("span").parentsUntil("div");
});
```

##  jQuery 遍历-后代

后代是子、孙、曾孙等等。

通过 jQuery，您能够向下遍历 DOM 树，以查找元素的后代。

下面是两个用于向下遍历 DOM 树的 jQuery 方法：

- children()
- find()

###  jQuery children()方法

children() 方法返回被选元素的所有**直接子元素**。

该方法只会**向下一级对 DOM 树**进行遍历。

**返回所有的直接子元素**

```javascript
$('div').children();
//返回div的所有直接子元素
```

**返回指定的直接子元素**

```javascript
$('div').childern('p.one');
//返回div直接子元素中class值为one的p元素
```

###  jQuery find()方法

find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。

**返回所有的后代元素**

```javascript
$('div').find('*');
//返回div的所有后代
```

**返回指定的后代元素**

```javascript
$('div').find('span');
//返回属于div后代的所有span元素
```

##  jQuery 遍历-同胞

有许多有用的方法让我们在 DOM 树进行水平遍历：

- siblings()
- next()
- nextAll()
- nextUntil()
- prev()
- prevAll()
- prevUntil()

###  jQuery siblings()

该方法返回被选元素的所有同胞元素。

**实例**

```html
<div>
  <p>p</p>
  <span>span</span>
  <h2>h2</h2>
  <h3>h3</h3>
  <p>p</p>
</div>
```

```javascript
$(function() {
   $('h2').siblings().css('color','red'); 
});
```

###  jQuery next()

next() 方法返回被选元素的下一个同胞元素。

该方法只返回一个元素。
```html
<div>
  <p>p</p>
  <span>span</span>
  <h2>h2</h2>
  <h3>h3</h3>
  <p>p</p>
</div>
```
```javascript
			$(function() {
				$('h2').next().css('color','red');
			})
```

###  jQuery nextAll()

nextAll() 方法返回被选元素的所有跟随的同胞元素。
```html
<div>
  <p>p</p>
  <span>span</span>
  <h2>h2</h2>
  <h3>h3</h3>
  <p>p</p>
</div>
```
```javascript
			$(function() {
				$('h1').nextAll().css('color','red');
			})
```

###  jQuery nextUntil()

nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素。

```html
		<div>
			<span>span</span>
			<h1>h1</h1>
			<h2>h2</h2>
			<h3>h3</h3>
			<h4>h4</h4>
			<h5>h5</h5>
			<h6>h6</h6>
			<a href="#">a</a>
		</div>
```

```javascript
			$(function() {
				// $('h2').siblings().css('color','red');
				// $('h2').next().css('color','red');
				// $('h1').nextAll().css('color','red');
				$('h1').nextUntil('h6').css('color','red');
			})
```

###  prev()   prevAll()    prevUntil()

##  jQuery 遍历-过滤

三个最基本的过滤方法是：first(), last() 和 eq()，它们允许您基于其在一组元素中的位置来选择一个特定的元素。

其他过滤方法，比如 filter() 和 not() 允许您选取匹配或不匹配某项指定标准的元素。

###  jQuery first()

first() 方法返回被选元素的首个元素。

```html
		<div>
			<p>1</p>
			<p>2</p>
			<p>3</p>
			<p>4</p>
			<p>5</p>
			<p>6</p>
		</div>
```

```javascript
			$(function() {
				$('p').first().css('color','red');
			});
```

###  jQuery last()

last() 方法返回被选元素的最后一个元素。

```javascript
			$(function() {
				$('p').last().css('color','red');
			});
```

###  jQuery eq()

eq() 方法返回被选元素中带有指定索引号的元素。

```javascript
			$(function() { 
				$('p').eq(2).css('color','red');
			});
```

###  jQuery filter()

filter() 方法允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。

```html
		<div>
			<p>1</p>
			<p>2</p>
			<p class="blue">3</p>
			<p>4</p>
			<p class="blue">5</p>
			<p>6</p>
		</div>
```

```javascript
			$(function() {
				$('p').filter('.blue').css('color','blue');
			});
```

###  jQuery not()

not() 方法返回不匹配标准的所有元素。

```javascript
			$(function() {
				$('p').not('.blue').css('color','red');
			});
```

