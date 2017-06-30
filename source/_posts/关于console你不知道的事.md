---
title: 关于console你不知道的事
date: 2016-06-24 00:08:14
tags: 
- js
- 浏览器
---

### 当我们开始接触前端这一行，对于谷歌浏览器的接触甚至多于与人的交流，对她的熟悉程度宛如自己的爱人。提及console，更是无人不知无人不晓。可是你知道么？console可以显示图片以及为文字加样式。

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051608.png)

<!--more-->

在正常模式下，一般只能向 console直至太输出简单的文字信息，但考虑到便于阅读，可以考虑使用console.warn()来输出警告信息，控制台中的效果如下：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051609.png)

在输出信息前面会有一个带感叹号的黄色三角警告符号。似乎比一般的console信息要友好得多了。虽然图标是黄色的，但输出的文字仍然是黑色。

另外经常用到的是输出错误信息。可以通过调用console.erro() 来实现。

输出的效果如下：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051610.png)

信息前面会出现一个带叉的红色圆形图标。

这个效果要比警告信息更友好了，字体颜色成红色了。

要更牛叉莫过于对文字应用样式。而现在这一特性已经在谷歌浏览器里实现了。

在Chrome的开发者工具里，console 可以加样式，可以显示缤纷的颜色，甚至图片。简直爽翻了。

具体来说，是可以对输出到console控制台的文字进行CSS控制。

格式如下：

```
concole.log("%c需要输出的信息","css代码")
例如：
console.log("%c我是一名前端","color:red;font-size:30px")

```

下面是console.log()的官方文档摘要

[点此传送门查看官方文档](https://developer.chrome.com/devtools/docs/console-api)

| Format Specifier | Description                              |
| ---------------- | ---------------------------------------- |
| %s               | Formats the value as a string. (将值转化为字符串类型) |
| %d or %i         | Formats the value as an integer. (将值转化为整数类型) |
| %f               | Formats the value as a floating point value. (将值转化为浮点型) |
| %o               | Formats the value as an expandable DOM element(as in the Elements panel).(将值转化为DOM标签) |
| %O               | Formats the value as an expandable JavaScript object. (将值转化为js对象) |
| `%c`             | Formats the output string according to CSS styles you provide.(将值按照你写的css样式进行输出) |

#### 留心最后一点，这就是能实现显示文字的关键所在

这里 我给大家留下 相关的代码块，还不快去复制到console里面去看看效果？

### 3D 文本：

```
console.log("%c3D Text"," text-shadow: 0 1px 0 #ccc,0 2px 0 #c9c9c9,0 3px 0 #bbb,0 4px 0 #b9b9b9,0 5px 0 #aaa,0 6px 1px rgba(0,0,0,.1),0 0 5px rgba(0,0,0,.1),0 1px 3px rgba(0,0,0,.3),0 3px 5px rgba(0,0,0,.2),0 5px 10px rgba(0,0,0,.25),0 10px 10px rgba(0,0,0,.2),0 20px 20px rgba(0,0,0,.15);font-size:5em")

```

### 多彩的 CSS

```
console.log("%cColorful CSS","background: rgba(252,234,187,1);background: -moz-linear-gradient(left, rgba(252,234,187,1) 0%, rgba(175,250,77,1) 12%, rgba(0,247,49,1) 28%, rgba(0,210,247,1) 39%,rgba(0,189,247,1) 51%, rgba(133,108,217,1) 64%, rgba(177,0,247,1) 78%, rgba(247,0,189,1) 87%, rgba(245,22,52,1) 100%);background: -webkit-gradient(left top, right top, color-stop(0%, rgba(252,234,187,1)), color-stop(12%, rgba(175,250,77,1)), color-stop(28%, rgba(0,247,49,1)), color-stop(39%, rgba(0,210,247,1)), color-stop(51%, rgba(0,189,247,1)), color-stop(64%, rgba(133,108,217,1)), color-stop(78%, rgba(177,0,247,1)), color-stop(87%, rgba(247,0,189,1)), color-stop(100%, rgba(245,22,52,1)));background: -webkit-linear-gradient(left, rgba(252,234,187,1) 0%, rgba(175,250,77,1) 12%, rgba(0,247,49,1) 28%, rgba(0,210,247,1) 39%, rgba(0,189,247,1) 51%, rgba(133,108,217,1) 64%, rgba(177,0,247,1) 78%, rgba(247,0,189,1) 87%, rgba(245,22,52,1) 100%);background: -o-linear-gradient(left, rgba(252,234,187,1) 0%, rgba(175,250,77,1) 12%, rgba(0,247,49,1) 28%, rgba(0,210,247,1) 39%, rgba(0,189,247,1) 51%, rgba(133,108,217,1) 64%, rgba(177,0,247,1) 78%, rgba(247,0,189,1) 87%, rgba(245,22,52,1) 100%);background: -ms-linear-gradient(left, rgba(252,234,187,1) 0%, rgba(175,250,77,1) 12%, rgba(0,247,49,1) 28%, rgba(0,210,247,1) 39%, rgba(0,189,247,1) 51%, rgba(133,108,217,1) 64%, rgba(177,0,247,1) 78%, rgba(247,0,189,1) 87%, rgba(245,22,52,1) 100%);background: linear-gradient(to right, rgba(252,234,187,1) 0%, rgba(175,250,77,1) 12%, rgba(0,247,49,1) 28%, rgba(0,210,247,1) 39%, rgba(0,189,247,1) 51%, rgba(133,108,217,1) 64%, rgba(177,0,247,1) 78%, rgba(247,0,189,1) 87%, rgba(245,22,52,1) 100%);filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#fceabb', endColorstr='#f51634', GradientType=1 );font-size:5em")

```

### 彩虹文字

```
console.log('%cRainbow Text ', 'background-image:-webkit-gradient( linear, left top, right top, color-stop(0, #f22), color-stop(0.15, #f2f), color-stop(0.3, #22f), color-stop(0.45, #2ff), color-stop(0.6, #2f2),color-stop(0.75, #2f2), color-stop(0.9, #ff2), color-stop(1, #f22) );color:transparent;-webkit-background-clip: text;font-size:5em;');

```

## 在Chrome控制台输出图片

除了上面介绍的那些炫目的文字效果外，你还可以在Chrome控制台中显示图片,自然地，显示gif这样的动态图片也是没问题的。

还是应用差不多的代码，只是将内容变成指定背景为图片。

下面是一个例子：

```
console.log("%c", "padding:100px 300px;line-height:150px;background:url('imgUrl') no-repeat;");

```

#### sorry！经本人测试，目前不只是我哪里出错，在console只有留下空白区域，并没有出现图片或者gif ，如果您成功了，请在下方的留言区交流建议

今天的还满意么？

-to be continue-

*Yours sincerely SunPing*