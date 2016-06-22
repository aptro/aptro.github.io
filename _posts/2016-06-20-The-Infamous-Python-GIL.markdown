---
layout: post
title:  "The Infamous Python GIL"
date:   2016-06-20 00:00:00 +0530
categories: Programming Language
tags: [Python, GIL, CPython]
---

When I started programming in python, I used to came across about the discussion regrading the Gil implementation in CPython which restricts the power of multicore machines. 

**So What Exactly is GIL?**

In CPython, the global interpreter lock, or GIL, is a mutex that prevents multiple native threads from executing Python bytecodes at once. This lock is necessary mainly because CPython's memory management is not thread-safe. (However, since the GIL exists, other features have grown to depend on the guarantees that it enforces.)

You can find more about it at the python [offical wiki](https://wiki.python.org/moin/GlobalInterpreterLock)


After searching and reading a lot of articles about the GIL and it's implementation I found a great talk by David Beazley which provides a deep down dissection of GIL. 
You can watch the Video here.

**Inside The Python GIL By David Beazley**
<br>
<iframe width="480" height="360" src="https://www.youtube.com/embed/ph374fJqFPE" frameborder="0" allowfullscreen></iframe>
<br>
[Here's the slide](http://www.dabeaz.com/python/GIL.pdf)

You can find the slides from Beazley's Personal blog and much more about python and [Gil](http://www.dabeaz.com/GIL/).


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-42894049-2', 'auto');
  ga('send', 'pageview');

</script>
