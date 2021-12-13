---
date: 2021/9/28 18:54:17
title: 关于校园网Wifi认证简便化的思路
cover: 
categories: [技巧分享]
tags: [Windows, Microsoft, Windows10, Windows11]
---

学校Wifi是Web认证，只需要发送一个 GET 请求即可。浏览器登录的时候直接 F12 打开开发者工具，找到类似于这么一长串的连接，登录时会跳转，建议打开 Preserve log 选项，这样跳转出去了再返回这些信息还在。

![](https://img.mol.ink/2021/school_wlan_1.png)

~~~
http://10.129.254.253:801/eportal/?c=Portal&a=logout&callback=dr1002&login_method=1&user_account={xuehao}&user_password={password}&ac_logout=0&register_mode=0&wlan_user_ip={ip}&wlan_user_ipv6=&wlan_vlan_id=1&wlan_user_mac=000000000000&wlan_ac_ip=&wlan_ac_name=&jsVersion=3.3.2&v=1218
~~~

其中重要的只有三个参数

```
user_account: 
user_password: 
wlan_user_ip:
```

分别对应账号和密码及设备IP。

---

所以可以直接按Win+R，输入curl命令来向认证服务器发送一个请求，即可完成Web认证。

但Windows Powershell中的&不允许被使用，所以需要用正则表达式替换一下。

![](https://img.mol.ink/2021/school_wlan_2.png)

从而得到

~~~
curl http://10.129.254.253:801/eportal/?c=Portal"&"a=login"&"callback=dr1004"&"login_method=1"&"user_account={xuehao}@DX"&"user_password={password}"&"wlan_user_ip={ip}"&"wlan_user_ipv6="&"wlan_user_mac=000000000000"&"wlan_ac_ip="&"wlan_ac_name="&"jsVersion=3.3.2"&"v=686
~~~

替换其中的{xuehao}，{password}，{ip}为自己的并保存为bat文件，每次运行一下就可以完成认证。
