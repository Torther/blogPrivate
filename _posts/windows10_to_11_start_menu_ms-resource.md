---
date: 2021/10/12 12:56:10
title: 关于Windows应用商店或Xbox应用安装程序时出现0x80073d0d的解决方法
cover: 
categories: [技巧分享]
tags: [Windows, Microsoft, Windows10, Windows11]
---

> 产生缘由：可能是通过其他工具或者方式删掉自带的应用/系统升级导致的应用错误

> 本文解决：Windows10升级Windows11时旧版安全中心遗留

找到升级后C盘的Windows.old文件夹，在Windows目录下的SystemApps目录中找到Microsoft.Windows.SecHealthUI_xxxxxx文件夹，将其复制到C:\Windows\SystemApps。

接着打开菜单，可看到ms-resource:DisplayName显示了旧版安全中心的图标，右键卸载即可。
