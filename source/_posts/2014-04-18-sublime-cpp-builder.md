---
layout: post
title: "sublime c++ builder"
date: 2014-04-18 21:21:56 +0800
comments: true
categories:
- other
tags:
- editor
- sublime
---
RT, just mark
``` json
{
  "cmd": ["g++", "${file}", "-o", "${file_path}/${file_base_name}"],
  "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
  "working_dir": "${file_path}",
  "selector": "source.c, source.c++, source.cpp",
  "shell": true,
  "variants":
  [
    {
      "name": "Run",
      "cmd": [ "start", "${file_path}/${file_base_name}.exe" ]
    }
  ]
}
```