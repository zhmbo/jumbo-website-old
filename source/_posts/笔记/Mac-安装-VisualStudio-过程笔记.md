---

title: Mac-安装-VisualStudio-过程笔记
date: 2016-07-20 15:00:00
tags: 笔记
<!--mathjax: true-->
---
![](http://upload-images.jianshu.io/upload_images/1874013-1e43d71a7fe6c011.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240 )

> 此过程安装时间 2017年3月22日。(部分内容参考[这篇文章](http://www.cnblogs.com/math/p/install-visualstudio-mac.h))

## 一、 准备工作

### 先到官网下载 Visaul Studio 安装包
#### [Visual Studio 官网下载地址](https://www.visualstudio.com/vs/visual-studio-mac/)

### 点击下载 Visual Studio For Mac 预览版

![](http://upload-images.jianshu.io/upload_images/1874013-cc9f0303926cb3db.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 双击 Visual Studio For Mac Preview Installer

![](http://upload-images.jianshu.io/upload_images/1874013-b2fe48b984c93bae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 按步骤点击 Accept

![](http://upload-images.jianshu.io/upload_images/1874013-061a8a307424afff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 来到这里等上一会

![](http://upload-images.jianshu.io/upload_images/1874013-4d703bbff2919fe2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 不管是否翻墙都会弹出这个安装失败的窗口（如果弹其他非安装成功的窗口请关掉重新双击安装程序），让我们手动逐个安装下面的包

![](http://upload-images.jianshu.io/upload_images/1874013-f1b298aba0b8955d.gif?imageMogr2/auto-orient/strip)
## 二、手动安装

### 1. 安装 Mono Framework
- 下载好按提示一顿 Next 就行了。
- 安装路径：/Library/Frameworks/Mono.framework/

![](http://upload-images.jianshu.io/upload_images/1874013-dedd2670196fd73a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2. 安装 JDK，Mac自带的不是官方的，装个最新版JDK也好
- 命令行下 `javac -version` 弹出对话框点击过去下载最新版JDK MacOS 版，一顿 Next 就行了
- 安装完成后，再次运行javac -version，正确显示JDK版本号
- 运行/usr/libexec/java_home得到JDK的安装路径
- 安装路径:/Library/Java/JavaVirtualMachines/jdk1.8.0_121.jdk/Contents/Home

![](http://upload-images.jianshu.io/upload_images/1874013-19121e24da86e6e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/1874013-4f6143ef8b7f3d3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3. 配置 Android 环境，分别下载 Android SDK 和 Android NDK
- SDK 
	- 将下载好的 `android-sdk-macosx` 手动拷贝到 VS 要求的目录(见下图)
	- 安装路径：/Users/xxx/Library/Developer/Xamarin/android-sdk-macosx/
- NDK 
	- 下载的NDK文件名为 `android-ndk-r10e-darwin-x86_64.bin` 需终端解压
	- cd 到.bin所在目录下 
	- 命令下 `chmod +x ./android-ndk-r10e-darwin-x86_64.bin`
 	- 命令下 `./android-ndk-r10e-darwin-x86_64.bin` 解压，手动拷贝到Android SDK同级目录
 	- 安装路径：/Users/xxx/Library/Developer/Xamarin/android-ndk-r10e/

![](http://upload-images.jianshu.io/upload_images/1874013-2852f884c562e4ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/1874013-0ca1b8701f86efbd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4. 安装 Xamarin 的开发框架
- 分别下载按步骤安装，一顿 Next 就行了
- xamarin.android 
	- 安装路径：/Library/Frameworks/Xamarin.Android.framework/
- xamarin.ios
	- 安装路径：/Library/Frameworks/Xamarin.iOS.framework/
- xamarin.mac
	- 安装路径：/Library/Frameworks/Xamarin.Mac.framework/

![](http://upload-images.jianshu.io/upload_images/1874013-c2feb7087c8fc76b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 5. 最后下载 Visual Studio For Mac Preview 的离线包
- 双击安装，直接拖到应用程序目录下

![](http://upload-images.jianshu.io/upload_images/1874013-2a30e798fc071ba5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 6. 如果你需要开发 .NET Core 要自己装下
- [.NET Core for Mac](https://www.microsoft.com/net/core#macos)


# Hello World

## 一、新建一个简单的 iOS 程序

1. 点击 new project
![](http://upload-images.jianshu.io/upload_images/1874013-9703e1b280d281c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 选择项目模板
![](http://upload-images.jianshu.io/upload_images/1874013-00c2349d63719cc3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 配置项目基本信息
![](http://upload-images.jianshu.io/upload_images/1874013-c11cb8ac261f36d6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 选择项目存储路径并创建
![](http://upload-images.jianshu.io/upload_images/1874013-d991815e7d913689.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. 双击选择 Main.storyboard 
![](http://upload-images.jianshu.io/upload_images/1874013-5765b5d4c39b1931.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. 熟悉的九宫格
![](http://upload-images.jianshu.io/upload_images/1874013-f6008b49f10171e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

7. 拽一个 UILabel
![](http://upload-images.jianshu.io/upload_images/1874013-f1e187e532cebe03.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

8. 设置 label 属性
![](http://upload-images.jianshu.io/upload_images/1874013-5aeca3be175ddf89.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

9. 添加约束
![](http://upload-images.jianshu.io/upload_images/1874013-1186081c20ce3244.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

10. 选择设备 Run
![](http://upload-images.jianshu.io/upload_images/1874013-25fb0ebaeecb1180.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

11. 模拟机效果图<br>
![](http://upload-images.jianshu.io/upload_images/1874013-fcf46124de1d4787.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

12. 双击选中 ViewController.cs 文件，代码添加 UIAlertView
![](http://upload-images.jianshu.io/upload_images/1874013-30b1e5194bb8eebc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

13. 模拟机效果图<br>
![](http://upload-images.jianshu.io/upload_images/1874013-1a5257eaf4f5b59b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 二、新建一个简单的 Android 程序

可以设置语言和主题
![](http://upload-images.jianshu.io/upload_images/1874013-59f7308054dbb7be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 注意！此处有坑
- 若果找不到需手动指定 SDK JDK NDK 路径，JDK 和 NDK 能找到，
但是 唯独 SDK ,在我电脑上明明指对了，就是找不到，后来我自己
有安装了 Android Studio 下载的 SDK 直接覆盖了这个就找到了。
如果不想安装 Android Studio 可以去官网下载一个 SDK 然后把这个
覆盖就 OK 了。
![](http://upload-images.jianshu.io/upload_images/1874013-73d90401cf1e5e1f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


1. new project
![](http://upload-images.jianshu.io/upload_images/1874013-69cf8807a6d30f78.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 选择项目模板
![](http://upload-images.jianshu.io/upload_images/1874013-672350af8d8eab92.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 配置项目基本信息
![](http://upload-images.jianshu.io/upload_images/1874013-e3f65bea82fdcffb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 选择项目存储路径并创建
![](http://upload-images.jianshu.io/upload_images/1874013-e556012fef025540.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. 运行程序到手机
![](http://upload-images.jianshu.io/upload_images/1874013-7f17e14102a52b19.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. 真机效果图<br>
![](http://upload-images.jianshu.io/upload_images/1874013-38c04d4f417ddf37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 总结
###### 此文记录安装 Visual Studio 的详细过程。

***
> ***曾经有一份真诚的爱情放在我面前，我没有珍惜，等我失去的时候我才后悔莫及，人世间最痛苦的事莫过于此。 
<br>
如果上天能够给我一个再来一次的机会，我会对那个女孩子说三个字：我爱你。 
<br>
如果非要在这份爱上加上一个期限，我希望是…… 
<br>
一万年                                                     
 — —  周星驰 《大话西游》***
