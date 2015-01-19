---
layout: post
title: "用octopress搭建github page"
date: "2014-04-28 14:32:04 +0800"
comments: true
categories:other
tags:- blog
---
尝试和失败了无数次，终于把博客搭好了，以下简述下我的搭建过程。

引言

> [Octopress](http://octopress.org/)是利用[Jekyll](http://jekyllrb.com/)博客引擎开发的一个博客系统，生成的静态页面能够很好的在[github page](https://pages.github.com/)上展现。号称是hacker专属的一个博客系统(A blogging framework for hackers.)

目录

1. 配置环境
2. 安装octopress
3. 配置github
4. 配置octopress
5. 开始部署
6. 完成
7. 一些小技巧

### 配置环境
安装octopress需要ruby和git环境，Mac OS 10.9 上自带有ruby和git环境，故不作述。
(大家可以检查下自己的ruby gem和git是否有正确配置好)

(以下命令请自觉用sudo来执行，不然可能有权限问题)

``` sh
ruby --version
git --version
gem --version
```
安装rbenv

``` sh
git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
# 用来编译安装 ruby
git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
# 用来管理 gemset, 可选, 因为有 bundler 也没什么必要
git clone git://github.com/jamis/rbenv-gemset.git  ~/.rbenv/plugins/rbenv-gemset
# 通过 gem 命令安装完 gem 后无需手动输入 rbenv rehash 命令, 推荐
git clone git://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
# 通过 rbenv update 命令来更新 rbenv 以及所有插件, 推荐
git clone https://github.com/rkh/rbenv-update.git ~/.rbenv/plugins/rbenv-update
```
然后把下面的代码放到`~/.bash_profile`里

``` sh
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```
### 安装octopress
通过以下命令安装

``` sh
git clone git://github.com/imathis/octopress.git octopress
cd octopress
```
接下来安装依赖项

``` sh
gem install bundle # 等待强迫症患者可以像我一样，在最后加个-V，这样它会告诉你已经进行到哪里
rbenv rehash
bundle install
```
安装默认的Octopress主题

``` sh
rake install # 若提示错误可尝试在其前加上bundle exec(原因是某些版本不一致)
```

### 配置github
要想把页面展示在[github](https://github.com/)上，请保证你已经注册了一个github帐号，然后创建一个名为`你的用户名.github.io`的仓库，并保存下它的github地址`example: https://github.com/yedeying999/yedeying999.github.io`

### 配置octopress
进入octopress文件夹

``` sh
cd octopress
```
编辑配置文件`_config.yml`，修改其中的`url`，填上刚刚的github仓库地址，然后还有就是`title` `subtitle` `author`这些，名字都写的很清楚了，根据自己的来填

接着，建议把文件末部的twitter, facebook, google plus等配置给注释掉，因为这些都是GFW以外的东西，会导致网页速度缓慢，同理，修改定制文件/source/_includes/custom/head.html 把google的自定义字体去掉。

### 开始部署
执行以下命令

``` sh
# 不行加bundle exec，原理同上，下同
rake setup_github_pages  #命令会要求我们输入github地址，还是刚刚那个仓库地址
```

``` sh
rake new_post['title']
```
然后进入`source/_post`中会看到20xx-xx-xx-title.md，title是自定义的，然后我们就可以通过编辑这个markdown文档来写博客啦，写完之后

``` sh
rake generate # 把source里面的内容，生成到_deploy文件夹
rake deploy   # 把_deploy的内容上传到github上
# 以上两命令在每次写新博文时都要执行一次
rake preview  # 可通过该命令在本地浏览生成的博客，地址http://localhost:4000
```
### 完成
做完这一切后，我们就可以通过`http://你的用户名.github.io`来访问你的博客了

### 一些小技巧
作为一个懒人，我当然不想每次都敲那么长命令来写博客啦，所以

``` sh
vim ~/deploy.sh
vim ~/new.sh
```
分别加入以下内容

``` sh deplog.sh
cd ~/octopress
bundle exec rake generate
bundle exec rake deploy
```

``` sh new.sh
cd ~/octopress
bundle exec rake new_post[$1]
```

然后，为普通用户添加执行权限

``` sh
sudo chmod a+x deploy.sh
sudo chmod a+x new.sh
```

大家应该都看得出，deploy就是发布的懒操作，而new就是新建博客的懒操作，用法如下：

``` sh
./new.sh name # name就是新博文的名字
./deploy.sh
```