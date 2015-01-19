---
layout: post
title: "配置node与express初试"
date: 2014-05-22 15:50:17 +0800
comments: true
categories:
- javascript
tags:
- javascript
- node
- express
---
[http://www.nodejs.org/](http://www.nodejs.org/)下载对应系统的node版本并安装<br>
用npm包管理器安装需要的包
``` bash
sudo npm install -g express
sudo npm install -g express-generator
sudo npm install -g coffee-script
```
找一个目录，运行以下命令创建一个工程，并运行
``` bash
express [-e] hello
cd hello
npm install
./bin/www
```