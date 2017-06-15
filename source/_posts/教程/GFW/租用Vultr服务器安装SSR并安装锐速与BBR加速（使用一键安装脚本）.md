---
title: 租用Vultr服务器安装SSR并安装锐速与BBR加速（使用一键安装脚本）
date: 2017-06-09 15:23:33
tags: 
- GFW
- 锐速
- BBR
categories: 
- 教程
- GFW
---

# 购买VPS

全世界好多好多家VPS商，我和好友[刘百川](http://liubaichuan.tk)选的是Vultr。

安装一个CentOS系统。

请注意：如果你后期想安装的是锐速加速，那么请安装CentOS 6；如果你后期想安装的是谷歌BBR加速，那么请安装CentOS 7。

（看了好多文章，觉得BBR更好一些）。

# 安装Putty for windows

这个软件的是使用方法见链接：http://jingyan.baidu.com/article/e73e26c0eb063324adb6a737.html

# 安装服务器端shadowsocksR

参考链接：https://shadowsocks.be/9.html

使用root用户登录，运行以下命令：<!--more-->

```shell
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```

安装完成后，脚本提示如下

> Congratulations, ShadowsocksR install completed!
> Server IP:your_server_ip
> Server Port:your_server_port
> Password:your_password
> Local IP:127.0.0.1
> Local Port:1080
> Protocol:origin
> obfs:plain
> Encryption Method:aes-256-cfb
>
> Welcome to visit:https://shadowsocks.be/9.html
> If you want to change protocol & obfs, reference URL:
> https://github.com/breakwa11/shadowsocks-rss/wiki/Server-Setup
> Enjoy it!

**卸载方法**

使用 root 用户登录，运行以下命令：

```
./shadowsocksR.sh uninstall

```

安装完成后即已后台启动 ShadowsocksR ，运行：

```
/etc/init.d/shadowsocks status

```

可以查看 ShadowsocksR 进程是否已经启动。
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

**使用命令：**
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json
日志文件路径：/var/log/shadowsocks.log
代码安装目录：/usr/local/shadowsocks

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