---
title: JS面向对象基本知识
date: 2016-07-16 00:21:44
tags: js
---

学习 `Javascript`，最难的地方是什么？个人觉得 就是`面对对象`这一块。对于初学者来说是`极为不友好`的一种 `编程思维方式`。这一篇博文我们讨论 `“封装”`，并会在之后再介绍学习`“继承”`
首先确认一个概念，`“万物皆是对象”`，具有`“属性”`或者`“方法”`亦或者都具备。

<!--more-->

### 原始模式

但是在原始的设计模式下，根据对象的属性进行简单的封装，常常遇到类似的问题：

如果需要生成多个实例的时候，就会发生代码冗余，不能找出存在的基本关系。

```
var car1 = {}
    car1.brand : "BMW",
    car1.color : "red",
    car1.speed : "500KM/h"
var car2 = {}
    car2.brand : "Audi",
    car2.color : "grey",
    car2.speed : "400KM/h"

```

### 原始模式的改进

就上面的问题，改进后的代码如下：

```
function car(band,color,speed){
    ruturn brand:brand,
        color:color,
        speed:speed
}
var car1 = new car("BMW",red,"500KM/h")
var car2 = new car("Audi",grey,"400KM/h")

```

不过两者之间没有内在联系，依然不是同一个原型对象的实例。

### 构造函数模式

所谓”构造函数”，其实就是一个普通函数，但是内部使用了this变量。对构造函数使用new运算符，就能生成实例，并且this变量会绑定在实例对象上。

```
function car(brand,color,speed){
    this.brand=brand;
    this.color=color;
    this.speed=speed
}
var car1 = new car("BMW",red,"500KM/h")
var car2 = new car("Audi",grey,"400KM/h")
alert(car1.brand)
alert(car2.speed)

```

这时cat1和cat2会自动含有一个constructor属性，指向它们的构造函数。

```
alert(car1.constructor == rar); //true
alert(car2.constructor == rar); //true

```

Javascript还提供了一个instanceof运算符，验证原型对象与实例对象之间的关系。

```
alert(car1 instanceof car); //true
alert(car2 instanceof car); //true

```

### 构造函数模式的问题

构造函数方法很好用，但是存在一个浪费内存的问题。
接下来，我们给他新增不变的属性 “Convertible”（敞篷汽车），再加上一个方法 drive（驾驶）

```
function car(brand,color,speed){
    this.brand=brand;
    this.color=color;
    this.speed=speed;
    this.Convertible=true;
    this.drive=function(){
        alert("炒鸡快呢")
    }
}
var car1 = new car("BMW",red,"500KM/h")
var car2 = new car("Audi",grey,"400KM/h")
alert(car1.Convertible)//是敞篷
car2.drive()//开得快

```

表面看似没啥问题，实际上有大问题，对于每个对象而言，每次生成实例，都会生成多于的内容，浪费内存。会影响性能。

```
alert(car1.Convertible == car2.Convertible);//false

```

为了解决上述问题，我们有了Prototype（原型链）模式

### Prototype模式

每一个构造函数都有一个prototype属性，指向另一个对象。这个对象的所有属性和方法，都会被构造函数的实例继承。
这意味着，我们可以把那些不变的属性和方法，直接定义在prototype对象上。

```
function Car(brand,color){
    this.brand = brand;
    this.color = color;
}
car.prototype.Convertible=true;
car.prototype.drive=function(){
    alert("炒鸡快呢")
}

```

##### 这时所有实例的Convertible属性和drive()方法，其实都是同一个内存地址，指向prototype对象，因此就提高了运行效率。

### Prototype模式的验证方法

为了配合prototype属性，Javascript定义了一些辅助方法，帮助我们使用它。，

#### isPrototypeOf()

这个方法用来判断，某个proptotype对象和某个实例之间的关系。

```
alert(Car.prototype.isPrototypeOf(car1)); //true
alert(Car.prototype.isPrototypeOf(car2)); //true

```

#### hasOwnProperty()

每个实例对象都有一个hasOwnProperty()方法，用来判断某一个属性到底是本地属性，还是继承自prototype对象的属性。

```
alert(car1.hasOwnProperty("name")); // true
alert(car1.hasOwnProperty("Convertible")); // false

```

#### in运算符

- in运算符可以用来判断，某个实例是否含有某个属性，不管是不是本地属性。

  ```
  alert("name" in car1); // true
  alert("Convertible" in car1); // true
  ```

- in运算符还可以用来遍历某个对象的所有属性。

  ```
  for(var prop in car1) { alert("car1["+prop+"]="+car1[prop]); }
  ```