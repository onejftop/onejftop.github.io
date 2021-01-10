---
title: Android 服务
tags:
  - Android
categories:
  - Android
abbrlink: 3b7e57a8
date: 2020-12-19 17:42:32
---

## 服务的创建

```
选中程序包名，右击选择【new】——【Service】——【Service】
```

### 注册服务

AndroidManifest.xml
```xml
<application ...>
    ...
    <!-- name属性表示服务的路径，
         enabled属性表示系统是否能够实例化该服务，
         exported属性表示该服务是否能够被其他应用程序中的组件调用或者进行交互。
    -->
    <service
        android:name=".MyService"
        android:enabled="true"
        android:exported="true">
    </service>
    ...
</application>
```

## 服务的生命周期

服务的生命周期与启动服务的方式有关，服务的启动方式有2种：一种是通过startService()方法启动，另一种是通过bindService()方法启动。使用不同的启动方式启动服务，其生命周期会不同。

### 通过startService()方法启动服务的生命周期

```
onCreate()、onStartCommand()、onDesstroy()
```

### 通过bindService()方法启动服务的生命周期

```
onCreate()、onBind()、onUnbind()、onDestory()
```

### 方法说明

| 方法 | 说明 |
| --- | --- |
| onCreate() | 第一次创建服务时执行的方法 |
| onStartCommand() | 调用startService()方法启动服务时执行的方法 |
| onBind() | 通过调用bindService()方法启动服务时执行的方法 |
| onUnBind() | 调用unBindService()方法断开服务绑定时执行的方法 |
| onDestory() | 服务被销毁时执行的方法 |