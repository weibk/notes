#  Less

##  变量(Variables)

定义变量：使用@定义变量。

```less
// 定义变量
@pink: pink;
@blue: blue;
@w200: 200px;
@h200: 200px;
@w400: 400px;
@h400: 400px;
```

使用变量：

```less
#box {
	width: @w400;
	height: @h400;
	background-color: @pink;
}
```

编译后：

```css
#box {
  width: 400px;
  height: 400px;
  background-color: pink;
}
```

变量不仅可以控制CSS规则中的值，还可以在其他地方使用，如选择器名称，属性名，URL和@import语句。

###  选择器(selector)

```less
// Variables
@my-selector: banner;

// Usage
.@{my-selector} {
  font-weight: bold;
  line-height: 40px;
  margin: 0 auto;
}
```

编译后：

```css
.banner {
  font-weight: bold;
  line-height: 40px;
  margin: 0 auto;
}
```

###  属性名(property)

```less
@property: color;

.widget {
  @{property}: #0ee;
  background-@{property}: #999;
}
```

编译后：

```css
.widget {
  color: #0ee;
  background-color: #999;
}
```

###  URL

```less
// Variables
@images: "../img";

// Usage
body {
  color: #444;
  background: url("@{images}/white-sand.png");
}
```

编译后：

```css
body {
  color: #444;
  background: url("../img/white-sand.png");
}
```

###  import 语句

```less
// Variables
@themes: "../../src/themes";

// Usage
@import "@{themes}/tidal-wave.less";
```

###  可变变量(Variable Variables)

在less中，可以使用另一个变量去定义变量的名称：

```less
@primary:  green;
@secondary: blue;

.section {
  @color: primary;

  .element {
    color: @@color;//相当于@primary
  }
}
```

编译为：

```css
.section .element {
  color: green;
}
```

###  变量的声明情况

**变量在使用之前可以不必声明：**

下面的less代码是有效的

```less
.lazy-eval {
  width: @var;
}

@var: @a;
@a: 9%;
```

```less
.lazy-eval {
  width: @var;
  @a: 9%;
}

@var: @a;
@a: 100%;
```

它们都可以编译为：

```css
.lazy-eval {
  width: 9%;
}
```

**多次声明一个变量时，从当前作用域向上搜索，使用最后一次的定义。**

```less
@var: 0;
.class {
  @var: 1;
  .brass {
    @var: 2;
    three: @var;
    @var: 3;
  }
  one: @var;
}
```

编译结果：

```css
.class {
  one: 1;
}
.class .brass {
  three: 3;
}
```

###  属性作为变量

**使用$prop可以将属性像变量一样对待。**

```less
.widget {
  color: #efefef;
  background-color: $color;
}
```

编译为：

```css
.widget {
  color: #efefef;
  background-color: #efefef;
}
```

**注意：**像变量一样，less将选择当前/父范围内的最后一个属性作为最终值。

##  Parent Selector(父选择器)

###  ＆运算符表示嵌套规则的父选择器，在将修改类或伪类应用于现有选择器时最常用：

```less
a {
  color: blue;
  &:hover {
    color: green;
  }
}
```

编译为

```css
a {
  color: blue;
}
a:hover {
  color: green;
 }
```

###  &可以用来产生重复的类名：

```less
.button {
  &-ok {
    background-image: url("ok.png");
  }
  &-cancel {
    background-image: url("cancel.png");
  }

  &-custom {
    background-image: url("custom.png");
  }
}
```

编译为：

```css
.button-ok {
  background-image: url("ok.png");
}
.button-cancel {
  background-image: url("cancel.png");
}
.button-custom {
  background-image: url("custom.png");
}
```

###  多个&

```less
.link {
  & + & {
    color: red;
  }

  & & {
    color: green;
  }

  && {
    color: blue;
  }

  &, &ish {
    color: cyan;
  }
}
```

编译为：

```css
.link + .link {
  color: red;
}
.link .link {
  color: green;
}
.link.link {
  color: blue;
}
.link, .linkish {
  color: cyan;
}
```

**注意：**＆代表所有父选择器（而不仅仅是最接近的祖先）

```less
.grand {
  .parent {
    & > & {
      color: red;
    }

    & & {
      color: green;
    }

    && {
      color: blue;
    }

    &, &ish {
      color: cyan;
    }
  }
}
```

编译为：


```css
.grand .parent > .grand .parent {
  color: red;
}
.grand .parent .grand .parent {
  color: green;
}
.grand .parent.grand .parent {
  color: blue;
}
.grand .parent,
.grand .parentish {
  color: cyan;
}
```

###  改变选择器的顺序

```less
.header {
  .menu {
    border-radius: 5px;
    .no-borderradius & {
      background-image: url('images/button-background.png');
    }
  }
}
```

编译为：

