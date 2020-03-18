---
title: vue 模板与指令 基础入门(一)
catalog: true
date: 2019-05-16 23:47:32
subtitle:
header-img:
tags:
  - vue
catagories:
  - vue
---

##### 入门

> vuejs，作者尤雨溪，渐进式 JavaScript 框架，轻巧，方便，通俗易懂。Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。

<!--more-->

##### 官网

> [https://cn.vuejs.org/](https://cn.vuejs.org/)

今天来学习 Vuejs 的一些指令开始，在学习指令之前必须先入门 vue 的语法模板，下面一起来学习吧！

#### 一、Vuejs 语法模板

```
<template>
    <div>
        {{ name }}
    </div>
</template>

<script>
    name: 'showName',
    data() {
        return {
            name: 'danny'
        }
    },

    methods: {
        //方法
        handleSomeThing() {
            //do something
        }
    },

    // 初始化执行
    created(){

    }
</script>

<style lang="scss" scoped>
    /* css 样式表 */
</style>
```

#### 二、文本插值

语法：两队花括号，里面是 data 里面的名称，如：{{ name }}

ShowName.vue 为例：

```
html

<section>
    <h2>{{ say }}</h2>
</section>
```

```
script

data() {
    return {
        say: "Hello World"
    }
}
```

#### 三、绑定元素特性 v-bind

动态获取 data 里的数据，渲染视图的节点上。用于接口返回的数据动态渲染页面上。

**v-bind:src 简写成 :src** ，直接省去 v-bind，很方便的语法。

```
html

<section>
    <img v-bind:src="imgPath" v-bind:title="imgInfo" v-bind:alt="imgInfo" />
</section>

```

也可简写：

```
html

<section>
    <img :src="imgPath" :title="imgInfo" :alt="imgInfo" />
</section>
```

```
script

data() {
    return {
        imgPath: "https://www.baidu.com/img/baidu_jgylogo3.gif",
        imgInfo: "百度图片地址"
    }
}
```

#### 四、条件 v-if

语法：v-if 控制一个元素是否显示，后面接的是一个布尔值。 v-if="isShow", 如果 isShow 是 true 为显示，为 false 则隐藏

> v-if 控制 h2 标签 dom 树，显示则 dom 树出现，如果**隐藏则移除该元素在 dom 的节点**(有点像 jquery 的 remove 语法)；
> v-show 的语法是控制 h2 标签，设置 display 值在 block 和 none 切换，它一直存在 dom 树上

```
html

<section>
    <h2 v-if="isShow">my Blog</h2>
    <h2 v-else>is show me?</h2>
</section>
```

```
script

data() {
    return {
        isShow: true
    }
}
```

#### 五、条件 v-show

语法：这个就是和 v-if 难兄难弟了。v-show 同时控制元素显示隐藏的，设置 display 值在 block 和 none 切换，它一直存在 dom 树上

```
html

<section>
    <h2 v-show="isShow">my Blog</h2>
</section>
```

```
script

data() {
    return {
        isShow: true
    }
}
```

#### 六、循环 v-for

语法：绑定数组的数据来渲染一个项目列表。
v-for="(item, index) in cityList"
其中

- item：循环出每一个对象放入了这个变量，后面可以直接打点引用，如：itme.id；
- index：对象的索引
- cityList: 为 data 数据里面的数组或对象了；
  > 官网提示要带上 :key 唯一关键属性，不然会警告报错的，而且使用数字和字符串类型，不要使用对象或数组类型

```
html

<section>
    <ul
        v-for="(item, index) in cityList"
        :key="index"
    >
        <li>{{itme.id}}、{{item.name}}</li>
    </ul>
</section>
```

```
script

data() {
    return {
        cityList: [
            {
                id: 1,
                name: "北京",
            },
            {
                id: 2,
                name: "上海",
            },
            {
                id: 3,
                name: "广州",
            },
            {
                id: 4,
                name: "深圳",
            },
        ]
    }
}
```

#### 八、双向绑定 v-model

语法： 多用于表单输入框的值和应用状态之间的双向绑定。

```
html

<section>
    <p>{{ name }}</p>
    <input v-model="name" />
    <!-- 输入框的值一变动，p标签的文本插值也变动了，也就是说 data里的值变动，都会受影响-->
</section>
```

```
script

data() {
    return {
        name: "danny"
    }
}
```

大家可以根据这个例子和正则表达式，写个手机号码输入空格提示框，身份证号码放大提示框，银行卡放大且每 4 个数字空格的提示框等等；

#### 九、事件 v-on

语法：添加一个事件监听器，监听事件处理的事情和逻辑

v-on:click="handleClcik" 简写: @click="handleClcik"

```
html

<section>
    <p>{{title}}</p>
    <button v-on:click="handleClcik">点我</button>
</section>
```

也可以写成：

```
html

<section>
    <p>{{title}}</p>
    <button @click="handleClcik">点我</button>
</section>
```

```
script

data() {
    return {
        title: "hello"
    }
},
methods: {
    handleClcik(){
        console.log("title的值改变了")
        this.title = "javascript"
    }
}
```
