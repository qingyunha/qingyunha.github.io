---
layout: post
title:  "ruby standard library"
date:   2015-1-3 10:50:43
categories: ruby
---

## Abbrev
Given a set of strings, calculates the set of unambiguous abbreviations for those strings and
returns a hash where the keys are all the possible abbreviations and the values are the full
strings.

The key point is the loop  
  `len = abbrev.rindex(/[\w\W]\z/)`  
  `abbrev = abbrev[0,len]` 

And also utilize the Open Class  
{% highlight ruby %}
  class Array
    def abbrev(pattern = nil)
      Abbrev.abbrev(self,pattern)
    end
  end
{% endhighlight %}

## Base64
Performs encoding and decoding of binary data using a Base64 representation. This allows
you to represent any binary data in purely printable characters.

It just use the pack and unpack method of Array and String.  
  `[bin].pack("m")`  
  `str.unpack("m")`  
  
## Delegetor
object delegation is a way of composing objects—extending an object with the capabilities
of another—at runtime.

## GServer
Simple framework for writing TCP servers. Subclasses the GServer class, sets the port (and
potentially other parameters) in the constructor, and then implements a serve method to
handle incoming requests.  
GServer manages a thread pool for incoming connections, so your serve method may be
running in multiple threads in parallel.  
You can run multiple GServer copies on different ports in the same application. 

# xmlrpc/httpserver
A simple HTTP server implemented by GServer
