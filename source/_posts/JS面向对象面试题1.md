---
title: JS面向对象面试题1
date: 2016-07-01 00:17:01
tags:
- js
- 面试题
---

学习JS过程中，迷茫的我们会考虑研究一些面试题来测试自己对于这块知识是否真的搞懂了，在浏览过程中，看见歇一歇比较有代表性的js 问题，由于很容易让人轻视，所以能 全部答对的少之又少。让我们来瞧瞧这些题目吧！
题目：

<!--more-->

```
/*题干开始*/
function Foo(){
	getName=function(){
	alert(1);};
	return this;};
Foo.getName=function(){alert(2);};
Foo.prototype.getName=function(){alert(3);};
var getName=function(){alert(4);};
function getName(){alert(5);};
/*题干结束*/
/*提问开始*/
请输出以下输出结果：
Foo.getName();
getName();
Foo().getName();
getName();
new Foo.getName();
new Foo().getName();
new new Foo().getName();
/*提问结束*/

```

## 解题思路

看到上面的题目，我会把题干的排序变成这样：

```
function Foo(){
	getName=function(){
	alert(1);};
	return this;};
function getName(){alert(5);};//提升函数声明，覆盖var的声明
var getName；//只提升变量声明
Foo.getName=function(){alert(2);};
Foo.prototype.getName=function(){alert(3);};
getName=function(){alert(4);};

```

### 首先为什么要这样子排序：

这里涉及到浏览器对于js 的解析，**浏览器解析到函数**时，会把**一般函数提到前面进行解析**不管函数是否会执行，排列顺序而言已经在前面了；可能你会注意到我把`var getName=function(){alert(4);};`改成了`var getName；getName=function(){alert(4);};`这种写法涉及到我们学过的知识点：**变量声明提升以及函数表达式**；

##### 什么叫做函数表达式

var getName 与 function getName 都是声明语句，区别在于 var getName 是函数表达式，而 function getName 是函数声明。关于JS中的各种函数创建方式可以看 [大部分人都会做错的经典JS闭包面试题](http://www.codeceo.com/article/javascript-closure-interview.html) 这篇文章有详细说明。

**函数表达式最大的问题，在于js会将此代码拆分为两行代码分别执行**。所以就变成了我上述的排序

### 所以看到题目先排序是个很好的习惯。

##### 解读第一题：

问Foo.getName(),在题干中与之相匹配的是弹出“2”，并且下面没有函数会覆盖，所以第一题答案为2，很明显的一道送分题， **拿下！！！**

```
getName()/*结果为2*/

```

##### 解读第二题：

问getName()，在题干中与之相匹配的是弹出“5”和弹出“4”，因为最下面的4是重新赋值的忙所以5被覆盖，所以此题答案为4（解题逻辑参考排序） **拿下！！！**

```
Foo.getName()/*结果为4*/

```

##### 解读第三题：

问Foo().getName()，好的，先执行Foo函数,执行后，首先，会把`getName=function(){alert(1);};`这一函数暴露在整个题干底部了，由于Foo()返回值为this,所以此处的**this 指向window**（待会儿分析），此时整个函数变成了：

```
function Foo(){
	getName=function(){
	alert(1);};
	return this;};
function getName(){alert(5);};//提升函数声明，覆盖var的声明
var getName；//只提升变量声明
Foo.getName=function(){alert(2);};
Foo.prototype.getName=function(){alert(3);};
getName=function(){alert(4);};
getName=function(){alert(1);};
求解
window.getName()的输出结果是什么

```

在此匹配到了 弹出“5”，弹出“4”和弹出“1”，由于下面覆盖上面的原因，所以此题答案为1 **拿下！！！**

```
Foo().getName()/*结果为4*/

```

### this 的指向问题

- 当全局作用域下直接调用this，指向window

```
alert(this)

```

- 普通函数下调用this，指向window

```
var aa=function(){
	return this
}

```

- 作用对象属性调用this，指向对象本身

```
function aa(){
	this.name="apple"
}
var bbb = new aa();
alert(bbb.name)

```

##### 解读第四题：

问getName()，由于上面的Foo()的函数暴露在正割函数底部，所以，在此执行getName()，得到的结果依然是“1”，上面一题对了，这一题是真的送分。**拿下！！！**

```
Foo().getName()/*结果为4*/

```

## 在解答下面问题前，有必要先了解 JS运算优先级排序

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051620.png)
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051621.png)
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051622.png)
[参考资料](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

##### 解读第五题：

问new Foo.getName(),首先我们得明白一点，就是 先拆分 问题 到底想叫我们做什么！！！

经过对于 JS面对对象的学习，知道js运算优先级，不难看出，这里可以看成是 new function(){}，所以先考虑后面的函数部分Foo.getName()的执行结果通过匹配题干可知为“2”，此时等同于

```
new function(){
alert(2)}

```

毫无疑问，这题结果等于2，看吧，掌握了JS面向对象的基本知识点，解决这类面试题简直简单的不要不要的。**拿下！！！**

```
new Foo.getName()/*结果为2*/

```

##### 解读第六题：

问new Foo().getName()，根据 优先级，实际执行情况为：先`new Foo()`在与后面的`getName()`综合考虑，这里有需要借助`构造函数返回值问题`。原题中，返回的是this，而this在构造函数中本来就代表当前实例化对象，遂最终Foo函数返回实例化对象。

之后调用实例化对象的getName函数，因为在Foo构造函数中没有为实例化对象添加任何属性，遂到当前对象的原型对象（prototype）中寻找getName，找到了。此题答案为“2”**有难点，但是没有超纲，继续**

```
new Foo().getName()/*结果为3*/

```

#### 构造函数返回值

在传统语言中，构造函数不应该有返回值，实际执行的返回值就是此构造函数的实例化对象。

而在js中构造函数可以有返回值也可以没有。

- 没有返回值则按照其他语言一样返回实例化对象。
  ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051623.png)
- 若有返回值则检查其返回值是否为引用类型。如果是非引用类型，如基本类型（string,number,boolean,null,undefined）则与无返回值相同，实际返回其实例化对象。
  ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051624.png)
- 若返回值是引用类型，则实际返回值为这个引用类型。

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051625.png)

##### 解读第七题：

问new new Foo().getName()，考虑优先级，先`new Foo()`在与后面的`getName()`，最后给这个整体`new`,上一题如果做对了，这一题也就摆明了送分 ,`new function(){alert("3")}`,结果依然为“3”。

```
new new Foo().getName()/*结果为3*/

```

## 总结

就知识点而言，要掌握 运算符，排序，构造函数返回值，this的指向等知识，灵活运用，即可很快捷很准确地完成该试题。不知道看完之后，你是否也有所想法，在下方留言区告诉我吧。