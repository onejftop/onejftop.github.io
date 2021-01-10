---
title: HTML 常用标签
tags:
  - HTML
  - 前端
categories:
  - 前端
abbrlink: f2f9e33e
date: 2020-12-19 17:42:32
---

| 标签 | 说明 |
| --------- | ---- |
| &lt;h1&gt;&lt;/h1&gt;-&lt;h6&gt;&lt;/h6&gt; |标题标签，h1为最大标题、h6为最小标题 |
| &lt;P&gt;&lt;/p&gt; | 段落标签      |
| &lt;br /&gt; | 换行标签 |

## 文本格式化标签

| 文本格式化标签 | 说明 |
| --- | ---|
| &lt;strong&gt;&lt;/stromg&gt;或者&lt;b&gt;&lt;/b&gt; | 加粗，推荐使用&lt;strong&gt; |
| &lt;em&gt;&lt;/em&gt;或者&lt;i&gt;&lt;/i&gt; | 斜体，推荐使用&lt;em&gt; |
| &lt;del&gt;&lt;/del&gt;或者&lt;s&gt;&lt;/s&gt; | 删除线，推荐使用&lt;del&gt; |
| &lt;ins&gt;&lt;/ins&gt;或者&lt;u&gt;&lt;/u&gt; | 下划线，推荐使用&lt;ins&gt; |
| &lt;big&gt;&lt;/big&gt; | 定义大号字 |
| &lt;sub&gt;&lt;/sub&gt; | 定义下标字 |
| &lt;sup&gt;&lt;/sup&gt; | 定义上标字 |


## 图像标签

```html
<img src="图像路径" />
```

### 图像标签的属性

| 属性 | 属性值 | 说明 |
| --- | --- | --- |
| src | 图像路径 | 必须属性 |
| alt | 文本 | 替换文本，图像不能显示的时候以文字替换 |
| title | 文本 | 提示文本，鼠标放到图像上显示的文字 |
| width | 像素 | 设置图像的宽度 |
| height | 像素 | 设置图像的高度 |
| border | 像素 | 设置图像的边框粗细 |

## 超链接标签

```html
<a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
```

| 超链接标签属性 | 说明 |
| --- | --- |
| href | 必须属性，用于指定链接目标的url地址，实现页面跳转 |
| target | 用于指定链接页面的打开方式，其中_self为默认值，表示当前页面打开，_blank表示在新窗口打开 |

### 链接分类

| 链接分类 | 说明 |
| --- | --- |
| 外部链接 | &lt;a href="https://www.baidu.com"&gt; |
| 内部链接 | &lt;a href="index.html"&gt; |
| 空链接 | &lt;a href="#"&gt; |
| 下载链接 | &lt;a href="下载.zip"&gt; |
| 网页元素链接 | 在网页中的各种网页元素，如文本、图像、表格、音频、视频等都可以添加超链接 |
| 锚点链接 | ``锚点链接``：点击链接，可以快速定位到页面中的某个位置<br>1.在链接文本的href属性中，设置属性值为#名字的形式，如：&lt;a href="#two"&gt;第2集&lt;/a&gt;<br> 2.找到目标位置标签，里面添加一个id属性=刚才的名字，如：&lt;a id="two"&gt;第2集介绍&lt;/a&gt; |
| E-mail链接 | 点击E-mail连接后，浏览器会打开系统默认的E-mail程序，打开一封新的电子邮件，href属性由“mailto”和E-mail地址组成。<br />&lt;a href="mailto:onejftop@onejftop.com"&gt;联系我们&lt;/a&gt; |

## 表格标签

```html
<table>
    <tr>
        <th>表头1</th>
        <th>表头2</th>
    </tr>
    <tr>
        <td>数据1</td>
        <td>数据2</td>
    </tr>
</table>
```

| 标签 | 说明 |
| --- | --- |
| &lt;tr&gt;&lt;/tr&gt; | 用于定义表格中的行，必须嵌套在&lt;table&gt;&lt;/table&gt;标签中。 |
| &lt;th&gt;&lt;/th&gt; | ``表头``，一般位于表格的第一行或第一列，表头单元格中的文本内容加粗居中显示。 |
| &lt;td&gt;&lt;/td&gt; | 用于定义表格中的单元格，必须嵌套在&lt;tr&gt;&lt;/tr&gt;标签中。 |

| 表格属性 | 属性值 | 说明 |
| --- | --- | --- |
| algin | left、center、right | 规定表格相对周围元素的对齐方式 |
| border | 1或"" | 规定单元格是否拥有边框，默认为""，表示没有边框 |
| cellpadding | 像素值 | 规定单元边沿与其内容之间的空白，默认1像素 |
| cellspacing | 像素值 | 规定单元格与单元格之间的空白，默认2像素 |
| width | 像素值或百分比 | 规定表格的宽度 |
| height | 像素值或百分比 | 规定表格的高度 |

