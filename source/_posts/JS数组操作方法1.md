---
title: JS数组操作方法1
date: 2016-10-11 06:35:32
tags: js
---

### 数组是JavaScript中常见的一个对象，它有一些经典的操作，比如数组的增、删、改、查。在这篇文章中主要整理这方面的相关操作方法。

<!--more-->

## 增加数组项

首先来看如何给一个数组增加数组项。假设有一个数组:

```
var arr = [];

```

上面声明了一个数组，但这个数组是一个空数组[]，其length的值为0。接下来我们看如何给数组arr增加数组项。最简单的方法可以通过索引值方式，给数组增加数组项：

```
var arr = [];
arr[0] = 'a';
arr[1] = 'b';
arr[2] = 1;
arr[3] = 2;
console.log(arr); // ["a", "b", 1, 2]
console.log(arr.length); // 4

```

另外也可以通过改为数组的length值给数组增加数组项，不过这种方法给数组增加的数组项都是undefined:

```
var arr = [];
arr[0] = 'a'; // 给数组arr添加一个`a`数组项
arr.length = 5; // 改变数组的`length`值为`5`
console.log(arr); // ["a", undefined × 4]

```

虽然这种方法也给数组增加了数组项，但相对来说都较为麻烦。其实给数组添加数组项，没有这么麻烦，可以通过数组提供的原生方法给数组添加数组项。

### push()

使用push()方法可以给数组末尾添加一个或多个数组项。

```
var arr = [];
arr.push('a','b');
console.log(arr); // ['a','b']
unshift()

```

使用push()方法可以给数组末尾添加一个或多个数组项，那么使用unshift()方法可以在数组的前面添加一个或多个数组项：

```
var arr = ['a','b'];
arr.unshift(1,2);
console.log(arr); // [1, 2, "a", "b"]

```

除了这两种方法之外，还可以使用splice()方法给数组添加数组项：

```
var arr = ['a','b','c',1,2];
arr.splice(2,0,'d','c','e');
console.log(arr); // ["a", "b", "d", "c", "e", "c", 1, 2]

```

另外除了splice()方法之外还可以使用concat()方法可以给数组添加数组项，只不过使用这种方法不会改变原数组，会在原数组中创建一个新数组：

```
var arr = ['a','b','c'];
var arr2 = arr.concat('d',1,2,['e',3]);
console.log(arr); // ["a", "b", "c"]
console.log(arr2); // ["a", "b", "c", "d", 1, 2, "e", 3]

```

## 删除数组项

对于数组的操作，除了增加数组项，很多时候还需要对数组进行删除操作。删除数组项常用的方法有pop()和shift()两种方法。

### pop()

pop()方法可以从数组的末尾删除一个数组项：

```
var arr = ['a','b','c','d',1,2];
arr.pop();
console.log(arr); // ["a", "b", "c", "d", 1]

```

### shift()

shift()方法和pop()方法刚好相反，它可以删除数组的第一项：

```
var arr = ['a','b','c','d',1,2];
arr.shift();
console.log(arr); // ["b", "c", "d", 1, 2]

```

不管是pop()或shift()方法每次只能给数组删除一个数组项，但很多时候这样删除数组项相对来说是比较麻烦的。在数组的操作中，除了这两种方法之外，还可以通过slice()和splice()方法来删除数组项。

### slice()

slice()方法可以给一个数组中删除多个数组项，只不过不同的是，slice()不会影响原数组，只是会在原数组基础上创建一个数组副本：

```
var arr = [1,2,3,4,'a','b'];
var arr2 = arr.slice(2);
console.log(arr); // [1, 2, 3, 4, "a", "b"]
console.log(arr2); // [3, 4, "a", "b"]
console.log(arr3); // ["a", "b"]
splice()

```

splice()方法除了能给数组添加数组项之外，还可以给数组删除数组项：

```
var arr = [1,2,3,4,'a','b','c'];
var arr2 = arr.splice(2,2);
console.log(arr); // [1, 2, "a", "b", "c"]
console.log(arr2); // [3, 4]

```

