
##  模态框
使用模态框的弹窗组件需要三层 div 容器元素，分别为 modal(模态声明层)、
dialog(窗口声明层)、content(内容层)。在内容层里面，还有三层，分别为 header(头
部)、body(主体)、footer(注脚)
```html
//基本实例

<!-- 模态声明，show 表示显示 --> <div class="modal show" tabindex="-1">

<!-- 窗口声明 --> <div class="modal-dialog">

<!-- 内容声明 --> <div class="modal-content">

<!-- 头部 -->

<div class="modal-header">

<button type="button" class="close" data-dismiss="modal">

<span>&times;</span>

</button>

<h4 class="modal-title">会员登录</h4> </div>
<!-- 主体 -->

<div class="modal-body">

<p>暂时无法登录会员</p> </div>
<!-- 注脚 -->

<div class="modal-footer">

<button type="button" class="btn btn-default">

注册</button> <button type="button" class="btn btn-primary">
登录</button>

</div>

</div>


</div>

</div>
```

如果想让模态框自动隐藏，然后通过点击按钮弹窗，那么需要做如下操作。
```html
//模态框去掉 show，增加一个 id <div class="modal" id="myModal">
```
/点击触发模态框显示
```html
<button class="btn btn-primary btn-lg" data-toggle="modal" data-target="#myModal">
点击弹窗

</button>
```
弹窗的大小有三种，默认情况下是正常，还有 lg(大)和 sm(小)
```html
<div class="modal-dialog modal-lg">

<div class="modal-dialog sm-lg">
```
可设置淡入淡出效果
```html
<div class="modal fade" id="myModal">
```
在主体部分使用栅格系统中的流体
```html
<!-- 主体 -->

<div class="modal-body">

<div class="container-fluid"> <div class="row">

<div class="col-md-4">1</div> <div class="col-md-4">1</div> <div class="col-md-4">1</div>

</div>

</div>

</div>
```
基本使用介绍结束之后，我们就来看下插件的各种重要用法。所有的插件，都是基于 JavaScript/jQuery 的。那么，就有四个要素：用法、参数、方法和事件。
#### - 用法 data-toggle
  第一种：可以通过 data 属性
```html
data-toggle="modal" data-target="#myModal"
data-toggle 表示触发类型
data-target 表示触发的节点
```
如果不是使用button，而是a，其中 data-target 也可以使用 href="#myModal"
取代。当然，我们建议使用 data-target。除了 data-toggle 和 data-target 两个声明属性外，还有一些可以用选项。
#### - 参数
可以通过在 HTML 元素上设置 data-*的属性声明来控制效果

|  属性名称 |  类型 |  默认值 |  描述 |
| ------------ | ------------ | ------------ | ------------ |
|  data-backdrop | 布尔值或'static'  |  true | 默认值 true，表示背景存在黑灰透明遮罩，且单击空白背景可关闭弹窗；<br>如果为 false，表示背景不存在黑灰透明遮罩，且点击空白背景不可关闭弹窗；<br>如果是字符串'static'，表示背景存在黑灰透明遮罩，且点击空白不可关闭弹窗。  |
|  data-keyboard | 布尔值  |  true | 如果是 true，按 esc 键会关闭窗口；<br>如果是 false，按 esc 键会不会关闭。  |
| data-show  | 布尔值  |  true | 如果是 true，初始化时，默认显示；<br>如果是 false，初始化时，默认隐藏。  |
|  href | url 路径  | 空值  | 如果值不是以#号开头，则表示一个url 地址，加载 url 内容到modal-content 容器里，并只加载一次。如果是#号，就是取代data-target 的方法。  |

//空白背景且点击不关闭
data-backdrop="false"

//按下 esc 不关闭
data-keyboard="false"

//初始化隐藏，如果是按钮点击触发，第一次点击则无法显示，第二次显示。
data-show="false"

//加载一次 index.html 到容器内 
href="index.html"

	当然，也可以在 JavaScript 直接设置。

|  属性名称 |  类型 |  默认值 |  描述 |
| ------------ | ------------ | ------------ | ------------ |
| backdrop | 布尔值或'static'  |  true | 默认值 true，表示背景存在黑灰透明遮罩，且单击空白背景可关闭弹窗；<br>如果为 false，表示背景不存在黑灰透明遮罩，且点击空白背景不可关闭弹窗；<br>如果是字符串'static'，表示背景存在黑灰透明遮罩，且点击空白不可关闭弹窗。  |
|  keyboard | 布尔值  |  true | 如果是 true，按 esc 键会关闭窗口；<br>如果是 false，按 esc 键会不会关闭。  |
|show  | 布尔值  |  true | 如果是 true，初始化时，默认显示；<br>如果是 false，初始化时，默认隐藏。  |
|  remote | url 路径  | 空值  | 远程获取指定内容填充到modal-content 容器内。  |

