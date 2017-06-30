---
title: 怎么保存hexo源代码到github
date: 2017-05-11 00:35:27
tags: 
- hexo
- git
---

### 写博客最怕之前写的东西弄丢了，重新写浪费时间，找回的话也是绞尽脑汁。出于稳妥考虑，建议备份博客，习惯性的备份对于一个程序员来说很有意义唷！

<!--more-->

年前的时候 我因为更换电脑没有做好 hexo博客的备份导致我一度放弃 继续写博客的念头，好在 自己 慢慢恢复回来了。

此处省略一万句  无Fuck可说!!!

今天教大家一种 把**hexo源代码备份到github**的方式，轻松应对 烦人的 丢失问题！



> 废话不多说。

#### 首先 在您已有的 github 博客的仓库新建 一个branch(分支),

![](http://7xjdah.com1.z0.glb.clouddn.com/pic2017051101.png)



#### 接下来克隆 到本地 (后面是你的仓库地址)

```markdown
git clone https://github.com/CracKerMe/CracKerMe.github.io.git
```

#### 克隆好后，cmd 进入此目录，输入,查看所有分支

```markdown
git branch -a
```

![](http://7xjdah.com1.z0.glb.clouddn.com/pic2017051102.png)

#### 切换到指定分支(我这里切换到 source)

```markdown
git checkout source
```

此时，把你的hexo 原文件复制到此处

![](http://7xjdah.com1.z0.glb.clouddn.com/pic2017051103.png)

回到CMD里面继续 依次操作

```markdown
git status
```

```markdown
git add .
```

```markdown
git commit -m "上传日志"
```

```markdown
git remote add origin git@github.com:CracKerMe/CracKerMe.github.io.git
```

* 注意 origin 后面的地址是你的仓库的 https的地址哟

```markdown
git push -u origin source
```

* 这里的origin后面的 跟着的是你的branch(分支)


------

OK，不知道您 是否清楚了呢，也欢迎你 随时向我提问

QQ:1160948478

__Yours sincerely AppleSun__