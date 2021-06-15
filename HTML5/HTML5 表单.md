#  HTML5 新的 Input 类型

##  Input 类型：color

color 类型用在input字段主要用于选取颜色，如下所示：

```html
<input type="color">
```

##  Input 类型：date

date 类型允许你从一个日期选择器选择一个日期。(年/月/日)

```html
生日：<input type="date" name="birthday">
```

## Input 类型：datetime

datetime 类型允许你选择一个日期（UTC 时间）。(chrome不支持)

```html
生日 (日期和时间): <input type="datetime" name="birthdaytime">
```

## Input 类型：datetime_local

datetime-local 类型允许你选择一个日期和时间 (无时区).

```html
生日 (日期和时间): <input type="datetime-local" name="bdaytime">
```

## Input 类型：email

email 类型用于应该包含 e-mail 地址的输入域。

在提交表单时，会自动验证 email 域的值是否合法有效:

```html
E-mail: <input type="email" name="email">
```

## Input 类型：month

month 类型允许你选择一个月份。

定义月与年 (无时区):

```html
生日 (月和年): <input type="month" name="bdaymonth">
```

## Input 类型：number

number 类型用于应该包含数值的输入域。

您还能够设定对所接受的数字的限定：

定义一个数值输入域(限定):

```html
数量 ( 1 到 5 之间 ): <input type="number" name="quantity" min="1" max="5">
```

使用下面的属性来规定对数字类型的限定：

| 属性      | 描述                       |
| :-------- | :------------------------- |
| disabled  | 规定输入字段是禁用的       |
| max       | 规定允许的最大值           |
| maxlength | 规定输入字段的最大字符长度 |
| min       | 规定允许的最小值           |
| pattern   | 规定用于验证输入字段的模式 |
| readonly  | 规定输入字段的值无法修改   |
| required  | 规定输入字段的值是必需的   |
| size      | 规定输入字段中的可见字符数 |
| step      | 规定输入字段的合法数字间隔 |
| value     | 规定输入字段的默认值       |

## Input 类型：range

range 类型用于应该包含一定范围内数字值的输入域。

range 类型显示为滑动条。

```html
<input type="range" name="points" min="1" max="10">
```

请使用下面的属性来规定对数字类型的限定：

- max - 规定允许的最大值
- min - 规定允许的最小值
- step - 规定合法的数字间隔
- value - 规定默认值

## Input 类型：search

search 类型用于搜索域，比如站点搜索或 Google 搜索。

```html
Search Google: <input type="search" name="googlesearch">
```

## Input 类型：tel

定义输入电话号码字段:

```html
电话号码: <input type="tel" name="usrtel">
```

## Input 类型：time

time 类型允许你选择一个时间。(时/分)

```html
选择时间: <input type="time" name="usr_time">
```

## Input 类型：url

url 类型用于应该包含 URL 地址的输入域。

在提交表单时，会自动验证 url 域的值。

```html
添加您的主页: <input type="url" name="homepage">
```

## Input 类型：week

week 类型允许你选择周和年。

```html
选择周: <input type="week" name="week_year">
```

#  HTML5 新的表单元素

##  HTML5 `<datalist>`元素

`<datalist>` 元素规定输入域的选项列表。

`<datalist>` 属性规定 form 或 input 域应该拥有自动完成功能。当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项：

使用 `<input>` 元素的列表属性与 `<datalist>` 元素绑定:

请使用 `<input> `元素的 list 属性来绑定`<datalist>` 元素。

**实例**

```html
<input list="browsers">
 
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```

## HTML5 `<keygen>`元素

`<keygen>` 元素的作用是提供一种验证用户的可靠方法。

`<keygen>`标签规定用于表单的密钥对生成器字段。

当提交表单时，会生成两个键，一个是私钥，一个公钥。

私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。

**实例**

```html
<form action="demo_keygen.asp" method="get">
用户名: <input type="text" name="usr_name">
加密: <keygen name="security">
<input type="submit">
</form>
```

## HTML5 `<output>`元素

`<output> `元素用于不同类型的输出，比如计算或脚本输出：

**实例**

```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100
+<input type="number" id="b" value="50">
=<output name="x" for="a b"></output>
</form>
```

###  属性

####  for

for 属性规定计算中使用的元素与计算结果之间的关系。

**语法**

```html
<output for="element_id">
```

**属性值**

| 值           | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| *element_id* | 规定一个或多个元素的 id 列表，以空格分隔。这些元素描述了计算中使用的元素与计算结果之间的关系。 |

####  name

name 属性规定 `<output>` 元素的名称。

name 属性用于在表单提交后引用表单数据，或者用于在 JavaScript 中引用元素。

#  HTML5 新的表单属性

........................................................................................................................................................................................................