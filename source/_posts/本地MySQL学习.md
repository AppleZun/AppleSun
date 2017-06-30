---
title: 本地MySQL学习
date: 2016-09-17 21:41:19
tags: php
---

要想做一名人见人爱花见花开的称职的前端开发工程师，就得 了解 后端以及数据库的基础知识。介于此，我们必须得学习一定的知识便于今后的开发工作。所以，今天来开启点亮我们的数据库天赋树.
(tips:本页面使用的 XAMPP for OS X 5.6.14，PHP版本为：5.6.14，MySQL版本为：mysqlnd 5.0.11。windows操作系统以及真实的操作环境，请根据实际情况进行操作)

<!--more-->

# 环境准备：

安装好 XAPMM ，打开并启动 所有服务(“Start All”),注意，本教程中所有使用的文件均在服务器环境下。

#### MAC系统下文件路径为：Mac->应用程序->XAMPP->htdocs

（很抱歉，我将尽快更新PHP的快速入门，原谅我整理速度过慢）

## 基础知识恶补：

1. 本地环境下，测试地址为：`localhost`,直接在浏览器地址栏输入即可。或者是`127.0.0.1` 或者是 `您的IP地址`。

2. 数据库是由很多表(table)构造起来的，且只有一个`主键`；

3. 数据库操作的基本机构案列：

   ```
   $sqli = new mysqli("localhost","root","","shh160");
   if($sqli->connect_errno){
   	die($mysqli->connect_error);
   }
   $sql = "SQL语句 增 查 改 删";
   $sqli->query("set names utf8");
   $result = $sqli->query($sql);
   	coding...数据的操作在这里；
   $sqli->close();

   ```

# 可视化操作数据库：

[点我打开phpmysql](http://127.0.0.1/phpmyadmin/)，看到如下界面，先简单介绍这个界面。左边是你的数据库名称，，我们需要打交道的便是SQL的部分，，还有注意我箭头标识的编码方式。
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061501.png)

### 新建一个数据库

点击左边的`New`，当你的中文输出时出现不正常显示时，最好将编码方式统一选择为`utf8_unicode_ci`.
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061502.png)

### 新建一个表单

```
CREATE TABLE students(id int(10) PRIMARY KEY AUTO_INCREMENT,name CHAR(10) DEFAULT '用户',sex CHAR(3) DEFAULT '男',age int(3) DEFAULT 18);

```

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061503.png)
![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061504.png)

##### 从 2张图 对比来看，似乎我们已经知道了我上面的代码每一字节所代表的含义了，很好。还差点什么？—缺少数据。

### 新建数据（增）

回到SQL界面，咱们接着来，**增加数据**

```
INSERT INTO students(id, name, sex, age) VALUES (NULL,"张三","女",30),(NULL,"李四","人妖",23);

```

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061505.png)
**文字总结如下：**

1. INSERT INTO 表名（字段1，字段2）VALUES(字段1的值，字段2的值)，(字段1的值，字段2的值)，(字段1的值，字段2的值)；

### 查找数据（查）

为了更好滴 让大家感受到 查找数据的便捷与具体实现，我 对表内数据实现了大量的添加，现数据库表单内容如下：

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061506.png)

- 要求1，找到所有姓孙的
  其实这里属于模糊搜索法， 运用like 搜索，通过在关键字后面添加”%”，完成以什么开头的查询

```
SELECT * FROM students WHERE name LIKE "孙%";

```

![img](http://7xjdah.com1.z0.glb.clouddn.com/pic2016061507.png)

下面不在截图举例！

- 要求2，找到所有以孙结尾的
  通过在关键字前面添加”%”，完成以什么开头的查询

```
SELECT * FROM students WHERE name LIKE "%孙";

```

- 要求3，找到所有包含孙的
  相比我不用说，你也猜出来了。通过在关键字前后添加”%”，完成以什么开头的查询

```
SELECT * FROM students WHERE name LIKE "%孙%";

```

- 要求4，找到年龄大于18的3个人

```
SELECT * FROM students WHERE age>18 LIMIT 3;

```

- 要求5，找到性别是女的姓名和年龄

```
SELECT name,age FROM students WHERE sex="女";

```

#### 好了，希望通过上面的5个例子能让你学习到有关查询的方法。

**文字总结如下：**

1. 查询数据
   从表里面查询字段1，字段2，字段3。表里面有多少条数据，就会显示多少条字段1，字段2，字段3的内容。
   SELECT 字段1，字段2，字段3。。 FROM 表名
2. 查询所有字段，星号是一个通配符，可以表示所有字段
   SELETE * FROM 表名
3. 查询符合条件的数据
   SELECT 字段1，字段2，字段3 FROM 表名 WHERE 字段=值
4. 模糊查询
   SELECT 字段1，字段2，字段3 FROM 表名 WHERE 字段 LIKE “%值%”

### 更新数据（改）

UPDATE 表名 SET 字段=值，字段=值 WHERE id= ；

### 删除数据（删）

DELETE FROM 表名 WHERE id= ；

#### 删除数据表单

DROP TABLE 表名

#### 删除数据库

DROP DATABASE 数据库名(从删除数据库到跑路)

未完待续(这篇博客 后期写的笔记急，还会再修整的)

**Yours sincerely SunPing**