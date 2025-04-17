---
layout: post
title: WindowsDefender防火墙无法更改某些设置
date: 2020-10-15
category: multimedia
tags: [multimedia]
excerpt: 打开防火墙
---


### 手贱系列，本人不小心手欠按到了破解器上面的“一键禁止Windows defenders”的按钮，无法恢复。导致防火墙整个被禁止掉了，进“服务”页面里面也无法开启。具体表现如下：

---
**Windows Defender防火墙未使用推荐的设置来保护计算机**
![](http://www.bbvdd.com/d/20201015142519mgp.png)


**这个报错就是服务没有打开的报错**

这样的话
鼠标右键点击开始菜单，选择运行，　运行regedit.exe打开注册表，删除下面两项：

1、
EY_LOCAL_MACHINE SOFTWARE Policies Microsoft WindowsFirewall

2、
EY_CURRENT_USER SOFTWARE Policies Microsoft WindowsFirewall（至少能找到一项），服务中重启Windows Firewall/Internet Connection Sharing(ICS)还有防火墙的服务
　　
　　
**方法无效的话，操作下这个方法**
打开注册表（win+R打开运行框，输入regedt32回车），定位到HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MpsSvc，查看start的数值数据是否为2，双击修改为2即可——但是要重启后才能生效。

![](http://www.bbvdd.com/d/20201015145402pwg.png)


然后，就可以修复好防火墙啦！

![](http://www.bbvdd.com/d/20201015145735t5k.png)

---
![](http://img31.mtime.cn/mg/2016/02/05/145836.38850143_210X210X4.jpg)
![](http://img31.mtime.cn/mg/2016/02/05/145836.38850143_210X210X4.jpg)
![](http://img31.mtime.cn/mg/2016/02/05/145836.38850143_210X210X4.jpg)
