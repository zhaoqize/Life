title: Weex的原生开发实践
tags:
  - weex
categories: 原生开发
date: 2017-11-21 15:54:00
---
> ![](http://images2017.cnblogs.com/blog/743207/201708/743207-20170815160450475-868670826.png)

<!--more-->

## weex概念与特性

---

最形象的理解就是类似`react native`。

Weex几大特点：
**1.帮助你构建原生应用**
与 Web App、HTML5 App 或 hybrid App 不同，您可以使用 Weex 构建一个真正的原生应用。更贴心的是你的代码只需使用 HTML、CSS、JavaScript 可以构建原生应用，上手非常简单。但实际上，应用的底层是 Objective-C 或 Java， 同时，Weex 提供很多 native 组件或模块供开发人员使用。
**2.一次编写，多端运行**
Weex 提供强大的跨平台能力，可以使用相同的 API 开发 Web，Android 和 iOS 应用。 同时，我们对接口了丰富的扩展能力。 这样，当您需要扩展原生组件或模块时，这将非常方便。
**3.支持 Vue 语法**
Weex 遵循 Web 标准，同时支持 vue.js 的语法。因此，您可以使用 vue.js 语法来开发应用程序

## weexpack

---

weexpack 是新一代的weex应用工程和插件工程开发套件，是基于weex快速搭建应用原型的利器。它能够帮助开发者通过命令行创建weex应用工程和插件工程，快速打包 weex 应用并安装到手机运行，对于具有分享精神的开发者而言还能够创建weex插件模版并发布插件到weex应用市场。 使用weexpack 能够方便的在在weex工程和native工程中安装插件。
具体介绍见：https://github.com/weexteam/weex-pack

## 原生开发之路

---

### 创建工程
首先，全局安装weexpack
```bash
$ npm install -g weexpack
```
然后，创建工程
```bash
weexpack create weexpack-demo
```
安装依赖
```bash
cd weexpack-demo && npm install
```
生成的目录结构如下：
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174407459-1509340459.png" width = "300" height = "400" alt="图片名称"/>

### 添加平台应用模版
*我这里添加的是Android
```bash
 $ weexpack platform add android
```
添加成功后platforms目录下会多出一个`android`目录
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174501459-458584613.png" width = "300" height = "400" alt="图片名称"/>

### 调试
这里的调试我们可以通过https://weex.apache.org/cn/guide/tools/toolkit.html的方法来进行调试。
这个调试分两种：
在浏览器上进行网页调试
通过Playground 在手机上扫描调试
但是这两种感觉Biger不够，我想要开发原生应用的free-使用真机来调试。

### 真机开发调试
这里就需要用到Android Studio了，下载AS，安装JDK，配置环境变量这是前置步骤。
这里就不再赘述这些流程了，我相信你可以（网上很多教程）。
当前置的步骤全部完成时，我们就要开始进入大坑了。
**1.第一个坑**
weex推荐使用weex run android命令来运行起安卓应用，但是很快会报错<font style="color:red">No android devices found.</font>
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174721256-1719922365.png" width = "300" height = "300" alt="图片名称"/> 
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174731131-1238833548.png" width = "300" height = "340" alt="图片名称"/>

Chrome中开的服务是可以的
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174816068-498806253.png" width = "250" height = "400" alt="图片名称"/>

你可能会疑问，我已经通过USB链接了手机为何还是不行？这个坑一般会耽误你一天左右时间。

> 解决方案：使用Android Studio打开我们的weex应用。

**2.第二个坑**
使用AS打开应用的时候没有发现Android应用
![](http://images2017.cnblogs.com/blog/743207/201708/743207-20170815174931771-1892114307.png)

> 解决方案：应该打开weex下的platforms/android。具体可以看：https://segmentfault.com/q/1010000010652802

选择安卓文件后，AS需要安装很多东西，稍等下，一般较长时间。报错信息只要按照AS的提示进行安装即可。
等一切完毕后，运行安卓项目。
![](http://images2017.cnblogs.com/blog/743207/201708/743207-20170815175030834-468703614.png)

手机上的效果

<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815175054178-855894297.jpg" width = "250" height = "400" alt="图片名称"/> <img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170815175108490-2025679706.png" width = "250" height = "400" alt="图片名称"/>

### 模拟器开发调试并自动热更新
这篇文章[Android Studio集成到Genymotion模拟器](http://www.cnblogs.com/zqzjs/p/7411361.html)已经告诉了我们如何集成模拟器

在我们的weex项目中运行下面这个命令，将会将`native JSbundle`替换成新的。
```bash
$ weexpack run android

...
:weexplugin:compileDebugShaders
:weexplugin:generateDebugAssets
:weexplugin:mergeDebugAssets
:weexplugin:mergeDebugProguardFiles
:weexplugin:packageDebugRenderscript UP-TO-DATE
:weexplugin:processDebugJavaRes UP-TO-DATE
:weexplugin:transformResourcesWithMergeJavaResForDebug UP-TO-DATE
:weexplugin:transformClassesAndResourcesWithSyncLibJarsForDebug UP-TO-DATE
:weexplugin:mergeDebugJniLibFolders UP-TO-DATE
:weexplugin:transformNativeLibsWithMergeJniLibsForDebug UP-TO-DATE
:weexplugin:transformNativeLibsWithSyncJniLibsForDebug UP-TO-DATE
:weexplugin:bundleDebug UP-TO-DATE
:weexplugin:compileDebugSources UP-TO-DATE
:weexplugin:assembleDebug UP-TO-DATE
:weexplugin:compileReleaseSources
:weexplugin:assembleRelease
:weexplugin:assemble

BUILD SUCCESSFUL

Total time: 7.404 secs
 => Install app ...
 => Running app ...
```
这时候在AS中会提示你有代码需要同步。
![](http://images2017.cnblogs.com/blog/743207/201708/743207-20170824141200168-617594644.png)

点击同步后，模拟器自动更新。
<img src="http://images2017.cnblogs.com/blog/743207/201708/743207-20170824141259589-1835922169.png" width = "250" height = "400" alt="图片名称"/>