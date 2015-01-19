---
layout: post
title: "csv转json文件"
date: 2014-04-11 10:01:44 +0800
comments: true
categories:
- other
tags:
- csv
- json
- javascript
- tools
---
今天因为需要帮一个同事的新闻内容录入为html, 每次手改不方便，所以就弄了个csv(excel)转json的c++程序，然后再利用ejs把它渲染成网页，打开渲染好的网页再保存(不能保存源文件，不然还是空的)，就可以把内容弄成一个html了，此作mark，以下为程序
``` cpp
// convert.cpp
#include <stdio.h>
#include <string>
#include <iostream>
using namespace std;
int main() {
    freopen("in.csv", "r", stdin);
    freopen("json.js", "w", stdout);
    string str, s[50];
    int g = 0;
    int status = 0;
    char ch;
    str = "";
    while((ch = cin.get()) != EOF) {
        str += ch;
    }
    for(int i = 0; i < str.size(); i++) {
        if(status == 0) {
            if(str[i] == '\"') {
                status = 1;
            } else {
                s[g] += str[i];
                status = 2;
            }
        } else if(status == 1) {
            if(str[i] == '\"') {
                if(i + 1 >= str.size()) {
                    g++;
                    break;
                } else if(str[i + 1] == '\"') {
                    s[g] += '\"';
                    ++i;
                } else if(str[i + 1] == ',') {
                    status = 0;
                    ++g;
                    ++i;
                } else if(str[i + 1] == '\n') {
                    status = 0;
                    ++g;
                    ++i;
                }
            } else {
                s[g] += str[i];
            }
        } else if(status == 2) {
            if(str[i] == ',') {
                ++g;
            } else if(str[i] == '\n') {
                ++g;
            } else {
                s[g] += str[i];
            }
        }
    }
    int x = 0;
    puts("var data = [");
    string name[] = {"title", "detail", "img", "url"};
    for(int i = 0; i < g; i++) {
        if(x == 0) {
            if(i == 0) {
                puts("\t{");
            } else {
                puts("\t},");
                puts("\t{");
            }
        }
        cout << "\t\t" << name[x] << ": \"" << s[i] << "\"" << (x == 3 ? "" : ",") << endl;
        x = (x + 1) % 4;
    }
    puts("\t}");
    puts("]");
    return 0;
}
```