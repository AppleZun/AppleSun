---
title: '''git的使用以及上线HEXO'''
date: 2016-05-14 13:09:37
tags: 
- hexo 
- git
---

##### 上一篇 给大家介绍了 如何在 本地搭建 HEXO 博客的文章，不过，很多人依然不能满足于让自己阅读，迫切想给更多的小伙伴分享，介于此，咱们说说 如何让自己的 博客上线

<!--more-->

# Hello ,我又回来了！(* ￣3)(ε￣ *)

## 浅谈 如何让网站上线

### 方法一：花钱！！！

##### 是的，通过 购买域名、租赁服务器、并做好域名解析跳转，达到可访问要求。这一套下来，花了不少钱。不过，很多人建网站，还是基于 自己爽，想让小伙伴们也能享受自己的 分享。所以，一般不大建议 使用 这个模式 进行前端学习使用。

### 方法二：免费！！！

##### 网络上一搜一大把的免费开源产品，在众多免费提供商中，github 更加符合我们的需求，并且有越来越多的人使用github 来做项目，所以在github上做博客亦作为知识的延伸。一举两得，何乐而不为之。

> Just Do It！！！

## 注册github

**网址** [https://github.com/login](https://github.com/login) 点击直接注册

注册好了之后打开页面 点击右上角的 + 号，选择 **News repository**

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051104.png)

### 请注意是以您的用户名开头的,例如我的为： “ CracKerMe.github.io ” 用户名后面的“.github.io”不得修改，此为您的二级域名。

回到首页，选择右下角的 **Your repositories** 下面 以您的用户名开头的链接打开。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051105.png)


#### 请务必注意这里的SSH 和 HTTPS 的切换，因为 会用到。

## 请先复制SSH下的 “ git@github.com: “ 开头的一串内容

OK👌 在用户界面上选择 **Settings** ，选择 **SSH and GPG keys **
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051106.png)

```
先别急着输入 key ，，等到后面解决

```

### 打开终端，输入 `ssh-keygen` ，3个回车，跳出一长串代码，这时候输入`vim ~/.ssh/id_rsa.pub` ，此时复制 ssh开头到local 的所有字符串，复制好了之后，填入 上面的 **key** 里面。 Add SSH key!

#### 不过，小伙伴们是不是 卡在刚才的界面，不得动弹？按下 Shift + : + q (注意是在英文输入法下(⊙o⊙)哦)

```
:q

```

> 很完美！

# 接下来配置 本地数据

### 此处的 yourname 为 您的 github 用户名，email@example.com 就是您在注册github时绑定的邮箱.注意是 2条命令

```
git config --global user.name “Your Name”

```

,

```
git config --global user.email "email@example.com"

```

,

```
e.g
git config --global user.name "CracKerMe"
git config --global user.email "1160948478@qq.com"

```

> 本地配置结束！！！

## 接下来就可以直接download 你的git仓库的内容了

```
git clone "git@github.com:XXXXXXXXXX"

```

注意哟，xxxxxxxx是那一长串字符

xxxxx是SSH下的 “ git@github.com: “ 开头的一串内容

当您的下载的文件有修改后想重新传回git 服务器端，
输入以下命令，检查 本地与服务器的差异

```
git status

```

#### 保留所有修改

```
git add .

```

#### 确认所有修改,’’里面可理解为更新日志（支持中文）

```
git commit -m 'i upload something new'

```

#### 将所有修改提交至缓存区，后面依然是SSH下的 “ git@github.com: “ 开头的一串内容

```
git remote add origin git@github.com:yourname/learngit.git

```

#### 确认推送至您的github服务器

```
git push -u origin master 

```

> 一次文件的下载、上传完成

# 想上传博客了么？别急 胜利在望

### 距离成功 只相差一个插件：hexo-deployer-git

```
npm install hexo-deployer-git --save

```

### 终端在您的 博客所在文件夹下，输入一下命令，即可完成github 的 推送

```
hexo g

```

then

```
hexo d

```

> —没了么？
>
> —是的。
>
> —真没了？
>
> —真没了！

#### 小结一下，可能会有小伙伴问，上传博客这么麻烦，那以后也要这么麻烦么？

## Of cause not！以后再更新博客的时候，只需要 重复最后两个命令即可。

```
hexo g

```

then

```
hexo d

```

### 相信您看完了这篇文章，跟着做一做还是会有收获的！

> 感谢您的浏览

**Yours sincerely SunPing**