---
layout: post
title: "js函数文件排序化"
date: 2014-04-08 12:19:22 +0800
comments: true
categories:
- other
tags:
- c++
- javascript
- tools
---
因为本人的某些小强迫症，写了一个格式化并根据js函数名排序的c++程序，此作mark
``` cpp
#include <stdio.h>
#include <map>
#include <string>
#include <iostream>
using namespace std;
int main() {
    freopen("in.js", "r", stdin);
    freopen("out.js", "w", stdout);
    string str, name, content;
    map<string, string> mp;
    char ch;
    while((ch = getchar()) != EOF) {
        str += ch;
    }
    for(int i = 0; i < str.size(); i++) {
        if(str.size() - i >= 8 && str.substr(i, 8) == "function") {
            int l = i + 9;
            int r = i + 9;
            while(str[r] != '{') {
                r++;
            }
            name = str.substr(l, r - l);
            l = r;
            r++;
            int g = 1;
            while(1) {
                ch = str[r++];
                if(ch == '{') {
                    g++;
                }
                else if(ch == '}') {
                    g--;
                }
                if(g == 0) {
                    break;
                }
            }
            content = str.substr(l, r - l);
            i = r;
            mp[name] = content;
        }
    }
    for (map<string, string>::iterator i = mp.begin(); i != mp.end(); ++i) {
        cout << "function " << i -> first  << i -> second << endl << endl;
    }
    return 0;
}
```