---
title: JS的变量提升
date: 2017-01-04 13:26:49
tags: 
- js
- 面试题
---

很多面试题喜欢在函数执行这一块下功夫，作为 开发者如果不能很好滴 掌握js的执行原理，在面试过程中肯定会被秀的体无完肤，基于此我去找了变量提升相关内容，一起学习。

<!--more-->

## JavaScript代码的运行规则

在JavaScript代码运行之前其实是有一个*编译阶段*的。编译之后才是**从上到下，一行一行解释执行**。这样一来也给初学者造成很大的误解。初学者会觉得JavaScript的代码是从上到下，一行一行的解释执行的。按这样的思路，在有些情况下就会造成惨案：

```
name = "AppleSun";
var name;
console.log(name);

```

按照代码从上到下一行一行解释执行的说法，有些同学可能会觉得`console.log(name)`输出的值是`undefined`。那是因为`name = "AppleSun"`在`var name`之前，变量`name`被重新定义了，而且没有给其赋值，所以认为此时`name`的值是`undefined`。输出的也应该是undefined。但事实上输出的值是`"AppleSun"`。下图是Chrome浏览器调试器下的输出结果：
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016071901.png)

**在看一段代码**:

```
console.log(name);
var name = "AppleSun";

```

当初我就以为它输出的结果是`Uncaught ReferenceError: name is not defined(…)`。因为变量`name`在没有声明的情况下就被使用了。而事实上呢，并如如此，它输出的结果是`undefined`。如下图所示：
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016071902.png)

为什么会这样呢？因为JavaScript代码运行时，它把变量和函数的声明提升至作用域的顶端。而这个阶段就发生了变量提升。同时JavaScript在编译阶段的工作之一就是将变量与其作用域进行关联。那么要彻底的理解JavaScript声明提升，需要对JavaScript的变量作用域有一定的了解。

## JavaScript变量作用域

对于JavaScript的初学者来说，变量作用域是最令人感到困惑的一部分。有关于JavaScript中变量的作用域，本文不做介绍，因为要说清楚它，需要大幅篇幅，而且对于我这样的新手也道不清说不明。拿张图向大家简单的展示一下：
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016071903.png)

#### 在JavaScript中，变量有4种基本方式进入作用域：

- 语言自身定义(Language-defined)：所有的作用域默认都会包含`this`和`arguments`
- 函数形参(Formal parameters)：函数有名字的形参会进入到函数体的作用域中
- 函数声明(Function decalrations)：通过`function foo() {...}`方式实现函数声明
- 变量声明(Variable declarations)：通过`var foo`;形式声明变量，当然在ES6中还增加了`let`和`const`声明变量

#### 有关于JavaScript作用域更多的介绍可以阅读下面这些文章：

