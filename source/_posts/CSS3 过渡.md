---
title: CSS3 过渡
tags:
  - CSS3
  - 前端
categories:
  - 前端
abbrlink: c182708c
date: 2020-12-19 17:42:32
---

| 过渡属性 | 说明 |
| --- | --- |
| transition | 简写属性，用于在一个属性中设置四个过渡属性。 |
| transition-property | 规定应用过渡的CSS属性名称 |
| transition-duration | 定义过渡效果花费的时间，默认是0 |
| transition-timing-function | 规定过渡效果的时间曲线，默认是"ease" |
| transition-delay | 规定过渡效果何时开始，默认是0。|

| transition-timing-function属性值 | 说明 |
| --- | --- |
| linear | 规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)） |
| ease | 规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。 |
| ease-in | 规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。 |
| ease-out | 规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。 |
| ease-in-out | 规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。 |
| cubic-bezier(n,n,n,n) | 在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。 |

要实现过渡效果，必须实现两点：
* 规定你希望把效果添加到那个属性上。
* 规定效果的时长。  
