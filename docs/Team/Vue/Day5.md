!> 注意 使用vuex的`mutations`的`...mapMutations`进行方式会出现编译错误

npm需要进行重装
```
rm -rf node_modules
rm package-lock.json
npm cache clean

//可以以上执行完成后 使用 cnpm install
npm install
```

### 状态管理

简单可以不使用vuex ，一般用在独立 局部的状态对象

复杂点全局的状态使用vuex


#### mutations

使用vuex的方法调用在`mutations`里面定义，通过`store.commit`来调用，`store.commit`类似事件一样机制

!> mutations 内是同步执行的函数，异步使用actions

#### actions
