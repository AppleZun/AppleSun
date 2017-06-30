---
title: 本地HEXO博客搭建
date: 2016-05-08 12:49:02
tags: hexo
---
### 一个看起来高大上的课题，大家一定认为很困难，可是其实通过学习，你就会发现真的很简单，今天就来一起快速入门HEXO
你需要做以下的准备工作（以mac为列）

<!--more-->

* 安装好nodeJS的终端
  * 去nodeJS官网去下载， 网址： https://nodejs.org/en/
  * 如图所示，在mac系统下，您看到了 这样的图片

![node安装成功](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051101.png)

个人开发者建议使用 `LTS版本`（即稳定版）
下载安装好了之后，在终端下 键入 node
![hexo运行截图](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051102.png)

当出现此界面时 ，证明安装成功

​	*tips：* `Ctrl + C` 退出 nodeJS状态

### 成功路上前进的第一步 QAQ

1. 安装好git

一般当您安装好了Xcode后会自动安装，这里我就不再赘述，具体安装步骤 请参照这里http://www.baidu.com

同样的，当出现

​	![](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051103.png)

即表示成功

好滴，准备工作做好了，接下来就是 正真 激动人心的时刻了

#### 安装HEXO

在 终端 界面下，输入 `npm install hexo` 如果 您出现权限不对，操作失败，请 提升权限。
e.g

​	`sudo npm install hexo`



##### 是不是炒鸡简单？

必须的因为这本来就是不难的啊。
同样的，在终端输入 hexo 出现很多内容的，也就证明你的 HEXO 安装成功。
开始我们的第一篇博客吧
新建一个文件夹 命名为 “myblog”（命名随意），并且 通过终端 进入文件夹
​	`cd Destop/`
​	`cd myblog/`
具体 按照您的路径进入，如果觉得有难点，难以消化关于DOS命令行的知识，老规矩 https://nodejs.org/en/

#### 初始化博客空间

​	`hexo init`
接下来就是等待时间，知道 那个转着的光标结束转动。OK，打开那个文件夹 ，你是不是 发现它自动生成了很多文件。
SO Exciting！！！
接下来 在 终端里面 输入

​	`hexo new 'firstblog'`
对滴，这就是 制作第一篇博客，在 source - _posts  路径下，出现了 firstblog.md 
我的天哪 .MD 是什么鬼？
别怕，这就是 这博客的编写格式，当然 它也能正确解析 HTML 标签，所以 别怕他。

有兴趣的同学也可以去 百度了解了解语法。
tips:推荐一款比较好用的MD编辑器：http://25.io/mou/(Mac可用)

#### 完成并发布

好了，我们写完了第一篇博客，怎么预览呢？
OK，很简单！！！
在终端 blog 文件夹下 输入 
​	`hexo server`
启动 hexo 本地服务器服务，然后 在浏览器地址栏输入：**http://localhost:4000/**
就这样就可以预览您写的博客
妈妈再也不用担心我不会写博客了

##### 本地搭建博客就介绍到这里，下一节，为您介绍：如何 上线自己的博客！

再次感谢您的访问
__Yours sincerely SunPing__