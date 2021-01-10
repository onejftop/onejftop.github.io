---
title: Android 网络编程
tags:
  - Android
categories:
  - Android
abbrlink: d424e4f7
date: 2020-12-19 17:42:32
---

## 使用HTTP访问网络

### 使用HttpURLConnection

获取HttpURLConnection的实例，一般只需new出一个URL对象，并传入目标的网络地址，然后调用openConnection()方法即可。

```java
URL url = new URL("https://www.baidu.com");
HttpURLConnection connection = (HttpURLConnection) url.openConnection();
```

```java
// 设置HTTP请求所使用的方法
connection.setRequestMethod("GET");
// 设置连接超时毫秒数
connection.setConnectTimeout(8000);
// 设置读取超时毫秒数
connection.setReadTimeout(8000);
```

调用getInputStream()方法获取服务器返回的输入流 

```java
InputStream is = connection.getInputStream();
```

调用disconnect()方法将HTTP连接关闭

```java
connection.disconnect();
```

### OKHttp

#### **添加依赖库**

方式一：

```
Open Module Settings---Dependencies---<All Modules>--- + ---Library Dependency
```

方式二：

```
implementation 'com.squareup.okhttp3:okhttp:4.8.0'
```

#### 使用步骤

**创建OkHttpClient对象**

```
// 方式一：默认构造
OkHttpClient client = new OkHttpClient();

// 方式二：
OkHttpClient client = new OkHttpClient.Builder().build();
```

**创建Request对象**

```
Request request = new Request.Builder().build();
```

**将Request对象封装为Call**

```
Call call = client.newCall(request);
```

**通过Call来执行同步或异步请求，调用execute方法同步执行，调用enqueue方法异步执行**

```
// 同步请求，返回Response，会抛出IO异常
Response response = call.execute();

// 异步请求，并设置回调方法
call.enqueue(new Callback(){
	@Override
    public void onFailure(@NotNull Call call, @NotNull IOException e) {
		// 失败调用
    }

    @Override
    public void onResponse(@NotNull Call call, @NotNull final Response response) throws IOException {
		// 成功调用
    }
});
```

注意：1.同步请求会阻塞主线程，一般不适用

​		    2.异步请求的回调方法是在子线程里的，我们不能在子线程更新UI，需要借助于 runOnUiThread() 方法或者 Handler 来处理

#### Get请求

```java
public void getRequest(){
	OkHttpClient client = new OkHttpClient();
    Request request = new Request.Builder()
        .url()
        .build();
    // 将Request封装成call
    Call call = client.newCall(request);
    // 执行call，异步请求
    call.enqueue(new Callback(){
        @Override
    	public void onFailure(@NotNull Call call, @NotNull IOException e) {
			// 失败调用
    	}

    	@Override
    	public void onResponse(@NotNull Call call, @NotNull final Response response) throws IOException {
			// 成功调用
    	}
    });
}
```

#### Post请求

```java
public void postRequest(){
    OkHttpClient client = new OkhttpClient();
    Request request = new Request.Builder
        .url()
        .
}
```



## 解析XML格式数据



## 解析JSON格式数据

