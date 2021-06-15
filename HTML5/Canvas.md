#  Canvas

HTML5 `<canvas>` 元素用于图形的绘制，通过脚本 (通常是JavaScript)来完成.

`<canvas> `标签只是图形容器，您必须使用脚本来绘制图形。

你可以通过多种方法使用 canvas 绘制路径,盒、圆、字符以及添加图像。

##  创建一个画布(Canvas)

一个画布在网页中是一个矩形框，通过 `<canvas>` 元素来绘制.

**注意:** 默认情况下 `<canvas>` 元素没有边框和内容。

**简单实例:**

```html
<canvas id="can1" width="200" height="200"></canvas>
```

**注意:** 标签通常需要指定一个id属性 (脚本中经常引用), width 和 height 属性定义的画布的大小.

**提示:**你可以在HTML页面中使用多个 `<canvas>` 元素.

通过css添加边框：

```css
#can1 {
	border: 1px solid #00f;
}
```

##  使用JavaScript来绘制图像

canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成：

```javascript
			//找到<canvas>元素
			var can1 = document.querySelector('#can1');
			// 创建context对象
			// getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。
			var ctx1 = can1.getContext('2d');
			// 设置fillStyle属性可以是CSS颜色，渐变，或图案。fillStyle 默认设置是#000000（黑色）。
			// fillRect(x,y,width,height) 方法定义了矩形当前的填充方式。
			ctx1.fillStyle = '#f00';
			ctx1.fillRect(0,0,150,75);
```

##  Canvas坐标

canvas 是一个二维网格。

canvas 的左上角坐标为 (0,0)

上面的 fillRect 方法拥有参数 (0,0,150,75)。

意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。

##  Canvas 路径

在Canvas上画线，我们将使用以下两种方法：

- moveTo(*x,y*) 定义线条开始坐标
- lineTo(*x,y*) 定义线条结束坐标

**实例**

```css
#can1 {
	border: 1px solid #00f;
}
```

```html
<canvas id="can1" width="200" height="200"></canvas>
```

**画对角线**

```javascript
var can1 = document.querySelector('#can1');
var ctx1 = can1.getContext('2d');
ctx1.moveTo(0,0);
ctx1.lineTo(200,200);
ctx1.stroke();
```

可以写多个lineTo(),让你的路径更长。

```javascript
ctx1.moveTo(0,0);
ctx1.lineTo(10,20);
ctx1.lineTo(10,80);
ctx1.lineTo(60,70);
ctx1.stroke();
```

##  Canvas 文本

使用 canvas 绘制文本，重要的属性和方法如下：

- font - 定义字体
- fillText(*text,x,y*) - 在 canvas 上绘制实心的文本
- strokeText(*text,x,y*) - 在 canvas 上绘制空心的文本

**使用fillTexe()**

```javascript
ctx1.font = '30px Arial';
ctx1.fillText('Hello World',20,70);
```

**使用strockText()**

```javascript
ctx1.font = '30px Arial';
ctx1.strokeText('Hello World',20,70);
```

##  Canvas 渐变

渐变可以填充在矩形, 圆形, 线条, 文本等等, 各种形状可以自己定义不同的颜色。

以下有两种不同的方式来设置Canvas渐变：

- createLinearGradient(*x,y,x1,y1*) - 创建线条渐变
- createRadialGradient(*x,y,r,x1,y1,r1*) - 创建一个径向/圆渐变

当我们使用渐变对象，必须使用两种或两种以上的停止颜色。

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以是0至1.

使用渐变，设置fillStyle或strokeStyle的值为 渐变，然后绘制形状，如矩形，文本，或一条线。

**使用 createLinearGradient():**

```javascript
var can1 = document.querySelector('#can1');
var ctx1 = can1.getContext('2d');
var grd = ctx1.createLinearGradient(0,0,200,0);
grd.addColorStop(0,'red');
grd.addColorStop(1,'white');
ctx1.fillStyle = grd;
ctx1.fillRect(10,10,150,80);
```

**使用 createRadialGradient():**

```javascript
var can1 = document.querySelector('#can1');
var ctx1 = can1.getContext('2d');
var grd2 = ctx1.createRadialGradient(75,50,5,90,60,100);
grd2.addColorStop(0,'red');
grd2.addColorStop(1,'white');
ctx1.fillStyle = grd2;
ctx1.fillRect(10,100,150,80);
```

##  Canvas 图像

把一幅图像放置到画布上, 使用以下方法:

- drawImage(*image,x,y*)

```javascript
var can1 = document.querySelector('#can1');
var img = document.querySelector('img');
var ctx1 = can1.getContext('2d');
ctx1.drawImage(img,10,10);
```

