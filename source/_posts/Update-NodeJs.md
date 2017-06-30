---
title: Update NodeJs
date: 2017-06-29 09:16:46
tags: node
---

## How to update your node version?

It's known to all that when we use MacOS , we can easily update nodejs.

<!--more-->

just like 

```shell
npm install -g n
```



if you have problem with `install -g`,you should run this:

```shell
sudo npm install -g n
```

and then,

```shell
n stable
```

It can automatically update to *The Stable Version*



However, it's useless when we use windows OS.

**nvm** always needed, i recommend the `gnvm`[Github_url](https://github.com/Kenshin/gnvm) here.

### But How to

(~~First,make sure that you have already install NodeJs any version~~)

- download it

  * [32 bit](https://raw.githubusercontent.com/Kenshin/gnvm-bin/master/32-bit/gnvm.exe)
  * [64bit](https://raw.githubusercontent.com/Kenshin/gnvm-bin/master/64-bit/gnvm.exe)

- put the package to the path of nodejs,

  Usually,its path is **C:\Program Files\nodejs**

- restart you cmd shell

- run `gnvm version`,until you see the correct version can go to the next ,or you should find the issues on github

- `gnvm install latest 7.1.2`

  It means you install `latest version` and `v7.1.2` at the same time,you can change any version you want

- `gnvm use latest`  it makes your computer to use latest nodejs version.

- anything else? no It's finished!



So easy!

__Yours sincerely SunPing__

