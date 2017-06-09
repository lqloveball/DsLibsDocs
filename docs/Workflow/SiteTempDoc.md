>通用项目模板代码结构剖析，更清楚知道什么样H5活动适合使用通用项目模板进行开发。

#### 项目模板环境配置说明

>  ##### webpack配置说明

详细配置查看`webpack.config.js`文件

1. 入口文件配置会根据开发项目文件 `./src/` 目录下所有 `*.js` 文件都会被设别成入口文件。
2. 输出文件配置 输出js会在 开发项目文件`./js/app/` 目录下。对应H5网站的`./js/app/`目录
3. 设置了一些常用`require`时候的别名如 `ds` 等同 `./src/Ds` 、`app` 等同 `./src/app`
```js
  require('ds/ui/PopLayer.min');
  //等同于
  require('./src/Ds/ui/PopLayer.min');
```
4. 当前webpack配置支持vue `vue-loader`
5. 当前webpack配置支持ES6 `babel-loader`
6. 当前配置 `url-loader` 资源加载 图片base64压缩，设置是 小于`<10k`图片文件会被压缩进js
7. 为了方便调试 定位bug ，`devtool`设置是 `#eval`

!>`更多查看webpack.config.js文件 内alias参数配置`

-------

>  ##### gulp配置

1. gulp 的开发任务命令 `webpack-dev` 。请在命令行工具内输入
``` js
gulp webpack-dev
```
2. 会运行`browserSync`服务，进行监听文件的变化 自动刷新多端浏览器。方便测试。
3. css编译使用`gulp-less`编译。使用`gulp-lazyimagecss` 为设置`background`为图片背景的元素 自动添加css宽高。 `gulp-less`只编译`项目开发文件\less\`目录下的 less 文件


#### 项目模板文件结构
```
--assets/               //资源目录，如flash动画资源
--css/                  //编译后css的样式文件目录
--js/                   //js代码目录
    |-libs/             //需要引用的第三方代码目录
    |-app/              //webpack编译完成的js代码文件目录
--images/               //项目图片资源目录
--less/                 //less源代码目录
    |-libs/             //less代码库目录
    |-main.less         //less入口文件
--src/                  //项目源文件目录
    |-main.js           //程序入口文件
    |-Ds/               //Ds代码库目录
    |-libs/             //第三方代码库目录
    |-app/              //项目逻辑代码目录
        |-AppMain.js       //项目主模块
        |-APIManager.js    //接口模块
        |-LoadModel.js     //loading模块
