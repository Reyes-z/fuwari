---
title: 为红米AX5400路由器开启SSH
published: 2026-01-31
description: 为我的路由器折腾SSH安装插件进一步配置网络环境的过程
image: ""
tags:
  - 路由器设置
  - 折腾
category: 网络
draft: false
lang: ""
pinned: false
---
## 原因
自从为家中宽带设置桥接之后我就发现受限于路由器的软件限制，我的公网环境处于一种"如有"的状态，并且我宽带的公网 IPV4 也因某些原因没有了，目前就只剩下了公网 IPV6。  
并且仅有的公网 IPV6 也只能下发到二级路由无法下发到我我们的终端设备，用于拨号的华为AX3 与二级的AX5400 官方系统那少的可怜的网络设置选项我真的没招，目前只能寄希望于修改我的二级路由将我们的端口转发出去，所以目前需要我们获得对红米 AX5400 系统的完全控制权来进行我的设置。
## 设备信息
- 路由器型号: Redmi路由器 AX5400
- 系统ROM版本: MiWiFi 稳定版 1.0.63
## 所需环境
1. 一台能连接路由的电脑
2. AX5400路由器的 SN 码
## 解锁 SSH 与固化
在此感谢恩山论坛的各位大佬，我也是照着大佬的教程一步一步做的，在此不再复述步骤，仅贴出原帖地址。  
解锁 SSH 请参考：[【教程】小米 AX3000/AX3600/AX9000/万兆路由器/AC2100/AC2350/AX1800/AX5400 开启SSH-小米无线路由器及小米网络设备-恩山无线论坛](https://www.right.com.cn/forum/thread-8348455-1-1.html)
若重启路由器后 SSH 关闭则可以通过以下命令添加自动开启 SSH 的脚本 ：
```bash
mkdir /data/auto_ssh && cd /data/auto_ssh
curl -O https://cdn.jsdelivr.net/gh/lemoeo/AX6S@main/auto_ssh.sh
chmod +x auto_ssh.sh
./auto_ssh.sh install
```
## 后续
我们解锁了 SSH 之后就获得了对路由器系统的 ROOT 权限，我们可以安装各种第三方插件或是直接编辑路由器配置文件进行自定义配置。