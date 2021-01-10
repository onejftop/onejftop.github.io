---
title: Vue.js 指令
tags:
  - Vue.js
categories:
  - 前端
abbrlink: f22eb676
date: 2020-12-30 11:37:53
---

### v-for

#### 循环普通数组

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>v-for指令 迭代普通数组</title>
</head>

<body>
    <div id="app">
        <ul>
            <li v-for="(item,i) in list">
                ---每一项值：{{item}}<br />
                ---索引值：{{i}}
            </li>
        </ul>
    </div>

    <script src="vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                list: [1, 2, 3, 4, 5]
            }
        })
    </script>
</body>
```

#### 循环对象数组

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        <ul>
            <li v-for="(name,i) in listObj">
                ---每一项id值：{{name.id}}<br />
                ---每一项name值：{{name.name}}<br /> 
                ---索引值：{{i}}              
            </li>
        </ul>
    </div>

    <script src="vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                listObj: [
                    { id: 1, name: "张三" },
                    { id: 2, name: "李四" },
                    { id: 3, name: "王五" }
                ]
            }
        })
    </script>
</body>

</html>
```

#### 循环对象

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        <ul>
            <li v-for="(val,key,i) in student">
                ---值是：{{val}}<br />
                ---键是：{{key}}<br />
                ---索引是：{{i}}
            </li>
        </ul>
    </div>

    <script src="vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                student: {
                    id: 1,
                    name: "张三",
                    sex: "男"
                }
            }
        })
    </script>
</body>

</html>
```

