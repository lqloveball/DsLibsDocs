
### 核心主要学习点

data  数据对象

methods 方法

v-on  等同于 @

v-bind  等同 ：

components 很重要一个属性 子组件


### 组件之间通信

vm.prop   事件机制，子组件传递事件给父组件
vm.$emit( event, […args] )  组件触发事件
vm.$on( )  监听组件发送事件
vm.$disptch()   派发时间，事件沿父链冒泡  v1.0 以后已经放弃使用
vm.$barodcast()  广播时间，事件向下传递所有的后代 v1.0 以后已经放弃使用

#### 父亲组件给子组件传递参数 prop

```
//子组件
Vue.component('child', {
  // 声明 props
  props: ['message'],
  // 就像 data 一样，prop 可以用在模板内
  // 同样也可以在 vm 实例中像“this.message”这样使用
  template: '<span>{{ message }}</span>'
})

//在父组件内 这时候1 是一个 string
<child message="1"></child>

//动态传递参数   这时候1 是一个 number
<child v-bind:message="1"></child>

```
!> prop是当向的，所以prop数据值请不要在子组件内进行修改，所以如果需要对prop需要修改

```js
props: ['initialCounter'],
data: function () {
  return { counter: this.initialCounter }
}
```

```js
props: ['size'],
computed: {
  normalizedSize: function () {
    return this.size.trim().toLowerCase() 
  }
}
```


#### 子组件发送事件给父组件

```

//父亲组件内嵌入的子组件标签  监听子组件的postData事件  触发父亲的childPostData方法
<component-child v-on:postData="childPostData"></component-child>

//父亲组件方法里面
methods:{
  childPostData(e){
    console.log(e);
  }
}

//子组件内

this.$emit('postData','我是子组件发送了一个数据给出来')

```
