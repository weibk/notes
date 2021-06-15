#  颜色、样式和阴影

##  属性

###  <span id="fillStyle">fillStyle</span>

fillStyle 属性设置或返回用于填充绘画的颜色、渐变或模式。

**默认值：**#000000

**JavaScript 语法：**

```javascript
context.fillStyle = color | gradient | pattern;
```

**属性值**

| 值       | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| color    | 指示绘图填充色的CSS颜色值。默认是#000000(黑色)。             |
| gradient | 用于填充绘图的渐变对象(线性渐变或径向渐变)                   |
| pattern  | 用于填充绘图的 [pattern](https://www.runoob.com/tags/canvas-createpattern.html) 对象。 |

###  strokeStyle

strokeStyle 属性设置或返回用于笔触的颜色、渐变或模式。

**默认值：**#000000

**JavaScript 语法：**

```javascript
context.strockStyle = color | gradient | pattern;
```

**属性值**

| 值       | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| color    | 指示绘图笔触颜色的CSS颜色值。默认是#000000(黑色)。           |
| gradient | 用于填充绘图的渐变对象(线性渐变或径向渐变)                   |
| pattern  | 用于创建 pattern 笔触的 [pattern](https://www.runoob.com/tags/canvas-createpattern.html) 对象。 |

###  shadowColor

shadowColor 属性设置或返回用于阴影的颜色。

**注意：**请将 shadowColor 属性与 **shadowBlur** 属性一起使用，来创建阴影。

**提示：**请通过使用 **shadowOffsetX**和 **shadowOffsetY**属性来调节阴影效果。                                                                                     

**默认值：**#000000

**JavaScript 语法：**

```javascript
context.shadowColor = color;
```

**属性值**

| 值    | 描述                                               |
| ----- | -------------------------------------------------- |
| color | 指示绘图笔触颜色的CSS颜色值。默认是#000000(黑色)。 |

###  shadowBlur

shadowBlur 属性设置或返回阴影的模糊级数。                                                                              

**默认值：**0

**JavaScript 语法：**

```javascript
context.shadowBlur = number;
```

**属性值**

| 值       | 描述           |
| -------- | -------------- |
| *number* | 阴影的模糊级数 |

###  shadowOffsetX()

shadowOffsetX 属性设置或返回阴影与形状的水平距离。

shadowOffsetX=0 指示阴影位于形状的正下方。

shadowOffsetX=20 指示阴影位于形状 left 位置右侧的 20 像素处。

shadowOffsetX=-20 指示阴影位于形状 left 位置左侧的 20 像素处。

**默认值：**0

**JavaScript 语法：**

```javascript
context.shadowoffsetX = number;
```

**属性值**

| 值       | 描述                                   |
| -------- | -------------------------------------- |
| *number* | 正值或负值，定义阴影与形状的水平距离。 |

###  shadowOffsetX()

shadowOffsetY 属性设置或返回阴影与形状的垂直距离。

shadowOffsety=0 指示阴影位于形状的正下方。

shadowOffsetY=20 指示阴影位于形状 top 位置下方的 20 像素处。

shadowOffsetY=-20 指示阴影位于形状 top 位置上方的 20 像素处。

**默认值：**0

**JavaScript 语法：**

```javascript
context.shadowoffsetY = number;
```

**属性值**

| 值       | 描述                                   |
| -------- | -------------------------------------- |
| *number* | 正值或负值，定义阴影与形状的垂直距离。 |

##  方法

###  createLinearGradient()

createLinearGradient() 方法创建线性的渐变对象。

渐变可用于填充矩形、圆形、线条、文本等等。

**提示：**请使用该对象作为 [strokeStyle](https://www.runoob.com/tags/canvas-strokestyle.html) 或 [fillStyle](https://www.runoob.com/tags/canvas-fillstyle.html) 属性的值。

**提示：**请使用 [addColorStop()](https://www.runoob.com/tags/canvas-addcolorstop.html) 方法规定不同的颜色，以及在 gradient 对象中的何处定位颜色。

**JavaScript 语法：**

```javascript
context.createLinearGradient(x0,y0,x1,y1);
```

**参数值**

| 参数 | 描述                |
| ---- | ------------------- |
| x0   | 渐变开始点的 x 坐标 |
| y0   | 渐变开始点的 y 坐标 |
| x1   | 渐变结束点的 x 坐标 |
| y1   | 渐变结束点的 y 坐标 |

###  createRadialGradient()

createRadialGradient() 方法创建放射状/圆形渐变对象。

渐变可用于填充矩形、圆形、线条、文本等等。

**JavaScript 语法**

```javascript
context.createRadialGradient(x0,y0,r0,x1,y1,r1);
```

**参数值**

| 参数 | 描述                  |
| :--- | :-------------------- |
| *x0* | 渐变的开始圆的 x 坐标 |
| *y0* | 渐变的开始圆的 y 坐标 |
| *r0* | 开始圆的半径          |
| *x1* | 渐变的结束圆的 x 坐标 |
| *y1* | 渐变的结束圆的 y 坐标 |
| *r1* | 结束圆的半径          |

###  addColorStop()

addColorStop() 方法规定渐变对象中的颜色和位置。

addColorStop() 方法与 [createLinearGradient()](https://www.runoob.com/tags/canvas-createlineargradient.html) 或 [createRadialGradient()](https://www.runoob.com/tags/canvas-createradialgradient.html) 一起使用。

**注意：**您可以多次调用 addColorStop() 方法来改变渐变。如果您不对渐变对象使用该方法，那么渐变将不可见。为了获得可见的渐变，您需要创建至少一个色标。

**JavaScript 语法：**

```javascript
gradient.addColorStop(stop,color);
```

**参数值**

| 参数    | 描述                                                       |
| :------ | :--------------------------------------------------------- |
| *stop*  | 介于 0.0 与 1.0 之间的值，表示渐变中开始与结束之间的位置。 |
| *color* | 在 *stop* 位置显示的 CSS 颜色值。                          |

###  createPattern()

createPattern() 方法在指定的方向内重复指定的元素。

元素可以是图片、视频，或者其他 `<canvas>` 元素。

被重复的元素可用于绘制/填充矩形、圆形或线条等等。

**JavaScript 语法：**

```javascript
context.createPattern(image,'repeat|repeat-x|repeat-y|no-repeat');
```

 **参数值**

| 参数      | 描述                                     |      |
| :-------- | :--------------------------------------- | ---- |
| *image*   | 规定要使用的模式的图片、画布或视频元素。 |      |
| repeat    | 默认。该模式在水平和垂直方向重复。       |      |
| repeat-x  | 该模式只在水平方向重复。                 |      |
| repeat-y  | 该模式只在垂直方向重复。                 |      |
| no-repeat | 该模式只显示一次（不重复）。             |      |

#  线条样式

##  属性

###  lineCap

lineCap 属性设置或返回线条末端线帽的样式。

**注意：**"round" 和 "square" 值会使线条略微变长。

**JavaScript 语法：**

```javascript
context.lineCap = 'butt|round|square';
```

**属性值**

| 值     | 描述                                   |
| :----- | :------------------------------------- |
| butt   | 默认。向线条的每个末端添加平直的边缘。 |
| round  | 向线条的每个末端添加圆形线帽。         |
| square | 向线条的每个末端添加正方形线帽。       |

###   lineJoin

lineJoin 属性设置或返回所创建边角的类型，当两条线交汇时。

**注意：**"miter" 值受 [miterLimit](https://www.runoob.com/tags/canvas-miterlimit.html) 属性的影响。

**默认值：**miter

**JavaScript 语法：**

```javascript
context.lineJoin = 'beve|round|miter';
```

**属性值**

| 值    | 描述             |
| :---- | :--------------- |
| bevel | 创建斜角。       |
| round | 创建圆角。       |
| miter | 默认。创建尖角。 |

###  lineWidth

lineWidth 属性设置或返回当前线条的宽度，以像素计。

**默认值：**miter

**JavaScript 语法：**

```javascript
context.lineWidth = number;
```

**属性值**

| 值       | 描述                       |
| :------- | :------------------------- |
| *number* | 当前线条的宽度，以像素计。 |

###  miterLimit

miterLimit 属性设置或返回最大斜接长度。

斜接长度指的是在两条线交汇处内角和外角之间的距离。

![Miter Limit figure 1](https://www.runoob.com/wp-content/uploads/2013/11/img_miterlimitFig.gif)

**提示：**只有当 lineJoin 属性为 "miter" 时，miterLimit 才有效。

边角的角度越小，斜接长度就会越大。

为了避免斜接长度*过长*，我们可以使用 miterLimit 属性。

如果斜接长度超过 miterLimit 的值，边角会以 lineJoin 的 "bevel" 类型来显示（Fig 3）：

![Miter Limit figure 2](https://www.runoob.com/wp-content/uploads/2013/11/img_miterlimitBevelFig.gif)

**默认值：**miter

**JavaScript 语法：**

```javascript
context.miterLimit = number;
```

**属性值**

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| *number* | 正数。规定最大斜接长度。如果斜接长度超过 miterLimit 的值，边角会以 lineJoin 的 "bevel" 类型来显示。 |

#  矩形

##  方法

###  rect()

rect() 方法创建矩形。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 或 [fill()](https://www.runoob.com/tags/canvas-fill.html) 方法在画布上实际地绘制矩形。

**JavaScript 语法：**

```javascript
context.rect(x,y,width,height);
```

**参数值**

| 参数     | 描述                   |
| :------- | :--------------------- |
| *x*      | 矩形左上角的 x 坐标。  |
| *y*      | 矩形左上角的 y 坐标。  |
| *width*  | 矩形的宽度，以像素计。 |
| *height* | 矩形的高度，以像素计。 |

###  fillRect()

fillRect() 方法绘制"已填充"的矩形。默认的填充颜色是黑色。

**提示：**请使用 [fillStyle](https://www.runoob.com/tags/canvas-fillstyle.html) 属性来设置用于填充绘图的颜色、渐变或模式。

**JavaScript 语法：**

```javascript
context.fillRect(x,y,width,height);
```

**参数值**

| 参数     | 描述                   |
| :------- | :--------------------- |
| *x*      | 矩形左上角的 x 坐标。  |
| *y*      | 矩形左上角的 y 坐标。  |
| *width*  | 矩形的宽度，以像素计。 |
| *height* | 矩形的高度，以像素计。 |

###  strokeRect()

strokeRect() 方法绘制矩形（无填充）。笔触的默认颜色是黑色。

**提示：**请使用 [strokeStyle](https://www.runoob.com/tags/canvas-strokestyle.html) 属性来设置笔触的颜色、渐变或模式。

**JavaScript 语法：**

```javascript
context.strokeRect(x,y,width,height);
```

**参数值**

| 参数     | 描述                   |
| :------- | :--------------------- |
| *x*      | 矩形左上角的 x 坐标。  |
| *y*      | 矩形左上角的 y 坐标。  |
| *width*  | 矩形的宽度，以像素计。 |
| *height* | 矩形的高度，以像素计。 |

###  clearRect()

clearRect() 方法清空给定矩形内的指定像素。

**JavaScript 语法：**

```javascript
context.clearRect(x,y,width,height);
```

**参数值**

| 参数     | 描述                           |
| :------- | :----------------------------- |
| *x*      | 要清除的矩形左上角的 x 坐标。  |
| *y*      | 要清除的矩形左上角的 y 坐标。  |
| *width*  | 要清除的矩形的宽度，以像素计。 |
| *height* | 要清除的矩形的高度，以像素计。 |

<img src="C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CHTML5%5Cimages%5CclearRect.png" style="zoom:80%;" />

#  路径

##  方法

###  fill()

fill() 方法填充当前的图像（路径）。默认颜色是黑色。

**提示：**请使用 [fillStyle](https://www.runoob.com/tags/canvas-fillstyle.html) 属性来填充另一种颜色/渐变。

**注意：**如果路径未关闭，那么 fill() 方法会从路径结束点到开始点之间添加一条线，以关闭该路径（正如 [closePath()](https://www.runoob.com/tags/canvas-closepath.html) 一样），然后填充该路径。

**JavaScript 语法：**

```javascript
context.fill();
```

###  stroke()

stroke() 方法会实际地绘制出通过 moveTo() 和 lineTo() 方法定义的路径。默认颜色是黑色。

**提示：**请使用 [strokeStyle](https://www.runoob.com/tags/canvas-strokestyle.html) 属性来绘制另一种颜色/渐变。

**JavaScript 语法：**

```javascript
context.stroke();
```

###  beginPath()

beginPath() 方法开始一条路径，或重置当前的路径。

**提示：**请使用这些方法来创建路径 moveTo()、lineTo()、quadricCurveTo()、bezierCurveTo()、arcTo() 和 arc()。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 方法在画布上绘制确切的路径。

**JavaScript 语法：**

```javascript
context.beginPath();
```

###  closePath()

closePath() 方法创建从当前点到开始点的路径。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 方法在画布上绘制确切的路径。

**JavaScript 语法：**

```javascript
context.closePath();
```

###  moveTo()

moveTo() 方法把路径移动到画布中的指定点，不创建线条。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 方法在画布上绘制确切的路径。

**JavaScript 语法：**

```javascript
context.moveTo(x,y);
```

**参数值****

| 参数 | 描述                      |
| :--- | :------------------------ |
| *x*  | 路径的目标位置的 x 坐标。 |
| *y*  | 路径的目标位置的 y 坐标。 |

###  moveTo()

lineTo() 方法添加一个新点，然后创建从该点到画布中最后指定点的线条（该方法并不会创建线条）。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 方法在画布上绘制确切的路径。

**JavaScript 语法：**

```javascript
context.lineTo(x,y);
```

**参数值****

| 参数 | 描述                      |
| :--- | :------------------------ |
| *x*  | 路径的目标位置的 x 坐标。 |
| *y*  | 路径的目标位置的 y 坐标。 |

###  clip()

clip()方法从原始画布中剪切任意形状和尺寸。

**提示：**一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内（不能访问画布上的其他区域）。您也可以在使用 clip() 方法前通过使用 save() 方法对当前画布区域进行保存，并在以后的任意时间对其进行恢复（通过 restore() 方法）。

**JavaScript 语法：**

```javascript
context.clip();
```

**实例**

<img src="C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CHTML5%5Cimages%5Cclip.png" style="zoom:33%;" />

```javascript
var c = document.querySelector('#c');
var ctx = c.getContext('2d');
ctx.strokeStyle = 'deeppink';
ctx.rect(100,100,300,300)
ctx.stroke();
ctx.clip();
ctx.fillStyle = 'red';
ctx.fillRect(0,0,300,300);
```

###  quadraticCurveTo()

quadraticCurveTo() 方法通过使用表示二次贝塞尔曲线的指定控制点，向当前路径添加一个点。

二次贝塞尔曲线需要两个点。第一个点是用于二次贝塞尔计算中的控制点，第二个点是曲线的结束点。曲线的开始点是当前路径中最后一个点。如果路径不存在，那么请使用 [beginPath()](https://www.runoob.com/tags/canvas-beginpath.html) 和 [moveTo() ](https://www.runoob.com/tags/canvas-moveto.html)方法来定义开始点。

**JavaScript 语法：**

```javascript
context.quadraticCyrveTo(cpx,cpy,x,y);
```

**参数值**

| 参数  | 描述                    |
| :---- | :---------------------- |
| *cpx* | 贝塞尔控制点的 x 坐标。 |
| *cpy* | 贝塞尔控制点的 y 坐标。 |
| *x*   | 结束点的 x 坐标。       |
| *y*   | 结束点的 y 坐标。       |

**实例**

![二次贝塞尔曲线](https://www.runoob.com/wp-content/uploads/2013/11/img_quadraticcurve.gif)



```javascript
ctx.beginPath();
ctx.moveTo(20,20);
ctx.quadraticCurveTo(20,100,200,20);
ctx.stroke();
```

###  bezierCurveTo()

bezierCurveTo() 方法通过使用表示三次贝塞尔曲线的指定控制点，向当前路径添加一个点。

三次贝塞尔曲线需要三个点。前两个点是用于三次贝塞尔计算中的控制点，第三个点是曲线的结束点。曲线的开始点是当前路径中最后一个点。如果路径不存在，那么请使用 [beginPath()](https://www.runoob.com/tags/canvas-beginpath.html) 和 [moveTo()](https://www.runoob.com/tags/canvas-moveto.html) 方法来定义开始点。

![三次贝塞尔曲线](https://www.runoob.com/wp-content/uploads/2013/11/img_beziercurve.gif)

**JavaScript 语法：**

```javascript
context.quadraticCyrveTo(cpx1,cpy1,cpx2,cpy2,x,y);
```

**参数值**

| 参数   | 描述                          |
| :----- | :---------------------------- |
| *cp1x* | 第一个贝塞尔控制点的 x 坐标。 |
| *cp1y* | 第一个贝塞尔控制点的 y 坐标。 |
| *cp2x* | 第二个贝塞尔控制点的 x 坐标。 |
| *cp2y* | 第二个贝塞尔控制点的 y 坐标。 |
| *x*    | 结束点的 x 坐标。             |
| *y*    | 结束点的 y 坐标。             |

###  arc()

arc() 方法创建弧/曲线（用于创建圆或部分圆）。

**提示：**如需通过 arc() 来创建圆，请把起始角设置为 0，结束角设置为 2*Math.PI。

**提示：**请使用 [stroke()](https://www.runoob.com/tags/canvas-stroke.html) 或 [fill()](https://www.runoob.com/tags/canvas-fill.html) 方法在画布上绘制实际的弧。

![An arc](https://www.runoob.com/wp-content/uploads/2013/11/img_arc.gif)

**JavaScript 语法：**

```javascript
context.arc(x,y,r,sAngle,eAngle,counterclockwise);
```

**参数值**

| 参数             | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| x                | 圆的中心的 x 坐标。                                          |
| y                | 圆的中心的 y 坐标。                                          |
| r                | 圆的半径。                                                   |
| sAngle           | 起始角，以弧度计（弧的圆形的三点钟位置是 0 度）。            |
| eAngle           | 结束角，以弧度计。                                           |
| counterclockwise | 可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。 |

###  isPointInPath()

如果指定的点位于当前路径中，isPointInPath() 方法返回 true，否则返回 false。

**JavaScript 语法：**

```javascript
context.isPointInPath(x,y);
```

**参数值**

| 参数 | 描述              |
| :--- | :---------------- |
| *x*  | 要测试的 x 坐标。 |
| *y*  | 要测试的 y 坐标。 |

#  转换

##  方法

###  scale()

scale() 方法缩放当前绘图至更大或更小。

**注意：**如果您对绘图进行缩放，所有之后的绘图也会被缩放。定位也会被缩放。如果您 scale(2,2)，那么绘图将定位于距离画布左上角两倍远的位置。

**JavaScript 语法：**

```javascript
context.scale(scalewidth,scaleheight);
```

**参数值**

| 参数          | 描述                                                      |
| :------------ | :-------------------------------------------------------- |
| *scalewidth*  | 缩放当前绘图的宽度（1=100%，0.5=50%，2=200%，依次类推）。 |
| *scaleheight* | 缩放当前绘图的高度（1=100%，0.5=50%，2=200%，依次类推）。 |

```javascript
ctx.strokeRect(5,5,25,15);
ctx.scale(2,2);
ctx.strokeRect(5,5,25,15);
```

###  rotate()

rotate() 方法旋转当前的绘图。

**注意：**旋转只会影响到旋转完成后的绘图。

**JavaScript 语法：**

```javascript
context.rotate(angle);
```

**参数值**

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| *angle* | 旋转角度，以弧度计。  如需将角度转换为弧度，请使用 *degrees**Math.PI/180 公式进行计算。 实例：如需旋转 5 度，可规定下面的公式：5*Math.PI/180。 |

```javascript
ctx.rotate(20*Math.PI/180);
ctx.fillRect(50,20,100,50);//旋转操作放在绘制之前
```

###  translate()

translate() 方法重新映射画布上的 (0,0) 位置。

**注意：**当您在 translate() 之后调用诸如 fillRect() 之类的方法时，值会添加到 x 和 y 坐标值上。

## 参数值

| 参数 | 描述                        |
| :--- | :-------------------------- |
| *x*  | 添加到水平坐标（x）上的值。 |
| *y*  | 添加到垂直坐标（y）上的值。 |

###  transform

画布上的每个对象都拥有一个当前的变换矩阵。

transform() 方法替换当前的变换矩阵。它以下面描述的矩阵来操作当前的变换矩阵：

| a    | c    | e    |
| ---- | ---- | ---- |
| b    | d    | f    |
| 0    | 0    | 1    |

换句话说，transform() 允许您缩放、旋转、移动并倾斜当前的环境。

**注意：**该变换只会影响 transform() 方法调用之后的绘图。

**注意：**transform() 方法的行为相对于由 rotate()、scale()、translate() 或 transform() 完成的其他变换。 例如：如果您已经将绘图设置为放到两倍，则 transform() 方法会把绘图放大两倍，您的绘图最终将放大四倍。

**提示：**请查看 [setTransform()](https://www.runoob.com/tags/canvas-settransform.html) 方法，它不会相对于其他变换来发生行为。

**JavaScript 语法：**

```javascript
context.transform(a,b,c,d,e,f);
```

**参数值**

| 参数 | 描述           |
| :--- | :------------- |
| *a*  | 水平缩放绘图。 |
| *b*  | 水平倾斜绘图。 |
| *c*  | 垂直倾斜绘图。 |
| *d*  | 垂直缩放绘图。 |
| *e*  | 水平移动绘图。 |
| *f*  | 垂直移动绘图。 |

###  setTransform

画布上的每个对象都拥有一个当前的变换矩阵。

setTransform() 方法把当前的变换矩阵重置为单位矩阵，然后以相同的参数运行 [transform()](https://www.runoob.com/tags/canvas-transform.html)。

换句话说，setTransform() 允许您缩放、旋转、移动并倾斜当前的环境。

**注意：**该变换只会影响 setTransform() 方法调用之后的绘图。

**JavaScript 语法：**

```javascript
context.setTransform(a,b,c,d,e,f);
```

**参数值**

| 参数 | 描述           |
| :--- | :------------- |
| a    | 水平缩放绘图。 |
| b    | 水平倾斜绘图。 |
| c    | 垂直倾斜绘图。 |
| d    | 垂直缩放绘图。 |
| e    | 水平移动绘图。 |
| f    | 垂直移动绘图。 |

#  文本

##  属性

### <span id="font"> font</span>

font 属性设置或返回画布上文本内容的当前字体属性。

font 属性使用的语法与 [CSS font 属性](https://www.runoob.com/cssref/pr-font-font.html) 相同。

**默认值：**10px sans-serif

**JavaScript 语法：**

```javascript
context.font="italic small-caps bold 12px arial";
```

## 属性值

| 值                      | 描述                                                         |
| :---------------------- | :----------------------------------------------------------- |
| *font-style*            | 规定字体样式。可能的值：normal，italic(斜体)，oblique        |
| *font-variant*          | 规定字体变体。可能的值：normal，small-caps(浏览器会显示小型大写字母的字体) |
| *font-weight*           | 规定字体的粗细。可能的值：normal，bold(粗体)，bolder(更粗)，lighter(更细)，100，200，300，400，500，600，700，800，900 |
| *font-size/line-height* | 规定字号和行高，以像素计。                                   |
| *font-family*           | 规定字体系列。                                               |
| caption                 | 使用标题控件的字体（比如按钮、下拉列表等）。                 |
| icon                    | 使用用于标记图标的字体。                                     |
| menu                    | 使用用于菜单中的字体（下拉列表和菜单列表）。                 |
| message-box             | 使用用于对话框中的字体。                                     |
| small-caption           | 使用用于标记小型控件的字体。                                 |
| status-bar              | 使用用于窗口状态栏中的字体。                                 |

###  textAlign

textAlign 属性根据锚点，设置或返回文本内容的当前对齐方式。

通常，文本会从指定位置**开始**，不过，如果您设置为 textAlign="right" 并将文本放置到位置 150，那么会在**位置 150** **结束**。

**JavaScript 语法：**

```javascript
context.textAlign="center|end|left|right|start";
```

![](C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CHTML5%5Cimages%5CtextAlign.png)

**属性值**

| 值     | 描述                           |
| :----- | :----------------------------- |
| start  | 默认。文本在指定的位置开始。   |
| end    | 文本在指定的位置结束。         |
| center | 文本的中心被放置在指定的位置。 |
| left   | 文本在指定的位置开始。         |
| right  | 文本在指定的位置结束。         |

###  textBaseline

textBaseline 属性设置或返回在绘制文本时的当前文本基线。

下面的图示演示了 textBaseline 属性支持的各种基线：

![](C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CHTML5%5Cimages%5CtextBaseline1.png)

**默认值：**alphabetic

**JavaScript 语法：**

```javascript
context.textBaseline="alphabetic|top|hanging|middle|ideographic|bottom";
```

![](C:%5CUsers%5CAdministrator%5CDesktop%5C%E5%89%8D%E7%AB%AF%E7%AC%94%E8%AE%B0%5CHTML5%5Cimages%5CtextBaseline2.png)

**属性值**

| 值          | 描述                             |
| :---------- | :------------------------------- |
| alphabetic  | 默认。文本基线是普通的字母基线。 |
| top         | 文本基线是 em 方框的顶端。       |
| hanging     | 文本基线是悬挂基线。             |
| middle      | 文本基线是 em 方框的正中。       |
| ideographic | 文本基线是表意基线。             |
| bottom      | 文本基线是 em 方框的底端。       |

##  方法

###  fillText()

fillText() 方法在画布上绘制填色的文本。文本的默认颜色是黑色。

**提示：**请使用[font](#font)属性来定义字体和字号，并使用 [fillStyle](#fillStyle)属性以另一种颜色/渐变来渲染文本。

**JavaScript 语法：**

```javascript
context.fillText(text,x,y,maxWidth);
```

**参数值**

| 参数       | 描述                                      |
| :--------- | :---------------------------------------- |
| *text*     | 规定在画布上输出的文本。                  |
| *x*        | 开始绘制文本的 x 坐标位置（相对于画布）。 |
| *y*        | 开始绘制文本的 y 坐标位置（相对于画布）。 |
| *maxWidth* | 可选。允许的最大文本宽度，以像素计。      |

###  strokeText()

strokeText() 方法在画布上绘制文本（无填充色）。文本的默认颜色是黑色。

**提示：**请使用 [font](#font) 属性来定义字体和字号，并使用 [strokeStyle](#strokeStyle) 属性以另一种颜色/渐变来渲染文本。

**JavaScript 语法：**

```javascript
context.strokeText(text,x,y,maxWidth);
```

**参数值**

| 参数       | 描述                                      |
| :--------- | :---------------------------------------- |
| *text*     | 规定在画布上输出的文本。                  |
| *x*        | 开始绘制文本的 x 坐标位置（相对于画布）。 |
| *y*        | 开始绘制文本的 y 坐标位置（相对于画布）。 |
| *maxWidth* | 可选。允许的最大文本宽度，以像素计。      |

###  measureText()

measureText()方法返回一个对象，该对象包含以像素计的指定字体宽度。

**提示：**如果您需要在文本向画布输出之前，就了解文本的宽度，那么请使用该方法。

**JavaScript 语法：**

```javascript
context.measureText(text).width;
```

**参数值**

| 参数   | 描述           |
| :----- | :------------- |
| *text* | 要测量的文本。 |

#  图像绘制

##  方法

###  drawImage()

drawImage() 方法在画布上绘制图像、画布或视频。

drawImage() 方法也能够绘制图像的某些部分，以及/或者增加或减少图像的尺寸。

**JavaScript 语法**

在画布上定位图像：

```javascript
context.drawImage(img,x,y);
```

在画布上定位图像，并规定图像的宽度和高度：

```javascript
context.drawImage(img,x,y,width,height);
```

剪切图像，并在画布上定位被剪切的部分：

```javascript
	context.drawImage(img,sx,sy,swidth,sheight,x,y,width,height);
```

#  像素操作

##  属性

###  width

width 属性返回 ImageData 对象的宽度，以像素计。

**提示：**请参阅 [createImageData()](#createImageData)、 [getImageData()](#getImageData) 和 [putImageData()](#putImageData) 方法，以获得更多关于 ImageData 对象的知识。

###  height

height 属性返回 ImageData 对象的高度，以像素计。

**提示：**请参阅 [createImageData()](#createImageData)、 [getImageData()](#getImageData) 和 [putImageData()](#putImageData) 方法，以获得更多关于 ImageData 对象的知识。

###  data

data 属性返回一个对象，该对象包含指定的 ImageData 对象的图像数据。

对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：

R - 红色（0-255）
G - 绿色（0-255）
B - 蓝色（0-255）
A - alpha 通道（0-255; 0 是透明的，255 是完全可见的）

color/alpha 信息以数组形式存在，并存储于 ImageData 对象的 data 属性中。

**实例**

把 ImageData 对象中的第一个像素变为红色的语法：

```javascript
imgData=ctx.createImageData(100,100);

imgData.data[0]=255;
imgData.data[1]=0;
imgData.data[2]=0;
imgData.data[3]=255;
```

把 ImageData 对象中的第二个像素变为绿色的语法：

```javascript
imgData=ctx.createImageData(100,100);

imgData.data[4]=0;
imgData.data[5]=255;
imgData.data[6]=0;
imgData.data[7]=255;
```

**提示：**请参阅 [createImageData()](#createImageData)、 [getImageData()](#getImageData) 和 [putImageData()](#putImageData) 方法，以获得更多关于 ImageData 对象的知识。

##  方法

###  createImageData()

createImageData() 方法创建新的空白 ImageData 对象。新对象的默认像素值 transparent black。

对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：

R - 红色（0-255）
G - 绿色（0-255）
B - 蓝色（0-255）
A - alpha 通道（0-255; 0 是透明的，255 是完全可见的）

因此 ，transparent black 表示 (0,0,0,0)。

color/alpha 信息以数组形式存在，并且由于数组包含了每个像素的四条信息，所以数组的大小是 ImageData 对象的四倍：width*height*4。（获得数组大小有更简单的办法，就是使用 ImageDataObject.data.length）

包含 color/alpha 信息的数组存储于 ImageData 对象的 [data](#data) 属性中。

**提示：**在操作完成数组中的 color/alpha 信息之后，您可以使用 [putImageData()](#putImageData) 方法将图像数据拷贝回画布上。

**JavaScript 语法**

1. 以指定的尺寸（以像素计）创建新的 ImageData 对象：

```javascript
var imgData=context.createImageData(width,height);
```

2. 创建与指定的另一个 ImageData 对象尺寸相同的新 ImageData 对象（不会复制图像数据）：

```javascript
var imgData2=context.createImageData(imageData1);
```

**参数值****

| 参数        | 描述                             |
| :---------- | :------------------------------- |
| *width*     | ImageData 对象的宽度，以像素计。 |
| *height*    | ImageData 对象的高度，以像素计。 |
| *imageData* | 另一个 ImageData 对象。          |

###  getImageData()

getImageData() 方法返回 ImageData 对象，该对象拷贝了画布指定矩形的像素数据。

**注意：**ImageData 对象不是图像，它规定了画布上一个部分（矩形），并保存了该矩形内每个像素的信息。

对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：

R - 红色（0-255）
G - 绿色（0-255）
B - 蓝色（0-255）
A - alpha 通道（0-255; 0 是透明的，255 是完全可见的）

color/alpha 信息以数组形式存在，并存储于 ImageData 对象的 [data](#data) 属性中。

**提示：**在操作完成数组中的 color/alpha 信息之后，您可以使用 [putImageData()](#putImageData) 方法将图像数据拷贝回画布上。

**JavaScript 语法**

```javascript
context.getImageData(x,y,width,height);
```

**参数值**

| 参数     | 描述                                        |
| :------- | :------------------------------------------ |
| *x*      | 开始复制的左上角位置的 x 坐标（以像素计）。 |
| *y*      | 开始复制的左上角位置的 y 坐标（以像素计）。 |
| *width*  | 要复制的矩形区域的宽度。                    |
| *height* | 要复制的矩形区域的高度。                    |

###  putImageData()

putImageData() 方法将图像数据（从指定的 ImageData 对象）放回画布上。

**JavaScript 语法**

```javascript
context.putImageData(imgData,x,y,dirtyX,dirtyY,dirtyWidth,dirtyHeight);
```

**参数值**

| 参数          | 描述                                                  |
| :------------ | :---------------------------------------------------- |
| *imgData*     | 规定要放回画布的 ImageData 对象。                     |
| *x*           | ImageData 对象左上角的 x 坐标，以像素计。             |
| *y*           | ImageData 对象左上角的 y 坐标，以像素计。             |
| *dirtyX*      | 可选。水平值（x），以像素计，在画布上放置图像的位置。 |
| *dirtyY*      | 可选。垂直值（y），以像素计，在画布上放置图像的位置。 |
| *dirtyWidth*  | 可选。在画布上绘制图像所使用的宽度。                  |
| *dirtyHeight* | 可选。在画布上绘制图像所使用的高度。                  |

#  合成

##  属性

###  globalAlpha

globalAlpha 属性设置或返回绘图的当前透明值（alpha 或 transparency）。

globalAlpha 属性值必须是介于 0.0（完全透明） 与 1.0（不透明） 之间的数字。

**JavaScript 语法：**

```javascript
context.globalAlpha=number;
```

**属性值**

| 值       | 描述                                                     |
| :------- | :------------------------------------------------------- |
| *number* | 透明值。必须介于 0.0（完全透明） 与 1.0（不透明） 之间。 |

###  globalCompositeOperation

globalCompositeOperation 属性设置或返回如何将一个源（新的）图像绘制到目标（已有的）的图像上。

*源图像 =* 您打算放置到画布上的绘图。

*目标图像 =* 您已经放置在画布上的绘图。

**默认值：**source-over

**JavaScript 语法：**

```javascript
context.globalCompositeOperation="source-in";
```

**属性值**

| 值               | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| source-over      | 默认。在*目标图像*上显示*源图像*。                           |
| source-atop      | 在*目标图像*顶部显示*源图像*。*源图像*位于*目标图像*之外的部分是不可见的。 |
| source-in        | 在*目标图像*中显示*源图像*。只有*目标图像*之内的*源图像*部分会显示，*目标图像*是透明的。 |
| source-out       | 在*目标图像*之外显示*源图像*。只有*目标图像*之外的*源图像*部分会显示，*目标图像*是透明的。 |
| destination-over | 在*源图像*上显示*目标图像*。                                 |
| destination-atop | 在*源图像*顶部显示*目标图像*。*目标图像*位于*源图像*之外的部分是不可见的。 |
| destination-in   | 在*源图像*中显示*目标图像*。只有*源图像*之内的*目标图像*部分会被显示，*源图像*是透明的。 |
| destination-out  | 在*源图像*之外显示*目标图像*。只有*源图像*之外的*目标图像*部分会被显示，*源图像*是透明的。 |
| lighter          | 显示*源图像* + *目标图像*。                                  |
| copy             | 显示*源图像*。忽略*目标图像*。                               |
| xor              | 使用异或操作对*源图像*与*目标图像*进行组合。                 |

#  其他

| 方法          | 描述                             |
| :------------ | :------------------------------- |
| save()        | 保存当前环境的状态。             |
| restore()     | 返回之前保存过的路径状态和属性。 |
| createEvent() |                                  |
| getContext()  |                                  |
| toDataURL()   |                                  |