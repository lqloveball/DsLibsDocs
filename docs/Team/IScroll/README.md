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
### less 方式编写
``` css
#要进行滚动容器 {
   position: relative; left: 0px; top: 0px;width:640px;height:1040px;overflow: hidden;

   #要进行滚动容器 .scrollBox{position: absolute;top:0px;left:0px;width: 100%;}

   //如果需要改变滚动条颜色等 进行设置
   .iScrollVerticalScrollbar{
       position: absolute;z-index: 9999;width: 7px;bottom: 2px;top: 2px;right: 2px;
       overflow: hidden;

       .iScrollIndicator{
         box-sizing: border-box;
         position: absolute;left:top: 0px; 0px;width: 100%;height: 308px;transition-duration: 0ms;display: block;
         border: 1px solid rgba(255, 255, 255, 0.9);
         border-radius: 3px;
         background: rgb(255, 0, 0);
       }
     }
}

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
    useTransform: true,
    useTransition: true,
    probeType:3,
  });
```


### config参数说明

```js
scrollbars                false 实现需要滚动条，参数设置`'custom'` 可以设置滚动条的样式
hScroll                   false 禁止横向滚动 true横向滚动 默认为true
vScroll                   false 精致垂直滚动 true垂直滚动 默认为true
hScrollbar                false 隐藏水平方向上的滚动条
vScrollbar                false 隐藏垂直方向上的滚动条
fixedScrollbar            在iOS系统上，当元素拖动超出了scroller的边界时，滚动条会收缩，设置为true可以禁止滚动条超出。scroller的可见区域。默认在Android上为true， iOS上为false
fadeScrollbar             false 指定在无渐隐效果时隐藏滚动条  节省资源
interactiveScrollbars     false 指此属性可以让滚动条能拖动，用户可以与之交互。
hideScrollbar             在没有用户交互时隐藏滚动条 默认为 true
shrinkScrollbars          当在滚动区域外面滚动时滚动条是否可以收缩到较小的尺寸。有效的值为：'clip' 和 'scale'。
bounce                    启用或禁用边界的反弹，默认为true
momentum                  启用或禁用惯性，默认为true，此参数在你想要保存资源的时候非常有用
lockDirection             false 取消拖动方向的锁定， true拖动只能在一个方向上（up/down 或者left/right）
useTransform              默认情况下引擎会使用 CSS transform 属性。如果现在还是2007年，那么可以设置这个属性为 false，这就是说：引擎将使用top/left属性来进行滚动。
useTransition             iScroll使用CSS transition来实现动画效果（动量和弹力）。如果设置为false，那么将使用requestAnimationFrame代替。在现在浏览器中这两者之间的差异并不明显。在老的设备上transitions执行得更好。
HWCompositing             true 这个选项尝试使用translateZ(0)来把滚动器附加到硬件层，以此来改变CSS属性。在移动设备上这将提高性能，但在有些情况下,你可能想要禁用它(特别是如果你有太多的元素和硬件性能跟不上)。
freeScroll                false 需要2个维度同时滚动时候使用
invertWheelDirection      false 是否反向滚动
mouseWheel                false 侦听鼠标滚轮事件。
preventDefault            true 当事件触发时是否执行preventDefault()。此属性应该设置为true，除非你真的知道你需要怎么做。
scrollX、scrollY           默认情况下只有纵向滚动条可以使用。如果你需要使用横向滚动条，需要将scrollX 属性值设置为 true。
tap                       true 设置此属性为true，当滚动区域被点击或者触摸但并没有滚动时，可以让iScroll抛出一个自定义的tap事件。如下
                            //element.addEventListener('tap', doSomething, false); //原生
                            //$('#element').on('tap', doSomething); //jQuery

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