```css
.header .menu {
  border-radius: 5px;
}
.no-borderradius .header .menu {
  background-image: url('images/button-background.png');
}
```

＆还可以用于生成逗号分隔列表中选择器的所有可能排列：

```less
p, a, ul, li {
  border-top: 2px dotted #366;
  & + & {
    border-top: 0;
  }
}
```

编译为：

```css
p,
a,
ul,
li {
  border-top: 2px dotted #366;
}
p + p,
p + a,
p + ul,
p + li,
a + p,
a + a,
a + ul,
a + li,
ul + p,
ul + a,
ul + ul,
ul + li,
li + p,
li + a,
li + ul,
li + li {
  border-top: 0;
}
```

##  Extnd(继承)

```less
nav ul {
  &:extend(.inline);
  background: blue;
}
.inline {
  color: red;
}
```

编译为

```css
nav ul {
  background: blue;
}
.inline,
nav ul {
  color: red;
}
```

###  Extend Syntax(语法)

```less
Selector:extend(Selector) {
    
}
Selecror {
    &.entend(Selector);
}
```

```less
Selector:extend(.d all) {
    //继承所有.d的实例，如".x .d"".d.g"
}
Selector:extend(.d) {
    //仅继承.d实例
}
```

可以包含一个或多个要继承的类：

```less
Selecror {
    &.entend(Selector1);
    &.entend(Selector2);
}
Selecror {
    &.entend(Selector1,Selector2...);
}
```

如果规则集包含多个选择器，则它们中的任何一个都可以具有extend关键字。在一个规则集中扩展的多个选择器：

```less
.big-division,
.big-bag:extend(.bag),
.big-bucket:extend(.bucket) {
  // body
}
```

extend必须在选择器之后。

选择器和extend之间允许有空格。

允许多个扩展，pre:hover:extend(div pre):extend(.bucket tr)相当于pre:hover:extend(div pre, .bucket tr)。

不允许在extend之后再添加选择器，extend必须是在最后，pre:hover:extend(div pre).nth-child(odd)不被允许。

####  extend写在规则集内部

```less
pre:hover,
.some-class {
  &:extend(div pre);
}
```

相当于每个选择器都继承

```css
pre:hover:extend(div pre),
.some-class:extend(div pre) {
    
}
```

####  extend可以匹配嵌套的选择器

```less
.bucket {
  tr { // nested ruleset with target selector
    color: blue;
  }
}
.some-class:extend(.bucket tr) {} // nested ruleset is recognized
```

相当于：

```css
.bucket tr,
.some-class {
  color: blue;
}
```

###  继承的精确匹配

####  不能省略* ：

```less
*.class {
  color: blue;
}
.noStar:extend(.class) {} //无法继承
```

####  伪类的顺序很重要，不能随意调整：

```less
link:hover:visited {
  color: blue;
}
.selector:extend(link:visited:hover) {}//无法继承
```

####  带有nth表达式的

```less
:nth-child(1n+3) {
  color: blue;
}
.child:extend(:nth-child(n+3)) {}//无法继承
```

####  属性选择器中的引用类型无关紧要

```less
[title=identifier] {
  color: blue;
}
[title='identifier'] {
  color: blue;
}
[title="identifier"] {
  color: blue;
}

.noQuote:extend([title=identifier]) {}
.singleQuote:extend([title='identifier']) {}
.doubleQuote:extend([title="identifier"]) {}
```

等同于

```css
[title=identifier],
.noQuote,
.singleQuote,
.doubleQuote {
  color: blue;
}

[title='identifier'],
.noQuote,
.singleQuote,
.doubleQuote {
  color: blue;
}

[title="identifier"],
.noQuote,
.singleQuote,
.doubleQuote {
  color: blue;
}
```

####  extend 中的"all"

当extend参数中最后指定all关键字时，它告诉Less将该选择器作为另一个选择器的一部分进行匹配。 将复制选择器，然后仅将选择器的匹配部分替换为扩展名，从而创建一个新的选择器。

```less
.a.b.test,
.test.c {
  color: orange;
}
.test {
  &:hover {
    color: green;
  }
}

.replacement:extend(.test all) {}
```

编译为

```css
.a.b.test,
.test.c,
.a.b.replacement,
.replacement.c {
  color: orange;
}
.test:hover,
.replacement:hover {
  color: green;
}
```

####  Extend无法将选择器与变量匹配。如果选择器包含变量，则extend将忽略它

```less
@variable: .bucket;
@{variable} { 
  color: blue;
}
.some-class:extend(.bucket) {} // 无效
```

在目标选择器中使用变量，extend不匹配。

```less
.bucket {
  color: blue;
}
.some-class:extend(@{variable}) {} // interpolated selector matches nothing
@variable: .bucket;
```

但是下面的情况extend生效

```less
.bucket {
  color: blue;
}
@{variable}:extend(.bucket) {}
@variable: .selector;
```

