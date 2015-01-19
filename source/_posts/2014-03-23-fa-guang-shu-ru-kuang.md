---
layout: post
title: "发光输入框"
date: 2014-03-23 15:43:06 +0800
comments: true
categories:
- css
tags:
- html
- css
- css3
---

CSS3 transition 以及 box-shadow实现，要注意的是`outline:none;`

##### demo:
<div>
  <input id="lightenBox" type="text" />
  <style>
    #lightenBox {
      font-size: 14px;
      transition: box-shadow linear .2s, border-color linear .2s;
      width: 200px;
      padding: 8px;
      border: 1px solid #aaaaaa;
      -webkit-border-radius: 5px;
      -moz-border-radius: 5px;
      border-radius: 5px;
    }
    #lightenBox:focus, 
    #lightenBox:hover {
      outline: none;
      box-shadow: 0 0 15px rgba(152,188,235,1.0);
      border-color: rgba(152,188,235,1.0)
    }
  </style>
</div>
##### code:

``` html
<div>
  <input id="lightenBox" type="text" />
  <style>
    #lightenBox {
      font-size: 14px;
      transition: box-shadow linear .2s, border-color linear .2s;
      width: 200px;
      padding: 8px;
      border: 1px solid #aaaaaa;
      -webkit-border-radius: 5px;
      -moz-border-radius: 5px;
      border-radius: 5px;
    }
    #lightenBox:focus, 
    #lightenBox:hover {
      outline: none;
      box-shadow: 0 0 15px rgba(152,188,235,1.0);
      border-color: rgba(152,188,235,1.0)
    }
  </style>
</div>
```