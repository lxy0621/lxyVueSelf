# vue 2.0 + 3.0 学习记录



## 一.vue简介

### MVVM

mvvm是vue实现数据驱动视图和双向绑定的核心原理，mvvm指的是Model,View和ModelView,它把每个html页面都拆分成了这三个部分，在MVVM概念中：

Model 表示当前页面渲染时所依赖的数据源。

View表示当前页面所渲染的DOM结构。

ViewModel表示vue实例，他是MVVM的核心。

### vue的两个特性

1.数据驱动视图

2.数据双向绑定

​	在网页中，form表单负责采集数据，ajax负责提交数据

​	页面上的表单采集的数据发生变化的时候，会被vue自动获取到，并更新到js数据中



### 基础结构

```js
    <div id="app">{{ message }}</div>

    <script src="./../js/vue 2.6.14.js"></script>
    <script>
        const vm = new Vue({
            el:'#app',
            data:{
                message:"lxy"
            }
        })
    </script>
```



## 二.vue的指令与过滤器

### 1.指令的概念

是vue为开发者提供的模板语法，用于辅助开发者渲染页面的基础结构。按照不同用途，分为6大类：

1.内容渲染指令；

​	1.v-text   2.{{}} (插值表达式，不会覆盖原有内容，用的最多)  3.v-html（带html标签渲染）

2.属性绑定指令;

​	v-bind    简写为：“ : ” 动态绑定值

3.事件绑定指令;

​	v-on : @     (data 中的 this === const vm = new Vue 中的vm)

​	常见的DOM原生事件（onclick oninput onkeyup 都可以 @click @input @keyup 绑定）

**$event:原生DOM事件对象e**

```js
<button @click="addCount(1,$event)">+1</button>
<button @click="addCount(-1,$event)">-1</button>

addCount(num,e) {
   this.count += num
   if(this.count % 2 == 0){
       e.target.style.backgroundColor = 'red'
   }else{
       e.target.style.backgroundColor = ''
   }
}
```

```js
@click.prevent="show"
等同于
show(){
   e.preventDefault()
   console.log('跳转了')
}								来阻止默认事件
```

**.prevent : 阻止默认事件**

**.stop:阻止事件冒泡**

.capture:以捕获模式触发当前的事件处理函数

.once:绑定的事件只触发一次

.self:只有在event.target是当前元素自身时触发事件处理函数


4.双向绑定指令;

​	v-model 表单元素使用

​	.number 自动将用户输入的值转为数值类型

​	.trim自动过滤用户输入的首尾空白符

​	.lazy在“change”时而非"input"时更新



5.条件渲染指令;

​	

​	v-if 原理：每次动态创建或移除元素，实现元素的显示与隐藏  

​	v-show 原理：动态为元素添加或移除display:none样式，来实现元素的显示与隐藏



6.列表渲染指令;



​	v-for

```js
<!-- v-for : 只要用到v-for 就一定绑定 :key 属性 尽量把id作为key的值 且key的值要求为字符串或number型 key的值不能重复-->

<div class="animal">
    <div v-for="(item,index) in animal" :title="item.id">{{ index }} -- {{ item.name }}</div>
</div>

animal:[
  {id:0,name:'狗'},
  {id:1,name:'猫'},
  {id:2,name:'鱼'},
  {id:3,name:'猪'},
]
```

























