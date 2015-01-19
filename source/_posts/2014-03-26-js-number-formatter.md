---
layout: post
title: "javascript小数格式化函数"
date: 2014-03-26 10:15:32 +0800
comments: true
categories:
- javascript
tags:
- javascript
---
直接上代码，参数number为待格式化整数或小数，fix是要保留有效位数，过亿以亿结尾，过万以万结尾，toFixed函数记得，免得再查
``` js
function shorten_number (number, fix) {
  var counter = '';
  if (number >= 100000000) {
    number /= 100000000;
    counter = '亿';
  } else if (number >= 10000) {
    number /= 10000;
    counter = '万';
  }
  var str = number.toFixed(fix);
  while(str.charAt(str.length - 1) == '0')
    str = str.substring(0, str.length - 1);
  if(str.charAt(str.length - 1) == '.')
    str = str.substring(0, str.length - 1);
  return str + counter;
}
```