```javascript
//通过 jQuery 方式声明 $('#myModal').modal({

show : true,

backdrop : false,

keyboard : false,

remote : 'index.html',

});
```
#### - 方法
如果说，默认不显示弹窗，那么怎么才能通过点击前后弹窗呢？

| 参数名称  | 使用方法  | 描述  |
| ------------ | ------------ | ------------ |
| toggle  |  .modal('toggle') | 触发时，反转切换弹窗状态  |
|  show | .modal('show')  | 触发时，显示弹窗  |
|  hide |  .modal('hide') | 触发时，关闭弹窗  |

```javascript
//点击显示弹窗

$('#btn').on('click', function () {

$('#myModal').modal('show');

});
```
#### - 事件
模态框支持 4 种事件，分别对应弹出前、弹出后、关闭前和关闭后

|  事件类型 |  描述 |
| ------------ | ------------ |
| show.bs.modal  | 在 show 方法调用时立即触发  |
|  shown.bs.modal | 在模态框完全显示出来,并且等css动画完成之后触发  |
|  hide.bs.modal | 在 hide 方法调用时，但还未关闭隐藏时触发  |
|  hidden.bs.modal | 在模态框完全隐藏之后，并且等 CSS 动画完成之后触发  |

```javascript
$('#myModal').on('show.bs.modal', function () {

alert('在 show 方法调用时立即触发！');

});

$('#myModal').on('shown.bs.modal', function () {

alert('在模态框显示完毕后触发！');

});

$('#myModal').on('hide.bs.modal', function () {

alert('在 hide 方法调用时立即触发！');

});

$('#myModal').on('hiden.bs.modal', function () {

alert('在模态框显示完毕后触发！');

});

$('#myModal').on('loaded.bs.modal', function () {

alert('远程数据加载完毕后触发！');

});
```
##  下拉菜单
常规使用中,和组件方法一样,代码如
```html
<div class="dropdown">

<button class="btn btn-primary" data-toggle="dropdown">

下拉菜单

<span class="caret"></span> </button>

<ul class="dropdown-menu"> <li><a href="#">首页</a></li> <li><a href="#">产品</a></li> <li><a href="#">资讯</a></li> <li><a href="#">关于</a></li>

</ul>

</div>
```
声明式用法的关键核心：<br>1.外围容器使用 class="dropdown"包裹；<br>2.内部点击按钮事件绑定 data-toggle="dropdown"；<br>3.菜单元素使用 class="dropdown-menu"。

如果按钮在容器外部，可以通过 data-target 进行绑定。
```html
<button class="btn btn-primary" id="btn" data-toggle="dropdown" data-target="#dropdown">
```
在 JavaScript 调用中，没有属性，方法并不好用<br></br下面介绍四个基本事件。//下拉菜单方法，但仍然需要>下面介绍四个基本事件。//下拉菜单方法，但仍然需要 data-*

```javascript
$('#btn').dropdown();
$('#btn').dropdown('toggle');
```
<br>
下拉菜单支持 4 种事件，分别对应弹出前、弹出后、关闭前和关闭后。

| 事件类型  | 描述  |
| ------------ | ------------ |
| show.bs.dropdown  | 在 show 方法调用时立即触发  |
| shown.bs.dropdown  |在下拉菜单完全显示出来，并且等 CSS 动画完成之后触发   |
|  hide.bs.dropdown |  在 hide 方法调用时，但还未关闭隐藏时触发 |
| hidden.bs.dropdown  | 在下拉菜单完全隐藏之后，并且等 CSS 动画完成之后触发  |

```javascript
//事件，其他雷同

$('#dropdown').on('show.bs.dropdown', function () {

alert('在调用 show 方法时立即触发！');
```

