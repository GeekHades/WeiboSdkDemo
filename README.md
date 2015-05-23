## 概述

这是新浪微博官方 Android SDK Demo 使用 Android Studio 导入、编译并运行通过的版本。

官方项目请点击: [weibo_android_sdk](https://github.com/sinaweibosdk/weibo_android_sdk)，当前版本 V3.0.1。

## 说明

在使用 Android Studio 导入新浪微博 SDK 时，遇到了一些问题，通过查看官方项目的 Issues 及 Google 后终于将问题解决，记录下来仅供参考。

## 运行环境

- Android Studio 1.2.1.1
- Android SDK 22
- JDK 1.7
- Gradle 2.2.1

请根据自己的开发环境修改 build.gradle 的配置。

## 使用说明

其实没什么好说的，直接拿来导入到 Android Studio 里用就行了，主要是根据 Demo 参考一下 SDK 的用法。

## Project 说明

官方项目中有两个 Project：

- WeiboSDK
- WeiboSDKDemo

WeiboSDKDemo 中引用了 WeiboSDK，我们在自己的实际项目中引用 WeiboSDK 即可。

## 问题及解决

官方项目导入到 Android Studio 后，WeiboSDK 没什么问题，问题主要出现在 WeiboSDKDemo，具体如下：

### jniLibs

需要在src\main目录下创建jniLibs目录，并将原 WeiboSDKDemo 中 libs 目录下三个文件夹及其中 so 文件拷贝至 src\main\jniLibs

### 图片资源报错

编译时，会有一个 png、三个 .9.png 报错。

一个png：修改后缀为 jpg 后，用 PhotoShop 将背景处理为透明再保存为 png 格式。

三个.9.png：在 Android Studio 直接打开，然后重新处理一下。（.9.png制作请 Google）

### 编译错误 com.android.dex.DexException: Multiple dex files define

Windows：用 Winrar 等压缩工具直接打开 weibosdkcore.jar，找到 com/sina/weibo/sdk/BuildConfig 并将其删除。

Mac OS：据 Issues里说用 Mac 自带的解压、压缩工具会有问题，请自己尝试。

### debug.keystore

如果不设置 debug.keystore，Demo App 可以成功运行，但是不能授权、分享，会有 sso package error 的报错。

设置方法：

1.选中 Project 根目录点击 F4 打开 Project Structure，选中 Modules 下面的 app, 再点击右边的Signing，点击绿色‘+’按钮，然后进行设置。如下图：

![Signing](https://github.com/CoderHanXin/WeiboSdkDemo/blob/master/screenshot/001.jpg?raw=true)

2.再选中 Build Types，并选择 Signing Config，如下图：

![BuildTypes](https://github.com/CoderHanXin/WeiboSdkDemo/blob/master/screenshot/002.jpg?raw=true)

## 版权

所有版权信息请参考官方项目: [weibo_android_sdk](https://github.com/sinaweibosdk/weibo_android_sdk)

## Thanks

- [weibo_android_sdk](https://github.com/sinaweibosdk/weibo_android_sdk)

- [Issues45](https://github.com/sinaweibosdk/weibo_android_sdk/issues/45)

- [Issues58](https://github.com/sinaweibosdk/weibo_android_sdk/issues/58)

