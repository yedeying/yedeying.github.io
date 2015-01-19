---
layout: post
title: "ubuntu杂记"
date: 2014-04-07 05:13:03 +0800
comments: true
categories:
- other
tags:
- linux
- ubuntu
---
#### 安装ssh:
``` bash
sudo apt-get install openssh-server
sudo /etc/init.d/ssh start
```
将主机中vmware8的网络改为自动获取ip, 就可以ping通了 

#### 安装sublime-text:
``` bash
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
```
Lampp config: 

[https://www.apachefriends.org/zh_cn/index.html](https://www.apachefriends.org/zh_cn/index.html)

#### 安装五笔输入法:
``` bash
sudo apt-get install ibus ibus-table ibus-table-wubi
```
1. 安装三个包：ibus,ibus-table ibus-table-wubi
2. 打开System setting面板, 点击language support,在Keyboard input method system右边的下拉框中选中ibus,退出
3. 注销, 再次进入系统, 在右上角的就会多一个ibus的东东, 点开下拉, 选择Preference, 打开ibus preference面板
4. 选择Input Method选项卡, 选择想要的输入法, 然后点击Add按扭.OK！除了五笔外, ibus还有拼音, 以及一些其它输入法.