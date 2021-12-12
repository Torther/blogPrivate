---
title: 记一次小米路由器mini刷openwrt教程
cover: https://img.mol.ink/2021/mini_openwrt_1.png
---

## 前言

最近从海鲜市场20块入手了一台小米路由器mini，详细配置如下

{% noteblock 详细配置 %}
ROM16MB SPI Flash
内存128MB DDR2
硬盘存储无
2.4G WiFi2*2（最高速率300Mbps）
5G WiFi2*2（最高速率867Mbps）
天线外置双频全向天线2根
{% endnoteblock %}

由于我已经刷过了breed，所以在之前的步骤网上都能找到。
固件的下载地址在文末会提供。

## 刷机过程

刷完breed后，在拔掉路由器电源情况下按住reset键，然后插上电源，待路由器指示灯变为红色（连续闪烁三次）时松开，可以见到指示灯变为蓝色闪烁（规律为：……亮—亮——亮—亮……）
此时就可以从浏览器进入breed恢复控制台

![Breed控制台](https://img.mol.ink/2021/mini_openwrt_1.png)

> **注：只能电脑通过网线和路由器相连才能进入**

选择固件更新，上传已下载的固件

![上传固件](https://img.mol.ink/2021/mini_openwrt_2.png)

> **为防止意外发生，建议备份自己的固件**

上传固件后，会出现以下界面

![确认更新](https://img.mol.ink/2021/mini_openwrt_3.png)

点击更新即可

![等待完成](https://img.mol.ink/2021/mini_openwrt_4.png)

等待进度条完成，路由器会自动重启

可以通过路由器的指示灯判断，蓝色闪烁代表正在启动，蓝色常亮代表正在运行

这时就可以通过 192.168.1.1 来访问openwrt的控制界面

![登录后台](https://img.mol.ink/2021/mini_openwrt_5.png)

**默认密码为：password**

登入后，就可以按照自己的需求进行设置了

固件：[点击下载](https://wwa.lanzouo.com/i5tPhxipbpc)