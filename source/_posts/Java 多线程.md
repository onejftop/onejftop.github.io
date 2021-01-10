---
title: Java 多线程
tags:
  - Java
categories:
  - Java
abbrlink: 3500f2c5
date: 2020-12-22 12:17:21
---

## 多线程实现

### 继承Thread类

java.lang.Thread 是一个负责线程操作的类，任何类只要继承 Thread 类就可以成为一个线程的主类。线程启动的主方法需要覆写``Thread``类中的``run()``方法实现，线程主体类格式的定义如下：

```java
Class 类名 extends Thread{
    属性...	// 类中定义属性
    方法...	// 类中定义方法
    // 覆写Thread类中的run()方法，此方法是线程的主体
    public void run(){
        线程主体方法;
    }
}
```

### 实现Runnable接口

```java
Class 类名 implements Runnable{
    @Override
    public void run() {
        
    }
}
```

```java
// 实例化多线程对象
MyThread mt = new MyThread();
// 利用Thread启动多线程
new Thread(mt).start();
```

### 利用Callable接口实现多线程

```java
class 类名 implements Callable<V> {
    @Override
    public String call() throws Exception {
        return null;
    }
}
```