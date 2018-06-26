
title: 【免费一年、科学上网】-- 30分钟搭建Google cloud SS
date: 2018-06-26 14:41:15
tags: 笔记

---
![](https://upload-images.jianshu.io/upload_images/1874013-b05ea5ad241228af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

# 前言

---

> 某N，某梯，某器被屏蔽，热搜也空空如也，Green 欠我的年费还未还我~ 
tnnd~~ 还是自己动手丰衣足食，傻瓜式教程，跟着操作实现科学上网！

## 账号准备工作

---

* Google 账号一枚
* 国际信用(visa\master)卡一张（用于申请Google免费云时$1验证，验证后退还）
* 临时可以访问海外网络（用于登陆 [谷歌云](https://cloud.google.com/) 网站，申请免费账号使用）可以代理

#### **1. 注册 Google 账号**

[创建账号直达入口](https://accounts.google.com/signup/v2/webcreateaccount?continue=https%3A%2F%2Fwww.google.com%2F&hl=zh-CN&flowName=GlifWebSignIn&flowEntry=SignUp)

#### **2. 免费试用一年（哇o~）** 注册Google账户后，进入：[https://cloud.google.com/](https://cloud.google.com/)，并点击“免费试用”。

![](https://upload-images.jianshu.io/upload_images/1874013-ca89eabdba0c3465.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/400)

#### **3. 登陆或创建账号**

![](https://upload-images.jianshu.io/upload_images/1874013-4b933266e0317199.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **4. 选择后同意并继续**

![](https://upload-images.jianshu.io/upload_images/1874013-98ff57ae74d813b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)


#### **5. 填表单，绑定信用卡，并收取$1** 可以看到，Google的服务还是非常感人的。**首先免费试用1年，再次试用结束后不自动收费。**

![](https://upload-images.jianshu.io/upload_images/1874013-c26fe86820276128.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

![](https://upload-images.jianshu.io/upload_images/1874013-87928cb26f2482b2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/320)

## 环境配置

---

#### **1\. 修改防火墙**

VPC网络 -> 防火墙规则 -> 创建防火墙（[https://console.cloud.google.com/networking/firewalls/list](https://console.cloud.google.com/networking/firewalls/list)）

![](https://upload-images.jianshu.io/upload_images/1874013-03c0e5e21b0269e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/320)

***注意以下几点即可***
- 目标：网络中所有的实例
- 来源过滤：IP地址范围，并设置为0.0.0.0/0
- 协议和端口：全部允许

![](https://upload-images.jianshu.io/upload_images/1874013-938bcef2b6a1954c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

#### **2\. 申请静态IP**

若长期使用，建议还是申请一个
VPC网络 -> 外部IP地址 -> 保留静态地址（即添加）（[https://console.cloud.google.com/networking/addresses/list](https://console.cloud.google.com/networking/addresses/list)）

![](https://upload-images.jianshu.io/upload_images/1874013-3e3d58fd592f2bae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/320)

***注意以下几点即可***

- 区域：asia-east1

![](https://upload-images.jianshu.io/upload_images/1874013-ae46d5ebc1dc8505.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

### **3\. 创建计算引擎**

Computer Engine -> VM实例 -> 创建实例（[https://console.cloud.google.com/compute/instances](https://console.cloud.google.com/compute/instances)）
注意以下几点即可
- 区域：asia-east1（台湾）~距离近
- 地区：asia-east1-b
- 机器类型：微型，1个共享vCPU（0.6GB内存）
- 启动磁盘：CentOS 7
- 防火全：允许 HTTP 流量、允许 HTTPS 流量

![](https://upload-images.jianshu.io/upload_images/1874013-3a13a581bc98c667.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

- 管理、磁盘、网络、SSH 密钥：打开，选择网络，选择之前申请的静态IP
**切记**：***这里一定不要忘记选择刚才申请的静态IP*** 

![](https://upload-images.jianshu.io/upload_images/1874013-42f4a6b452c8339e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520)

**然后创建**
待实例创建完成以后，服务器的搭建就完成了，现在需要通过SSH连接到服务器，安装软件了。其实很简单，只需要粘贴几行代码即可。

## 搭建 SS
[一键脚本搭建 SS 服务并开启BBR加速](https://www.jianshu.com/p/391fb7eb3bb3)

## 总结

---
> 科学上网吧，兄弟！[Google](https://www.google.com/) 
小伙伴们，有不明白的地方可以在下方留言，lz看到后会耐心解答。如果你实在是懒的不想折腾~ 大赏小弟点零花钱，**可代为完成**以上操作。

