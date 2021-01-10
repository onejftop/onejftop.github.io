---
title: Vue.js 组件
abbrlink: 43050d17
date: 2020-12-20 20:51:40
tags:
  -Vue.js
categories:
  - 前端
excerpt:
  - 组件是构成页面中独立结构单元，能够减少重复代码的编写，提高开发效率，降低代码之间的耦合程度，使项目更易于维护和管理。
---

> 组件是构成页面中独立结构单元，能够减少重复代码的编写，提高开发效率，降低代码之间的耦合程度，使项目更易于维护和管理。组件主要以页面结构的形式存在，不同组件也具有基本交互功能，根据业务逻辑实现复杂的项目功能。

## 组件的基本使用

### Vue.extend():

1.创建组件构造器对象

```javascript
// 1.创建组件构造器对象，传入template代表我们自定义组件的模板
const cpnC = Vue.extend({
	template: '<div><h2>22</h2></div>'
})
```

2.注册组件

```javascript
// 全局注册组件，第一参数：组件标签名，第二个参数：组件构造器对象
Vue.component('my-cpn', cpnC)

const app = new Vue({
	el: '#app',
    // 局部注册组件
    components: {
        // cpn：组件标签名，cpnC：组件构造器对象
    	cpn: cpnC
    }
})
```

3.使用组件

```html
<div id="app">
	<!-- 使用组件 -->
    <my-cpn></my-cpn>
</div>
```

### 语法糖写法:Vue.component():

```javascript
Vue.component('cpn', {
	template: '<div><h2>22</h2></div>'
})
```