## 改变数组

数组中splice()方法是数组中一个强大的方法，其除了可以给数组添加数组项、删除数组项之外，还可以改变一个数组：

```
var arr = [1,2,3,4,5,6];
var arr2 = arr.splice(2,3,'a','b','c');
console.log(arr); // [1, 2, "a", "b", "c", 6]
console.log(arr2); // [3, 4, 5]

```

## 数组的查询

这里所说的数组查询其实指的是数组的查询提取。其使用的方法是slice()方法:

```
var arr = [1,2,3,4,5,6];
var arr2 = arr.slice(-3);
console.log(arr); // [1, 2, 3, 4, 5, 6]
console.log(arr2); // [4, 5, 6]

```

# 总结

#### 这里简单的整理了一个数组的增、删、改、查的相关方法。简单的总结一下：

1. 增加数组项方法：除了直接改变数组项的值和修改数组的length给数组添加数组项方法之外，还可以使用push()、unshift()、concat()和splice()添加数组项
2. 删除数组项方法：删除数组项方法有pop()、shift()、slice()和splice()方法
3. 改变数组项方法：在数组中主要通过splice()方法来改变数组项
4. 查询数组项方法： 查询数组项方法其实就是对数组做查询提取功能，主要使用的方法是slice()方法

## 有关于pop()、push()、shift()和unshift()操作方法可以点击这里；

### push()方法

该方法是向数组末尾添加一个或者多个元素，并返回新的长度。

push()方法可以接收任意数量的参数，把它们逐个添加到数组的末尾，并返回修改后数组的长度。如：

```
var arr = []; //创建一个空数组
console.log(arr); // []
console.log("入栈"); // 入栈
arr.push(1); // 将1添加到数组arr中
console.log(arr); // [1]
arr.push(2); //将2添加到数组arr中
console.log(arr); //[1,2]
arr.push([3,4]); // 将数组[3,4]添加到arr中
console.log(arr); // [1,2,[3,4]]
console.log(arr.length); // 3

```

在Chrome浏览器控制台输出的效果如下图所示：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061524.png)

### pop()方法

pop()方法刚好和push()方法相反。pop()方法删除数组的最后一个元素，把数组的长度减1，并且返回它被删除元素的值，如果数组变为空，则该方法不改变数组，返回undefine值。如下代码演示：

```
var arr = [1,2,3,4]; //创建一个数组
console.log(arr); // [1,2,3,4]
console.log(arr.length); // 4
console.log("出栈，后进先出"); // 出栈，后进先出
arr.pop();
console.log(arr); //  // [1,2,3]
arr.pop();
console.log(arr); // [1,2]
arr.pop();
console.log(arr); // [1]
arr.pop();
console.log(arr); // []

```

在Chrome浏览器控制台输出的效果如下图所示：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061525.png)

### unshift()方法

unshift()方法是向数组的开头添加一个或多个元素，并且返回新的长度。

```
var arr = []; //创建一个空的数组
console.log(arr); // []
console.log("入队"); // 入队
arr.unshift(1,2,3,4); // 将1,2,3,4推入到数组arr
console.log(arr); // [1,2,3,4]
console.log(arr.length); // 4

```

在Chrome浏览器控制台输出的效果如下图所示：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061526.png)

### shift()方法

shift()方法和unshift()方法恰恰相反。该方法用于把数组的第一个元素从其中删除，并返回被删除的值。如果数组是空的，shift()方法将不进行任何操作，返回undefined的值。

```
var arr = [1,2,3,4]; // 创建一个数组
console.log(arr); // [1,2,3,4]
arr.shift(); // 取得第一项
console.log(arr); // [2,3,4]
arr.shift(); // 取得第一项
console.log(arr); // [3,4]
arr.shift(); // 取得第一项
console.log(arr); // [4]
arr.shift(); // 取得第一项
console.log(arr); // []

```

在Chrome浏览器控制台输出的效果如下图所示：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061527.png)

### 关于concat()、slice()和splice()方法的相关介绍可以关注我的下一篇博文。

**Yours Sincerely SunPing**