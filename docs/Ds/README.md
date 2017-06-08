---

### Ds 库结构
> 关于Ds取名，一开始来源至团队的称呼。现在更多是一种愿景。

关于Ds库的分包按曾经开发as互动ixiyou库的习惯，目前主要分包情况如下

- Ds.createjs 基于createjs的canvas开发包
- Ds.createjs.display  基于createjs封装的常用交互对象包
- Ds.gemo 一些常用的算法、交互、逻辑管理模块包。
`Ds.gemo 取名时候童心作祟，gemo像无穷的宝藏。 gem->宝石 o->吃惊张大了嘴`
- Ds.media 多媒体相关模块包
- Ds.utils 判断工具、算法相关模块包
- Ds.ui 界面控件相关模块包
- Ds.net 网络交互相关模块包
- Ds.map 地图相关模块包

### 全局方法

> #### Ds.Extend

对象进行扩展赋值。支持多个对象属性继承扩展。`平时用在对类对象简单继承扩展`

> #### Ds.ExtendNoCover

对象进行扩展赋值。但对对象原有值不进行覆盖

> #### Ds.ExtendFactory

对 Function 构建的类，创建子类继承工厂方法

> #### Ds.alert

代替默认alert使用


### 索引
>基础

[Ds.EventDispatcher.js](Ds/EventDispatcher)                    事件管理类 <br/>
[Ds.SiteMoblieResizeModel.js](Ds/SiteMoblieResizeModel)         H5自适应管理<br/>

>createjs 支持

[Ds.createjs.DsCreatejs.js]()                                   createjs扩展库<br/>
[Ds.createjs.BitmapData.js]()                                   createjs进行高级位图像素计算<br/>
[Ds.createjs.CJSLoadFontsModel.js]()                            createjs进行动态特殊字体管理<br/>

~~[Ds.createjs.display.CutlineContainer.js]()                   模拟切写西瓜画线<br/>~~
[Ds.createjs.display.DrawingBoard.js]()                         画板类`（需要增强）`<br/>
~~[Ds.createjs.display.DrawingBoardSenior.js]()                 高级画板类`（需要重新思考定义）`<br/>~~
[Ds.createjs.display.Gallery360Week.js]()                       360度浏览画廊头尾衔接<br/>
[Ds.createjs.display.GalleryLooper.js]()  作品循环滚动浏览控件<br/>
[Ds.createjs.display.GalleyModel.js]()  长画幅画廊管理类<br/>
[Ds.createjs.display.HorizontalScreenAutoContainer.js]()  强制横竖屏显示容器<br/>
[Ds.createjs.display.Object369ByFrames.js]()  产品360度浏览管理<br/>
~~[Ds.createjs.display.SliderSelectionPanel.js]()  模拟IOS下Select控件`（需要重新思考定义）`<br/>~~

>快速处理宝库

[Ds.gemo.Devicer.js]()  设备类型判断<br/>
[Ds.gemo.DeviceOrientationer.js]()  陀螺仪、摇一摇<br/>
[Ds.gemo.Gesture.js]()  手势控制<br/>
[Ds.gemo.GIFBuilder.js]()  前端GIF合成处理<br/>
[Ds.gemo.GalleryAnnularLoopManager.js]()  作品循环滚动数据处理<br/>
[Ds.gemo.InputInteractive.js]()  输入交互联动`(这个类需要重新设计)`<br/>
[Ds.gemo.JT3D.js]()       使用shark的CSS3D.js进行运动简化操作<br/>
[Ds.gemo.OGerModel.js]()  陀螺仪与拖动的控制.<br/>
[Ds.gemo.PageSlider.js]()  touch平滑拖动计算<br/>
[Ds.gemo.Pano2vr45Manager.js]()  对VR 的 Pano2vr项目管理<br/>
[Ds.gemo.QueueLoad.js]()  图片队列加载管理`(这个类需要重新设计)`<br/>
[Ds.gemo.QuickTrack.js]()  快速添加检测代码  百度  GA<br/>
[Ds.gemo.requestAnimationFrame.js]()  解决requestAnimationFrame兼容问题<br/>
[Ds.gemo.SitePageManager.js]()  对项目模板的页面跳转管理<br/>
[Ds.gemo.SliderDistance.js]()  对平滑拖动距离长度的管理封装`（这个类废除，仅支持纵向.推荐使用SliderHVDistance.js）`<br/>
[Ds.gemo.SliderHVDistance.js]()  对平滑拖动距离长度的管理封装<br/>
[Ds.gemo.WebHash.js]() 对地址栏的hash路由简单管理<br/>

>快速处理宝库

[Ds.ui.PopLayer.js]() Ds.alert代替默认alert <br/>
[Ds.ui.HorizontalScreenAutoContainer.js]() DOM的强制横屏容器 <br/>
[Ds.ui.DatePickers.js]() 快速设置日期控件 <br/>
[Ds.ui.DatePickers.js]() 快速设置日期控件 <br/>
[Ds.ui.OrientationTip.js]() 竖屏提示 <br/>
~~[Ds.ui.DIVMovieClip.js]() 使用精灵图的DIV MovieChilp <br/>~~
~~[Ds.ui.PictureListBox.js]() 图片galley框，快速实现左右滑动切换图片效果内容 <br/>~~

>net 网络

[Ds.net.QuickAjax.js]() ajax数据请求 <br/>
[Ds.net.SocketModel.js]() socket.io快速管理 <br/>

>media 多媒体

[Ds.media.MobileAudioAutoPlayLister.js]() 手机背景声音与声音初始化管理 <br/>
[Ds.media.VideoInteractivePlayer.js]() H5视频互动的封装 <br/>
[Ds.media.VideoPlayerByFrames.js]() 视频互动基于序列帧 <br/>
[Ds.media.VidePlayerByMpeg.js]() 视频互动基于前端对mepg格式解析，用在andorid微信视频互动项目<br/>
[Ds.media.VidePlayerByMpegTS.js]() 视频互动基于前端对ts格式解析，用在andorid微信视频互动项目<br/>
[Ds.media.VidePlayerByVideoTag.js]() 视频互动基于video标签，用在ios微信视频互动项目<br/>

>utils 工具

[Ds.utils.ArcMath.js]() 三角函数计算 <br/>
[Ds.utils.Bezier.js]() 贝塞尔计算 <br/>
[Ds.utils.LayoutFitArea.js]() 显示区域布局计算`基本无用` <br/>
[Ds.utils.TimeUtils.js]() 时间处理类 Date 与 字符直接处理 <br/>
[Ds.utils.Utils.js]() 常用判断 <br/>

>map

[Ds.map.BMapRoutePath.js]() 百度地图计算路径 <br/>

>threejs

[Ds.threejs.LoadManager.js]() threejs加载资源管理 <br/>
[Ds.threejs.Three3DModel.js]() threejs快速搭建结构 <br/>
[Ds.threejs.ThroughSpace.js]() 穿越空间互动 <br/>
