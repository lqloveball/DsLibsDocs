----
这是关于VUE学习过程笔记

写这篇笔记目的是对自己学习一个过程记录与梳理从零学VUE的注意事项

对于开发大型的项目，框架重要性大家都清楚。React 与Vue  先撇开一堆选择争议问题，就以Vue中文社区活跃性与对中文学习友好来说，必然是首选。

从零开始的建议

### 上官方文档

[访问地址](https://cn.vuejs.org)

### 安装配置Vue开发环境

团队配置过webpack，相信对大家来说 这步不会是太大的问题

https://cn.vuejs.org/v2/guide/installation.html

### Vue的介绍

建议粗略看看，相信很多经验式学习的小伙伴们完整的也看不下去，无法完全理解 `不代表不用懂，有了经验后回头来学习`

https://cn.vuejs.org/v2/guide/index.html

### Vue 实例

建议粗略看看，有个大致的概念，特是生命周期这些对于很多小伙伴是一头雾水 `不代表不用懂，有了经验后回头来学习`

https://cn.vuejs.org/v2/guide/instance.html

主要生命周期有
- `beforeCreate` 创建前
- `created`  创建完成
- `beforeMounte` 进行装配前
- `mounted` 装配完成
- `beforeUpdate` 进行数据更新前
- `updated` 数据更新后
- `activated`
- `deactivated`
- `beforeDestroy` 进行摧毁前
- `destroyed` 摧毁完成

### 模板语法

- 文本插入
```html
  <span>Message: {{ msg }}</span>
```
- 只执行一次插入 `v-once`
```html
  <span v-once>
```
- 纯 HTML `v-html`
```html
  <div v-html="rawHtml"></div>
```

- 判断指令 `带有 v- 前缀的特殊属性`
  - v-if   判断
  - v-for  for循环
  - v-on   事件
  ```html
  <!-- 完整语法 -->
  <a v-on:click="doSomething"></a>
  <!-- 缩写 -->
  <a @click="doSomething"></a>
  ```
  - v-bind 数据绑定
  ```html
    <!-- 完整语法 -->
    <a v-bind:href="url"></a>
    <!-- 缩写 -->
    <a :href="url"></a>
  ```
### 属性计算

https://cn.vuejs.org/v2/guide/computed.html

有必要清楚 `computed`、`watch`、`methods` 适用场景

- methods 主要用来定义组件的方法
- computed  属性需要经过逻辑计算后 可以定义在计算方法属性内
- watch 用来执行数据变化 生产的异步操作与大开销的操作



### 渲染相关

建议上手 进行测试学习。这个很关键，学习Vue的目的，对于小伙伴来说这是初步基础。也属于刚开始来体验Vue的神奇之处

条件渲染
https://cn.vuejs.org/v2/guide/conditional.html

列表渲染
https://cn.vuejs.org/v2/guide/list.html

### 事件处理

交互离开不了事件，建议多练习学习

https://cn.vuejs.org/v2/guide/events.html

### 组件  `重头戏来了，组件化让工作越来越轻松`

关于以上章节都是为这部分做基础，这块学习要的时间最多。多练习都思考

https://cn.vuejs.org/v2/guide/components.html


- 组件注册 (熟读)
- 组件构成
https://cn.vuejs.org/v2/guide/components.html#构成组件
- `Prop` （建议熟读，对经验学习者不想开发自己组件可越过，但也必须思路上熟悉）
   这是组件与组件之间交互基本知识点
- `Slot` （熟读，大型项目是组件与组件搭建出来，这块建议熟读）
https://cn.vuejs.org/v2/guide/components.html#使用-Slot-分发内容
- `scope` 插槽 子组件与父组件直接配合
https://cn.vuejs.org/v2/guide/components.html#作用域插槽
