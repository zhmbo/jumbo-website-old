
title: Mac+Win 上 MySQL 安装过程笔记
date: 2017-08-07 13:00:00
tags: 笔记

---
![](http://upload-images.jianshu.io/upload_images/1874013-bfe3be6c6e2ff723.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 此过程安装于 *2017年08月07日 10:46:30*.  版本：**5.7.19**.

# 官网下载
> 使用 MySQL 需要两个东西，一个 MySQL Server 服务器，还需一个 MySQL Workbench(图形化管理工具)

#### 1.MAC
MySQL Server：[mysql-5.7.19-macos10.12-x86_64.dmg](https://dev.mysql.com/downloads/file/?id=471631)
MySQL Workbench：[mysql-workbench-community-6.3.9-osx-x86_64.dmg](https://dev.mysql.com/downloads/file/?id=468289)

#### 2.MicroSoft Windows
`windows 这里的安装包是Server+workbench 都有的`
MySQL Server + Workbench：[mysql-installer-community-5.7.19.0.msi](https://dev.mysql.com/downloads/file/?id=471661)

#### 3. 下载界面
> 点进去之后，你会看到两个大大的按钮，登录和注册。如果你不想做这些繁琐的动作，别急，看下图红框圈中的文字，点击就可以直接下载了。

![下载界面.png](http://upload-images.jianshu.io/upload_images/1874013-b0db67d101bd7ae9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 4. 注意
> 安装完成会弹出一个窗口，上面有个 root 账户的默认密码这个要记下。大致意思就是：
***2017-08-07t02:15: 23.908963Z 1 [注]临时密码是 root@localhost：ENd)fo--D8hP
如果您丢失了该密码，请参阅MySQL参考手册中如何重置root密码的一节。***

![默认密码.png](http://upload-images.jianshu.io/upload_images/1874013-9bcccb89c0c8b374.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 启动
#### 1. Mac 启动
**启动方式 1 -- 进入系统偏好设置，最下边一行，找到mysql打开，点击"Start MySQL Server"，启动mysql**

![1.png](http://upload-images.jianshu.io/upload_images/1874013-bb8a54339139d911.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![2.png](http://upload-images.jianshu.io/upload_images/1874013-918557da4174c85b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**启动方式 2 -- 命令行运行** 

在应用程序中找到 iTerm 打开，首先运行下面两条命令：(这两条命令是为了方便直接打开 iTerm 就可以运行mysql命令，而不是必须进入mysql安装目录才能运行)
`alias mysql=/usr/local/mysql/bin/mysql`
`alias mysqladmin=/usr/local/mysql/bin/mysqladmin`

**接下来，你要做的是重置密码**
`mysqladmin -u root -p password newpass` newpass 是你的新密码
> 运行重置密码的命令后，系统提示输入旧密码。安装过mysql5.6或之前版本的同学知道，mysql首次运行会给root用户分配一个默认密码：root, 这个旧密码就是root。但是现在如果你输入root，系统提示密码错误，怎么回事呢？
原来5.7的版本不会再给 root 用户分配默认密码，而是会给一个临时密码**这个默认密码就是上面保存的临时密码**。如果你细心的话，安装mysql成功后会弹出一个临时密码让你保存。如果你没有保存，没关系，右侧的通知栏里会有，如图：

![ 默认密码.png](http://upload-images.jianshu.io/upload_images/1874013-62fa2e637c42e61a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

输入临时密码，密码修改成功，然后用新密码登录：
`mysql -u root -p`

回车，新密码，回车，登录成功！
现在你可以写你的 sql 命令了！

#### 2. Windows 启动

- 搜索服务
- 找到 MySQL57(57为版本号)
- 右键属性查看运行状态，启动

![wiindows 启动.png](http://upload-images.jianshu.io/upload_images/1874013-8b3f0998925e87ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 完