编译为：

```css
.bucket, .selector {
  color: blue;
}
```

###  @media 中的继承

####  xtend仅匹配同一媒体声明中的选择器：

```less
@media print {
  .screenClass:extend(.selector) {} 
  .selector { 
    color: black;
  }
}
.selector { 
  color: red;
}
@media screen {
  .selector {  
    color: blue;
  }
}
```

编译为

```css
@media print {
  .selector,
  .screenClass { 
    color: black;
  }
}
.selector { 
  color: red;
}
@media screen {
  .selector { 
    color: blue;
  }
}
```

extend不匹配嵌套@media中的选择器

```less
@media screen {
  .screenClass:extend(.selector) {} 
  @media (min-width: 1023px) {
    .selector {  
      color: blue;
    }
  }
}
```

```css
@media screen and (min-width: 1023px) {
  .selector { 
    color: blue;
  }
}
```

顶级继承匹配所有内容，包括嵌套媒体中的选择器：

```less
@media screen {
  .selector { 
    color: blue;
  }
  @media (min-width: 1023px) {
    .selector {  
      color: blue;
    }
  }
}

.topLevel:extend(.selector) {}
```

编译为

```css
@media screen {
  .selector,
  .topLevel { 
    color: blue;
  }
}
@media screen and (min-width: 1023px) {
  .selector,
  .topLevel { 
    color: blue;
  }
}
```

##  Merge(合并属性)

合并功能允许将多个属性中的值聚合到单个属性下的逗号或空格分隔的列表中。合并对于诸如背景和变换之类的属性很有用。

###  逗号(Comma)

```less
.mixin() {
  box-shadow+: inset 0 0 10px #555;
}
.myclass {
  .mixin();
  box-shadow+: 0 0 20px black;
}
```

编译为

```css
.myclass {
  box-shadow: inset 0 0 10px #555, 0 0 20px black;
}
```

###  空格(Space)

```less
.mixin() {
  transform+_: scale(2);
}
.myclass {
  .mixin();
  transform+_: rotate(15deg);
}
```

编译为

```css
.myclass {
  transform: scale(2) rotate(15deg);
}
```

##  Mixins(混合)

可以混合使用类选择器和ID选择器

```less
.a, #b {
  color: red;
}
.mixin-class {
  .a();
}
.mixin-id {
  #b();
}
```

编译为

```css
.a, #b {
  color: red;
}
.mixin-class {
  color: red;
}
.mixin-id {
  color: red;
}
```

Mixins调用中的括号，不建议省略。

###  如果要创建一个mixin，但又不希望该mixin出现在CSS输出中，请在mixin定义后加上括号。

```less
.my-mixin {
  color: black;
}
.my-other-mixin() {
  background: white;
}
.class {
  .my-mixin();
  .my-other-mixin();
}
```

编译后

```css
.my-mixin {
  color: black;
}
.class {
  color: black;
  background: white;
}
```

###  Mixins中的选择器

Mixins不仅可以包含属性，还可以包含选择器。

```less
.my-hover-mixin() {
  &:hover {
    border: 1px solid red;
  }
}
button {
  .my-hover-mixin();
}
```

编译为

```css
button:hover {
  border: 1px solid red;
}
```

如果要在更复杂的选择器中混合属性，则可以堆叠多个ID或类。

```less
#outer() {
  .inner {
    color: red;
  }
}

.c {
  #outer > .inner();
}
```

空格和>都是可选的

```less
#outer > .inner();
#outer .inner();
#outer.inner();
```

给mixins命名，可以减少与其他库的命名冲突。

```less
#my-library {
  .my-mixin() {
    color: black;
  }
}
//可以这样去使用它
.class {
  #my-library.my-mixin();
}
```

###  `!important` 关键字

在minixs调用之后使用`!important`关键字，可以将其继承的所有属性标记为`!important`。

```less
.foo (@bg: #f5f5f5; @color: #900) {
  background: @bg;
  color: @color;
}
.unimportant {
  .foo();
}
.important {
  .foo() !important;
}
```

编译为

```css
.unimportant {
  background: #f5f5f5;
  color: #900;
}
.important {
  background: #f5f5f5 !important;
  color: #900 !important;
}
```

###  Minixs参数

####  如何给Minixs传递参数：

```less
.border-radius(@radius) {
  -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
          border-radius: @radius;
}
```

可以这样使用：

```less
#header {
  .border-radius(4px);
}
.button {
  .border-radius(6px);
}
```

####  Minixs参数也可以有默认值

```less
.border-radius(@radius: 5px) {
  -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
          border-radius: @radius;
}
```

可以这样调用它：

```less
#header {
  .border-radius();
}
```

###  具有多个参数的Minixs

参数以分号或逗号分隔。建议使用**分号**。因为逗号具有双重含义：可以将其解释为混合参数分隔符或CSS列表分隔符。