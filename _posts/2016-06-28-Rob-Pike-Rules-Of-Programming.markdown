---
layout: post
title:  "Rob Pike's 5 Rules of Programming"
date:   2016-06-28 06:30:00 +0530
categories: Programming Language
tags: [Golang, Rob Pike, UTF-8, Plan9]
author: Akash Patro
---

Rob Pike is the cocreator of [Golang](https://golang.org/) and creator of Plan 9 OS and UTF-8.


**Rob Pike's 5 Rules of Programming**

**Rule 1.** 

You can't tell where a program is going to spend its time. Bottlenecks occur in surprising places, so don't try to second guess and put in a speed hack until you've proven that's where the bottleneck is.

**Rule 2.** 

Measure. Don't tune for speed until you've measured, and even then don't unless one part of the code overwhelms the rest.

**Rule 3.** 

Fancy algorithms are slow when n is small, and n is usually small. Fancy algorithms have big constants. Until you know that n is frequently going to be big, don't get fancy. (Even if n does get big, use Rule 2 first.)

**Rule 4.** 

Fancy algorithms are buggier than simple ones, and they're much harder to implement. Use simple algorithms as well as simple data structures.

**Rule 5.** 

Data dominates. If you've chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming.



[Source](http://users.ece.utexas.edu/~adnan/pike.html)


**Other Threads About the topic**

[Reddit](https://www.reddit.com/r/programming/comments/29yj61/rob_pikes_5_rules_of_programming/)

[Y Combinator](https://news.ycombinator.com/item?id=7994102)

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-42894049-2', 'auto');
  ga('send', 'pageview');

</script>

