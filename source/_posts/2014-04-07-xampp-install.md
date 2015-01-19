---
layout: post
title: "Linux下xampp的install"
date: 2014-04-07 22:56:09 +0800
comments: true
categories:
- other
tags:
- xampp
- linux
---
the way of restart:
``` bash
sudo /opt/lampp/lampp restart
```
config root:
``` bash
  /opt/lampp/etc/httpd.conf
  /opt/lampp/etc/httpd-xampp.conf
  # in each file we should change the deny config to allow
```
and one more thing is to change the rights of htdocs directory, with the order below:
``` bash
  sudo chmod a+w -R /opt/lampp/htdocs  #change the rights of htdocs directory
  sudo ln -sf /opt/lampp/htdocs/ ~/Public/  #create a link of htdocs for convience
```
reference pages:<br>
[http://haobinnan.blog.51cto.com/775253/750435](http://haobinnan.blog.51cto.com/775253/750435)<br>
[http://ifalone.me/569.html](http://ifalone.me/569.html)<br>
[http://blog.163.com/yuanzhf_2012/blog/static/2112011482012842515448/](http://blog.163.com/yuanzhf_2012/blog/static/2112011482012842515448/) 