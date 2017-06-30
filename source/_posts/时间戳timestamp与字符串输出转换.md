---
title: 时间戳timestamp与字符串输出转换
date: 2017-02-20 16:37:22
tags: js
---

在前后端数据处理过程中，常常会和 时间戳打交道，并且 有规定格式去输出，为此 收集了一些常用的 timestamp的 输出，供大家参考

<!--more-->

废话不多说，直接分析例子

如果json传输过来的是 这样的数据

```
var timestamp1 = 1403058804；

```

```
var newDate = new Date();
newDate.setTime(timestamp3 * 1000);
//把时间戳转换为标准时间
------------------------------------
// Wed Jun 18 2014 
console.log(newDate.toDateString());
------------------------------------
// Wed, 18 Jun 2014 02:33:24 GMT 
console.log(newDate.toGMTString());
------------------------------------
// 2014-06-18T02:33:24.000Z
console.log(newDate.toISOString());
------------------------------------
// 2014-06-18T02:33:24.000Z 
console.log(newDate.toJSON());
------------------------------------
// 2014年6月18日 
console.log(newDate.toLocaleDateString());
------------------------------------
// 2014年6月18日 上午10:33:24 
console.log(newDate.toLocaleString());
------------------------------------
// 上午10:33:24 
console.log(newDate.toLocaleTimeString());
------------------------------------
// Wed Jun 18 2014 10:33:24 GMT+0800 (中国标准时间)
console.log(newDate.toString());
------------------------------------
// 10:33:24 GMT+0800 (中国标准时间) 
console.log(newDate.toTimeString());
-------------------------------------
// Wed, 18 Jun 2014 02:33:24 GMT
console.log(newDate.toUTCString());

```

以上可以根据您的需求进行 转换，需要注意的是，看清楚你的timestamp的位数。

我这里 示例的 `timestamp是 10位`，如果后端给你返回的是`13位数`，请 在setTime里面`不要在*1000`

**Yours Sincerely AppleSun**