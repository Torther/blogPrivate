---
date: 2021/9/23 12:32:16
title: 关于Windows应用商店或Xbox应用安装程序时出现0x80073d0d的解决方法
cover: 
categories: [技巧分享]
tags: [Windows, Microsoft, 0x80073d0d]
---

> 造成原因(之一)：强制删除磁盘下的 WindowsApps 文件夹

因为磁盘下 WindowsApps 目录不存在，但注册表中仍记录该值，所以导致错误的产生。

![image.png](https://img.mol.ink/2021/1639364265863.png)

可见D盘对应的WindowsApps是离线的

## 解决方法

通过卸载该卷然后在 Windows应用商店 中重新选择安装位置可重新建立 WindowsApps 文件夹

````
PS C:\Windows\system32> Remove-AppxVolume -Volume D:\
PS C:\Windows\system32>
````

重启应用商店恢复正常
