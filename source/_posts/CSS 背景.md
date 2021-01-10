---
title: CSS 背景
tags:
  - CSS
  - 前端
categories:
  - 前端
abbrlink: 29971dc9
date: 2020-12-19 17:42:32
---

## CSS 背景属性

| 属性                  | 属性值                                                       | 说明                                                         |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| background-color      | 十六进制、rgb、颜色名称                                      | 设置背景颜色                                                 |
| background-image      | url('图片路径')、none(无背景图片，默认)                      | 设置背景图像，默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体 |
| background-repeat     | repeat(默认。背景图像将在垂直方向和水平方向重复)、<br />no-repeat(背景图像将仅显示一次)、<br />repeat-x(背景图像将在水平方向重复)、<br />repeat-y(背景图像将在垂直方向重复)、<br />inherit(规定应该从父元素继承 background-repeat 属性的设置) | 设置是否及如何重复背景图像                                   |
| background-attachment | scrool(背景图像随对象内容滚动)、fixed(背景图像固定)          | 背景图像是否固定或者随着页面的其余部分滚动                   |
| background-position   | x y (x坐标 y坐标，可以使用方位名词或精确单位)                | 设置背景图像的起始位置                                       |

**背景简写属性**

```css
background:属性1:属性值1 属性2:属性值2 属性3:属性值3...
```

注意：当使用简写属性时，没有特定的书写顺序，一般约定的顺序为：

* background-color
* background-image
* background-repeat
* background-attachment
* background-position

### background-position

```html
background-position: x y;
```

| 参数值   | 说明                                       |
| -------- | ------------------------------------------ |
| length   | 百分比、由浮点数字和单位标识符组成的长度值 |
| position | top、center、bottom、left、right 方位名词  |

1. 参数是方位名词

* 如果指定两个值都是方位名词，则两个值前后顺序无关，比如left top和top left 效果一致。
* 如果只指定了一个方位名词，另一个省略，则第二个值默认是居中对齐

2. 参数是精确单位

* 如果参数是精确单位，那么第一个值肯定是x坐标，第二个值肯定是y坐标。
* 如果只指定一个数值，那该数值一定是x坐标，另一个值默认垂直居中。<br />

3. 参数是混合单位

* 如果指定的两个值是精确单位和方位名词使用，则第一个值是x坐标，第二个值是y坐标。