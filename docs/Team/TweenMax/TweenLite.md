TweenLite是一个非常快速、轻量级、灵活的动画工具。TweenLite可以处对象一个或多个属性的变化。TweenLite可以自行完成大多数动画，并且它很效果。

### 使用
TweenLite 使用起来非常的简单与方便。最常用的就是 **TweenLite.to()**


对一个id为 photo的元素进行动画变化成 宽200px 高200px
```js
var photo = document.getElementById("photo");
TweenLite.to(photo, 2, {width:"200px", height:"150px"});
```

如果想要进行更方便控制dom元素的 css动画，可以引用 **CSSPlugin** ，这可以让你更快选择需要进行操作的dom与控制更多css样式的动画，如**backgroundColor**等。

```js
//可以快速通过ID进行选取 执行动画
TweenLite.to("#myID", 2, {backgroundColor:"#ff0000", width:"50%", top:"100px", ease:Power2.easeInOut});

//如果拥有jQuery 或者 Zepto，可以更高级方式进行选择 执行动画
TweenLite.to(".myClass", 2, {boxShadow:"0px 0px 20px red", color:"#FC0"});
```

也可以同时对多个元素进行动画操作

```js
TweenLite.to([obj1, obj2, obj3], 1, {opacity:0.5, rotation:45});
```

除了 **TweenLite.to()** 从当前状态运动到最终状态，还可以使用 **TweenLite.from()** 从初始化状态运动到当前状态。出此以外还能
**TweenLite.fromTo()** 设置从初始化状态到最终状态。

如果还需要使用到 **paused,play** 等还可以用面对对象写法来编写运动效果。这样可以获取到一个运动控制对象。

```js
var tween = new TweenLite(element, 2, {width:200, height:150});
//或者
var tween = TweenLite.to(element, 2, {width:200, height:150});
```

### 运动参数配置

- #### delay: `Number`
延迟开始运动的时间设置
- #### ease: `Ease` (or Function or String)
运动的方式、变化速度。如`Elastic.easeOut`,`Strong.easeInOut`,运动方式类型有`Linear, Power0, Power1, Power2, Power3, Power4, Quad, Cubic, Quart, Quint,Strong`等，具体可以参考 **`Easing`**

- #### onComplete: `Function`
运动结束后调用的方法

- #### onCompleteParams: `Array`
运动结束后调用的方法内调用的参数<br>
example:

```js
var element = document.getElementById("selectDIV");

TweenLite.to(element, 1, {left:"100px", onComplete:myFunction,onCompleteParams:[element, "param2"]});

function myFunction(value1,value2) {
  console.log(value1,value2);
}
```


如果需要传入当前这个运动对象还能如下写法 使用`"{self}"`

```js
var element = document.getElementById("selectDIV");

TweenLite.to(element, 1, {left:"100px",onComplete:myFunction,onCompleteParams:["{self}", "param2"]});

function myFunction(value1,value2) {
  console.log(value1,value2);
}
```

- #### onCompleteScope: `Object`
可以指定onComplete里面的`this`指向


- #### onReverseComplete: `Function`
一个运动已经完成并进行反向运动，如果反向运动完成后会调用
- #### onReverseCompleteParams: `Array`
反向运动完成后回调函数内的参数设置。（具体参考`onCompleteParams`）
- #### onReverseCompleteScope: `Object`
可以指定onReverseComplete里面的`this`指向


- #### onStart: `Function`
一个运动开始时候
- #### onStartParams: `Array`
一个运动开始时候回调函数内的参数设置。（具体参考`onCompleteParams`）
- #### onStartScope: `Object`
可以指定onStart里面的`this`指向



- #### onUpdate: `Function`
运动过程中的回调
- #### onUpdateParams: `Array`
运动过程中的回调函数内的参数设置。（具体参考`onCompleteParams`）
- #### onUpdateScope: `Object`
可以指定onUpdate里面的`this`指向

- #### onOverwrite: `Function`
运动被覆盖时候的回调
- #### autoCSS: `Boolean`
默认开启，如果`utoCSS:false` 那在运动参数里面进行对运动值的设置必须是`css:{}`内设置
- #### callbackScope: `Object`
设置所有的回调函数的 `this`指向

- #### useFrames: `Boolean`
如果这里设置成**true** 这里进行计算的时候就是按帧来计算而不是秒。具体的FPS的设置在根的帧设置内。
- #### lazy: `Boolean`
惰性，这个参数默认基本不需要去管。根性能相关，想深入了解可以官方查文档`可以忽略这个参数，一般很少使用到`

- #### paused: `Boolean`
是否立刻暂停之前动画运动，可以理解成是否覆盖之前动画。`可以忽略这个参数，一般很少使用到`
- #### immediateRender: `Boolean`
是否立刻开始渲染，但如果设置delay 这个设置忽略，默认是false `可以忽略这个参数，一般很少使用到`
- #### overwrite: `String` (or integer)  
默认是 `auto`,但之前对象已经在运动时候，如果在对这个对象执行运动，那运动引擎要如何处理。`可以忽略这个参数，一般很少使用到`
  - "none" (0) 忽略什么都不做
  - "all" (1) 全部覆盖
  - "auto" (2) 只有有冲突运动属性才会做覆盖
  - "concurrent" (3) 干掉所有，从当前重新开始(个人理解、有误请指出)
  - "allOnStart" (4) 干掉所有对这个对象进行运动的显示对象，只要是已经开始的运动对象(个人理解、有误请指出)
  - "preexisting" (5)理解太挠，建议自己看英文文档并尝试(个人理解、有误请指出)
