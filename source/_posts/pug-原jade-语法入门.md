---
title: pug(原jade)语法入门
date: 2016-06-10 19:23:00
tags: 
- jade
- 入门
---

### PUG(原jade，后统称jade) 是一款高性能的模板引擎

通过javascript实现，基于node编译的html更具效率,让我们好好学习这一语言吧

![img](https://sfault-image.b0.upaiyun.com/01/50/0150d755a8cb45e45251aea67d4d0cd2_articlex)

<!--more-->

## 特性

- 客户端支持
- 代码高可读
- 灵活的缩进
- 块展开
- Mixins
- 静态包含
- 属性改写
- 安全，默认代码是转义的
- 运行时和编译时上下文错误报告
- 命令行下编译jade模板
- HTML5 模式 (使用 !!! 5 文档类型)
- 在内存中缓存(可选)
- 合并动态和静态标签类
- 可以通过 filters 修改树
- 模板继承
- 原生支持 Express JS
- 通过 each 枚举对象、数组甚至是不能枚举的对象
- 块注释
- 没有前缀的标签
- AST Filters
- 过滤器

## 安装

(基础：配置好nodejs环境,并通过 `npm init` 初始化 `package.json` )，简单的一行命令即可安装使用

```
npm install gulp-jade --save

```

------

## 编写语法

- html 直接编写
  注意点 我都已经放到下面的demo 去了

```
doctype
html
	head	     /*通过tab缩进表示层级*/
		title
		meta(charset="utf-8")       
		link(rel="stylesheet";href="css/style.css" /*多属性用 , 分隔开*/
	body
		h2#heihei.go Hello
			span.sp1.sp2 user     			/*可以同时添加很多class 以及 id*/
			| World							/* | + 空格后面接内容会原样输出 */
			em 我是em标签      /*同级标签写在同一缩进列上面*/

```

### 通过上述jade 文件最终得到的 html结构为：

```
<!DOCTYPE html>
<html lang="en">
<head>
	<title></title>
	<meta charset="utf-8">
	<link rel="stylesheet" href="css/style.css">
</head>
<body>
	<h2 id="heihei" class="go">
		Hello 
		<span class="sp1 sp2">
			user
		</span>
		World
	</h2>
</body>
</html>

```

- html 引入多用结构

```
doctype
html
	head	     /*通过tab缩进表示层级*/
		title
		meta(charset="utf-8")       
		link(rel="stylesheet",href="css/style.css" /*多属性用 , 分隔开*/
	body
		include head.jade  /*引入路径的.jade文件*/
		<div>我是内容</div>
		include foot.jade

```

#### 通过编译 依然没有问题

------

------

## 怎么编译？

first of all:安装gulp以及gulp-jade

```
npm install gulp gulp-jade --save

```

配置好 `package.json` 后，编辑 `gulpfile.js` 文件（有看不懂的推荐去看我的上一篇博文）

```
var gulp = require('gulp');
var jade = require('gulp-jade');
gulp.task('jade',function(){ 
gulp.src('..dir/*.jade')	 /* ..dir/为目标路径*/
.pipe(jade())
.pipe(gulp.dest('..dir/html/'))		
})

```

然后在终端 输入

```
gulp jade

```

#### OK ，就这样就可以跑起来了

To be continue!

*Yours Sincerely SunPing*