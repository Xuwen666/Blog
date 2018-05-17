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
##  模态框
