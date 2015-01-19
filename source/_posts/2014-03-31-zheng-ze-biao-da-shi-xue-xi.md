---
layout: post
title: "正则表达式学习"
date: 2014-03-31 14:43:07 +0800
comments: true
categories:
- javascript
tags:
- regex
- javascript
---
#### 符号
```
/ 用于转义
^ 非集合中为行头，集合中为非
$ 行末，与^对应
* 闭包[0-n]
+ 不包括0的闭包[1-n]
? 匹配0或1次[0-1],?接其它量词(*,+,?,{})之后将变成非贪婪模式(默认贪婪)
. 匹配非换行符的所有字符
() 捕获括号，结果以[1],[2],...,[n]输出
(?:x) 非捕获括号，与()相反
x(?=y) 匹配x仅当x后有y,向后查询
x(?!y) 匹配x仅当x后无y,反向向前查询
x|y 或运算符
{n} 刚好匹配n个
{n,m} 匹配n-m个
[abc] 集合,匹配集合中的任一个
[a-c] 集合，连续写法
[^abc] 匹配不在集合的所有
[\b] 表示转义字符，而非元字符
\b 匹配单词边界
\B 匹配非单词边界
\d [0-9]
\D [^0-9]
\f 换页符
\n 换行符
\r 回车符
\s 空白符
\S 非空白符
\t tab
\v vertical tab
\w [A-Za-z0-9_]
\W [^A-Za-z0-9_]
\0 '\0'
\xhh 2位16进制转义
\uhhhh 4位16进制转义
```
#### 用法
string:
``` js
　str.replace(reg, s); //将str中匹配reg的内容替换为s,参数g以搜全局
　str.match(reg); //返回满足匹配的值
　str.search(reg); //返回满足匹配的索引
　str.split(reg); //以匹配内容为分割，返回数组
```
RegExp:
``` js
  reg.exec(str); //类似于str.match
  reg.test(str); //测试对否匹配str
```