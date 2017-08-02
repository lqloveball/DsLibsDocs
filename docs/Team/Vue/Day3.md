### Vue几种入门写法

#### 创建一个Vue挂载到DOM上  ES6

```js

import Vue from 'libs/vue/vue.min.js'; //79k
var app = new Vue({
  data: {},
  el: '#app',
  render: h => h(App),
  created() {},
  watch: {},
  methods: {}
});

```
#### 直接js内编写模板
```js
var vmA = new Vue({
  el:'#app .vmA',
  template: `<div>{{ count }}</div>`,
  data: {
    privateState: {},
  },
  computed:{
    count() {
      return 'Hello~~~!'
    }
  }
});
```


#### 直接操作页面上DOM 非ES6

```html
<div class="vueLabel">
  <div class="bg"></div>
  <div class="test">{{label}}</div>
</div>
```

```js
var Vue=require('vue');//导入框架
//创建一个vue对象
var _vue=new Vue({
  el:$('.vueLabel')[0],//渲染的dom（其实应该称为挂载，对于初步认识先认为是渲染到这里）
  data:{
    label:'Hi Label!' //数据
  }
});

//来做一个数据变化 渲染测试
var _num=0;
function timeUpdata(){
  _vue.label='Hi '+_num;
  _num++;
  setTimeout(timeUpdata,1000);
}
timeUpdata();
```

#### 通过模板创建挂载到DOM上  非ES6

```html
<div id="vuePanel"></div>
```

```vue
<template lang="html">
  <div >
    {{label}}
  </div>
</template>

<script>
export default {
  data(){
    return {
      label:'张田艹'
    }
  }
}
</script>

<style lang="css">
</style>
```

```js
var _component= require('../components/Test.vue');

var _cp = new Vue({
     el: '#vuePanel',
     render:(function (createElement) {return createElement(_component);}),//render: h => h(_component),  ES6使用箭头函数来编写 h等于createElement
 });
//做个数据变化来看看
var _num1=0;
function timeUpdata1(){
 _cp.label='Hi '+_num1;
 _num1++;
 setTimeout(timeUpdata,1000);
}
timeUpdata1();
```


### 直接组件挂载到html上

```
//html
<div id="app">
  <app></app>
</div>

//js
import App from './App.vue';
var app=new Vue({
  el:'#app',
  components:{App},
});
```
