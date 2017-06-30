---
title: 经典JS闭包分析
date: 2017-02-18 13:35:37
tags: 
- js
- 面试题
---

最近 ，在交流群里 有人提出了 一个问题：

```
for (var i = 0; i < 10; i++) {
	setTimeout(function () {
		console.log(i)
	},1000)
}

```

记住你的答案，开始查看博客。

<!--more-->

首先，我们先注意最外层的 for循环，如果忽略 里面的的setTimeot，相信 很多人知道 答案是 **1,2,3,4,5,6,7,8,9**

```
for(var i=0;i<10;i++){
	console.log(i);
}

```

#### 那么问题来了，加上 这个 setTimeout 难道答案就不是 1到9 了么？

放到 chrome 开发者工具跑一下

```
for (var i = 0; i < 10; i++) {
	setTimeout(function () {
		console.log(i)
	},1000)
}

```

#### Excuse Me，这 结果 居然是 10个10

好吧，然我们来分析一下 这个函数运行的整个过程：通过 chrome 断点调试，一步一步执行函数就会发现一个有趣的现象；

其实整个函数先执行的是for循环，当i = 10，的时候跳出循环，这个时候才开始执行 setTimeout 的 打印输出

黄轶解释说：

> 其实这是一个JS Event Loop的问题，setTimeout里的回调都会再每一次EventLoop中去check，达到时间了就会执行。
> 你这个case中， for循环会在当前Event Loop中执行完毕，i会加到10跳出循环体，setTimeout中所有回调函数都会在之后的Event Loop中执行，所以输出全部都是10

大神解释完其实还是 不懂 为啥就这样的，可以参考 阮一峰老师的 关于浏览器事件的分析：
[JavaScript 运行机制详解：再谈Event Loop](http://www.ruanyifeng.com/blog/2014/10/event-loop.html) 和 [什么事event loop](http://www.ruanyifeng.com/blog/2013/10/event_loop.html)

小伙伴们，看了 这篇 实列分析加上 阮老师的指导对了此类问题明白了么？

**Yours Sincerely AppleSun**