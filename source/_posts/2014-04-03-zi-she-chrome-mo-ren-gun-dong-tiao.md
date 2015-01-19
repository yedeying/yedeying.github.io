---
layout: post
title: "自设chrome默认滚动条"
date: 2014-04-03 21:19:07 +0800
comments: true
categories:
- css
tags:
- css
- chrome
---
今天无聊，想着chrome这种全面使用html的浏览器，可不可以让我自行改变它的默认CSS呢，结果去查查，有，很好 
win7/8目录为 `C:\Users\[你的用户名]\AppData\Local\Google\Chrome\User Data\Default\User StyleSheets` 
在这个目录下找到`Custom.css`打开修改即可 
立马套上了之前做的一个滚动条样式，代码如下:
``` css
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}
::-webkit-scrollbar-track {
  border-radius: 10px;
  background: rgba(255,255,255,0.5);
  -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.5);
}
::-webkit-scrollbar-thumb {
  border-radius: 10px;
  -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.8); 
}
```
保存即可，效果如下：

![Alt 演示效果](/images/201404031.png) 

其它的滚动条效果设置这都有，可以参考下：[http://css-tricks.com/custom-scrollbars-in-webkit/](http://css-tricks.com/custom-scrollbars-in-webkit/) 

更多的，你可以试试在代码里加个`body{display:none}`，见识下这个文件的好玩之处哦^.^