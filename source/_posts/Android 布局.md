---
title: Android 布局
tags:
  - Android
categories:
  - Android
abbrlink: 19af2497
date: 2020-12-19 17:42:32
---

## ConstraintLayout（约束布局）

| 属性 | 值 | 说明 |
| --- | --- | --- |
| android:layout_width  | match_parent、wrap_content | 必须属性，设置布局宽度     |
| android:layout_height | match_parent、wrap_content | 必须属性，设置布局高度     |

| ConstraintLayout子控件属性 | 值 | 说明 |
| --- | --- | --- |
| 


## LinearLayout(线性布局)

| 属性                  | 值                         | 说明             |
| :-------------------- | -------------------------- | ---------------- |
| android:layout_width  | match_parent、wrap_content | 设置布局宽度     |
| android:layout_height | match_parent、wrap_content | 设置布局高度     |
| android:layout_weight |                            | 设置布局权重     |
| android:orientation   | vertical、horizontal       | 设置布局排列方向 |

## RelativeLayout(相对布局)

定义：通过相对定位的方式指定子控件的位置。

| 属性                  | 值                         | 说明         |
| --------------------- | -------------------------- | ------------ |
| android:layout_width  | match_parent、wrap_content | 设置布局宽度 |
| android:layout_height | match_parent、wrap_content | 设置布局高度 |

### RelativeLayout中子控件的属性：

| 属性                             | 值   | 说明                                     |
| -------------------------------- | ---- | ---------------------------------------- |
| android:layout_centerParent      |      | 设置当前控件位于父布局的中央位置         |
| android:layout_centerVertical    |      | 设置当前控件位于父布局的垂直居中位置     |
| android:layout_centerHorizontal  |      | 设置当前控件位于父布局的水平居中位置     |
| android:layout_above             |      | 设置当前控件位于某控件上方               |
| android:layout_below             |      | 设置当前控件位于某控件下方               |
| android:layout_toLeftOf          |      | 设置当前控件位于某控件左侧               |
| android:layout_toRightOf         |      | 设置当前控件位于某控件右侧               |
| android:layout_alignParentTop    |      | 设置当前控件是否与父控件顶端对齐         |
| android:layout_alignParentLeft   |      | 设置当前控件是否与父控件左对齐           |
| android:layout_alignParentRight  |      | 设置当前控件是否与父控件右对齐           |
| android:layout_alignParentBottom |      | 设置当前控件是否与父控件底端对齐         |
| android:layout_alignTop          |      | 设置当前控件的上边界与某控件的上边界对齐 |
| android:layout_alignBottom       |      | 设置当前控件的下边界与某控件的下边界对齐 |
| android:layout_alignLeft         |      | 设置当前控件的左边界与某控件的左边界对齐 |
| android:layout_alignRight        |      | 设置当前控件的右边界与某控件的右边界对齐 |

## FrameLayout(帧布局)

定义：帧布局用于在屏幕上创建一块空白区域，添加到该区域中的每个子控件占一帧，这些帧会一个一个叠加在一起，后加入的控件会叠加在上一个控件上层。默认情况下，帧布局的所有控件会与左上角对齐。

| 属性                      | 值            | 说明                                         |
| ------------------------- | ------------- | -------------------------------------------- |
| android:layout_width      |               |                                              |
| android:layout_height     | wrap_perent、 |                                              |
| android:foreground        |               | 设置帧布局容器的前景图像(始终在所有控件之上) |
| android:foregroundGravity |               | 设置前景图像显示的位置                       |

