---
layout: post
title: "监听div内容改变"
date: 2014-03-28 15:25:56 +0800
comments: true
categories:
- javascript
tags:
- javascript
- canvas
---
做前端突击队，外星人那道是自己手动模拟那个时间的变化的，但正确思路应该是监听div内容的变化然后同步到输入框中，遂今天找了一下
结果如下：
``` js
$('div').on('DOMNodeInserted', function (e) {
  // TO DO
});
```