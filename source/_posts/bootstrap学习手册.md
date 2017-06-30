---
title: bootstrap学习手册
date: 2016-06-18 00:04:32
tags: css
---

### Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。让前端开发更快速、简单,让开发者快速上手。—-Bootstrap如是说

<!--more-->

##### 强大的 api功能让一个后端人员 快速开发出视觉项目，成为目前比较受欢迎的 选择之一

基于jQuery的bootstrap，考虑到适配，所以，最基本的bootstrap模板如下：(为了方便，我选择了CDN引入的方式)

```
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap</title>
    <link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.5/css/bootstrap.min.css">
  </head>
  <body>
  		这里都是内容区。。。
    <script src="http://cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
   <script src="http://cdn.bootcss.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
  </body>
</html>

```

- `http-equiv` 这一行表示 ie 强制用最新的edge渲染，减少出bug的几率；
- `viewport` 这一行表示 禁止用户缩放防止排版出错；
- `bootstrap`的`V3.X`版本均不支持`ie6，ie7` ，所以如果您需要兼容 `ie6，7`请更换bootstrap的 `2.X` 版本

**注意 bootstrap的js文件必须放在jQuery的js 文件后面**

# **我在本文末尾给大家留下了关于bootstrap最详细的思维脑图，对此感兴趣的可以去看看**

[点击查看大图![img](http://7xjdah.com1.z0.glb.clouddn.com/bootstrap.min.png)](http://7xjdah.com1.z0.glb.clouddn.com/bootstrap.png)

## 简单的回顾 BS（以下BS简称为“bootstrap”）V3.3.6 做出了那些改动

- # 基础样式

- ## 排版

- ### 标题：

  - 可以用h1-h6赋予标题样式，标题内通过small标签或者带.small类的元素添加副标题。

- ### 内联文本

  - 使用mark标签标示标注文本，del删除，s无用，ins插入，u下划线，
  - small小号（继承父级），strong着重，em斜体。

- ### 文本对齐类

  - text-left，text-center，text-right，text-justify，text-nowrap

- ### 文本大小写类

  - text-lowercase，text-uppercase，text-capitalize

- ### 地址

  - 以日常使用的格式呈现，在行结尾加 br 保留需要的样式即可。

- ### 引用

  - 将 HTML 元素包裹在 blockquote 中即可表现为引用样式。
  - 对于直接引用，建议用 p 标签。

- ### 列表

  - list-unstyled类移除默认 list-style 样式和左侧外边距的一组元素（只针对直接子元素）。
  - list-inline类通过设置 display: inline-block; 并添加少量的内补（padding），将所有元素放置于同一行。 dl-horizontal类让 dl 内的短语及其描述排在一行。

- ### 代码

  - code 标签包裹内联样式的代码片段，
  - kbd标签标记用户通过键盘输入的内容，
  - pre 展示代码块 。可用pre-scrollable 类设置最高350px带垂直滚动条。
  - var标签标记变量，
  - samp标签标记程序输出的内容。

- ### 表格

  - .table 类指定基本样式，
  - .table-striped 条纹样式，
  - .table-bordered 类为边框样式，
  - .table-hover 类带鼠标悬停样式，
  - .table-condensed 类紧凑样式。

- ### 状态类(行或单元格设置颜色)：

  - active，success，info，warning，info。
  - 将任何 .table 元素包裹在 .table-responsive 元素内，即可创建响应式表格，其响应式表格: 会在小屏幕设备上（小于768px）水平滚动。当屏幕大于 768px 宽度时，水平滚动条消失。

- ### 表单

  基本实例，所有设置了 .form-control 类的 input、textarea和 select

  - 元素都将被默认设置宽度属性为 width: 100%;。 将 label 元素和前面提到的控件包裹在 .form-group 中可以获得最好的排列。
  - 不要讲表单组直接和输入框组混合使用。建议将输入框组嵌套到表单组中使用。
  - form-group，input-group，control-group，
  - 内联表单，form元素添加 .form-inline 类可使其内容左对齐并且表现为 inline-block 级别的控件。
    - (只适用于视口（viewport）至少在 768px 宽度时（视口宽度再小的话就会使表单折叠。)
    - 在内联表单中单选/多选框控件的宽度设置为 width: auto;
    - 如果你没有为每个输入控件设置 label 标签，屏幕阅读器将无法正确识别。对于这些内联表单，你可以通过为label 设置 .sr-only 类将其隐藏。
  - 水平排列的表单
    - 通过为表单添加 .form-horizontal 类改变 .form-group 的行为，使其表现为栅格系统中的行（row）多选和单选框.radio、.radio-inline、.checkbox、.checkbox-inline 。
    - 静态控件水平布局的表单中，如需将一行纯文本和 label 元素放置于同一行，为 p元素添加 .form-control-static类即可。

- ### 控件状态

  - .disabled类禁用控件，为fieldset设置disabled 时则禁用包含的所有控件。
  - a标签不受此类影响。readonly 属性可以禁止用户输入.has-warning、.has-error 或 .has-success 类到这些控件的父元素即可。
  - 任何包含在此元素之内的 .control-label、.form-control 和 .help-block 元素都将接受这些校验状态的样式。
  - 你还可以针对校验状态为输入框添加额外的图标（注意依赖于label标签）。只需设置相应的 .has-feedback 类并添加正确的图标即可。
  - 控件尺寸.通过 .input-lg .input-sm类似的类可以为控件设置高度，通过 .col-lg-* 类似的类可以为控件设置宽度通过添加 .form-group-lg 或 .form-group-sm 类，为 .form-horizontal 包裹的 label 元素和
  - 表单控件快速设置尺寸。用栅格系统中的列（column）包裹输入框或其任何父元素，都可很容易的为其设置宽度。

- ### 辅助文本

  help-block类，针对表单控件的“块（block）”级辅助文本。

- ### 按钮

  - 基本样式，btn、btn-default、btn-primary、btn-success、btn-info、btn-warning、btn-danger、active
    展现形式，btn-link、btn-block、close
  - 尺寸样式，.btn-lg、.btn-sm 、.btn-xs 。
  - 可通过 a、button或 input 元素应用按钮类，但建议用 button元素来获得

在各个浏览器上获得相匹配的绘制效果。

- ### 图片

 * 图片形状，img-rounded，img-circle，img-thumbnail，IE8 不支持 CSS3 中的圆角属性。

- ### 辅助

  - text-muted、text-primary、text-success、text-info、text-warning、text-danger
    bg-primary、bg-success、bg-info、bg-warning、bg-danger、
  - 三角符号，caret
  - 浮动
  - 居中

# [bootstrap思维脑图献上](http://naotu.baidu.com/file/d29d143baa5c6694a6fa48eeb2ebf047?token=e3ea665e3c4fba3b)

*Yours sincerely SunPing*