---
title: react native之环境搭建2
date: 2016-12-06 13:25:16
tags: js
---

## Window平台配置Android环境

（本人以win10操作系统介绍，当前RN0.30.0）
内附安装包合集和详细安装指南，带你避开那些坑。

<!--more-->

### 安装Chocolatey（包管理器）

- 以管理员身份打开 命令提示符窗口，运行以下代码

```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin

```

### 安装Python 2

- 打开命令提示符，通过Chocolatey安装Python

```
choco install python2

```

### 安装Node

- 自行去官网下载安装

由于“墙”的原因，我们不得不使用特别手段加速下载过程
执行下面两条命令

```
npm config set registry https://registry.npm.taobao.org --global
npm config set disturl https://npm.taobao.org/dist --global

```

### React Native命令行工具

- 用于执行创建、初始化、更新项目、运行打包服务（packager）等任务

```
npm install -g react-native-cli

```

### 安装git

[http://yunpan.cn/c6bvpDreetNkh](http://yunpan.cn/c6bvpDreetNkh) 访问密码 8168

------

以上说的都很简单，下面才是最困扰RN开发者环境配置的难题。

## 安装JDK和JRE（1.7版本以上）

[http://yunpan.cn/c6bMKRqdE2F2w](http://yunpan.cn/c6bMKRqdE2F2w) 访问密码 162a
**重点来了**

- 请记住您安装的路径
- 我的电脑右击–>属性–>高级系统设置–>环境变量–>点击系统变量的新建系统变量
  - 变量名JAVA_HOME 变量值 为你的jdk安装目录

#### 怎么样算成功？

在命令行输入 `java -version`可以看到您的版本号而不是报错，证明安装成功

## 安装Android Studio 2.0或者更高版本。

[http://yunpan.cn/c6b67gKDau7hq](http://yunpan.cn/c6b67gKDau7h) 访问密码 f188

## 安装过程中，请注意 您的程序安装目录以及SDK存放目录

- 我的电脑右击–>属性–>高级系统设置–>环境变量–>点击系统变量的新建系统变量
  - 变量名ANDROID_HOME 变量值 为你的SDK存放目录
- 修改系统变量path，在后面新增 变量值 Android SDK的tools和platform-tools目录（注意 ; 分隔开）
- 进入SDKManager(可通过Android Studio菜单Tools-Android-SDK Manager)，确保以下项目已经安装并更新到最新：
  - Tools/Android SDK Tools (24.3.3)
  - Tools/Android SDK Platform-tools (22)
  - Tools/Android SDK Build-tools (23.0.1)（这个必须版本严格匹配23.0.1）
  - Android 6.0 (API 23)/SDK Platform (1)
  - Extras/Android Support Library(23.0.1)
  - Extras/Local Maven repository for Support Libraries(之前叫做Android Support Repository)
  - 推荐使用腾讯Bugly的镜像加速下载。查看说明[http://android-mirror.bugly.qq.com:8080/include/usage.html](http://android-mirror.bugly.qq.com:8080/include/usage.html)
    如图所示: ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016080801.png)

#### 怎么样算成功？

关闭所有命令提示行后，在命令行输入 `adb devices`可以看到当前连接计算机的安卓真机或者虚拟机设备即成功。

------

接下来就是激动人心的项目创建环节

```
react-native init projectName
cd projectName
react-native run-android
react-native start

```

## PS：不得不说，RN确实有很多坑，所以 选择RN，就得做好与坑斗争下去的准备

### win平台RN所有需要下载安装的软件包：[http://yunpan.cn/c6bM2erEZ6iK8](http://yunpan.cn/c6bM2erEZ6iK8) 访问密码 3b06

网盘链接失效请及时告知我

**Yours Sincerely SunPing**