##  滚动监听(注意水平滚动监元素要绑定body身上)
滚动监听插件是用来根据滚动条所处在的位置自动更新导航项目，显示导航项目高亮显示。
```html
<nav id="nav" class="navbar navbar-default">

<a href="#" class="navbar-brand">Web 开发</a> <ul class="nav navbar-nav">

<li><a href="#html5">HTML5</a></li>

<li><a href="#bootstrap">Bootstrap</a></li> <li class="dropdown">

<a href="#" data-toggle="dropdown">JavaScript <span class="caret"></span></a>

<ul class="dropdown-menu">

<li><a href="#jquery">jQuery</a></li> <li><a href="#yui">Yui</a></li> <li><a href="#extjs">Extjs</a></li>

</ul>

</li>

</ul>

</nav>

<div data-offset="0" data-target="#nav" data-spy="scroll" style="height: 200px; overflow: auto; position: relative;padding: 0 10px;">

<h4 id="html5">HTML5</h4>
<p>标准通用标记语言下的一个应用 HTML 标准自 1999 年 12 月发布的 HTML4.01 后，后继的 HTML5 和其它标准被束之高阁，为了推动 Web 标准化运动的发展，一些公司联合起来，成立了一个叫做 Web Hypertext Application Technology Working Group
（Web 超文本应用技术工作组 -WHATWG）的组织。WHATWG 致力于 Web 表单和应用程序，而 W3C（World Wide Web Consortium，万维网联盟） 专注于 XHTML2.0。在 2006 年，双方决定进行合作，来创建一个新版本的 HTML。</p>

<h4 id="bootstrap">Bootstrap</h4>
<p>Bootstrap，来自 Twitter，是目前很受欢迎的前端框架。Bootstrap 是基
于 HTML、CSS、JAVASCRIPT 的，它简洁灵活，使得 Web 开发更加快捷。[1] 它由 Twitter 的设计师 Mark Otto 和 Jacob Thornton 合作开发，是一个 CSS/HTML 框架。Bootstrap提供了优雅的 HTML 和 CSS 规范，它即是由动态 CSS 语言 Less 写成。Bootstrap 一经推出后颇受欢迎，一直是 GitHub 上的热门开源项目，包括 NASA 的 MSNBC（微软全国广播公司）的 Breaking News 都使用了该项目。[2] 国内一些移动开发者较为熟悉的框架，如 WeX5 前端开源框架等，也是基于 Bootstrap 源码进行性能优化而来。[3] </p>

<h4 id="jquery">jQuery</h4> 
<p>JQuery 是继 prototype 之后又一个优秀的 Javascript 库。它是轻量级的 js库 ，它兼容 CSS3，还兼容各种浏览器（IE 6.0+, FF 1.5+, Safari 2.0+, Opera 9.0+）， jQuery2.0 及后续版本将不再支持 IE6/7/8 浏览器。jQuery 使用户能更方便地处理 HTML
（标准通用标记语言下的一个应用）、events、实现动画效果，并且方便地为网站提供 AJAX 交互。jQuery 还有一个比较大的优势是，它的文档说明很全，而且各种应用也说得很详细，同时还有许多成熟的插件可供选择。jQuery 能够使用户的 html 页面保持代码和 html 内容分离，也就是说，不用再在 html 里面插入一堆 js 来调用命令了，只需要定义 id 即可。</p>

<h4 id="yui">Yui</h4>
<p>近几年随着 jQuery、Ext 以及 CSS3 的发展，以 Bootstrap 为代表的前端开发框架如雨后春笋般挤入视野，可谓应接不暇。不论是桌面浏览器端还是移动端都涌现出很多优秀的框架，极大丰富了开发素材，也方便了大家的开发。这些框架各有特点，本文对这些框架进行初步的介绍与比较，希望能够为大家选择框架提供一点帮助，也为后续详细研究这些框架的抛砖引玉。</p>

<h4 id="extjs">Extjs</h4>
<p>ExtJS 可以用来开发 RIA 也即富客户端的 AJAX 应用，是一个用 javascript写的，主要用于创建前端用户界面，是一个与后台技术无关的前端 ajax 框架。因此，可以把 ExtJS 用在.Net、Java、Php 等各种开发语言开发的应用中。ExtJs 最开始基于 YUI 技术，由开发人员 JackSlocum 开发，通过参考 JavaSwing 等机制来组织可视化组件，无论从 UI 界面上 CSS 样式的应用，到数据解析上的异常处理，都可算是一款不可多得的JavaScript 客户端技术的精品。</p> </div>
```

这里有两个重要的属性，如下图：

| 属性名  |  描述 |
| ------------ | ------------ |
|  data-offset | 默认值为 10，固定弄内容距滚动容器 10 像素以内，就高亮显示所对应的菜单  |
| data-spy  | 设置 scroll，将设置滚动容器监听。  |
|  data-target | 设置#nav，绑定指定监听的菜单  |

PS：在一个菜单和一个导航的时候，data-target 不设置也可以稳定实现滚动监听高亮。但多个导航时，你不关联其中一个，会导致错误，所以，一般要加上。
<br>
#### - 参数
如果使用 JavaScript 脚本方式，可以去掉 data-*，使用脚本属性定义：offset、spy和 target。具体方法如下
```javascript
$('#content').scrollspy({
offset : 0,
target : '#nav',
});
```
#### - 事件

|  事件名 | 描述  |
| ------------ | ------------ |
|  activate.bs.scrollspy | 每当一个新条目被激活后都将由滚动监听插件触发此事件。 |

```javascript
//事件绑定在导航上

$('#nav').on('activate.bs.scrollspy', function () {

alert('新条目被激活后触发此事件！');

});
```
#### - 方法

| 方法名  |  描述 |
| ------------ | ------------ |
| refresh  |  更新容器 DOM 的方法 |
```javascript
//HTML 部分	
<section class="sec">	
<h4 id="html5">HTML5	

<a href="#" onclick="removeSec(this)">删除此项</a></h4> <p>...</p>

</section>

//删除内容时，刷新一下 DOM，避免导航监听错位

function removeSec(e) {

$(e).parents('.sec').remove();

$('#content').scrollspy('refresh');

}
```