- [JavaScript学习笔记： 局部变量和全局变量](http://www.w3cplus.com/javascript/the-basics-of-variable-scope-in-javascript.html)
- [理解 Javascript 中变量的作用域](https://segmentfault.com/a/1190000002960647)
- [ES6中的变量和作用域](http://www.w3cplus.com/javascript/variables-and-scoping-in-es6.html)
- [深入理解JavaScript的变量作用域](http://www.cnblogs.com/rainman/archive/2009/04/28/1445687.html)

可能你跟我一样，对变量作用域并没有理解透彻，但我们不能因为这个原因而不继续。

## JavaScript变量提升

在JavaScript中，变量的声明可以放在它的使用之后。换句话说，变量可以先使用后声明。这主要是因为JavaScript的提升(hoisting)机制在作怪。简单点说，提升(hoisting)是JavaScript中默认就具有的一种机制，它将当用作用域内的所有声明都提升到最顶部。如此一来，可以把变量提升归纳为：

**JavaScript引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行。这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升（hoisting）。**

为了理解上面的含义，我们来看一个简单的示例。下面的代码中定义了一个函数`foo()`:

```
function foo () {
    var name = "AWebMan";
    var address = "http://www.awebman.cn";
    var age = 1;
}

```

其实他会变成这样：

```
function foo () {
    var name,address,age;
    name = "AWebMan";
    address = "http://www.awebman.cn";
    age = 1;
}

```

#### JavaScript的提升将会影响一个变量的生命周期，JavaScript中的一个变量，其生命周期主要包含三个阶段：

- 声明变量：创建一个新变量，如`var name`;
- 变量初始化：给变量初始化一个值，如`name = "AppleSun"`;
- 变量使用： 使用变量的值，如`console.log(name)`;

知道这个概念之后，再回过头来看文章开头的示例代码：

```
name = "AppleSun";
var name;
console.log(name);

```

在编写代码时应该这样做处理：

```
var name;    //代码编译阶段
name = "AppleSun";  //代码运行阶段
console.log(name);  //代码运行阶段

```

所以这段代码最终输出的结果将会是`AppleSun`。

**第二个示例代码**

```
console.log(name);
var name = "AppleSun";

```

我们应该这样处理：

```
var name;    //代码编译阶段
console.log(name);  // 代码运行阶段
name = "AppleSun";  // 代码运行阶段

```

所以代码最终结果是`undefined`.

## 理解变量提升

变量提升就是把变量提升到函数的顶部。需要特别说明的是：变量提升只是提升变量的声明，并不会把赋值也提升上来。

其实前面的示例已经说明了这一切，咱们重新来看看这个`foo()`函数：

```
function foo () {
    var name = "AppleSun";
    var address = "http://www.awebman.cn";
    var age = 1;
}

```

实际上foo()函数是这样子：

```
var name,address,age;
name = "AppleSun";
address = "http://www.awebman.cn";
age = 1;

```

这时候酒吧变量提升了。

##### 上面的事例比较简单，咱们来一个稍微复杂的示例：

```
var foo = 1;
function bar () {
    if (!foo) {
        var foo = 10;
    }
    console.log(foo);
}
bar();
var foo = 1;

```

答案是`10`。你一定觉得非常奇怪，`foo`等于`1`,if条件`!foo`应该是`false`，也就是说if代码块的代码是不会被执行。返回的值应该是`undefined`呀，怎么就变成`10`了呢？实际上，正如前面所说，变量`foo`被提升到了`bar()`函数最顶部，那么程序就变成这样：

```
function bar () {
    console.log(foo); // => undefined
    if (!foo) {
        var foo = 10;
        console.log(foo); // => 10
    }
    console.log(foo); // => 10
}
bar();

```

`bar()`函数运行后，输出的值是`undefined` `10` `10`,如下图所示：
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016071904.png)

说明当在函数内使用var声明变量的时候，这个变量的声明被提升到了bar()函数的最顶部（最开始处），所以这个例子等同于：

```
var foo = 1;
function bar () {
    var foo; // 定义局部变量foo
    if (!foo) { // foo是undefined (false),那么!foo就是true，所以会执行if语句块
        foo = 10;
    }
    console.log(foo);
}
bar(); // => 输出的结果是10

```

这样一来就明白了，结果为啥会是10了吧。

接着往下看，如果把`bar()`函数内的`var foo = 10`;换成`foo = 10`，其结果又将是如何呢？

```
function bar(){
    if(!foo){
        foo=10;
    }
    console.log(foo);
}
bar();
var foo=1;

```

其上面的代码变成：

```
var foo=1;
function bar(){
    if(!foo){
        foo=10;
    }
    console.log(foo);
}
bar(); // => 1

```

因为`bar()`中的变量`foo`没有使用`var`声明，变量不再提升。所以`(!foo)`会到函数外寻找定义的合局变量`foo`，结果是`1`，那`!foo`返回的值是`false`，也就不会执行if语句块内的代码。最终得到的结果是`1`。如果这个时候没有定义全局变量`foo`，就会报错。

```
function bar(){
    if(!foo){
        foo=10;
    }
    console.log(foo);
}
bar(); // => Uncaught ReferenceError: foo is not defined(…)

```

如下图所示：
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016071905.png)
也就是说，只有在有var声明的变量才会被提升到函数最顶部。

## 函数声明提升

函数在声明时也会像变量一样被提升。不同的是，函数表达式不会被提升。

## 函数声明

函数声明提升

```
foo();
function foo() {
    console.log(n);
    var n = 2;
}

```

实际上上面的代码将会按下面的形式执行：

```
function foo () {
    var n;
    console.log(n);
    n = 2;
}
foo(); // => undefined

```

函数foo()的作用域内的变量n提升到了作用域顶部，全局作用域里的foo()函数声明民会被提前到所处的作用域顶部，即全局作用域的顶部。但是函数表达式的话只有变量被声明，但是赋值给变量的函数不会被提升。

## 函数表达式

函数表达式不会被提长：

```
foo();
var foo = function bar () {
    console.log(foo);
}

```

函数表达式的提升类似于变量的提升：

```
var foo;
foo(); // => Uncaught TypeError: foo is not a function(…)
foo = function bar () {
    console.log(foo);
}

```

这样会引发TypeError异常，因为当时的foo并没有赋值，对undefined进行函数调用会导致非法操作抛出异常。

## 函数优先

函数会首先被提升，然后跟着才是变量。也就是说同时存在函数声明与函数表达式时，函数声明会优先于函数表达式提升。

```
foo();
function foo() {
  console.log('1');
}
var foo = function () {
  console.log('2');
}

```

上面的代码将会被理解成下面的形式：

```
function foo() {
  console.log('1');
}
var foo;
foo(); // 1
foo = function () {
    console.log('2');
}

```

所以实际上的输出是 1，因为函数表达式的赋值操作会在原来的位置，而声明操作则是提升到作用域顶部，但是优先级低于函数声明。

重复声明同名变量在 JavaScript 非严格模式中将会被忽略，所以实际上函数表达式的位置并没有改变。

#### 通过上面的介绍之后，简单的总结一下：

- 使用var声明的变量（包括函数）其声明会被提升到方法体最顶部，而赋值不会被提升；
- 未使用var声明的变量，不会被提升；
- 使用函数表达式function bar(){}定义的函数会函数声明连带函数体提升到方法体最顶部；
- 注意JavaScript中的作用域问题，JavaScript中没有块作用域(在ES6中改变了这一格局，使用let和const声明的变量，作用于块用域)

事实上，变量提升在不同方面的影响也不同：

- 变量声明: 使用var, let或const关键字
- 函数声明: 使用function () {…}语法
- 类声明: 使用class关键字

## 总结

看到这里，是不是有点晕了，说真的，我自己都晕了。不过理解清楚下面这段话，你理解JavaScript中的变量提升会有很大的帮助：

**如果变量在函数体内声明，它的作用域是函数作用域。否则，它就是全局作用域。变量将会在执行进入作用域时被创建。块不会定义新的作用域，只有函数声明和程序才可以。变量在创建的时候会被初始化为undefined。如果变量声明语句带有赋值操作，则赋值操作只有在被执行的时候才会发生，而不是创建的时候。如果文章中有不对之处，或者你有更好的意见欢迎在下面的评论中与我们分享。**

------

本博文已得到作者授权，如需转载，请联系W3cplus 大漠本人
[如需转载出处](http://www.w3cplus.com/javascript/javascript-hoisting-in-details.html)