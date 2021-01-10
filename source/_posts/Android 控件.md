---
title: Android 控件
tags:
  - Android
categories:
  - Android
abbrlink: aa9d3452
date: 2020-12-19 17:42:32
---

## TextView

用于在界面显示文字

| 属性                  | 值                                                           | 说明                                 |
| --------------------- | ------------------------------------------------------------ | ------------------------------------ |
| android:id            | @+id/id名                                                    | 控件唯一标识                         |
| android:layout_width  | match_parent、wrap_content、xdp                              | 必须属性，布局宽度                             |
| android:layout_height | match_parent、wrap_content、xdp                              | 必须属性，布局高度                             |
| android:text          |                                                              | 控件显示文本                                    |
| android:textSize      | xsp                                                          |                                      |
| android:textStyle     | bold、                                                       |                                      |
| android:gravity       | center、top、botton、left、right、center_vertical、center_horizontal | 指定文字对齐方式                     |
| android:background    |                                                              |                                      |
| android:ellipsize     | start(省略号显示在开头)、end(省略号显示在结尾)、middle(省略号显示在中间)、marquee(以横向滚动方式显示) | 当文字超过Textview的宽度时的显示方式 |

## EditText

| 属性              | 值  |     说明       |
| ----------------- | ------------------------------------------ | ---------- |
| android:id            | @+id/id名                                                    | 控件唯一标识                         |
| android:layout_width  | match_parent、wrap_content、xdp                              | 必须属性，布局宽度                             |
| android:layout_height | match_parent、wrap_content、xdp                              | 必须属性，布局高度                             |
| android:hint      |                                            | 输入框提示 |
| android:inputType | number、numberPassword、text、textpassword | 输入类型   |
|                   |                                            |            |

## ImageView

| 属性              | 值                                                           | 说明 |
| ----------------- | ------------------------------------------------------------ | ---- |
| android:src       |                                                              | 图片 |
| android:scaleType | fitXY、fitCenter、fitStart、fitEnd、center、centerCrop、centerInside、matrix |      |
|                   |                                                              |      |

### ScaleType属性

| 值           | 说明                                                      |
| ------------ | --------------------------------------------------------- |
| fitXY        | 横向、纵向独立缩放，以适应该ImageView                     |
| fitCenter    | 保持纵横比缩放图片，缩放完成后将图片放在ImageView的中央   |
| fitStart     | 保持纵横比缩放图片，并且将图片放在ImageView的左上角       |
| fitEnd       | 保持纵横比缩放图片，缩放完成后将图片放在ImageView的右下角 |
| center       | 把图片放在ImageView的中央，但是不进行任何缩放             |
| centerCrop   | 保持纵横比缩放图片，以使图片能完全覆盖ImageView           |
| centerInside | 保持纵横比缩放图片，以使得ImageView能完全显示该图片       |
| matrix       | 使用matrix方式进行缩放                                    |

## ScrollView


## RecyclerView

### 添加依赖库

```
implementation 'androidx.recyclerview:recyclerview:1.2.0-alpha06'
```

### 布局代码

```xml
<androidx.recyclerview.widget.RecyclerView
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```

### 适配器

#### 定义内部类

```java
static class ViewHolder extends RecyclerView.ViewHolder{
	public ViewHolder(View view){
        super(view);
    }
}
```

#### 重写3个方法

```java
@Override
public ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
    View view = LayoutInflater.from((parent.getContext()).inflate(R.layout.布局文件名,parent,false);
    ViewHolder holder = new ViewHolder(view);
    return holder;
 }

@Override
public void onBindViewHolder(@NonNull ViewHolder holder, int position) {

}

@Override
public int getItemCount() {
     return 0;
 }
```

- onCreateViewHolder()：用于创建 Viewholder 实例，并把加载的布局传入到构造方法中，在把 Viewholder 实例返回。
- onBindViewHolder()：用于对子项的数据进行赋值,会在每个子项被滚动到屏幕内时执行。
- getItemCount()：返回RecyclerView的子项数目。