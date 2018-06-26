
title: 一键脚本搭建 SS 服务并开启BBR加速
date: 2018-06-26 14:41:15
tags: 笔记

---
# 前言

---

> 及上篇博客完成 Google Cloud 免费一年申请 [【免费一年、科学上网】-- 30分钟搭建Google cloud SS](http://itzhangbao.com/2018/06/26/笔记/【免费一年、科学上网】--%2030分钟搭建Google%20cloud%20SS/)

## 安装 Shadowsocks

---

#### **1\. 通过SSH连接到服务器**

![](https://upload-images.jianshu.io/upload_images/1874013-94d1b769b810863d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **2\.  切换到root**

输入命令 `sudo -i`

![](https://upload-images.jianshu.io/upload_images/1874013-7599c8864a805c66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **3\.  安装 git**

输入命令 `yum -y install git`

![](https://upload-images.jianshu.io/upload_images/1874013-a58fbe695895a340.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

![](https://upload-images.jianshu.io/upload_images/1874013-a83781f48ab879df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **4\. 下载一键搭建ss脚本文件**

输入命令 `git clone https://github.com/itzhangbao/ss-fly`

> 其中flyzy2005.com换成你要设置的shadowsocks的密码即可（这个flyzy2005.com就是你ss的密码了，是需要填在客户端的密码那一栏的），密码随便设置，最好只包含字母+数字，一些特殊字符可能会导致冲突。

![](https://upload-images.jianshu.io/upload_images/1874013-d937da635a3d2a37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **5\. 运行搭建ss脚本代码**

输入命令  `ss-fly/ss-fly.sh -i itzhangbao.com 1024`

![](https://upload-images.jianshu.io/upload_images/1874013-111435ea881afee3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

界面如下就表示一键搭建ss成功了：

![](https://upload-images.jianshu.io/upload_images/1874013-13c17ce535b34545.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

**注：**如果需要改密码或者改端口，只需要重新再执行一次搭建ss脚本代码就可以了，或者修改/etc/shadowsocks.json这个配置文件。

**相关 ss 操作**

```
修改配置文件：vim /etc/shadowsocks.json
停止ss服务：ssserver -c /etc/shadowsocks.json -d stop
启动ss服务：ssserver -c /etc/shadowsocks.json -d start
重启ss服务：ssserver -c /etc/shadowsocks.json -d restart
```

#### **5\. 卸载ss服务**
	
输入命令  `sss -fly/ss-fly.sh -ssr`

## 一键开启BBR加速

---

输入命令  `ss-fly/ss-fly.sh -bbr`

**装完后需要重启系统，输入y即可立即重启，或者之后输入reboot命令重启。**

**判断BBR加速有没有开启成功。输入以下命令：**

输入命令  `sysctl net.ipv4.tcp_available_congestion_control`

**如果返回值为：**

`net.ipv4.tcp_available_congestion_control = bbr cubic reno`

**后面有bbr，则说明已经开启成功了。**

#### **shadowsocks各版本官方下载地址**

---

**1\.** Windows客户端下载地址：Windows对Framework的版本要求比价高，我的是4.0.2的要求Framework4.6.2。如果是XP或者Framework比较低的，可以直接下载低版本的ss（windows 2.3.1下载地址：[https://github.com/shadowsocks/shadowsocks-windows/releases?after=2.5.1](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-windows/releases?after=2.5.1)）。

**2\.** Mac客户端下载地址：[https://github.com/shadowsocks/ShadowsocksX-NG/releases](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/ShadowsocksX-NG/releases)。

**3\.** Linux客户端下载地址：[https://github.com/shadowsocks/shadowsocks-qt5/wiki/Installation](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-qt5/wiki/Installation)。

**4\.** Android/安卓客户端下载地址：[https://github.com/shadowsocks/shadowsocks-android/releases](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-android/releases)。

**5\.** iOS/苹果客户端直接在App Store里搜索shadowsock关键字（或者wingy关键字，FirstWingy可用 2018.03.25），软件经常被下架，我目前用的是Wingy & Shadowrocket~如果找不到，你也可以通过**PP助手**去下载Shadowrocket。（2018年6月18日更，目前App Store可用免费iOS软件：暂无。收费软件：SuperWingy，ShadowBroken。**推荐免费下载iOS客户端方法**：也可以电脑下载PP助手，手机连上电脑后会自动将PP助手同步至手机，不需要越狱，之后在手机上通过PP助手下载shadowrocket）

**各版本shadowsocks客户端百度云下载地址：**[https://pan.baidu.com/s/1GgzKSzEmqctQ5MUvQ4RR1g](https://www.flyzy2005.com/go/go.php?url=https://pan.baidu.com/s/1GgzKSzEmqctQ5MUvQ4RR1g) 密码：e66v

### **客户端搭建ss代理**

---

**Windows**

根据上面下载好windows电脑版相应客户端程序后，双击打开可运行文件（shadowsocks.exe），根据你的服务器配置，填入相应配置信息，设置如下图所示：

![](https://upload-images.jianshu.io/upload_images/1874013-e7e3e8beb77c785a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

在shadowsocks的windows客户端中，**服务器IP**指你购买的VPS的IP，**服务器端口**指你服务器的配置文件中的端口，**密码**指你服务器的配置文件中的密码，**加密**指你服务器的配置文件中的加密方式，**代理端口**默认为1080不需要改动。设置好后，点击**添加按钮**即可~

其中，高版本的windows客户端可能有**更多的选项**，其他**都可以默认**，只要配置正确这几点即可。

右击任务栏右下角的**小飞机图标**，可以设置相应的**属性项**，包括开启自启，显示日志，PAC设置，系统代理模式等等。其中系统代理模式中的全局模式是指所有的请求都走代理（国内以及国外的），而PAC模式则是自动识别，国内的直连，国外的（例如Google，YouTube）走代理。

如果你的某个**特定的网址**不能通过PAC模式访问，通常情况下是指如YouTube头像无法加载，或者你某些网站直接无法打开，你可以尝试通过全局模式解决。如果你不希望走全局模式，那么可以在Windows客户端中设置PAC，使用本地的PAC，再在规则中加入相应网站即可~

OK，以上就是shadowsocks电脑版（windows）客户端常用的一些配置~

**MAC**

根据上面教程下载好Mac OS电脑版相应客户端程序后，双击打开可运行文件（shadowsocksX-NG.app），之后会在任务栏有一个小飞机图标，右击小飞机图标，选择**服务器**->**服务器设置**，根据你的服务器配置，填入相应配置信息，设置如下图所示：

![](http://upload-images.jianshu.io/upload_images/1874013-12039bd0d80c71ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在shadowsocks的Mac OS客户端中，**地址**指你购买的VPS的IP，**冒号**后面跟上配置文件中的端口，**密码**指你服务器的配置文件中的密码，**加密**指你服务器的配置文件中的加密方式。设置好后，点击**确认**即可~

其中，高版本的Mac OS客户端可能有**更多的选项**，其他**都可以默认**，只要配置正确这几点即可。

OK，以上就是shadowsocks电脑版（Mac OS）客户端常用的一些配置~

**Android**

根据教程下载好Android手机端相应客户端程序后，将apk文件拷贝至手机中（shadowsocks-universal-4.5.0.apk），正常安装apk文件，安装好后打开影梭客户端，主界面如下图所示：

![](http://upload-images.jianshu.io/upload_images/1874013-85dda1f8637b0352.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击左上角的编辑按钮，根据你的服务器配置，在shadowsocks安卓客户端的配置中填入相应配置信息，服务器设置如下图所示：

![](http://upload-images.jianshu.io/upload_images/1874013-9fc0d9faf765ff27.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其中，**功能设置**中，**路由**改成如上图所示，其他都可以默认。

服务器配置好后，保存进入到主界面，点击下方的小飞机图标即可连接（延时不准，请无视）~不用的时候建议在影梭中将其关闭，不然比较耗电：

![](http://upload-images.jianshu.io/upload_images/1874013-ff2e922cd655e8f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

OK，以上就是shadowsocks手机版（Android/安卓）客户端影梭常用的一些配置~

**iOS**

shadowsocks苹果客户端经常会被App Store下架，可以在App Store搜索关键字shadowsock或者wingy，找到一个软件截图中包括填写ip，加密方式，密码的软件一般就是对的了（目前可以用的是FirstWingy）。当然，你也可以下载PP助手，之后在PP助手上下载Wingy（Wingy支持ssr）或者shadowrocket（shadowrocket支持ssr）。之后根据你的服务器配置，填入相应配置信息，设置如下图所示（以Wingy为例）：

![](http://upload-images.jianshu.io/upload_images/1874013-56dde8a6f8e24708.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在shadowsocks的iOS客户端Wingy中，**Host**指你购买的VPS的IP，**Port**指你服务器的配置文件中的端口，**Password**指你服务器的配置文件中的密码，**Method**指你服务器的配置文件中的加密方式。设置好后，点击**Done**即可~

其中系统ProxyRule中的Global Mode是指所有的请求都走代理（国内以及国外的），而Auto Mode则是自动识别，国内的直连，国外的（例如Google，YouTube）走代理。

其中，iOS客户端可能有**更多的选项**，例如Protocol，Obfs，如果没有**都可以默认**，只要填正确这几点即可。

OK，以上就是shadowsocks手机版（iOS/苹果）客户端常用的一些配置~