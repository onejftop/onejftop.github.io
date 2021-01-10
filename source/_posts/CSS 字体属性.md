---
title: CSS 字体属性
tags:
  - CSS
  - 前端
categories:
  - 前端
abbrlink: 49b372a2
date: 2020-12-19 17:42:32
---

CSS Fonts（字体）属性用于定义字体系列、大小、粗细、和文字样式（如斜体）。

| 属性 | 值 | 说明 |
| --- | --- | --- |
| font-family | "微软雅黑"、"宋体"... | 设置字体系列，可设置多种字体，字体之间以“,”隔开。 |
| font-size | px | 设置字体大小,谷歌浏览器默认字体大小16px。 |
| font-weight | normal(正常字体，默认)、bold(粗体)、bolder(特粗体)、lighter(细体) | 设置字体粗细 |
| font-style | normal(默认值)、italic(斜体) | 设置文字样式 |

**字体复合属性**
```css
font: font-style font-weight font-size/line-height font-family;
```
**注意**：  
* 使用font属性时，必须严格按照语法格式中的顺序书写，**不能更换顺序**，并且各个属性间以``空格``隔开。
* 不需要的属性可以省略（省略即取默认值），但必须保留**font-size和font-family属性**，否则font属性将不起作用。