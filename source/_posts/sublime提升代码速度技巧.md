---
title: sublime提升代码速度技巧
date: 2016-08-22 10:31:08
tags: 奇技淫巧
---

##### 工欲善其事必先利其器！！！当你还在惊羡大牛们的打字速度，你是否在想，他们的手速为何如此之快？其实他们不过比你更懂得如何使用它们的代码工具。

Sublime Text3举例，这里有一个 ~~15~~ 16 个快捷键的精选列表(1个自定义快捷键)，以gif动画展示，每天使用，享受码字乐趣吧!

<!--more-->

## (译者注：原文所列快捷键均为OS X环境，为了方便Windows和Linux环境童鞋的学习，译者将备注Windows和Linux下对应的快捷键)

- 选择
  - 选择一个选中项的下一个匹配项
  - 选择一个选中项的所有匹配项
  - 选择与光标关联的开始和结束标签
  - 选择容器内内容（新）
  - 选择括号内的内容
- 移动行和文本
  - 上移或下移行
  - 复制行或选中项
  - 增加和减少缩进
- 剪切和删除，复制和粘贴
  - 剪切行或选中项
  - 粘贴并保持缩进
  - 用标签包裹行或选中项
  - 移除未闭合的容器元素
- 文本和数字操作
  - 计算数学表达式
  - 递增和递减
  - 大写和小写
- 注释和对齐变量
  - 注释选中项/行
  - AlignTab自定义快捷键

### 选择一个选中项的下一个匹配项: ⌘ + D

（译者注：ctrl+d）

把光标放在一个单词上，按下⌘+ D,将选择这个单词。一直按住⌘且按D多次，将选择当前选中项的下一个匹配项。通过按住⌘,再按D三次,将选择三个相同的文本。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051626.gif)

### 选择一个选中项的所有匹配项: CTRL + ⌘ + G

（译者注：alt+f3）

和上面一样,但它选择文件中的所有匹配项。小心使用这个,因为它能选择一个文件中的所有匹配项. .
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051627.gif)

### 选择与光标关联的开始和结束标签:⌘+⇧+ K

（译者注：ctrl+shift+’）

这是一个法宝。也许你希望所有属性保持不变,但只是想选择标签。这个快捷键为你这样做,会注意到你可以在一次操作多个标签。*需要Emmet插件
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051628.gif)

### 选择容器内内容:CTRL + D

（译者注：ctrl+shift+a）

如果你把光标放在文本间再按下上面的键将选择文本,就像⌘+ D。但是再次按下它，将选择父容器,再按,将选择父容器的父容器。*需要Emmet插件
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051629.gif)

### 选择括号内的内容: ⌘ + ⇧ + Space

（译者注：ctrl+shift+m）

这有助于选择括号之间的一切。同样适用于CSS。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051630.gif)

### 上移或下移行: CTRL + ⌘ + ↑ 或 ↓

（译者注：ctrl+shift+↑ 或 ↓）
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051631.gif)

### 复制行或选中项: ⌘ + ⇧ + D

（译者注：ctrl+shift+d）如果你已经选中了文本,它会复制你的选中项。否则,把光标放在行上,会复制整行。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051632.gif)

### 增加和减少缩进: ⌘ + [ 或 ]

（译者注：ctrl+[ 或 ]）

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051633.gif)

### 剪切行或选中项: ⌘ + X

（译者注：ctrl+x）

剪切一行到你的剪切板，你可以粘贴到其他地方.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051634.gif)

### 粘贴并保持缩进: ⇧ + ⌘ + V

（译者注：ctrl+shift+v）这是又一个我每次都用的快捷键。在gif中我显示了普通粘贴(⌘+ V)和缩进粘贴两种效果的对比。注意缩进如何排列。

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051635.gif)

### 用标签包裹行或选中项: CTRL + ⇧ + W

（译者注：alt+shift+w）

使用标签包裹一行; 开始输入你想使用的标签,你成功了.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051636.gif)

### 移除未闭合的容器元素: ⌘ + ‘

（译者注：ctrl+shift+;）这会移除与你的光标相关的父标签。对清除标记很有帮助。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051637.gif)

### 计算数学表达式: ⌘ + ⇧ + Y

（译者注：ctrl+shift+y）我从未想过我会经常使用这个，但是确实很好用
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051638.gif)

### 递增和递减: ⇧ + OPTION + ↑ or ↓, OPTION + ↑ or ↓

（译者注：alt+shift+↑ 或 ↓，ctrl+ ↑ 或 ↓）

按住 ⇧ 将以10的步长改变数字, 不按住以1为步长. 同时注意到你不需要选择数字, Sublime Text 足够聪明到更新本行最近的数字.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051639.gif)

### 大写和小写: ⌘ + K then U, ⌘ + K then L

（译者注：ctrl+k+u,ctrl+k+l）
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051640.gif)

### 注释选中项/行: ⌘ + /

（译者注：ctrl+/）

这个在所有语言下都可用, 对行和选中项都可用.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051641.gif)

## 额外令人高兴的事情!使用AlignTab自定义快捷键

上面的快捷键都是Sublime Text默认的快捷键,但是你也可以添加你自己的自定义快捷键。以下示例应用 AlignTab插件使用 三个自定义键绑定 来基于=> ,=,和:进行内容垂直对齐。因为我工作中主要使用JavaScript和PHP,这些绑定对于几乎我需要的每一个场景都有用,但是你可以用任何你想要的字符进行垂直对齐。

在你自己的编辑器实现下面gif的效果,只需安装 AlignTab, ,添加自定义绑定到您的自定义键绑定文件中,选择一些代码,并点击CTRL + ⇧ + . 或 ; 或 =.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051642.gif)

## 结论

一旦你看到多行代码发生了一个改变,通常有一个使用几个按键来实现改变的方法，而不是一个个地编辑它们。通过连续使用上面快捷键的组合去执行重复的或可预见的改变,你可以大大提高你编码的速度。

这里是一个简短的Gif,包括选择所有匹配项,复制链接的文本,利用多行光标粘贴复制的文本,并将该文本转换为小写。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051643.gif)