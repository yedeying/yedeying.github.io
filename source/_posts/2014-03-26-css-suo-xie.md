---
layout: post
title: "CSS缩写"
date: 2014-03-26 09:24:18 +0800
comments: true
categories:
- css
tags:
- css
---
### CSS缩写属性
一、CSS文本(css text):
``` css
* {
  /* 原样式 */
  font-size: 12px;
  font-weight: bold;
  font-family: Arial, Helvetica, sans-serif;
  line-height: 22px;
  /* 缩写后样式 */
  font: 12px/22px bold Arial, Helvetica, sans-serif;
}
```
二、CSS背景(CSS background):
``` css
* {
  /* 原样式 */
  background-color: #ff0000;
  background-image: url('url');
  background-position: bottom;
  background-repeat: no-repeat;
  /* 缩写后样式 */
  background:#f00 url('url') no-repeat left bottom;
}
```
三、CSS内补距(CSS padding):
``` css
* {
  /* 原样式 */
  padding-top: 5px;
  padding-bottom: 10px;
  padding-left: 15px;
  padding-right: 0px;
  /* 缩写后样式 */
  padding: 5px 10px 15px 0;

  /* 原样式 */
  padding-top: 5px;
  padding-bottom: 5px;
  padding-left: 10px;
  padding-right: 10px;
  /* 缩写后样式 */
  padding: 5px 10px;

  /* 原样式 */
  padding-top: 5px;
  padding-bottom: 15px;
  padding-left: 10px;
  padding-right: 10px;
  /* 缩写后样式 */
  padding: 5px 10px 15px;
}
```
四、CSS外边距(CSS margin):
``` css
* {
  /* 原样式 */
  margin-top: 5px;
  margin-bottom: 10px;
  margin-left: 15px;
  margin-right: 0px;
  /* 缩写后样式 */
  margin: 5px 10px 15px 0;

  /* 原样式 */
  margin-top: 5px;
  margin-bottom: 5px;
  margin-left: 10px;
  margin-right: 10px;
  /* 缩写后样式 */
  margin: 5px 10px;

  /* 原样式 */
  margin-top: 5px;
  margin-bottom: 15px;
  margin-left: 10px;
  margin-right: 10px;
  /* 缩写后样式 */
  margin: 5px 10px 15px;
}
```
五、CSS边框(CSS border):
``` css
* {
  /* 原样式 */
  border-left: 1px solid #000;
  border-right: 1px solid #000;
  border-top: 1px solid #000;
  border-bottom: 1px solid #000;
  /* 缩写后样式 */
  border: 1px solid #000;
}
```
更多的，待补充，左右上下要记清