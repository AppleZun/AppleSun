---
title: react native之环境搭建1
date: 2016-12-03 13:23:27
tags: js
---

React Native 是facebook 旗下的一款开源项目，由于媲美原生的APP的性能(比当前native主流框架好很多),组件化编程，可以采用js(参考ES6语法)编写IOS与Android的APP，备受市场关注。支持热更新(可以绕过app store的审核机制),以及他的宣传“Learn once,write everywhere”看着都让人兴奋。

<!--more-->

本来在前端的路上的我 根本不会遇见他。因为一次面试，雇主说叫我用react native(后面统称“RN”)写一个DEMO。要实现的功能可不少：登录注册、爬数据库、列表展示、图文展示、底栏导航器、数据处理、页面交互。只给了我一周。鄙人先前不造这些知识啊。各种博客、文档书籍…翻翻翻，无果，遂走向自我提升学习的道路。—-好了废话不多说没开始最基础的学习(前面都是题外话，可以不用看的。)

## MAC 如何配置IOS环境（win请往下戳）

- 一台Mac电脑，建议入一个；
- Mac需安装好 Xcode，且版本不得低于 6.3；
- 安装 **Homebrew** mac的包管理器，用于安装NodeJS和其他工具；

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

```

- 安装Node，需要NodeJS 4.0或更高版本。本文Homebrew默认安装的是6.x版本，完全满足要求。

```
brew install node

```

- React Native的命令行工具（react-native-cli）

```
npm install -g react-native-cli

```

- 建议安装watchman，用来监视文件并且记录文件的改动情况

```
brew install watchman

```

tips:如果在命令安装过程中出现“access”或者“permission denied”等关键字眼的报错，大多为权限问题，可是通过在命令前面在 sudo 的形式 或者 用以下代码修复

```
sudo chown -R `whoami` /usr/local

```

#### 强烈安利：使用 [Webstorm EAP](https://confluence.jetbrains.com/display/WI/WebStorm+EAP) 版本进行编辑，理由：正版、对ES6语法支持高，react提示好。

### MAC 下环境配置完毕

## Windows 如何配置Android环境(以win7举例)

（题外话：确认自己的电脑版本是X86的就安装32位的，X64就安装64位系统，不懂的可以咨询您的电脑购买方，总之要确保以下安装的文件的一致性）
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016062313.png)

tips:打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量 -> 选中PATH -> 双击进行编辑

- 下载安装JDK [下载地址](http://www.androiddevtools.cn/)

  - JAVA_HOME的设置：
    - JAVA_HOME=C:\Program Files\Java\jdk1.8.0_45（JDK安装所在目录）
    - 在 path 中加入 %JAVA_HOME%in

  tips: 命令提示行中 输入 java -version 出现您的版本号 证明 JDK配置正确


- 安装SDK 不用翻墙的[下载地址同上](http://www.androiddevtools.cn/)在此处直接解压 您的ADT Bundle到C://Program Files文件夹下

  - ANDROID_HOME的设置：
    - ANDROID_HOME=C:\Program Files\android-sdk（android sdk所在目录）
    - 在 path 中加入 %ANDROID_HOME% ools与%ANDROID_HOME%platform-tools(用 ; 分割开)
  - CLASSPATH的设置：
    - CLASSPATH=.;%JAVA_HOME%\lib\tools.jar

  tips: 命令提示行中 输入 android 没有出现“android不是可用的程序”，即证明成功

  - 安装NodeJS，建议去[官网下载](https://nodejs.org/en/)
  - [安装GIT](https://git-for-windows.github.io/)
  - 安装React Native命令行工具

```
npm install -g react-native-cli

```

tips:npm仓库源替换为国内镜像以加速后面的过程，
设置全局使用指定的镜像命令：

```
npm config set registry https://registry.npm.taobao.org --global 	
npm config set disturl https://npm.taobao.org/dist --global

```

注意：SDK需要保证以下内容均已安装—在 Android 6.0 (Marshmallow) 中勾选 Google APIs 、 Intel x86 Atom System Image 、Intel x86 Atom_64 System Image 以及 Google APIs Intel x86 Atom_64 System Image 。以及在 Android SDK Build Tools 中勾选 Android SDK Build-Tools 23.0.1

### 至此 所有的 环境变量配置结束：

------

# 创建React Native 项目

### 初始化 AwesomeProject为项目名称，自己随便取

```
react-native init AwesomeProject

```

耗时特别久，网速好的话 1~3分钟，下载一个预计400M的包，如果你等不了，建议去github上直接down一个包进行react native 的学习，[地址在这里](https://github.com/facebook/react-native)

初始化好之后，cd 进入项目所在位置，执行以下命令 即可 开始跑 项目了。

### 修改项目

现在你已经成功运行了项目，我们可以开始尝试动手改一改了：

- 使用你喜欢的编辑器打开index.ios.js并随便改上几行。
- 在iOS Emulator中按下⌘-R就可以刷新APP并看到你的最新修改！

## 恭喜你完成了最基础的学习，请关注我，会带来更多 RN的学习内容

PS：当前RN版本0.27，如果您需要在Mac系统下配置Android环境，或者 win虚拟机下配置IOS，可以借助百度或者联系本人：[QQ：1160948478](http://wpa.qq.com/msgrd?v=3&uin=1160948478&site=qq&menu=yes)

**Yours Sincerely SunPing**