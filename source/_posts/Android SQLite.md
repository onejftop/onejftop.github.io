---
title: Android SQLite
tags:
  - Android
categories:
  - Android
abbrlink: '50145819'
date: 2020-12-19 17:42:32
---

## 数据类型

| 数据类型 | 说明       |
| -------- | ---------- |
| integer  | 整形       |
| real     | 浮点型     |
| text     | 文本类型   |
| blob     | 二进制类型 |
| null     | 零         |

## SQLiteOpenHelper抽象类

| 抽象方法    | 说明 |
| ----------- | ---- |
| onCreate()  |      |
| onUpgrade() |      |

| 实例方法              | 说明                                                         |
| --------------------- | ------------------------------------------------------------ |
| getReadableDatabase() | 当数据库不可写入的时候，该方法返回的对象将以只读的方式打开数据库 |
| getWritableDatabase() | 当数据库不可写入的时候，该方法则出现异常                     |

注：这两个方法都可以创建或打开一个现有的数据库（如果数据库已经存在则直接打开，否则创建一个新的数据库），并返回一个可对数据库进行读写操作的 对象。

| 构造方法                                                     | 参数说明                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| public MyDatabaseHelper(@Nullable Context context, @Nullable String name, @Nullable SQLiteDatabase.CursorFactory factory, int version) | 1:Context；2.数据库名；3.允许我们在查询数据的时候返回一个自定义的Cursor，一般传入null；4.当前数据库版本号 |
|                                                              |                                                              |

## SQLiteDatabase

数据库访问类，我们可以通过该类的对象对数据库做一些增删改查操作。

| 方法     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| insert() | 向表增加数据，接收3个参数，1：表名、2：用于在未指定添加数据的情况下给某些可为空的列自动赋值为Null，一般传入Null、3：ContentValues对象，它提供一系列的put()方法重载，用于向ContentValues中添加数据，只需将表中的每个列名及相应待添加的数据传入即可。 |
| update() | 对表数据进行更新，接收4个参数，1：表名、2：ContentValues对象，把要更新的数据在这里组装进去、3&4：用于约束更新某一行或某几行中的数据，不指定的话默认更新所有行 |
| delete() | 对表数据进行删除，接收3个参数，1：表名、2&3：用于约束删除某一行或某几行中的数据，不指定的话默认删除所有行 |
| query()  | 查询数据，至少7个参数，1：表名、2：指定去查询哪几列，如不指定则默认查询所有列、3&4：用于约定查询某一行或某几行的数据，不指定则默认查询所有行的数据、5：用于指定需要去group by的列，不指定则表示不对查询结果进行group by操作。6：用于对group by之后的数据进行进一步的过滤，不指定则表示不进行过滤。7：用于指定查询结果的排列方式，不指定则表示使用后默认的排列方式。 |

## 数据库升级



# adb调试工具

adb调试工具位于：C:\Users\用户名\AppData\Local\Android\Sdk\platform-tools（默认sdk安装路径）

配置环境变量：将adb的路径配置到环境变量中

命令行

| 命令             | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| adb shell        | 进入设备控制台，#表示超级管理员，$表示普通管理员，可使用 su 切换超级管理员 |
| cd               | 切换目录                                                     |
| ls               | 查看当前目录下的所有文件                                     |
| sqlite3 数据库名 | 打开数据库                                                   |
| .table           | 查看当前数据库有哪些表                                       |
| .schema          | 查看建表语句                                                 |
| .exit            | 退出数据库的编辑                                             |
| .quit            | 退出数据库的编辑                                             |
| exit             | 退出设备控制台                                               |

# SQLite数据库框架——Litepal

## 配置Litepal

### 引入库

```
implementation 'org.litepal.guolindev:core:3.2.2'
```

### 配置litepal.xml文件

右击app/src/main——new——Directory，创建assets目录，然后在其目录下创建 litepal.xml。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<litepal>
    <!--数据库名称-->
    <dbname value="BookStore"></dbname>
    <!--数据库版本号-->
    <version value="1"></version>
    <!--指定指定所有的映射模型-->
    <list>
    	<mapping class="实体类完整路径"></mapping>
    </list>
</litepal>
```

## 增删改查

LitePal进行CRUD操作时，必须继承 LitePalSupport

### 增

```java 
Book book = new Book();
// 设置数据
book.setName("西游记");
book.setAuthor("吴承恩");
book.setPages(888);
book.save();	//保存设置的数据到表
```

### 删

```Java
//删除book表id<3的数据，如果不指定约束条件则默认删除所有数据
LitePal.deleteAll(Book.class,"id < ?","3");
```

### 改

方法一：

```java
Book book = new Book();
// 设置数据
book.setName("西游记");
book.setAuthor("吴承恩");
book.setPages(888);
book.save();	//保存设置的数据到表
book.setPages(999);
book.save();	//当前Book对象是已存储的，LitePal不会向数据库中去添加数据，而是直接更新当前数据
```

方法二：

```java
Book book = new Book();
book.setPages(999);
book.setPrice(99.9);
//指定条件约束：name="西游记"和Author="吴承恩",不指定则默认更新所有数据
book.updateAll("name = ? and Author = ?","西游记","吴承恩");
```

注意：updateAll()不能直接更新为默认值。

将数据更新为默认值

```Java
Book book = new Book();
book.setToDefault("pages");
book.updateAll();
```

### 查

```Java
List<Book> books = LitePal.findAll(Book.class);
```

