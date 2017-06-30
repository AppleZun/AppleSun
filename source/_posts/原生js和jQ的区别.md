---
title: 原生js和jQ的区别
date: 2016-06-29 09:12:31
tags: js
---

本篇博文 为大家列举一些常用的 原生js 和 jQ 的语法不一样的地方，以便小伙伴在运用过程中 灵活转换，方便学习开发。

<!--more-->

### 选择元素

```
//jq
$('.el');
//js
document.querySelector("div");
div.querySelectorAll('.el');
//mui
mui(".el")[0];

```

### 父、兄弟元素

```
//jq
$('.el').parent();
$('.el').prev();
$('.el').next();
$('.el').last();
$('.el').first();
//js
document.querySelector('.el').parentNode;
document.querySelector('.el').previousElementSibling;
document.querySelector('.el').nextElementSibling;
document.querySelector(".el").lastElementChild;
document.querySelector(".el").children[0];

```

### 获取元素文本

```
//jq
$('.el').html();
$('.el').val();
$('.el').text();
$(el).replaceWith(string);
//js
document.getElementById('el').innerHTML;
document.getElementById('el').value;
document.getElementById('el').textContent
document.getElementById('el').outerHTML = string;

```

### 创建元素

```
//jq
var newEl = $('
');
//js
var newEl = document.createElement('div');

```

### Set/get属性

```
//jq
$('.el').filter(':first').attr('key', 'value');
$('.el').filter(':first').attr('key');
$('.el').addClass('class');
$('.el').removeClass('class');
$('.el').toggleClass('class');
$(el).css('border-width', '20px');
//js
document.querySelector('.el').setAttribute('key', 'value');
document.querySelector('.el').getAttribute('key');
document.querySelector('.el').classList.add('class');
document.querySelector('.el').classList.remove('class');
document.querySelector('.el').classList.toggle('class');
document.querySelector('.el').style.borderWidth = '20px';

```

### 附加

```
//jq
$('.el').append($('
'));
//js
document.querySelector('.el').appendChild(document.createElement('div'));

```

### 克隆

```
//jq
var clonedEl = $('.el').clone();
//js
var clonedEl = document.querySelector('.el').cloneNode(true);

```

### 移除

```
//jq
$('.el').remove();
// js
var toRemove = document.querySelector(el);
toRemove.parentNode.removeChild(toRemove);

```

### ajax

```
//jq
$.get('url', function (data) {
});
$.post('url', {data: data}, function (data) {
});
//js
// get
var xhr = new XMLHttpRequest();
xhr.open('GET', url);
xhr.onreadystatechange = function (data) {
}
xhr.send();
// post
var xhr = new XMLHttpRequest()
xhr.open('POST', url);
xhr.onreadystatechange = function (data) {
}
xhr.send({data: data});

```

### 显示和隐藏

```
//jq
$(el).show();
$(el).hide();
//js
el.style.display = '';
el.style.display = 'none';

```

### 是否包含某个 class

```
//jq
$(el).hasClass(className);
//js
if (el.classList)
  el.classList.contains(className);
else
  new RegExp('(^| )' + className + '( |$)', 'gi').test(el.className);

```

### 添加 Class

```
//jq
$(el).addClass(className);
//js
if (el.classList)
  el.classList.add(className);
else
  el.className += ' ' + className;

```

### 移除class

```
//jq
$(el).removeClass(className);
//js
// removeClass, takes two params: element and classname
function removeClass(el, cls) {
  var reg = new RegExp("(\\s|^)" + cls + "(\\s|$)");
  el.className = el.className.replace(reg, " ").replace(/(^\s*)|(\s*$)/g,"");
}

```

###### Tips: 如果你只需要支持像IE10+,Chrome,FireFox,Opera和Safari这样较现代的浏览器，那么你可以开始使用HTML5的classList功能，它让增加和删除类变得更简单

```
el.classList.add(className);
el.classList.remove("foo")
el.classList.contains("foo");
el.classList.toggle("active");

```

### 插入 HTML

```
//jq
$(el).before(htmlString);
$(parent).append(el);
$(el).after(htmlString);
//js
el.insertAdjacentHTML('beforebegin', htmlString);
parent.appendChild(el);
el.insertAdjacentHTML('afterend', htmlString);

```

### 获取子节点

```
//jq
$(el).children();
//js
el.children

```

### Trim

```
//jq
$.trim(string);
//js
string.trim();

```

###### Tips:css 统制文本显示两行 超过省略号显示

```
{
	display: -webkit-box;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 2;
	word-break: break-all;
	overflow: hidden;
}

```

**Yours Sincerely Apple Sun**