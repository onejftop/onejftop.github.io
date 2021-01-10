---
title: CSS 引入方式
tags:
  - CSS
  - 前端
categories:
  - 前端
abbrlink: 244e0c16
date: 2020-12-19 17:42:32
---

## 行内样式表（行内式）

``行内样式表``是在元素标签内部的style属性中设置CSS样式，适合于修改简单样式。
```html
<div style="color: red; font-size: 18px;">
    青春
</div>
```

## 内部样式表（嵌入式）

``内部样式表``是写到HTML内部，是将所有CSS代码抽取出来，单独放到一个&lt;style&gt;标签中。  
&lt;style&gt;理论上，可以放在HTML文档的任何地方，但一般会放在文档的&lt;head&gt;标签中。
```html
<style>
    div {
        color:pink;
        font-size: 18px;
    }
</style>
```

## 外部样式表（链接式）

``外部样式表``:样式单独写到CSS文件中，之后把CSS文件引入到HTML页面中使用。
```html
<link rel="stylesheet" href="css文件路径">
```