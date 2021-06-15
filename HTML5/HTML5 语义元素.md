#  HTML5 语义元素

##  什么是语义元素

一个语义元素能够清楚的描述其意义给浏览器和开发者。

**无语义** 元素实例: `<div> `和 `<span>` - 无需考虑内容.

**语义**元素实例: `<form>`, `<table>`, and `<img>` - 清楚的定义了它的内容.

## HTML5中新的语义元素

许多现有网站都包含以下HTML代码： `<div id="nav">`, `<div class="header">`, 或者 `<div id="footer">`, 来指明导航链接, 头部, 以及尾部.

HTML5 提供了新的语义元素来明确一个Web页面的不同部分:

- `<header>`
- `<nav>`
- `<section>`
- `<article>`
- `<aside>`
- `<figcaption>`
- `<figure>`
- `<footer>`

## HTML5 `<section>` 元素

<section> 标签定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分。

## HTML5 `<article>` 元素

`<article>` 标签定义独立的内容。.

`<article> `元素使用实例:

- Forum post(论坛帖子)
- Blog post(博客文章)
- News story(新闻)
- Comment(评论)

## HTML5 `<nav>` 元素

`<nav>` 标签定义导航链接的部分。

<nav> 元素用于定义页面的导航链接部分区域，但是，不是所有的链接都需要包含在 <nav> 元素中!
## HTML5 `<aside>` 元素

`<aside>` 标签定义页面主区域内容之外的内容（比如侧边栏）。

aside 标签的内容应与主区域的内容相关.

## HTML5 `<header>` 元素

`<header>`元素描述了文档的头部区域

`<header>`元素主要用于定义内容的介绍展示区域.

在页面中你可以使用多个`<header>` 元素.

## HTML5 `<footer>` 元素

`<footer>` 元素描述了文档的底部区域.

`<footer>` 元素应该包含它的包含元素

一个页脚通常包含文档的作者，著作权信息，链接的使用条款，联系信息等

文档中你可以使用多个 `<footer>`元素.

## HTML5 `<figure> `和 `<figcaption>` 元素

<figure>标签规定独立的流内容（图像、图表、照片、代码等等）。

<figure> 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。

`<figcaption>` 标签定义 `<figure> `元素的标题.

`<figcaption>`元素应该被置于 "figure" 元素的第一个或最后一个子元素的位置。