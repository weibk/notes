#  HTML DOM 事件

##  鼠标事件

###  点击事件 onclick

当指定元素被点击时触发的事件。

###  oncontextmenu

单击鼠标右键时触发。

###  ondblclick

当指定元素被双击时触发的事件。

###  onmousedown

鼠标按下时触发的事件。

**提示**

与onmousedown事件相关联的事件发生次序：(鼠标左侧/中间  按键)

1. onmousedown
2. onmouseup、
3. onclick

鼠标右键：

1. onmousedown
2. onmouseup
3. oncontextmenu

###  onmouseup

鼠标按键被松开时触发。

###  onmouseenter

鼠标指针移动到指定元素上时触发。

通常与onmouseleave配合使用，不支持事件冒泡。

###  onmouseleave

鼠标指针离开元素时触发。

###  onmousemove

鼠标指针移动到指定元素上触发。

###  onmouseover

鼠标指针移动到指定的元素上时发生。

支持事件冒泡。

###  onmouseout

鼠标指针移出指定的对象时发生。

##  键盘事件

###  onkeydown

用户按下一个键盘按键时触发。

###  onkeyup

onkeyup 事件会在键盘按键被松开时发生。

**提示：**与onkeyup 事件相关的事件发生次序：

1. onkeydown
2. onkeypress
3. onkeyup

###  onkeypress

onkeypress 事件会在键盘按键被按下并释放一个键时发生。

**提示：**与 onkeypress 事件的关联的事件发生次序:

1. onkeydown
2. onkeypress
3. onkeyup

不支持alt  ctrl  shift   esc键

##  表单事件

###  onblur

在对象失去焦点时触发。

###  onchange

onchange 事件会在域的内容改变时发生。在失去焦点后触发判断。

onchange 事件也可用于单选框与复选框改变后触发的事件。

###  onfocus

onfocus 事件在对象获得焦点时发生。

Onfocus 通常用于 `<input>`, `<select>`, 和`<a>`.

###  oninput

oninput 事件在用户输入时触发。

**提示：** 该事件类似于 onchange 事件。不同之处在于 oninput 事件在元素值发生变化是立即触发， onchange 在元素失去焦点时触发。另外一点不同是 onchange 事件也可以作用于 `<keygen>` 和 `<select> `元素。

###  onreset

onreset 事件在表单被重置后触发。绑定在form表单上。

###  onsubmit

onsubmit 事件在表单提交时触发。绑定在form表单上。

###  onselect

onselect 事件会在文本框中的文本被选中时发生。

###  onsearch

onsearch 事件在用户按下"ENTER（回车）" 按键或点击 type="search" 的 <input> 元素的 "x(搜索)" 按钮时触发。

###  onfocusin

onfocusin 事件在一个元素即将获得焦点时触发。

**提示：** onfocusin 事件类似于 onfocus 事件。 主要的区别是 onfocus 事件不支持冒泡。因此，如果你想知道元素或者其子元素是否获取焦点，需要使用 onfocusin 事件。

###  onfocusout

onfocusout 事件在元素即将失去焦点时触发。

**提示：** onfocusout 事件类似于 onblur事件。 主要的区别是 onblur 事件不支持冒泡。因此，如果你需要查看元素或其子元素是否获取焦点，需要使用 onfocusout 事件。

##  框架/对象(Frame/Object)事件

###  onload()

onload 事件会在页面或图像加载完成后立即发生。

onload 通常用于 `<body> `元素，在页面完全载入后(包括图片、css文件等等。)执行脚本代码。

###  onresize

在窗口或框架被调整大小时触发。

在监控的过程中发现每次改变浏览器窗口的时候 onresize 事件都会触发两次(产生 的原因貌似比较复杂，网上没有定论，发现在最大化浏览器的时候，浏览器也会闪一下，有两次窗口大小的改变)。

解决方法: **setTimeout()**

```javascript
function windowResizeEvent(callback) {
    var firstFire = null;
    window.onresize = function () {
        if(firstFire === null) {
            firstFire = setTimeout(function() {
                firstFire = null;
                callback();
            }, 100);
        }
    }
}
```

