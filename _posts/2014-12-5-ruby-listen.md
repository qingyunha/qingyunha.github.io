---
layout: post
title:  "ruby listen"
date:   2014-12-5 18:50:43
categories: ruby
---

项目主页的简介: 
The Listen gem listens to file modifications and notifies you about the changes.

这个项目目前有856个commit,77次release,40个contributor.

学习这个项目的目的是我想了解是否有一些机制可以监控文件的变化,就像respec,每次文件发生改变时测试会自动执行,我最初猜想是
可以根据文件的修改时间来判断文件是否改变.

我在本地clone了这个项目,它的基本用法是

{% highlight ruby %}
listener = Listen.to('dir/to/listen', 'dir/to/listen2') do |modified, added, removed|
  puts "modified absolute path: #{modified}"
  puts "added absolute path: #{added}"
  puts "removed absolute path: #{removed}"
end
listener.start # not blocking
sleep
{% endhighlight %}

尝试阅读源码,发现了这个celluloid,一个多线程编程框架,放弃.....

于是我准备从它的第一个发行版本开始学习.  
    `git checkout v0.1.0`  
    `git checkout -b 010`

##v0.1.0
- class Listener
- class Adapte

初始化一个listener,注册了要监控的目录和一个可以回调的代码块,每当这个目录下有变化时,这个代码块就会被调用.  
实例变量`@path`(二维Hash)保存了该目录下所有的文件和子目录的状态`File::Stat`,就是根据这个Stat.ctime来判断文件是否改变.  
`@path`由方法`init_paths`完成,调用了标准库中的`find`方法,并略过了一些可以忽略的文件-`DEFAULT_INGONERD_PATHS`,`@ingonerd_paths`.  

listener负责对文件变化的检测,由方法`on_change`完成,这个方法由adapter调用,在这个版本中,只有一种adapter, Adapters::Polling,    
它通过轮询的方式每隔一个latency,就调用一次`on_change`


##v0.2.0
