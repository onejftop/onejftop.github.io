---
title: Android 解析异步消息处理机制
tags:
  - Android
categories:
  - Android
abbrlink: 3a46110f
date: 2020-12-19 17:42:32
---

Android中异步消息处理主要有4个部分组成：Message、Handler、MessageQueue和Looper。

## Message

Message是在线程之间传递消息，它可以在内部携带少量的信息，用于在不同线程之间交换数据。

## Handler

Handler主要用于发送和处理消息。发送消息一般是使用Handler的sendMessage()方法，而发出的消息经过一系列地辗转处理后，最终会传递到Handler的handleMessage()方法中。

## MessageQueue

MessageQueue是消息队列的意思，它主要用于存放所有通过Handler发送的消息。这部分消息会一直存在于消息队列中，等待被处理。每个线程只会有一个MessageQueue对象。

## Looper

Looper是每个线程中的MessageQueue的管家，调用Looper的loop()方法后，就会进入到一个无限循环当中。然后每当发现MessageQueue中存在一条消息，就会将它取出，并传递到Handler的handleMessage()方法中。每个线程只会有一个Looper对象。


## 异步消息处理流程

首先需要在主线程中创建一个Handler对象，并重写handleMessage()方法。然后当子线程中需要进行UI操作时，就创建一个Message对象，并通过Handler将这条消息发送出去。之后这条消息会被添加到MessageQueue的队列中等待被处理，而Looper则会一直尝试从MessageQueue中取出待处理消息，最后分发会Handler的handleMessage()方法中。由于Handler是在主线程中创建的，所以此时的handleMessage()方法中的代码也会在主线程中运行（UI操作）。