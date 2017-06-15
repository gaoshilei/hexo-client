---
title: 租用Vultr服务器安装SSR并安装BBR加速（不使用一键安装脚本）
date: 2017-06-11 08:33:33
tags: 
- GFW
- Vultr
- SSR
- BBR
categories: 
- 教程
- GFW
---

为了安全性与后期可自定义，此教程不再使用一键安装脚本，而是自己动手设置。

**这是单用户版安装教程！**

**我是个人以及几个好友使用，不需要限制流量，所以只选择单用户版安装！**

**所有源代码来源于SSR的原作者：breakwa11**

# 购买VPS

全世界好多好多家VPS商，我和好友[刘百川](http://liubaichuan.tk)选的是Vultr。

安装一个CentOS系统。

请注意：如果你后期想安装的是锐速加速，那么请安装CentOS 6；如果你后期想安装的是谷歌BBR加速，那么请安装CentOS 7；

<!--more-->

# 安装Putty for windows

这个软件的是使用方法见链接：http://jingyan.baidu.com/article/e73e26c0eb063324adb6a737.html

# 安装服务器端shadowsocksR

参考链接：https://shadowsocks.be/11.html



# 安装锐速（推荐与CentOS 6搭配使用）

 [教程：CentOS更换内核，提供锐速可用的内核下载](https://www.91yun.org/archives/795)

 [锐速破解版linux一键自动安装包（5月28日更新）](https://www.91yun.org/archives/683)

我是依次执行以下命令：

```shell
rpm -ivh http://soft.91yun.org/ISO/Linux/CentOS/kernel/kernel-firmware-2.6.32-504.3.3.el6.noarch.rpm
rpm -ivh http://soft.91yun.org/ISO/Linux/CentOS/kernel/kernel-2.6.32-504.3.3.el6.x86_64.rpm --force
rpm -qa | grep kernel
reboot
```

然后关掉终端，重新登陆。

```shell
uname -r
wget -N --no-check-certificate https://github.com/91yun/serverspeeder/raw/master/serverspeeder.sh && bash serverspeeder.sh
```

可以通过下面这行命令查看锐速运行状态。

```shell
/serverspeeder/bin/serverSpeeder.sh status
```

# 安装谷歌BBR（推荐与CentOS 7搭配使用）

参考链接见：https://www.vultr.com/docs/how-to-deploy-google-bbr-on-centos-7