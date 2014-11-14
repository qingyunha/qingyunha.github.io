---
layout: post
title:  "Jekyll and gitpages"
date:   2014-11-14 17:50:43
categories: jekyll
---

1. 在github上创建库username.github.io

2. 在本地克隆
   
   `git clone https://github.com/username/username.github.io`

3. 创建jekyll站点的目录结构
  
   `jekyll new .`

4. 在myblog主目录下创建文件RubyGems,内容为

   `source 'https://rubygems.org`

   `gem 'github-pages`

5. 安装相关的gem

   `bundle install`

6. 运行jekyll
  
   `bundle exec jekyll serve`

7. 推送到远程库
 
   `git add .`
   
   `git commit -m "Initial commit"`

   `git push orign master` (master不能省，因为远程库还没有任何分支） 



###参考
[Using jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/) 