###  onscroll

元素的滚动条发生滚动时触发。

###  onpagehide

用户离开当前网页跳转到另外一个页面时触发。

###  onpageshow

用户访问页面时触发。

##  拖动事件

| 事件                                                         | 描述                                 | DOM  |
| :----------------------------------------------------------- | :----------------------------------- | :--- |
| [ondrag](https://www.runoob.com/jsref/event-ondrag.html)     | 该事件在元素正在拖动时触发           |      |
| [ondragend](https://www.runoob.com/jsref/event-ondragend.html) | 该事件在用户完成元素的拖动时触发     |      |
| [ondragenter](https://www.runoob.com/jsref/event-ondragenter.html) | 该事件在拖动的元素进入放置目标时触发 |      |
| [ondragleave](https://www.runoob.com/jsref/event-ondragleave.html) | 该事件在拖动元素离开放置目标时触发   |      |
| [ondragover](https://www.runoob.com/jsref/event-ondragover.html) | 该事件在拖动元素在放置目标上时触发   |      |
| [ondragstart](https://www.runoob.com/jsref/event-ondragstart.html) | 该事件在用户开始拖动元素时触发       |      |
| [ondrop](https://www.runoob.com/jsref/event-ondrop.html)     | 该事件在拖动元素放置在目标区域时触发 |      |

##  多媒体(Media)事件

###  onabort

onabort 事件在视频/音频（audio/video）终止加载时触发。

该事件在多媒体数据终止加载时触发，而不是发生错误时触发。

**提示：** 影响多媒体加载的事件有:

- onemptied
- [onerror](https://www.runoob.com/jsref/event-onerror-media.html)
- [onstalled](https://www.runoob.com/jsref/event-onstalled.html)
- [onsuspend](https://www.runoob.com/jsref/event-onsuspend.html)

###  oncanplay

oncanplay 事件在用户可以开始播放视频/音频（audio/video）时触发。

在视频/音频（audio/video）加载过程中，事件的触发顺序如下：

1. onloadstart    开始寻找指定视频/音频（audio/video）触发。
2. ondurationchange    在视频/音频（audio/video）的时长发生变化时触发。
3. onloadedmetadata    在指定视频/音频（audio/video）的元数据加载后触发。
4. onloadeddata    在浏览器加载视频/音频（audio/video）当前帧时触发触发。
5. onprogress      在浏览器下载指定的视频/音频（audio/video）时触发。
6. oncanplay     在用户可以开始播放视频/音频（audio/video）时触发。
7. oncanplaythrough    在视频/音频（audio/video）可以正常播放且无需停顿和缓冲时触发。

###  onended

在视频/音频（audio/video）播放结束时触发。

###  onerror

在视频/音频（audio/video）数据加载期间发生错误时触发。

##  事件对象

###  属性

####  bubbles

返回布尔值，指示事件是否是起泡事件类型。如果是则返回true，否则返回false。

####  cancelable

返回一个布尔值。如果用 preventDefault() 方法可以取消与事件关联的默认动作，则为 true，否则为 fasle。

####  currentTarget

currentTarget 事件属性返回其监听器触发事件的节点，即当前处理该事件的元素、文档或窗口。

在捕获和起泡阶段，该属性是非常有用的，因为在这两个节点，它不同于 target 属性。

####  target

target 事件属性可返回事件的目标节点（触发该事件的节点），如生成事件的元素、文档或窗口。

####  timeStamp

事件属性可返回一个时间戳。指示发生事件的日期和时间（从 epoch 开始的毫秒数）。

epoch 是一个事件参考点。在这里，它是客户机启动的时间。

并非所有系统都提供该信息，因此，timeStamp 属性并非对所有系统/事件都是可用的。

####  type

type 事件属性返回发生的事件的类型，即当前 Event 对象表示的事件的名称。

它与注册的事件句柄同名，或者是事件句柄属性删除前缀 "on" 比如 "submit"、"load" 或 "click"。

###  方法

####  stopPropagation()

阻止事件继续传递。不再派发事件。

####  preventDefault()

通知浏览器不要执行与事件关联的默认动作。

####  initEvent()

初始化新创建的 Event 对象的属性。

##  鼠标键盘事件对象

###  属性

####  altKey

altKey 事件属性返回一个布尔值。指示在指定的事件发生时，Alt 键是否被按下并保持住了。如果事件发生时Alt键被按下则返回true，否则返回false。

####  button

button 事件属性可返回一个整数，指示当事件被触发时哪个鼠标按键被点击。

| 参数 | 描述           |
| :--- | :------------- |
| 0    | 指定鼠标左键。 |
| 1    | 指定鼠标中键。 |
| 2    | 指定鼠标右键。 |

**注意：** Internet Explorer 8 及更早IE版本有不同的参数：

| 参数 | 描述                             |
| :--- | :------------------------------- |
| 1    | 指定鼠标左键。 (IE8及更早IE版本) |
| 4    | 指定鼠标中键。 (IE8及更早IE版本) |
| 2    | 指定鼠标右键。                   |

####  clientX

clientX 事件属性返回当事件被触发时鼠标指针相对于浏览器页面（或客户区）的水平坐标。

####  clientY

clientY 事件属性返回当事件被触发时鼠标指针向对于浏览器页面（客户区）的垂直坐标。

####  ctrlKey

ctrlKey 事件属性可返回一个布尔值，指示当事件发生时，Ctrl 键是否被按下并保持住。如果事件发生时ctrl键被按下则返回true，否则返回false。

####  location

location 属性返回按键在键盘或设置上的位置。

数字可由 4 个常数表示：

**0. DOM_KEY_LOCATION_STANDARD:**

表示不是最左边或者最右边的按键，也不是数字键盘上的数字（该值几乎包含了所有的按键，如 "A", "U", "SPACE" 或 "5")

**1. DOM_KEY_LOCATION_LEFT:**

左侧按键 (如果左侧的 "CTRL" 键或左侧的 "ALT" 键)

**2. DOM_KEY_LOCATION_RIGHT:**

右侧按键 (如果右侧的 "CTRL" 键或左侧的 "ALT" 键)

**3. DOM_KEY_LOCATION_NUMPAD:**

数字按键（在标准键盘的右侧）

**注意：** location 属性可用于 onkeydown 和 onkeyup 事件，但不能用于onkeypress事件。

**注意：** 该属性是只读的。

####  key

key 事件在按下按键时返回按键的标识符。

按键标识符是表示键盘按钮的字符串，该属性的返回值可以是：

- 单个字母 (如 "a", "W", "4", "+" 或 "$")
- 多个字母 (如 "F1", "Enter", "HOME" 或 "CAPS LOCK")

####  keyCode

keyCode 属性返回onkeypress事件触发的键的值的字符代码，或者onkeydown或onkeyup 事件的键的代码。

####  which

返回onkeypress事件触发的键的值的字符代码，或者 onkeydown 或 onkeyup 事件的键的代码。

####  metaKey

metaKey 事件属性可返回一个布尔值，指示当事件发生时，"meta" 键是否被按下并保持住。如果事件发生时meta键被按下则返回true，否则返回false。

####  relatedTarget

relatedTarget 事件属性返回与事件的目标节点相关的节点。

对于 mouseover 事件来说，该属性是鼠标指针移到目标节点上时所离开的那个节点。

对于 mouseout 事件来说，该属性是离开目标时，鼠标指针进入的节点。

对于其他类型的事件来说，这个属性没有用。

####  screenX

screenX 事件属性可返回事件发生时鼠标指针相对于屏幕的水平坐标。

####  screenY

screenY 事件属性可返回事件发生时鼠标指针相对于屏幕的垂直坐标。

####  shiftKey

shiftKey 事件属性可返回一个布尔值，指示当事件发生时，"SHIFT" 键是否被按下并保持住。