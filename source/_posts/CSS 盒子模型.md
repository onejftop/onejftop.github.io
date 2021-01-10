---
title: CSS 盒子模型
tags:
  - CSS
  - 前端
categories:
  - 前端
abbrlink: 7ea51b1c
date: 2020-12-19 17:42:32
---

## 边框（border）

border可以设置元素边框。边框由三部分组成：边框宽度（粗细）、边框样式和边框颜色。
| 边框属性 | 值 |说明 |
| --- | --- | --- |
| border-width | xpx | 定义边框粗细 |
| border-style | solid(实线)、dashed(虚线)、dotted(点线) | 边框的样式 |
| border-color |  | 边框颜色 |
| border-collapse | collapse | 合并相邻边框 |
| border-radius |  | CSS3新增，设置元素的外边框圆角 |
边框简写：
```html
border: 1px solid pink;    没有顺序
```
边框分开写法：
```
border-top: 1px solid pink;    /* 只设定上边框，其余同理 */
```

## 内边距（padding）

padding属性用于设置内边距，即边框与内容之间的距离。
| 属性 | 说明 |
| --- | --- |
| padding-left | 左内边距 |
| padding-right | 右内边距 |
| padding-top | 上内边距 |
| padding-bottom | 下内边距 |
padding属性（简写属性)可以有1到4个值。
| 值的个数 | 说明 |
| --- | --- |
| padding:5px | 表示上下左右都有5px内边距 |
| padding:5px 10px | 表示上下内边距5px，左右内边距10px |
| padding:5px 10px 20px | 表示上内边距5px，左右内边距10px，下内边距20px |
| padding；5px 10px 20px 30px | 表示上内边距5px，右内边距10px，下内边距20px，左内边距30px 顺时针 |

## 外边距（margin）

margin属性用于设置外边距，即控制盒子和盒子之间的距离。

### 外边距合并

使用margin定义元素的垂直外边距时，可能会出现外边距的合并。

#### 嵌套块元素垂直外边距的塌陷

对于两个嵌套关系（父子关系)的块元素，父元素上有外边距同时子元素上也有外边距，此时父元素会塌陷较大的外边距值。  
**解决方案**：
* 可以为父元素定义上边框。
* 可以为父元素定义上内边距。
* 可以为父元素添加overflow:hidden

## 清除内外边距

```
* {
    padding: 0;
    margin:0;
}
```