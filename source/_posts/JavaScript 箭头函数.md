---
title: JavaScript 箭头函数
tags:
  - JavaScript
  - 前端
categories:
  - 前端
abbrlink: '307e5568'
date: 2020-12-21 20:56:55
---

## 箭头函数

> 箭头函数：ES6标准新增了一种新的函数：Arrow Function（箭头函数）。

### 基础语法

#### 箭头函数的定义方法：

将原函数的关键``functio``和函数名都删掉，并使用 ``=>``连接参数列表和函数体(参数列表 => 函数体)。

```javascript
function add(a,b){
    return a+b
}
(a,b) => {
    return a+b
}
```

当只有一个参数时，括号可以省略；但是没有参数时，括号不可以省略。

```javascript
var fun1 = function(a){}
var fun1 = a => {}

var fun2 = function(){}
var fun2 = () => {}
```