### 合并单元格

#### 跨行合并单元格

```
rowspan="合并单元格的个数"
```

#### 跨列合并单元格

```
colspan="合并单元格的个数"
```

#### 目标单元格（写合并代码）

跨行：最上侧单元格为目标单元格，写合并代码<br />
跨列：最左侧单元格为目标单元格，写合并代码

#### 合并单元格三部曲

1. 确定是跨行还是跨列
2. 找到目标单元格，写上合并方式=合并单元格的数量，比如：&lt;td colspan="2"&gt;&lt;/td&gt;
3. 删除多余的单元格

## 列表标签

列表可以分为三大类：有序列表、无序列表、自定义列表。

### 有序列表

```html
<ol>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ...
</ol>
```

### 无序列表

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ...
</ul>
```

### 自定义列表

自定义列表使用场景：常用于对术语或名词进行解释和描述，定义列表的列表项前没有任何项目符号。  
&lt;dl&gt;标签用于定义描述列表（或定义列表），该标签会与&lt;dt&gt;（定义项目/名字）和&lt;dd&gt;（描述每一个项目/名字）一起使用。

```html
<dl>
    <dt>名词1</dt>
    <dd>名词1解释1</dd>
    <dd>名词1解释2</dd>
</dl>
```

## 表单标签

在HTML中，一个完整的表单通常由**表单域**、**表单控件（也称为表单元素）**、**提示信息**3个部分构成。  
**表单域**是一个包含表单元素的区域，在HTML中，&lt;form&gt;标签用于定义表单域，以实现用户信息的收集和传递。

| 表单域常用标签 | 属性值 | 作用 |
| --- | --- | ---|
| action | url地址 | 用于指定接收并处理表单数据的服务器程序的url地址 |
| method | get/post | 用于设置表单数据的提交方式 |
| name | 名称 | 用于指定表单的名称，以区分同一个页面中的多个表单域 |

| 表单控件 | 属性值 | 作用 |
| --- | --- | --- |
| &lt;input type="属性值" /&gt; |  |  |
| &lt;select&gt;&lt;/select&gt; |  | 下拉列表，提供多个选项让用户选择，节约页面空间 |
| &lt;textarea&gt; |  | 用于定义多行文本输入的控件 |
| &lt;label for=""&gt;&lt;/label&gt; |  | 为input元素定义标注，用于绑定一个表单元素，当点击一个&lt;label&gt;标签内的文本时，浏览器就会自动将焦点(光标)转到或者选择对应的表单元素上 |

### &lt;input&gt;元素

| &lt;input&gt;属性 | 属性值 | 描述 |
| --- | --- | --- |
| name | 由用户自定义 | 定义input元素的名称 |
| value | 由用户自定义 | 规定input元素的值 |
| checked | checked | 规定此input元素首次被加载时应当被选中 |
| maxlength | 正整数 | 规定输入字段中的字符的最大长度 |

| &lt;input&gt;属性的type属性的属性值 | 描述 |
| --- | --- |
| button | 定义点击按钮（多数情况下，用于通过JavaScript启动脚本） |
| checkbox | 定义复选框 |
| file | 定义输入字段和"浏览"按钮，供文件上传 |
| hidden | 定义隐藏的输入字段 |
| image | 定义图像形式的提交按钮 |
| password | 定义密码字段，该字段中的字符被掩码 |
| radio | 定义单选按钮 |
| reset | 定义重置按钮，重置按钮会清除表单中的所有数据 |
| submit | 定义提交按钮，提交按钮会把表单数据提交到服务器 |
| text | 定义单行的输入字段，用户可在其输入文本，默认宽度为为20个字符 |

### &lt;select&gt;表单元素

**语法：**
```html
<select>
    <option>选项1</option>
    <option>选项2</option>
    <option>选项3</option>
    ...
</select>
```

| &lt;option&gt;属性 | 属性值 | 描述 |
| --- | --- | --- |
| selected | selected | 设置当前选项为默认选项 |

### &lt;textarea&gt;表单元素

**语法：**
```html
<textarea rows="3" cols="20">
    文本内容
</textarea>
```

| &lt;textarea&gt;属性 | 属性值 | 描述 |
| --- | --- | --- |
| rows | 数值 | 设置文本域显示的行数 |
| cols | 数值 | 设置文本域每行中的字符 |

### &lt;label&gt;标签

**语法：**
```html
<label for="sex">男</label>
<input type="radio" name="sex" id="sex" />
```
核心：&lt;label&gt;标签的**for属性**应当与相关元素的**id属性相同**。