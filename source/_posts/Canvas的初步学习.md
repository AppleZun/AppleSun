---
title: Canvas的初步学习
date: 2016-09-05 07:21:28
tags: html5
---

HTML5新增便签canvas，从他出生似乎很有争议：有人看好canvas的强大操作性，觉得移动端游戏开发可以依靠canvas侵占市场；有人看悲他，因为不够成熟的API，并不足以完成 HTML5 的重大期望。不过，作为HTML5 的一部分，还有有必要去学习了解canvas的。

<!--more-->

### 明确：Canvas 能做什么？

- `游戏开发`：替代Flash游戏是他的根本使命，流畅度跨平台能发挥潜力
- `图表制作`：不过实际生产过程中会考虑使用`SVG`或者`ECharts`来实现
- `banner广告`：同样是取代flash在广告的领域
- `字体图片设计`：字体的自定义渲染可以通过HTML5技术实现
- `模拟器`：无论从视觉效果还是核心功能方面来说，模拟器产品可以完全由JavaScript来实现
- `其他可嵌入网站的内容`：类似音频、视频等，能更好地与Web融合
- and so on

### 基础知识学习

HTML：

```
<canvas id="canvas" width="800" height="600">您的浏览器版本过低，请升级您的浏览器</canvas>//宽高属性直接在canvas行间设置

```

script：

```
var canvas = document.getElementById('canvas')
var context = canvas.getContext('2d')//当前参数仅支持2d，以后可能有“3d”参数
context.beginPath()//在新的图层上渲染
context.fillStyle="#fff"//此处为填充颜色的选择
context.strokeStyle="blue"//此处为描边颜色的选择
context.arc(x,y,r,degS,degE)//参数分别为“圆心横坐标”，“圆心纵坐标”，“圆心半径”，“起始弧度”，“终止弧度”
context.rect(x,y,wid,heig)//参数分别为“起点横坐标”，“起点纵坐标”，“矩形宽”，“矩形高”
context.fill()//确认填充区域
context.stroke()//确认描边
context.lineWidth=3//线宽
context.moTo(x1,y1)//讲画笔移到起始点
context.lineTo(x2,y2)//以上一个点连接到当前点作画
context.closePath()//闭合封闭图形

```

- 其中要注意的就是 当出现 context.rotate();context.scale();context.translate()时，要配合使用context.save();context.restore()。可以理解为游戏的存档与读档;以rotate为例，使用方法如下：

```
context.save();//保存上面
context.rotate(Math.PI*2);//顺时针旋转2π
context.fillStyle="red"//填充色为红色
context.translate(50，50)讲原点移动到50，50 的位置
context.fillRect(0,0,100,200);//填充一个100*200的红色矩形（实际是在50，50的位置绘制的）
context.restore();//恢复保存
context.fillRect(0,0,300,200);//此时填充一个黑色的（默认颜色）300*200的矩形（依然是在0，0的位置绘制）

```

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016051644.png)

##### 完成上图内容，完成基础知识的考核

#### 案例1：clock demo

```
HTML:
    <canvas id="canvas" width=400 height=400>

SCRIPT:
    var canvas = document.getElementById('canvas')
    var context = canvas.getContext('2d')
    var r = canvas.width/2
    var anglePerHour = Math.PI/6
    var anglePerMinute = Math.PI/30
    var anglePerSecond = Math.PI/30
        context.translate(r,r)
    function surface() {
        context.fillStyle="purple"
        context.lineCap="round"
        context.beginPath()
        context.arc(0,0,r,0,Math.PI*2,true)
        context.fill()
        //时针刻度
        context.beginPath()
        context.strokeStyle="#fff"
        context.lineWidth=10
        for (var i = 0; i < 12; i++) {
            context.save()
            context.rotate(anglePerHour*i)
            context.moveTo(r-40,0)
            context.lineTo(r-5,0)
            context.stroke()
            context.restore()
        }
        //分针刻度
        context.beginPath()
        context.strokeStyle="#0ff"
        context.lineWidth=5
        for (var i = 0; i < 60; i++) {
            if (i%5!=0) {
                context.save()
                context.rotate(anglePerMinute*i)
                context.moveTo(r-25,0)
                context.lineTo(r-5,0)
                context.stroke()
                context.restore()
            }
        }
    }
    function timeGo() {
        var date = new Date()
        var hour = date.getHours()
        var minute = date.getMinutes()
        var second = date.getSeconds()
        //时针
        context.beginPath()
        context.strokeStyle="#f0f"
        context.lineWidth=8
        context.save()
        context.rotate(anglePerHour*hour+anglePerMinute*minute/12+anglePerSecond*second/60/12-Math.PI/2)
        context.moveTo(0,0)
        context.lineTo(100,0)
        context.stroke()
        context.restore()
        //分针
        context.beginPath()
        context.strokeStyle="#ff0"
        context.lineWidth=6
        context.save()
        context.rotate(anglePerMinute*minute+anglePerSecond*second/60-Math.PI/2)
        context.moveTo(0,0)
        context.lineTo(120,0)
        context.stroke()
        context.restore()
        //秒针
        context.beginPath()
        context.strokeStyle="#f3f3f3"
        context.lineWidth=4
        context.save()
        context.rotate(anglePerSecond*second-Math.PI/2)
        context.moveTo(0,0)
        context.lineTo(150,0)
        context.stroke()
        context.restore()
    }
    surface()
    timeGo()
    setInterval(function () {
        context.clearRect(-r,-r,400,400)
        surface()
        timeGo()
    }, 500)


```

## [点击这里查看Online-Clock在线演示](http://crackerme.github.io/DemoForCanvas/)

#### 案例2：在线涂鸦

```
HTML:
    <canvas id=”canvas” width=600 height=400>
SCRIPT:
    var canvas = document.getElementById(‘canvas’)
    var context = canvas.getContext(‘2d’)
    canvas.onmousedown=function (e) {
        context.beginPath()
        var ev = ev||window.event
        var disX = ev.clientX-canvas.offsetLeft;
        var disY = ev.clientY-canvas.offsetTop;
        context.moveTo(disX,disY)
document.onmousemove=function (e) {
            var ev = ev||window.event
            var dX = ev.clientX-canvas.offsetLeft;
            var dY = ev.clientY-canvas.offsetTop;
            var gradient = context.createLinearGradient(0,0,600,400)
            gradient.addColorStop(0,’red’)
            gradient.addColorStop(0.2,’orange’)
            gradient.addColorStop(0.4,’yellow’)
            gradient.addColorStop(0.6,’green’)
            gradient.addColorStop(0.8,’blue’)
            gradient.addColorStop(1,’purple’)
            context.strokeStyle=gradient;
            // context.strokeStyle=”red”
            context.lineWidth=3
            context.lineTo(dX,dY)
            context.stroke()}
document.onmouseup=function(){
    document.onmousemove=null}}


```

## [点击这里查看Free Doodle在线演示](http://crackerme.github.io/DemoForCanvas/)

#### 手机状态下预览不佳，建议使用PC登陆查看，谢谢合作

未完待续。。。

*Yours Sincerely SunPing*