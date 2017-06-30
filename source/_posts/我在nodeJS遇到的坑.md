---
title: 我在nodeJS遇到的坑
date: 2016-12-12 09:14:22
tags: js
---

### 天知道前端的学习 咋这么多坑，当你 发出“天哪，这么简单就解决了？”的时候，我想我们是否该整理一下 曾经因为二 犯下的错。(很多BUG是可以避免的)

<!--more-->

### 误区1: node = git

 很多人在刚接触 `nodeJs` 的学习的时候，会分不清这两个的关系。尤其是在安装配置git 的时候最容易蒙圈。

##### 错误案例1:

当你兴高采烈 尝试`github`绑定设备的 **SSH and GPG keys** 时，你会发现 第一步操作 “输入`ssh-keygen`并回车” 就出问题了，系统提示 ssh-keygen 不是内部或外部命令，like this

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016121301.png)

当你去百度求解的时候，看到的解答无疑是这样子的

> Git生成密钥，出现ssh-keygen不是内部或外部命令，解决方法如下：
>
> 原因是ssh-keygen没有加入Path环境变量，系统就执行不了这个命令，解决步骤：
>
> 1. 点击“计算机”，搜索ssh-keygen，复制所在路径；
> 2. 右击“计算机”，属性–>高级系统设置–>环境变量–>系统变量,找到Path变量，进行编辑，End到最后，输入分号，粘贴复制的ssh-keygen所在的路径，保存；
>
> 重新cmd，执行ssh-keygen,成功！

但是你试了之后依旧无效，原因很简单。你这是在 node 环境下，并非 git环境，正确的应该是在 git bash 命令行里面输入才对，like this

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016121302.png)

至于 git bash 在哪里，你需要安装nodeJs安装包，以及 git安装包，然后 在 **C:\Program Files\Git**这个目录下可以找到。git 翻墙下载速度过慢的话，就[点这个链接去下载吧](http://pan.baidu.com/s/1o898qU2)

未完待续

**Yours Sincerely SunPing**