### Plugins
主要是 **CSSPlugin** ，对k数要求高，不希望引入 **CSSPlugin** 。<br>
会在写法上有区别,不引入插件 对dom元素进行运动 css变化必须如下写法
```js
TweenLite.to(element, 1, {css:{top:"100px", left:"50px", backgroundColor:"#ff0000", fontSize:"12px"}, delay:0.5});
```
### Function-based values
可以动态通过逻辑进行编写运动引擎。
```js
TweenLite.to(".box", 1, {
  x: function() {
    return Math.random() * 300;
  }
});
```
参数值: index, target
  - index： 如".box" 选择器选择运动对象索引值
  - target：当前这个执行运动的对象
```js
TweenLite.to(".box", 1, {
  x: function(index, target) {
    console.log(index, target);
    return (index + 1) * 100 // 100, 200, 300
  }
})
```
### 其他
  - 运动值的编写可以使用 `"+="` or `"-="` 如：`TweenLite.to(element, 2, {left:"-=20px"});`
  - 可以设置默认运动引擎的默认运动方式 `TweenLite.defaultEase` 设置成 `Power1.easeOut`
  - 可以删除指定的对象运动执行 `TweenLite.killTweensOf("#myID");`
----
### 构造函数
  TweenLite( target:`Object`, duration:`Number`, vars:`Object` ) ;
### 属性
  #### .data : *
   设置运动的参数数据
  #### .target : Object
   [只读] 运动的对象
  #### .timeline : SimpleTimeline
   [只读] 运动时间轴队列
  #### .vars : Object
   运动过程与运动结束时候 运动变化的数据
   ### 方法
   #### .delay( value:Number ) : *
   #### .duration( value:Number ) : *
   #### .endTime( includeRepeats:Boolean ) : Number
   #### .eventCallback( type:String, callback:Function, params:Array, scope:* ) : *
   #### .invalidate( ) : *
   #### .isActive( ) : Boolean
   #### .kill( vars:Object, target:Object ) : *
   #### .pause( atTime:\*, suppressEvents:Boolean ) : \*
   #### .paused( value:Boolean ) : *
   #### .play( from:\*, suppressEvents:Boolean ) : \*
   #### .progress( value:Number, suppressEvents:Boolean ) : \*
   #### .restart( includeDelay:Boolean, suppressEvents:Boolean ) : *
   #### .resume( from:\*, suppressEvents:Boolean ) : \*
   #### .reverse( from:\*, suppressEvents:Boolean ) : \*
   #### .reversed( value:Boolean ) : *
   #### .seek( time:\*, suppressEvents:Boolean ) : \*
   #### .startTime( value:Number ) : *
   #### .time( value:Number, suppressEvents:Boolean ) : *
   #### .timeScale( value:Number ) : *
   #### .totalDuration( value:Number ) : *
   #### .totalProgress( value:Number, suppressEvents:Boolean ) : *
   #### .totalTime( time:Number, suppressEvents:Boolean ) : *
### 全局属性
-----
#### TweenLite.defaultEase : Ease
[静态方法] 全局设置运动的方式
#### TweenLite.defaultOverwrite : String = "auto"
[静态方法] 默认运动覆盖方式 默认值 "auto". 还可以设置"auto", "all", "none", "allOnStart", "concurrent", "preexisting".
#### TweenLite.onOverwrite : Function
[静态方法] 覆盖运动时候回调函数
#### TweenLite.selector : * = document.getElementById()
[静态方法] 使用的dom选择器
#### TweenLite.ticker : Object
[静态方法] 运动引擎的触发器。
```js
  //add listener
  TweenLite.ticker.addEventListener("tick", myFunction);

  function myFunction(event) {
      //executes on every tick after the core engine updates
  }

  //to remove the listener later...
  TweenLite.ticker.removeEventListener("tick", myFunction);
```
默认使用requestAnimationFrame，没有requestAnimationFrame支持的浏览器，自动会使用setTimeout来代替。<br>
可以强制使用setTimout() 代替 requestAnimationFrame
```js
TweenLite.ticker.useRAF(false);
```
如果运动时候使用帧来代替，可以设置全局的 fps
```js
TweenLite.ticker.fps(30);
```
添加对运动引擎触发器的监听
```js
addEventListener(type, callback, scope, useParam, priority)
```
1. type : String - 监听类型 "tick"
2. callback : Function - 监听执行事件函数
3. scope : Object - 回调函数内的 `this` 指向
4. useParam : Boolean - 如果是ture 一直监听  false会监听一次后取消监听 提供性能。
5. priority : Integer - 监听次数
```js
TweenLite.ticker.addEventListener("tick", myFunction, this, true, 1);

function myFunction(event) {
    //executes on every tick after the core engine updates
}

//to remove the listener later...
TweenLite.ticker.removeEventListener("tick", myFunction);
```

### 全局方法
#### TweenLite.delayedCall( delay:Number, callback:Function, params:Array , scope:\*, useFrames:Boolean ) : TweenLite
#### TweenLite.from( target:Object, duration:Number, vars:Object ) : TweenLite
#### TweenLite.fromTo( target:Object, duration:Number, fromVars:Object, toVars:Object ) : TweenLite
#### TweenLite.getTweensOf( target:\*, onlyActive:Boolean ) : Array
#### TweenLite.killDelayedCallsTo( func:Function ) :
#### TweenLite.killTweensOf( target:Object, onlyActive:Boolean, vars:Object ) :
#### TweenLite.lagSmoothing( threshold:Number, adjustedLag:Number ) :
#### TweenLite.render( ) :
#### TweenLite.set( target:Object, vars:Object ) : TweenLite
#### TweenLite.to( target:Object, duration:Number, vars:Object ) : TweenLite
