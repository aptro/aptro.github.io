---
layout: post
title:  "Golang And Its Concurrency Model"
date:   2016-08-12 00:00:00 +0530
categories: Programming Language
tags: [Golang, Concurrency, Parallelism, Google]
---

Go is an open source system programming language built by Robert Griesemer, Rob Pike, and Ken Thompson at Google.
Golang has built in Concurrency model, syntax similar to a scripting language(with strictly typed), rich import system which makes a good 
choice for building high perfomance micro services with less lines of code than c/c++/java.

According to the creaters of Golang, it is not a completely new design but combines the goodness of both the worlds, 
it takes CSP (Communicating sequential processes) by Tony Hoare as building blocks for its Concurrency Model. But when it comes to Concurrency, Parallelism
most of the developer things its same. 


**Here's a talk by Rob Pike which will help you the basic difference between Concurrency and Parallelism**

<iframe src="https://player.vimeo.com/video/49718712?color=a086ee&title=0&byline=0&portrait=0" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/49718712">Rob Pike - &#039;Concurrency Is Not Parallelism&#039;</a> from <a href="https://vimeo.com/herokuwaza">Waza</a> on <a href="https://vimeo.com">Vimeo</a>.</p>


for more information go to [golang blog](https://blog.golang.org/concurrency-is-not-parallelism)

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-42894049-2', 'auto');
  ga('send', 'pageview');

</script>