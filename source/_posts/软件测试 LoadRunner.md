---
title: LoadRunner 性能测试工具的使用
tags:
  - 软件测试
categories:
  - 软件测试
abbrlink: 34e6e9b1
date: 2021-01-08 16:58:49
---

​		Mercury LoadRunner 是一种预测系统行为和性能的负载测试工具。通过以模拟上千万用户实施并发负载及实时性能监测的方式来确认和查找问题，LoadRunner 能够对整个企业架构进行测试。通过使用LoadRunner ，企业能最大限度地缩短测试时间，优化性能和加速应用系统的发布周期。

<!-- more -->

## LoadRunner 的使用

### VuGen

> VuGen（Virtual User Generator） 在创建脚本时，VuGen会生成多个函数用于记录虚拟用户所执行的操作，并将这些函数插入到VuGen编辑器生成基本的虚拟用户脚本，这个创建脚本的过程也叫做录制脚本



#### 插入Text/Image检查点

在进行压力测试时，为了检查Web 服务器返回的网页是否正确，VuGen 允许我们插入Text/Imag 检查点，这些检查点验证网页上是否存在指定的Text 或者Imag，还可以测试在比较大的压力测试环境中，被测的网站功能是否保持正确。

**View => Steps Toolbox => 搜索(web_reg_find)**

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210108-01.png)

```
web_reg_find("Text=Welcome, <b>jojo</b>",
		LAST);
```

#### 关联

* 所谓的关联（correlation）就是把脚本中某些写死的（hard-coded）数据，转变成是撷取自服务器所送的、动态的、每次都不一样的数据。

* 举一个常见的例子，服务器在每个浏览器第一次跟它要数据时，都会在数据中夹带一个唯一的辨识码，接下来就会利用这个辨识码来辨识跟它要数据的是不是同一个浏览器。一般称这个辨识码为Session ID。对于每个新的交易，服务器都会产生新的Session ID给浏览器。这也就是为什么执行脚本会失败的原因，因为VuGen还是用旧的Session ID向服务器要数据，服务器会发现这个Session ID是失效的或是它根本不认识这个Session ID，当然就不会传送正确的网页数据给VuGen了。

web_reg_save_param_ex

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210108-02.png)

```
web_reg_save_param_ex(
		"ParamName=userSession",
		"LB=name=\"userSession\" value=\"",
		"RB=\"",
		SEARCH_FILTERS,
		LAST);
```

替换所需要的关联的数据：选中需替换的数据 => 右键 => Replace with Parameter => 选择关联的参数

#### 参数化

* 用参数表示用户的脚本有两个优点：

  –① 可以使脚本的长度变短。

  –② 可以使用不同的数值来测试你的脚本。例如，如果你企图搜索不同名称的图书，你仅仅需要写提交函数一次。在回放的过程中，你可以使用不同的参数值，而不只搜索一个特定名称的值。

* 参数化包含以下两项任务：

  –① 在脚本中用参数取代常量值。

  –② 设置参数的属性以及数据源。

选中需要参数化的值 => 右键 => Replace with Parameter => Create New Parameter

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210108-03.png)

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-01.png)

##### 参数取值相关设置

Select next row：选择下一行

* Sequential：按照参数化的数据顺序，一个个的来取。
* Random：参数化中的数据,每次随机的从中抽取数据。
* Unique ：为每个虚拟用户分配一条唯一的数据。

Update value on：更新时的值

* Each iteration ：每次迭代时取新的值。
* Each occurrence ：每次参数化时取新的值，这里强调前后两次取值不能相同。
* Once ：参数话中的数据，一条数据只能抽取一次

When out values：值不够的情况如何取值

* Abort Vuser：停止测试
* Continue in a cyclic manner：循环取值，再重新开始新一轮的unique取值
* Continue with last value：沿用最后一个值

### 场景运行器

#### 创建场景控制器方案

VuGen => 菜单栏 (Tools) => Create Controller Scenario...

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-02.png)

#### 场景运行器相关设置

##### Schedule设置：

主要是用来设置用户的行为方式

![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-03.png)

Schedule Name：场景名称

Schedule By：

* Secnario(按场景计划)

  **Initialize**：设置脚本运行前如何初始化每个虚拟用户。包含3种方式：

  ​    ![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-04.png)

   **Start Vusers** ：设置虚拟用户加载的过程（是指总的虚拟用户数）。包含2种加载方式：

  ​     ![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-05.png)

   **Duration** ：设置场景执行的时间，包含2种方式：

  ​     ![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-06.png)

   **Stop Vusers** ：设置场景执行完成后虚拟用户如何释放的策略。（只有duration设置为按指定时间运行时才需要设置该项）

  ​    ![onejftop](http://onejftop-image.test.upcdn.net/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95/20210109-07.png)

* Group(按分组计划)



