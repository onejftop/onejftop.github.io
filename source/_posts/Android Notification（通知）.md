---
title: Android Notification（通知）
tags:
  - Android
categories:
  - Android
abbrlink: f86dcab6
date: 2020-12-19 17:42:32
---

## 基本用法
1.需要一个NotificationManager来对通知进行管理，可以调用Context的getSystemService()方法获得,getSystemService()方法接受一个字符串参数用于确定获取系统哪个服务。
```java
NotificationManager manager = (NotificationManager)getSystemService(NOTIFICATION_SERVICE);
```

2.使用Builder构造器来创建Notification对象
```java
Notification notification = new NotificationCompat.Builder(this)
                        // 指定通知的标题内容
                        .setContentTitle("这是标题")
                        // 指定通知的正文内容
                        .setContentText("这是内容")
                        // 指定通知被创建的时间，以毫秒为单位
                        .setWhen(System.currentTimeMillis())
                        // 设置通知的小图标（只能使用纯alpha图层的图片进行设置），小图标显示在系统状态栏上
                        .setSmallIcon(R.mipmap.ic_launcher)
                        // 设置通知大图标，当下拉系统状态栏时可见
                        .setLargeIcon(BitmapFactory.decodeResource(getResources(),R.mipmap.ic_launcher))
                        .build();
```


3.调用NotificationManager的notify()方法,notify接受两个参数，第一个参数是id，第二个参数是Notification对象
```java
manager.notify(1,notification);
```