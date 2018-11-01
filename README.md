# Bootstrap-3-
Bootstrap 3 的学习笔记
# Bootstrap
Bootstrap 是一个用于快速开发 Web 应用程序和网站的前端框架。基于 HTML、CSS、JavaScript。
## 优点
* **移动设备优先**：框架包含了贯穿于整个库的移动设备优先的样式。
* 主流浏览器都支持
* **响应式设计**：响应式 CSS 能够自适应于台式机、平板和手机。
  ![设备](http://www.runoob.com/wp-content/uploads/2014/06/responsive.jpg)

### 自带特性：全局 CSS 设置、定义基本的 HTML 元素样式、可扩展的 class，先进的网格系统。

### 组件：十几个可重用组件，用于创建图像、下拉菜单、导航、警告框、弹出框等等。

### JavaScript 插件：包含十几个自定义的 jQuery 插件。

### 定制：定制组件、LESS 变量和 jQuery 插件。

* Bootstrap 的 JavaScript 插件需要引入 jQuery
* 国内推荐使用 Staticfile CDN 上的库：
```html
<!-- 新 Bootstrap 核心 CSS 文件 -->
<link href="https://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
 
<!-- jQuery文件。务必在bootstrap.min.js 之前引入 -->
<script src="https://cdn.staticfile.org/jquery/2.1.1/jquery.min.js"></script>
 
<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.staticfile.org/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
```
----------------------------
## CSS 概览
### HTML5 文档类型（Doctype）
```html
<!DOCTYPE html>
<html>
....
</html>
```
### 移动设备优先
为了让 Bootstrap 开发的网站对移动设备友好，确保适当的绘制和触屏缩放，需要在网页的 head 之中添加 viewport meta 标签：
```html
<meta name="viewport" content="width=device-width,  initial-scale=1.0">
```
### 响应式图像
通过添加 *img-responsive* class 可以让图像对响应式布局的支持更友好。
```html
<img src="..." class="img-responsive" alt="响应式图像">
```
这个 class 包含的 css 属性如下：
```css
.img-responsive {
    display:block;
    height:auto;
    max-width:100%;
}
```
## 全局显示、排版和链接
### 基本的全局显示
Bootstrap 3 使用 *body {margin:0;}* 来移除 body 的边距。
有关 body 的设置：
```css
body {
    font-family:"Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    line-height: 1.428571429;
    color: #333333;
    background-color: #ffffff;
}
```
### 排版
使用 @font-family-base、@font-size-base 和 line-height-base 属性作为排版样式。
### 链接样式
通过属性 @link-color 设置全局链接的颜色。
对于链接的默认样式，如下设置：
```css
a:hover,
a:focus {
    color: #2a6496;
    text-decoration: underline;
}

a:focus {
    outline: thin dotted #333;
    outline: 5px auto -webkit-focus-ring-color;
    outline-offset: -2px;
}
```
当鼠标悬停在链接上，或者点击过的链接，颜色会被设置为 #2a6496。同时会呈现一条下划线。
除此之外，点击过的链接会呈现一个颜色码为 #333 的细的虚线轮廓。5 像素宽，且对于基于 webkit 浏览器有一个 -webkit-focus-ring-color 的浏览器扩展。轮廓偏移设置为 -2 像素。

## 容器（Container）
```html
<div class="container">
  ...
</div>
```
Bootstrap 3 的 *container* class 用于包裹页面上的内容，在 bootstrap.css 文件中的设置如下：
```css
.container {
    padding-right: 15px;
    padding-left: 15px;
    margin-right: auto;
    margin-left: auto;
}
```
左右外边距交由浏览器决定，内边距为固定宽度。因此默认情况下容器是不可嵌套的。

-------------------------------
## Bootstrap 网格系统 Grid System
Bootstrap 提供了一套响应式、移动设备优先的流式网格系统，随着屏幕或视口（viewport）尺寸的增加，屏幕会自动分为最多 12 列。
>网页设计中的网格用于组织内容，让网站易于浏览，并降低用户端的负载。
### Bootstrap 网格系统的工作原理
网格系统通过一系列包含内容的行和列来创建页面布局。
* 行必须放在 .**container** class 内，以便获得适当的对齐（alignment）和内边距（padding）。
* 使用行来创建列的水平组。
* 内容应该放置在列内，且唯有列可以是行的直接子元素。
* 预定义的网格类，比如 .**row** 和 .**col-xs-4**，可用于快速创建网格布局。LESS 混合类可用于更多语义布局。
* 列通过内边距（padding）来创建列内容之间的间隙。该内边距是通过 .**rows** 上的外边距（margin）取负，表示第一列和最后一列的行偏移。
* 网格系统是通过指定您想要横跨的十二个可用的列来创建的。例如要创建三个相等的列，则使用三个 .**col-xs-4**。

### 媒体查询是非常别致的“有条件的 CSS 规则”。
Bootstrap 中的媒体查询允许您基于视口大小移动、显示并隐藏内容。下面的媒体查询在 LESS 文件中使用，用来创建 Bootstrap 网格系统中的关键的分界点阈值。
```css
/* 超小设备（手机，小于 768px） */
/* Bootstrap 中默认情况下没有媒体查询 */

/* 小型设备（平板电脑，768px 起） */
@media (min-width: @screen-sm-min) { ... }

/* 中型设备（台式电脑，992px 起） */
@media (min-width: @screen-md-min) { ... }

/* 大型设备（大台式电脑，1200px 起） */
@media (min-width: @screen-lg-min) { ... }
```

### 基本的网格结构
```html
<div class="container">
  <div class="row">
    <div class="col-*-*"></div>
    <div class="col-*-*"></div>
  </div>
  <div class="row">...</div>
</div>
<div class="container">...</div>
```
## 实例
```html
<div class="col-sm-3 col-md-6 col-lg-4">....</div>
<div class="col-sm-9 col-md-6 col-lg-8">....</div>
```
现在，给我们提供了 3 种不同的列布局，分别适用于三种设备。在手机上，它将是左边 25% 右边 75% 的布局。在平板电脑上，它将是 50%/50% 的布局。在大型视口的设备上，它将是 33%/66% 的布局。

### 偏移列
为了在大屏幕显示器上使用偏移，请使用 .col-md-offset-* 类。
实例中，我们有 <div class="col-md-6">..</div>，我们将使用 .col-md-offset-3 class 来居中这个 div。
```html
<div class="container">
    <h1>Hello, world!</h1>
    <div class="row" >
        <div class="col-md-6 col-md-offset-3" 
        style="background-color: #dedef8;box-shadow: 
        inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing 
            elit.
            </p>
        </div>
    </div>
</div>
```
### 嵌套列
为了在内容中嵌套默认的网格，请添加一个新的 .row，并在一个已有的 .col-md-* 列内添加一组 .col-md-* 列。被嵌套的行应包含一组列，这组列个数不能超过12（其实，没有要求你必须占满12列）。

在下面的实例中，布局有两个列，第二列被分为两行四个盒子。
```html
<div class="container">
    <h1>Hello, world!</h1>
    <div class="row">
        <div class="col-md-3" style="background-color: #dedef8;box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
            <h4>第一列</h4>
            <p>
                Lorem ipsum dolor sit amet, consectetur adipisicing elit.
            </p>
        </div>
        <div class="col-md-9" style="background-color: #dedef8;box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
            <h4>第二列 - 分为四个盒子</h4>
            <div class="row">
                <div class="col-md-6" style="background-color: #B18904; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
                    <p>
                        Consectetur art party Tonx culpa semiotics. Pinterest 
        assumenda minim organic quis.
                    </p>
                </div>
                <div class="col-md-6" style="background-color: #B18904; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
                    <p>
                         sed do eiusmod tempor incididunt ut labore et dolore magna 
        aliqua. Ut enim ad minim veniam, quis nostrud exercitation 
        ullamco laboris nisi ut aliquip ex ea commodo consequat.
                    </p>
                </div>
            </div>
            <div class="row">
                <div class="col-md-6" style="background-color: #B18904; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
                    <p>
                        quis nostrud exercitation ullamco laboris nisi ut 
        aliquip ex ea commodo consequat.
                    </p>
                </div>
                <div class="col-md-6" style="background-color: #B18904; box-shadow: inset 1px -1px 1px #444, inset -1px 1px 1px #444;">
                    <p>
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit, 
        sed do eiusmod tempor incididunt ut labore et dolore magna 
        aliqua. Ut enim ad minim.
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>
```

---------------------
## Bootstrap 排版
### 强调
为了给段落添加强调文本，则可以添加 class="lead"，这将得到更大更粗、行高更高的文本。

HTML 的默认强调标签 `<small>`（设置文本为父文本大小的 85%）、`<strong>`（设置文本为更粗的文本）、`<em>`（设置文本为斜体）。

Bootstrap 提供了一些用于强调文本的类，如下面实例所示：
```html
<small>本行内容是在标签内</small><br>
<strong>本行内容是在标签内</strong><br>
<em>本行内容是在标签内，并呈现为斜体</em><br>
<p class="text-left">向左对齐文本</p>
<p class="text-center">居中对齐文本</p>
<p class="text-right">向右对齐文本</p>
<p class="text-muted">本行内容是减弱的</p>
<p class="text-primary">本行内容带有一个 primary class</p>
<p class="text-success">本行内容带有一个 success class</p>
<p class="text-info">本行内容带有一个 info class</p>
<p class="text-warning">本行内容带有一个 warning class</p>
<p class="text-danger">本行内容带有一个 danger class</p>
```
### 缩写
HTML 元素提供了用于缩写的标记，比如 WWW 或 HTTP。Bootstrap 定义 `<abbr>` 元素的样式为显示在文本底部的一条虚线边框，当鼠标悬停在上面时会显示完整的文本（只要您为 `<abbr>` title 属性添加了文本）。为了得到一个更小字体的文本，请添加 .initialism 到 `<abbr>`。
```html
<abbr title="World Wide Web">WWW</abbr><br>
<abbr title="Real Simple Syndication" class="initialism">RSS</abbr>
```
### 地址（Address）
使用 `<address>` 标签，您可以在网页上显示联系信息。由于 `<address>` 默认为 display:block;，您需要使用 `<br>` 标签来为封闭的地址文本添加换行。
```html
<address>
  <strong>Some Company, Inc.</strong><br>
  007 street<br>
  Some City, State XXXXX<br>
  <abbr title="Phone">P:</abbr> (123) 456-7890
</address>
<address>
  <strong>Full Name</strong><br>
  <a href="mailto:#">mailto@somedomain.com</a>
</address>
```
将会如下显示：
![地址](http://www.runoob.com/wp-content/uploads/2013/10/address_demo.jpg)

## 引用（Blockquote）
您可以在任意的 HTML 文本旁使用默认的 `<blockquote>`。其他选项包括，添加一个 `<small> `标签来标识引用的来源，使用 class .pull-right 向右对齐引用。下面的实例演示了这些特性：
```html
<blockquote>
  <p>
  这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。
  </p>
</blockquote>
<blockquote>
  这是一个带有源标题的引用。
  <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
</blockquote>
<blockquote class="pull-right">
  这是一个向右对齐的引用。
  <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
</blockquote>
```
结果显示如下：

![](http://www.runoob.com/wp-content/uploads/2014/06/blockquote_demo.jpg)
## Bootstrap 代码

Bootstrap 允许您以两种方式显示代码：

第一种是 &lt;code&gt; 标签。如果您想要内联显示代码，那么您应该使用 &lt;code&gt; 标签。
第二种是 &lt;pre&gt; 标签。如果代码需要被显示为一个独立的块元素或者代码有多行，那么您应该使用 &lt;pre&gt; 标签。
请确保当您使用 &lt;pre&gt; 和 &lt;code&gt; 标签时，开始和结束标签使用了 unicode 变体： \&lt; 和 \&gt;。

让我们来看看下面的实例：
```html
<p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
<p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
<pre>
    &lt;article&gt;
        &lt;h1&gt;Article Heading&lt;/h1&gt;
    &lt;/article&gt;
</pre>
```
实例展示如下图：

![图片](http://www.runoob.com/wp-content/uploads/2014/06/code_demo.jpg)

## 响应式表格
通过把任意的 .table 包在 .table-responsive class 内，您可以让表格水平滚动以适应小型设备（小于 768px）。当在大于 768px 宽的大型设备上查看时，您将看不到任何的差别。
```html
<div class="table-responsive">
  <table class="table">
    <caption>响应式表格布局</caption>
    <thead>
      <tr>
        <th>产品</th>
        ...
    </thead>
    <tbody>
        ...
    </tbody>
  </table>
</div>
```
