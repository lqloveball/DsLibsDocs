列出常用的一些内容

### 全局配置

- ##### `Vue.config.keyCodes` 配置按键

```js
Vue.config.keyCodes = {
  v: 86,
  f1: 112,
  // camelCase 不可用
  mediaPlayPause: 179,
  // 取而代之的是 kebab-case 且用双引号括起来
  "media-play-pause": 179,
  up: [38, 87]
}
```
### 全局API

- ##### `Vue.extend`  构建一个Vue扩展对象
- #####  `Vue.component` 注册一个Vue的组件 或者也能用来获取一个Vue的组件
- ##### `Vue.use` 插件制作 会进行控制只会注册一次插件 ，插件必须提供`install`方法
- ##### `Vue.mixin`  全局混合方法进去 ，一般不会这么去做

### 数据

- #####`data` 只要记住组件使用的话，data必须是function来实现

```js
Vue.extend({
  data: function () {
    return { a: 1 }
  }
})
```

-  ##### `props` 用来接收来自父组件的数据

```js
// 简单语法
Vue.component('props-demo-simple', {
  props: ['size', 'myMessage']
})
// 对象语法，提供校验
Vue.component('props-demo-advanced', {
  props: {
    // 只检测类型
    height: Number,
    // 检测类型 + 其他验证
    age: {
      type: Number,
      default: 0,
      required: true,
      validator: function (value) {
        return value >= 0
      }
    }
  }
})
```

-  #####  `computed` 计算方式获取到属性
-  #####  `methods`  方法指令，共有方法写到这里
-  #####  `watch`  用来监听数据的变化

```js
var vm = new Vue({
  data: {
    a: 1,
    b: 2,
    c: 3
  },
  watch: {
    a: function (val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal)
    },
    // 方法名
    b: 'someMethod',
    // 深度 watcher
    c: {
      handler: function (val, oldVal) { /* ... */ },
      deep: true
    }
  }
})
vm.a = 2 // -> new: 2, old: 1
```
-  #####  `el` 提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标
-  #####  `template` 模板将会 替换 挂载的元素
-  #####  `directives` 模包含 Vue 实例可用指令的索引。
-  #####  `components` vue子组件的索引
-  #####  `mixins` 混合对象的数组
-  #####  `extends` 允许声明扩展另一个组件
-  #####  `delimiters` 改变纯文本插入分隔符。 这个选择只有在独立构建时才有用。
```js
new Vue({
  delimiters: ['${', '}']
})
```
-  #####  `vm.$data` Vue 实例观察的数据对象。Vue 实例代理了对其 data 对象属性的访问。
-  #####  `vm.$props`
-  #####  `vm.$el`  Vue 实例使用的根 DOM 元素。
-  #####  `vm.$options`   Vue 实例的初始化选项
-  #####  `vm.$parent`   父实例，如果当前实例有的话。
-  #####  `vm.$root`   当前组件树的根 Vue 实例。如果当前实例没有父实例，此实例将会是其自已。
-  #####  `vm.$children`   当前实例的直接子组件。
-  #####  `vm.$slots`   用来访问被 slot 分发的内容。每个具名 slot 有其相应的属性（例如：slot="foo" 中的内容将会在 vm.$slots.foo 中被找到）。
-  #####  `vm.$scopedSlots`   用来访问 scoped slots。对于包括 默认 slot 在内的每一个 slot， 该对象都包含一个返回相应 VNode 的函数。
-  #####  `vm.$refs`   一个对象，其中包含了所有拥有 ref 注册的子组件。
-  #####  `vm.$watch`   观察数据的变化
-  #####  `vm.$on`   监听当前实例上的自定义事件 事件可以由`vm.$emit`触发
-  #####  `vm.$once`   监听一个自定义事件，但是只触发一次，在第一次触发之后移除监听器。
-  #####  `vm.$off`   移除自定义事件监听器。
-  #####  `vm.$emit`   触发当前实例上的事件。附加参数都会传给监听器回调。
-  #####  `vm.$mount`   挂载
-  #####  `vm.$forceUpdate()`   迫使Vue实例重新渲染。注意它仅仅影响实例本身和插入插槽内容的子组件，
-  #####  `vm.$nextTick`   将回调延迟到下次 DOM 更新循环之后执行。
-  #####  `vm.$destroy()`  完全销毁一个实例。清理它与其它实例的连接，解绑它的全部指令及事件监听器。

### 指令

- #####  `v-text`

```html
<span v-text="msg"></span>
<!-- 和下面的一样 -->
<span>{{msg}}</span>
```

- #####  `v-html`
- #####  `v-show` 根据表达式之真假值，切换元素的 display CSS 属性。
- #####  `v-if` 根据表达式的值的真假条件渲染元素。在切换时元素及它的数据绑定 / 组件被销毁并重建。如果元素是 <template> ，将提出它的内容作为条件块。
- #####  `v-else` 前一兄弟元素必须有 v-if 或 v-else-if。
- #####  `v-else-if` 前一兄弟元素必须有 v-if 或 v-else-if。
- #####  `v-for` 基于源数据多次渲染元素或模板块

```html
<div v-for="item in items">
  {{ item.text }}
</div>
//或者
<div v-for="(item, index) in items"></div>
<div v-for="(val, key) in object"></div>
<div v-for="(val, key, index) in object"></div>
```
- #####  `v-on` 事件绑定

https://cn.vuejs.org/v2/api/#v-on

- #####  `v-bind` 数据的绑定


https://cn.vuejs.org/v2/api/#v-bind

- #####  `v-model` 只是表单 input select textarea 或者自定义components 使用
- #####  `v-pre` 跳过这个元素和它的子元素的编译过程。 **这不明白 需要之后再学习**
- #####  `v-cloak` 这个指令保持在元素上直到关联实例结束编译 **这不明白 需要之后再学习**
- #####  `v-once` 只渲染元素和组件一次。随后的重新渲染,元素/组件及其所有的子节点将被视为静态内容并跳过。
- #####  `ref` 子组件索引
https://cn.vuejs.org/v2/guide/components.html#子组件索引
- #####  `slot` 用于标记往哪个slot中插入子组件内容。
- #####  `component` 渲染一个“元组件”为动态组件。依 is 的值，来决定哪个组件被渲染。
- #####  `transition` 元素作为单个元素/组件的过渡效果 需要css知识
- #####  `transition-group`
