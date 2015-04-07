---
layout: post
title:  "Build Awesome Command-Line App"
date:   2015-1-1 21:50:43
categories: ruby
---

What I learned from this book is that some convention of command-line apps. Now I can distinct argument and
option. There are two kind of option, flag and switch. Mostly the flag follow argument. Also, the option has
two form----long-form and short-form. The long-form flag can use '=' to argument.

The invocation syntax or usage should follow a fairly strict format. It will be as follows:    
	executable [options] arg_name1 arg_name2

There are two useful ruby libraries OptionParese and GLI.

Others: Adding colors using ANSI Escape. There is also a gem can make it simple -- rainbow.
