layout: post
title: css3 圆内环动画
comments: true
categories:
- CSS3
tags:
- animation
- css3
- sass
date: 2014-09-02 13:32:00
---
layout: post
title: "css3 圆内环动画"
date: 2014-09-02 13:32:37 +0800
comments: true
categories: CSS3
tags: animation css3 sass
---
某一天, 在网上看到这幅图, 兴趣袭来  
![Alt circle animation](/images/201409021.gif)  
仔细看, 发现有以下几个特点

* 八个点一直在做直线运动
* 每个点并非匀速运动
* 每个点永远处于一个假想内环圆的圆边上  

于是就想到去codepen做一个这东西的css版, 来锻炼下自已捉急的CSS水平

### 首先, 建立html结构
这个很简单, 不过为了这个图的每个数量可控性, 这里用jade来写  
outer类是大圆, inner类是小圆  
``` jade
-num=(8)
.outer
  while num--
    .inner
```
### 其次, 给结构赋予样式
这一步, 要给大圆加上半径, 宽高, 背景各种, 小圆用absolute在大圆内定位, 它们的半径就用`$R`和`$r`来表示  
最初将小圆定位在大圆的中心
``` sass
$R: 200px;
$r: 25px;
.outer {
  background: red;
  position: relative;
  width: $R * 2;
  height: $R * 2;
  border-radius: $R;
  .inner {
    position: absolute;
    left: $R;
    top: $R;
    background: #fff;
    width: $r * 2;
    height: $r * 2;
    margin-left: $r * -1;
    margin-top: $r * -1;
    border-radius: $r;
  }
}
```
然后就得到了它大概的样子
<div class="outer">
  <style>
    .outer {
      background: red;
      position: relative;
      width: 400px;
      height: 400px;
      border-radius: 200px;
    }
    .outer .inner {
      position: absolute;
      left: 200px;
      top: 200px;
      background: #fff;
      width: 50px;
      height: 50px;
      margin-left: -25px;
      margin-top: -25px;
      border-radius: 25px;
    }
  </style>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
  <div class="inner"></div>
</div>
### 接着, 添加动画
添加动画要注意很多细节:  
1. 每个点的初始位置  
这里可以把对应数量的圆平均分布在一个半圆内, 不过注意这个半圆弧只有一个端点上有圆  
计算出它们的极角, 再利用sin cos以及圆心, 可以求得它们的left, top值  
2. 每个点的运动延迟时间  
观察原图, 或者自己画一下分析图, 发现当内圆环绕一圈时, 一个小点会完成一次来回, 也就可以认为一次来或回的时间, 等于每个球的延迟时间 * 数量, 也就可以求得了  
3. 每个点的运动速度变化  
这是相对难的一部分, 自己从圆环绕这个动作研究了一下每个小圆的运动轨迹, 发现它的速度变化和三角函数有着很大的联系, 但CSS提供的是三次贝塞尔曲线函数, 所以退了一步找到一个相似的时间函数  

最终结果如下:
``` sass
$R: 200px;
$r: 2px;
$speed: 1s;
$num: 64;
$radius: $R - $r;
$i: $num;
@while $i > 0 {
  @keyframes move#{$i} {
    $angle: ($i - 1) * 180 / $num;
    from {
      left: $R - $radius * sin($angle * pi() / 180);
      top: $R - $radius * cos($angle * pi() / 180);
    } to {
      left: $R + $radius * sin($angle * pi() / 180);
      top: $R + $radius * cos($angle * pi() / 180);
    }
  }
  $i: $i - 1;
}
.outer {
  background: red;
  position: relative;
  width: $R * 2;
  height: $R * 2;
  border-radius: $R;
  .inner {
    position: absolute;
    left: $R;
    top: $R;
    background: #fff;
    width: $r * 2;
    height: $r * 2;
    margin-left: $r * -1;
    margin-top: $r * -1;
    border-radius: $r;
    animation-duration: $speed;
    animation-iteration-count: infinite;
    animation-direction: alternate;
    animation-timing-function: cubic-bezier(0.4,0,0.6,1);
    $i: $num;
    @while $i > 0 {
      &:nth-of-type(#{$i}) {
        animation-delay: $speed / $num * ($i - 1);
        animation-name: move#{$i};
      }
      $i: $i - 1;
    }
  }
}
```
为增强效果, 我把数量由8改成了64, 然后更加赞叹了, 竟然是由直线运动组成的

DEMO:
{% codepen yedeying999 hjHkb result 500 %}