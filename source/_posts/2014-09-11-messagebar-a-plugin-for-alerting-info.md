---
layout: post
title: "messagebar: a plugin for alerting info"
date: 2014-09-11 11:33:36 +0800
comments: true
categories:
- javascript
tips:
- plugin
- js
- singleton
---
这是一个插件, 一个提示框插件, 十分轻量, 十分精简, 为本人无聊打发时间作品  
详戳[github repo](https://github.com/yedeying999/messagebar)  
以下是插件的介绍~~~

messagebar.js
=============
This is a plugin for alerting info.

### Usage

#### include:  
``` html
<script src="messagebar.js"></script>
```

#### usage:  
messagebar can be used in the ways shown below
``` js
messagebar.alert(message);
messagebar.alert(message, preventAutoClosing);
messagebar.alert(option);
```
**Notice:** The variable message is a string you want to alert, then preventAutoClosing means that if you need to click a closing button by yourself to have it disappear. The 3rd line recieve an object to be the arguments, we expect the object to be formatted as below, or you will get an error.  
**option format:**
``` js
{
  // string: the message you want to show
  message: 'you have not input any message',
  // string: a string only include one of left or right and one of up and down, a space to split
  position: 'right top',
  // number: a time delay after which the messagebar will show
  delay: 0, 
  // number: if property 'pause' is false, the messagebar will disappear after this time
  time: 3000,
  // boolean: control that if you need to click a closing button by yourself to have it disappear
  pause: false
}
```
**tips:** the values of every property of option will be set if you ignore it. That is to say, you can offer any number propertys of the option, if you want to use the default value.

#### Demo
[Here is a demo](/sites/messagebar/index.html)