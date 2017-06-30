---
title: JS面向对象的5种写法
date: 2016-07-23 00:27:40
tags: js
---

### 简单介绍js 面向对象的5种写法，让你们更快对于对面对象的结构了解清楚。

<!--more-->

(转载自Web前端技术论坛)
定义一个对象圆cicle，拥有变量半径 r，常量π Pi ，求解圆的面积 area()

第一种写法
DEMO1.

```
function cicle(r){
	this.r = r;
}
cicle.Pi = 3.14159;
cicle.prototype.area = function(){
	return cicle.Pi*this.r*this.r;
}
//调用执行
var c = new cicle(2.0);//传参调用
alert(c.area());

```

第二种写法
DEMO2.

```
var cicle = function(){
	var obj = {}
	obj.Pi = 3.14159;
	obj.area=function(){
		return this.Pi*r*r;
	}
	return obj;
}
//调用执行
var c = new cicle();
alert(c.area(2.0));

```

第三种写法
DEMO3.

```
var cicle = new Object();
cicle.Pi = 3.14159;
cicle.area = function(){
	return this.Pi*r*r;
}
//调用执行
alert(c.area(2.0));

```

第四种写法
DEMO4.

```
var cicle = {
"Pi" : 3.14159,
"area":function(r){
	return this.Pi*r*r
}
}
//调用执行
alert(cicle.area(2.0));

```

第五种写法
DEMO5.

```
var cicle = new Function("this.Pi=3.14159;this.aera = function(r){return this.Pi*r*r;}");
//调用执行
alert((new cicle()).area(2.0));

```

*Yours Sincerely SunPing*