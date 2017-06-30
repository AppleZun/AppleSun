---
title: HEXO博客优化
date: 2016-05-20 10:20:33
tags: hexo
---

#### 原生的永远有人看不上，总有一个合适的第三方等着你去使用。看腻了landscape主题的你是否也有如此体会，今天咱们来 聊聊关于HEXO的优化的那些事

<!--more-->

## 更换主题

#### 最简单粗暴的解决方式

```
通过直接百度 “hexo 主题”，从知乎那边，我们得到了很多的参考。

```

#### 下面就列举几个本人觉得挺棒的几个主题:

- [Next](https://github.com/iissnan/hexo-theme-next) —- [DEMO预览](http://litten.github.io/2014/08/31/hexo-theme-yilia/) snapshot:![img](https://camo.githubusercontent.com/2e2c5c6d351ebe899fcebed0f56a5b72b2660b06/687474703a2f2f696973736e616e2e636f6d2f6e657875732f6e6578742f6e6578742d736368656d65732e6a7067)

  ```
  NexT 简洁优雅，对使用者和访问者都比较友好

  ```


- [hexo-theme-yilia](https://github.com/iissnan/hexo-theme-next) —- [DEMO预览](http://notes.iissnan.com/) snapshot:![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051108.png)

  ​       **本博客采自本主题**

```
响应式比较优秀，动画过渡很舒服
去除了近期文章，去除了搜索框
不支持IE6,7,8

```

- [Pacman](https://github.com/A-limon/pacman) —- [DEMO预览](https://yangjian.me/pacman/) snapshot:![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051109.png)

```
扁平化风格
重在 分类与 时间的归档
适合纯文字的博客
对语言支持高

```

- [Maupassant](https://github.com/tufu9441/maupassant-hexo) —- [DEMO预览](https://www.haomwei.com/) snapshot:![img](https://camo.githubusercontent.com/74fd2ccea00a682742515ce1d3725283c3385721/687474703a2f2f6f6f6f2e306f302e6f6f6f2f323031352f31302f32342f353632623562653132313737652e6a7067)

```
纯净白底黑字；
轻度博客，重内容本身
访问速度最快
不支持IE6,7,8
缺点：用图片的时候会显得不协调

```

##### and so so

## 其他更多优秀的HEXO 主题。请点击   [传送门1](https://www.zhihu.com/question/24422335)     [传送门2](https://hexo.io/themes/)

# 好了，以上我们介绍了那么多的HEXO主题 ，该怎么用呢？

以本人所使用的yilia 举例吧：

1. 解压下载的yilia 文件夹下， 放在 `blog` / `theme` / 路径下
2. 修改yilia文件夹下面的 `_config.yml`,可参考我的*yml*设置
   ![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051110.png)
3. 接下来，设置 `blog` / `_config.yml` 的设置

###### 这里的分项分别表示 标题、副标题、网站描述、网站作者、网站使用的语言、时间线

```
title: 爱尚轻博客
subtitle: 前端路上的这些那些，有你有我
description:  基础,交流,成长
author: Apple Sun
language: zh-CH
timezone:

```

###### 这里的type为你的博客所在的网站平台（本站使用的github，所以填写git）、repo后面的地址是 前面所提到的https的github仓库的地址，不知道的请看我前面的博文。

```
deploy:
  type: git
  repo: https://github.com/CracKerMe/CracKerMe.github.io.git

```

##### 这时候直接 `hexo g` ， `hexo d` 就可以推送您的git 服务器空间了。

### 以上为主题的筛选及使用

------

### 说重要的事关键分割线

#### 优化的事 咱们还一点都没说呢

1. CDN接入。

   - 比较靠谱的有**7牛云**、360CDN节点，使用第三方可以 极大可能地提高自身的访问速度。

2. SEO引擎优化。

   - 添加百度推送代码，让搜索引擎最快发现文章

     #### 方法：

     ##### <博客根目录>/themes/yilia/layout/_partial/article.ejs 的尾部评论位置, 添加:

```
<% if="" (!index){="" %="">
<script>
(function(){
    var bp = document.createElement('script');
    bp.src = '//push.zhanzhang.baidu.com/push.js';
    var s = document.getElementsByTagName("script")[0];
    s.parentNode.insertBefore(bp, s);
})();
</script>     
<% }="" %="">
```

#### 之后，每次用户访问界面，都会调用推送代码

**Yours sincerely SunPing**