```

#### 项目模板代码结构

>  ##### src/main.js 入口文件

**。构建H5网站模块 `SiteModel`,这里代码基本无需修改。修改配置设置网站类型，<br/>**
`SiteModel.Devicer` 设备判断，具体内容查看 `Ds.gemo.Devicer 类的实例`<br/>
`SiteModel.AppMain` 网站的单页面应用主模块 `app/AppMain.js 类的实例`<br/>
`SiteModel.LoadModel` 网站的loading模块 `app/LoadModel.js 类的实例`<br/>
`SiteModel.Debug` 判断是本地测试环境`Boolean`<br/>
`SiteModel.SiteResizeModel` 自适应模块 `Ds.SiteMoblieResizeModel  类的实例`<br/>
`SiteModel.LoadPanel` loading界面 `DOM 或者 createjs的MovieChilp`<br/>
`SiteModel.CJSModel` createjs项目模块 `Ds.createjs.CCJSModel 类的实例`<br/>
`SiteModel.AudioAutoPlayLister` 声音管理器 `Ds.media.MobileAudioAutoPlayLister 类的实例`<br/>
`SiteModel.ReSize` 进行自适应计算方法`Function`<br/>
`SiteModel.ShowProgress` 加载进度方法`Function`<br/>
`SiteModel.HitLoadPanel` 隐藏加载界面方法`Function`<br/>
`SiteModel.IsWeixin` 是否微信`Boolean`<br/>
`SiteModel.IsIOS` 是否IOS`Boolean`<br/>
`SiteModel.IsMobile` 是否手机端`Boolean`<br/>
`SiteModel.Pager` 页面跳转管理器 `Ds.gemo.SitePageManagerr 类的实例`<br/>
`SiteModel.APIer` 项目的接口模块 `app/APIManager.js 类的实例`<br/>


!>详细内容看文件代码注释与源文件代码实现逻辑

-----

>  ##### src/app/AppMain.js 单页面程序主模块

`SiteModel.AppMain` 单页面程序主模块 以下称 `AppMain`<br/>

- `AppMain.Init` 当页面程序初始化方法`Function`<br/>

?> AppMain.Init 方法里面进行设置默认微信分享  加载资源处理  页面初始化数据处理（如：作品页面链接 上作品id参数识别判断处理）

- `AppMain.LoadMainAssets` 开始加载页面资源方法，需要根据需要自行实现`Function`<br/>

?> AppMain.LoadMainAssets 这里进行处理项目需要进行初始化加载资源逻辑

- `AppMain.GotoPage` 页面跳转控制`Function`<br/>

?> AppMain.GotoPage 页面跳转处理 页面PV监测  ，特殊页面跳转逻辑页面这里来处理

- `私有方法 InitModels` 进行项目`页面模块`或者`数据模块`初始化

```js
//初始化项目模块
function InitModels() {
  //隐藏loading 界面
  SiteModel.HitLoadPanel();
  //添加一个页面模块  首页
  _Pager.Add(require('app/HomePage'));
  // _Pager.Add(require('app/Page1'));
  // _Pager.Add(require('app/Page2'));
  // _Pager.Add(require('app/Page3'));
  //跳转进入首页
  GotoPage('HomePage');
}
```


!>详细内容看文件代码注释与源文件代码实现逻辑


-----

>  ##### src/app/APIManager.js 程序接口模块

`SiteModel.APIer` 是整个项目接口管理对象。这里会完成 微信分享接口 、数据提交 、分享回流等处理


!>详细内容看文件代码注释与源文件代码实现逻辑

-----

>  ##### src/app/LoadModel.js 程序loading模块

`SiteModel.LoadModel` 网站loading界面具体实现类，关于网站loading实现 修改在这个类里面去修改 实现。


!>详细内容看文件代码注释与源文件代码实现逻辑

-----

#### 项目模板打包结构说明
  - `js/app/main.js`<br/>
    *
    src/Ds/gemo/Devicer.js 设备判断管理<br/>
    src/app/LoadModel.js 加载进度条模块<br/>
    *
  - `js/app/base.js`<br/>
    *
    src/libs/base/zepto.min.js dom选择器<br/>
    src/Ds/EventDispatcher.js 事件实现类<br/>
    src/Ds/SiteMoblieResizeModel.js H5自适应屏幕类<br/>
    src/Ds/gemo/QuickTrack.js 快速添加检测代码类<br/>
    src/Ds/media/MobileAudioAutoPlayLister.js 背景声音管理类<br/>
    *
  - `js/app/vendors1.js`<br/>
    *
    src/libs/shrek/jstween.min.js 运动引擎<br/>
    *
  - `js/app/vendors2.js`<br/>
    *
    src/libs/shrek/jstween.min.js 运动引擎<br/>
    src/libs/createjs/createjs0.8.2.min.js createjs框架<br/>
    src/Ds/createjs/DsCreatejs.js createjs Ds扩展工具集框<br/>
    *
  - `js/app/AppMain.js` <br/>
    *
    src/libs/touch/touchjs.min.js 手势管理<br/>
    src/app/APIManager.js 分享接口 数据提交接口  作品回流接口管理<br/>
    src/Ds/ui/PopLayer.min.js 通用alert提示框<br/>
    src/Ds/gemo/SitePageManager.js 页面跳转管理<br/>
    src/app/\*\*/?.js 其他项目逻辑代码<br/>
-----

#### 子页面代码模板 

Atom 编辑器代码片段 `具体使用请百度 Atom编辑器代码片段设置`,
``` js
'通用项目模板 页面模块代码片段':
    'prefix': 'wpjs'
    'body': """
            /**
             * $3
             * @type {[Class]}
            **/
            function $1(){
              var _Self=this;
              //页面名称
              this.name='$1';
              //事件继承
              // Ds.Extend(this, new Ds.EventDispatcher());
              //主模块
              var _AppMain=SiteModel.AppMain;
              //如果有用到 createjs 部分代码
              var _Root, _Stage, _CJSModel;
              if(SiteModel.CJSModel){
                //createjs
                _CJSModel=SiteModel.CJSModel;
                _Root = _CJSModel.Root;
                _Stage = _CJSModel.Stage;
              }

              //页面进场
              this.MovieIn=function(){
                $2
              };
            }
            module.exports=new $1();
            """
```
!> 请编辑器如何设置快速代码片段，请 百度 或者 google
