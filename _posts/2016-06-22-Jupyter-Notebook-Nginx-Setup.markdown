---
layout: post
title:  "Jupyter Notebook and Nginx Setup"
date:   2016-06-22 00:00:00 +0530
categories: Server Architecture
tags: [Jupyter, Python, Nginx, Websocket, DataScience, Upstart, Ubuntu]
---

The Jupyter Notebook is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. Uses include: data cleaning and transformation, numerical simulation, statistical modeling, machine learning and much more.

Jupyter project had a long history of development, It started with the Ipython project which provides a rich set of tools for computing and visualization with Python at it's core. In the recent years the Ipython project broke into small components and the Kernal is the core of Jupyter.

Jupyter supports multiple programming languages.

For more information [click here](http://jupyter.org/)



**Jupyter Installation**


I would suggest installing from continuum anaconda project. It provides a seemless package management and virtual env setup tool. And also provides a rich set of libraries bundled with the setup. You can find the instruction [here](https://www.continuum.io/downloads)



**Setting up the Notebook Server**


You can start the notebook server as: 

{% highlight bash linenos %}

jupyter notebook
#for all the args
jupyter notebook --help-all
{% endhighlight %}

The Notebook is a Python tornado Server which serves the Terminal and kernal UI.


**Demonizing the Notebook Server For Ubuntu**

{% highlight bash linenos %}
touch /etc/init/yourupstartjobname.conf
#content for your Upstart file
description "Service for jupyter notebook"
author      "You"

start on filesystem or runlevel [2345]
stop on shutdown
respawn

script
    echo $$ > /var/run/jupyter.pid
    exec /pathto/anaconda3/bin/jupyter notebook --no-browser 
    --NotebookApp.allow_origin='*' --notebook-dir='/pathtoworkspace'

end script

pre-stop script
    rm /var/run/jupyter.pid
end script
{% endhighlight %}


**Setting Up Nginx server**


As the Notebook server runs On Tornado which uses the websockets for some part of the Client Interaction. Standard nginx proxy pass uses the Http protocal. So we need to add some configuration to work. 

For Interacting with the Terminal and And Kernal it uses the WSS(websocket protocal). You can find more about this [here](https://github.com/jupyter/notebook/issues/625#issue-112465411)

**Heres My Nginx configuation.**

{% highlight nginx linenos %}
upstream notebook {
    server localhost:8888;
}
server{
listen 80;
server_name xyz.abc.com;
location / {
        proxy_pass            http://notebook;
        proxy_set_header      Host $host;
}

location ~ /api/kernels/ {
        proxy_pass            http://notebook;
        proxy_set_header      Host $host;
        # websocket support
        proxy_http_version    1.1;
        proxy_set_header      Upgrade "websocket";
        proxy_set_header      Connection "Upgrade";
        proxy_read_timeout    86400;
    }
location ~ /terminals/ {
        proxy_pass            http://notebook;
        proxy_set_header      Host $host;
        # websocket support
        proxy_http_version    1.1;
        proxy_set_header      Upgrade "websocket";
        proxy_set_header      Connection "Upgrade";
        proxy_read_timeout    86400;
}
}

{% endhighlight %}

 
 **NOTE:** 
 If you are using Apache Server or AWS ELB you need similar kind of tweaks to work for you.



<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-42894049-2', 'auto');
  ga('send', 'pageview');

</script>





