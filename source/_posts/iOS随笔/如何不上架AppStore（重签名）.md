---

title: 如何不上架AppStore（重签名）
date: 2018-05-23 10:24:40
tags: iOS随笔
<!--mathjax: true-->
---

![](https://upload-images.jianshu.io/upload_images/1874013-0abccca47208d111.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

# 前言

> 自己开发的或朋友给的 `.ipa` *or* `.app` 如何让亲朋好友安装后把玩？

那个谁把手机的UDID给我~ 
那个谁把手机拿过来我给你用 **Xcode** 装一个~ 
...
![](https://upload-images.jianshu.io/upload_images/1874013-6d12dbbae7fa1b6c.gif?imageMogr2/auto-orient/strip)

---

### 解决方案
除了上架 *App Store* 我们还可以利用 ***重签名*** 让我或者公司开发的 `app` 安装到非测试设备上，也就是本文主要内容。

### 准备工作
1、需要被重签名app、archive包、 ipa

2、$ 299 企业开发者账号 **or** 企业证书（P12文件）+ 与此证书相匹配的任意描述文件（.mobileprovision）

3、有效的证书（可以在钥匙串中查找），记录一下企业证书名称备用
![证书](https://upload-images.jianshu.io/upload_images/1874013-83d926f8e4f2f371.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

4、.mobileprovision 配置描述文件** （以下三种获得途径）

  * 存储路径：` ~/Library/MobileDevice/Provisioning Profiles` 拷贝出来重命名 `embedded.mobileprovision`

  * 可以在 **Xcode** 中找一个有效的，右键 `show in finder`，将文件复制出来，重命名为 `embedded.mobileprovision`
![描述文件](https://upload-images.jianshu.io/upload_images/1874013-997196cea01ab633.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

* 解压又当前企业账号build后的到app `显示包内容` 得到 `embedded.mobileprovision` 拷贝出来备用

![embedded.mobileprovision](https://upload-images.jianshu.io/upload_images/1874013-bfe1a8fdc5d9ffdc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
（* 注：安装包与描述文件放到同一目录下，我这里全部都放到桌面）

### 重签名 
> 新建 **Demo** 项目, 用我个人账号对编译出 **Demo.app** ，再用企业账号对 **Demo.app** 重签名。

###### 1、选择非企业开发者账号编译工程得到 **Demo.app** ，拷贝到桌面与上面得到的 `embedded.mobileprovision` 放到同一目录下

![Demo.app](https://upload-images.jianshu.io/upload_images/1874013-309d2a18bbb64415.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

`Show in Finder`

![Show in Finder](https://upload-images.jianshu.io/upload_images/1874013-cf99317230da7148.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/400)

显示包内容

![包内容](https://upload-images.jianshu.io/upload_images/1874013-1c227219d0125f7a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/400)

将 *准备工作* 的第4步中 `embedded.mobileprovision` 拷贝到这里进行替换

###### 2、 生成 `entitlements.plist` 文件
先通过“security”命令，从 `mobileprovision` 文件中生成一个完整的 plist 文件
命令 :  `security cms -D -i "mobileprovision文件" > "entitlements文件"  `
![命令-1](https://upload-images.jianshu.io/upload_images/1874013-cb02850c9a40e7f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)

得到结果：
![](https://upload-images.jianshu.io/upload_images/1874013-40db7b89e20c1059.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

我们只是为了得到里面的 `Entitlements` 字段，使用如下的命令
命令 : ` /usr/libexec/PlistBuddy -x -c 'Print:Entitlements'  tmp_entitlements.plist > Entitlements.plist `

![命令-2](https://upload-images.jianshu.io/upload_images/1874013-452af46e42c1a8c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)

得到结果：
![](https://upload-images.jianshu.io/upload_images/1874013-1409d1a6191ff678.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

###### 3、签名
命令 :  ` codesign -f -s "证书" --entitlements "entitlements文件"  "需要签名的app文件"   `
![命令-3](https://upload-images.jianshu.io/upload_images/1874013-d4f334fdd6237147.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)

新建文件夹 Payload，将 Demo.app 拷贝到文件夹 Payload 中执行命令
命令：` zip -r new_demo.ipa Payload `
![](https://upload-images.jianshu.io/upload_images/1874013-3fbb0b943044a005.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)

---
# 总结
![](https://upload-images.jianshu.io/upload_images/1874013-054b57bbcef31311.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

