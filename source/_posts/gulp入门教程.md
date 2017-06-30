---
title: gulp入门教程
date: 2016-06-08 13:19:51
tags: 
- gulp 
- 入门
---

## 自动化构建工具的使用

#### 简而言之，通过配置好task任务，使用强大的插件，管道般的顺畅操作，即可自动构建代码，极大地提高效率，让我们来揭开gulp的神秘面纱

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016080810.png)

<!--more-->

### 明确目标

##### 我们能通过gulp做什么？

- 压缩html，css，js 等文件（分别使用 gulp-htmlmin，gulp-cssmin，gulp-jsmin）;
- 自动合并同类型文件为一个文件（gulp-concat）;
- 更高效的编辑语言（less来编写css，jade来编写html）
- 更亲近读者的代码阅读（通过查看package.json的内容 一键配置环境）
- 更强大的处理速度（编译速度很快）
- 。
- 。
- 。

### 了解了这些，让我们来学习这个强大的工具吧

#### 如何安装？

基于nodejs的 gulp 需要您首先 配置好nodejs环境，[nodeJS 传送门](http://nodejs.cn/download/)

在项目文件夹内，首先初始化npm

```
npm init

```

接下来全局安装 gulp：（如发生权限不够的情况，在前面添加“sudu”）

```
npm install gulp -g --save

```

在package.json所在文件夹内 新建一个”gulpfile.js”此文件是gulp用来编写任务的。

编辑 `"gulpfile.js"`，开始第一段gulp的代码

```
var gulp = require('gulp');
gulp.task('mission1',function(){
console.log("hello gulp")		
})
gulp.task('default',function(){
console.log("hello user")		
})

```

##### 这时候在终端调用 `gulp mission1` 会直接输出 `hello gulp`

**注意点1：** 这里的 mission1 默认值为 `default` ，也就是说如果你直接运行 `gult` 会输出 `hello user`

**注意点2：** 如下面例子，中间为可选，正式调用的时候，执行顺序为：mission2–mission3–mission1

```
gulp.task('mission1',['mission2','mission3'],function(){
	fn();/*你的功能函数写在这里*/
})

```

------

## Q:如何利用gulp 压缩代码？

### A:以js 为例：首先需要安装 `gulp-jsmin` 的插件：

```
npm install gulp-jsmin --save

```

如何 使用呢？ 举例说明 ：

local.js的路径为 `save/src/js/local.js` ,

我现在需要完成的任务为：讲压缩好的js代码放到 `save/desk/js/`中；

按照理解，先找到src 下面的js文件，然后进行压缩，然后选择存放路径；
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051601.png)
既然缕清思路，具体怎么实现呢？在gulpfile.js文件中

```
var gulp = require('gulp');

var jsmin = require('gulp-jsmin');

gulp.task('jsmin',function(){

gulp.src('src/js/local.js')
	
.pipe(jsmin())
		
.pipe(gulp.dest('desk/js/'))
		
})

```

接下来 在终端中调用 `gulp jsmin` 就会在该路径下生成 js 的压缩文件

## cssmin，htmlmin 同上

------

## Q:如何利用gulp编译less并压缩修改名称？

### A:提高了要求，必要需要更多元素（gulp-less,gulp-rename）的加入

目标：test.less的路径为 `save/src/css/test.less` ,

我现在需要完成的任务为：讲less转译成css并压缩，重新命名的代码放到 `save/desk/css/`中；
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051602.png)

```
var gulp = require('gulp');

var less = require('gulp-less');

var rename = require('gulp-rename');

var cssmin = require('gulp-cssmin');

gulp.task('cssgo',function(){

gulp.src('src/css/*.less')
	
.pipe(less())
	
.pipe(cssmin())
	
.pipe(rename({suffix: '.min'}))
	
.pipe(gulp.dest('desk/css/'))
	
})

```

最终运行结果为： `test.min.css`

### 怎么样，你运行成功了么？

更多的 知识点 靠你自己去挖掘；希望你看了这篇文档能有所收获！

## 开启传送门：[gulp中文网](http://www.gulpjs.com.cn/)[gulp插件网](http://gulpjs.com/plugins/)

### 感谢您一如既往地支持

**Yours sincerely SunPing**