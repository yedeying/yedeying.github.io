---
layout: post
title: "RCP学习笔记"
date: 2014-07-15 11:10:32 +0800
comments: true
categories:
- other
tags:
- java
- rcp
---
```
一些model特征:
    Trimmed Window: 带最小化最大化的窗体
    Perspective Stack: 装载Perspective的容器
    Perspective：一个透视，可以直接包含PartSashContainer, Part Stack或Part
    PartSashContainer: 装载Part Stack的容器
    Part Stack: 可以装载多个Part, 分多个标签栏显示
    Part: 一个标签以及对应的editor, 可通过URI定位代码类来扩展内容
SWT:
    组件:
        Text 输入框
        Button 按钮
        Browser 浏览器
    事件:
        addSelectionListener方法，new SelectionAdapeor()类作为参数，或实现SelectionListener接口的类
ANNOTATION API:
    @PostConstruct: 将于构建组件时被调用
    @PreDestroy: 将于摧毁组件前被调用
    @Focus: 当组件或得焦点时被调用
    @Persists: 当保存状态改变时被调用
    @PersistState: 在@PreDestroy及摧毁组件前被调用，主要用于保存Persist信息
TIPS:
    关于事件参数，*Adapter类为实现了默认参数的*Listener类，无须强制重载
```
