---
layout: post
title: "css position 学习"
date: 2014-03-26 00:03:14 +0800
comments: true
categories:
- css
tags:
- html
- css
---
今天重新看了下绝对定位，总算明白那个绝对居中的原理了。
绝对定位是对它关系最近的一个有定位属性的父元素进行定位，参数先看left top，再看right bottom。
绝对居中布局是指(对其关系最近的一个有定位属性的父元素进行居中)
``` css
.div {
    position: absolute;
    margin: auto;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0
}
```
margin: auto起到的作用是将div相对其父元素延伸出左右上下相等的外补丁从而实现居中
``` html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    .outer {
      position: absolute;
      margin: auto;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      height: 200px;
      width: 200px;
      background: yellow;
    }
    .inner {
      position: absolute;
      margin: auto;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      height: 100px;
      width: 100px;
      background: blue;
    }
  </style>
</head>
<body>
  <div class="outer">
    <div class="inner"></div>
  </div>
</body>
</html>
```
demo如下:
<div style="position: relative; width: 200px; height: 200px; background: yellow; text-align: center;">外
<div style="top: 0; bottom: 0; left: 0; right: 0; margin: auto; position: absolute; width: 100px; height: 100px; background: #4791ff; text-align: center; vertical-align: middle;">里</div>
</div>
同样地，我们可以活用这个规则，创建出指定宽度的分列布局，只需要将上例的四个方向属性由0改为一个规定的百分值，即可实现，下为我把一个div划为三列的写法：
``` html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    .outer {
      position: relative;
      margin: auto;
      height: 200px;
      width: 600px;
      background: yellow;
    }
    .inner {
      height: 200px;
      width: 33.33333333%;
      position: absolute;
      margin: 0 auto;
    }
    .a {
      left: 0;
      right: 66.66666667%;
      background: green;
    }
    .b {
      left: 0;
      right: 0;
      background: blue;
    }
    .c {
      left: 66.66666667%;
      right: 0;
      background: red;
    }
  </style>
</head>
<body>
  <div class="outer">
    <div class="inner a"></div>
    <div class="inner b"></div>
    <div class="inner c"></div>
  </div>
</body>
</html>
```
Demo:
<div style="position: relative; height: 200px; width: 600px; background: yellow;">
<div style="height: 200px; width: 33.33333333%; position: absolute; margin: 0 auto; left: 0; right: 66.66666667%; background: green; text-align: center;">左</div>
<div style="height: 200px; width: 33.33333333%; position: absolute; margin: 0 auto; left: 0; right: 0; background: blue; text-align: center;">中</div>
<div style="height: 200px; width: 33.33333333%; position: absolute; margin: 0 auto; left: 66.66666667%; right: 0; background: red; text-align: center;">右</div>
</div>