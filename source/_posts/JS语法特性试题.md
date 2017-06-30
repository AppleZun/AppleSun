---
title: JS语法特性试题
date: 2016-07-03 00:19:33
tags: 
- js
- 面试题
---

#### 看完了我的前一篇博文，很多人觉得自己学的很懂了，想来操练操练，看看自己究竟学的多扎实了.这不，我就搞来了13道题目，给各位试（打）炼（击）

~~我真的只是想来打击你的信心的~~

<!--more-->

##### 不信你往下看：

- (一)

  ​

  ```
  (function () {
  return typeof arguments;
  })(); 
  ```

  ​

  A. “object”

  ​

  B. “array”

  ​

  C. “arguments”

  ​

  D. “undefined”


- (二)

  ​

  ```
  var f = function g() {
  return 23;
  };
  typeof g();

  ```

  ​

  A. “number”

  ​

  B. “undefined”

  ​

  C. “function”

  ​

  D. Eorror


- (三)

  ​

  ```
  (function (x) {
  delete x;
  return x;
  })(1);

  ```

  ​

  A. 1

  ​

  B. null

  ​

  C. undefined

  ​

  D. Error


- (四)

  ​

  ```
  var y = 1,
  x = y = typeof x;
  x;

  ```

  ​

  A. 1

  ​

  B. “number”

  ​

  C. undefined

  ​

  D. “undefined”


- (五)

  ​

  ```
  (function f(f) {
    return typeof f();
  })(function () {
    return 1;
  });

  ```

  ​

  A. “number”

  ​

  B. “undefined”

  ​

  C. “function”

  ​

  D. Error


- (六)

  ​

  ```
  var foo = {
    bar: function () {
   return this.baz;
    },
    baz: 1
  };
  (function () {
    return typeof arguments0;
  })(foo.bar);

  ```

  ​

  A. “undefined”

  ​

  B. “object”

  ​

  C. “number”

  ​

  D. “function”


- (七)

  ​

  ```
  var foo = {
    bar: function () {
     return this.baz;
    },
    baz: 1
  };
  typeof (f = foo.bar)();

  ```

  ​

  A. “undefined”

  ​

  B. “object”

  ​

  C. “number”

  ​

  D. “function”


- (八)

  ​

  ```
  var f = (function f() {
    return “1”;
  }, function g() {
    return 2;
  })();
  typeof f;

  ```

  ​

  A. “string”

  ​

  B. “number”

  ​

  C. “function”

  ​

  D. “undefined”


- (九)

  ​

  ```
  var x = 1;
  if (function f() {}) {
    x += typeof f;
  }
  x;

  ```

  ​

  A. 1

  ​

  B. “1function”

  ​

  C. “1undefined”

  ​

  D. NaN


- (十)

  ​

  ```
  var x = [typeof x, typeof y][1];
  typeof typeof x;

  ```

  ​

  A. “number”

  ​

  B. “string”

  ​

  C. “undefined”

  ​

  D. “object”


- (十一)

  ​

  ```
  (function (foo) {
    return typeof foo.bar;
  })({
    foo: {
    bar: 1
    }
  });

  ```

  ​

  A. “undefined”

  ​

  B. “object”

  ​

  C. “number”

  ​

  D. Error


- (十二)

  ​

  ```
  (function f() {
    function f() {
    return 1;
    }
    return f();
    function f() {
    return 2;
    }
  })();

  ```

  ​

  A、1

  ​

  B、2

  ​

  C、Error (e.g. “Too much recursion”)

  ​

  D、undefined


- (十三)

  ​

  ```
  function f() {
    return f;
  }
  new f() instanceof f;

  ```

  ​

  A、true

  ​

  B、false

## A D A D A A A B C B A B B

### 具体答案大家可以自己运行得出，为什么会得出这样的结果，我也有一些不懂的地方，怕误人子弟，所以这里就不解答这里的问题了。