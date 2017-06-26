### 代码示例

#### html

```
<div class="要进行滚动容器">
  <div class="scrollBox">
      这个容器是被滚动，注意这个容器内部如果没有高就不会滚动
  </div>
</div>
```

#### css

```css
#要进行滚动容器 {
   position: relative; left: 0px; top: 0px;width:640px;height:1040px;overflow: hidden;
}
#要进行滚动容器 .scrollBox{position: absolute;top:0px;left:0px;width: 100%;}
```


#### js


```js
var _myScroll = new IScroll($('要进行滚动容器')[0],
{
    scrollX: false,
    scrollY: true,
    click:true,
    scrollbars: false ,
    // ,interactiveScrollbars: true
    useTransform: false,
    useTransition: false,
    probeType:3,
  });
```


### config参数说明

```js
hScroll                   false 禁止横向滚动 true横向滚动 默认为true
vScroll                   false 精致垂直滚动 true垂直滚动 默认为true
hScrollbar                false 隐藏水平方向上的滚动条
vScrollbar                false 隐藏垂直方向上的滚动条
fixedScrollbar            在iOS系统上，当元素拖动超出了scroller的边界时，滚动条会收缩，设置为true可以禁止滚动条超出。scroller的可见区域。默认在Android上为true， iOS上为false
fadeScrollbar             false 指定在无渐隐效果时隐藏滚动条
hideScrollbar             在没有用户交互时隐藏滚动条 默认为true
bounce                    启用或禁用边界的反弹，默认为true
momentum                  启用或禁用惯性，默认为true，此参数在你想要保存资源的时候非常有用
lockDirection             false取消拖动方向的锁定， true拖动只能在一个方向上（up/down 或者left/right）
```


### 方法

```js
myScroll.refresh();               刷新滚动条状态
refresh()                         在DOM树发生变化时，应该调用此方法
scrollTo()                        滚动到某个位置
如: myscroll.scrollTo(0,10,200,true);
scrollToElement()                 滚动到某个元素
如: myscroll.scrolToElement("li:nth-child(10)",100);
detroy()                          完全消除myscroll及其占用的内存空间
```


### 事件处理

```js
myScroll.on('scrollEnd', doSomething);
```


* beforeScrollStart, executed as soon as user touches the screen but before the scrolling has initiated.
* scrollCancel, scroll initiated but didn't happen.
* scrollStart, the scroll started.
* scroll, the content is scrolling. Available only in scroll-probe.js edition. See onScroll event.
* scrollEnd, content stopped scrolling.
* flick, user flicked left/right.
* zoomStart, user started zooming.
* zoomEnd, zoom ended.
