---
title: React Native遇到的坑-持续更新
date: 2016-12-13 23:29:28
tags: js
---

因为工作需要，需要用react-native去开发一款APP，在学习时间如此珍贵的前提下，竟然发生了N多开发前的准备问题。本博客适合小白遇到的问题，希望您与我交流。

<!--more-->

# 问题1:代码更新后，reload不更新

我们在真机上面调试是需要实时更新代码，让代码生效的。一般来说我们会设置`Enable Hot Reloading`【轻轻摇晃手机就可以设置】。但是有时候我们修改了代码，在手机上并不会实时更新代码。浪费太多的时间在关闭开启包服务器，很是头疼

### 解决方法打开文件：

```
你的app名称\node_modules\react-native\node_modules\node-haste\lib\FileWatcher\index.js

```

- 修改变量`MAX_WAIT_TIME：`

```
// var MAX_WAIT_TIME = 120000;
var MAX_WAIT_TIME = 360000;

```

- 修改部分代码

```
key: '_createWatcher',
    value: function _createWatcher(rootConfig) {
      var watcher = new WatcherClass(rootConfig.dir, {
        glob: rootConfig.globs,
        dot: false
      });

      return new Promise(function (resolve, reject) {

        const rejectTimeout = setTimeout(function() {
          reject(new Error([
            'Watcher took too long to load',
            'Try running `watchman version` from your terminal',
            'https://facebook.github.io/watchman/docs/troubleshooting.html',
          ].join('\n')));
        }, MAX_WAIT_TIME);

        watcher.once('ready', function () {
          clearTimeout(rejectTimeout);
          resolve(watcher);
        });
      });
    }

```

通过这么几步，就可以实现即时reload预览（前提是环境变量配置正确）。

- 打开白屏
  ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016080803.png)
  解决方法：开启 当前应用的 *悬浮窗* 权限。具体操作方法 百度之
  （MIUI系统 需要在此基础上`关闭MIUI优化`–一种排版优化功能，关闭就好）


- 注意一下RN所支持的最低iOS和Android版本，如果不是下面的 报错就不用纠结了
  - Android >= 4.1 (API 16)
  - iOS >= 7.0

------

## 报错信息解读

- Unable to download JS bundle
  ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016080802.png)

首先 确认你的服务器是否正常开启

```
react-native start

```

其次确定 8081端口 是否正常打开

```
adb reverse tcp:8081 tcp:8081

```

注意点：PC和手机连接到同一个wifi环境下，否则不能访问

------

- Invariant Violation:Application XXXX has not been registered.

请确保index.ios.js中的

```
AppRegistry.registerComponent('项目名',() => ...);

```

与appDelegate.m中的

```
RCTRootView*rootView = [[RCTRootViewalloc]initWithBundleURL:jsCodeLocation

moduleName:@"项目名" launchOptions:launchOptions];

```

或是MainActivity.java中的

```
mReactRootView.startReactApplication(mReactInstanceManager, "项目名", null);
```

都保持一致。

------

- 使用Image时报错：You are trying to render the global Image variable as a React element. You probably forgot to require Image

由于React的Image组件和全局的Image对象重名，所以使用Image组件时一定要记得在文件开头正确引入React的Image组件。