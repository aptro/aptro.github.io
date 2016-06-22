---
layout: post
title:  "Jupyter Notebook and Nginx Setup"
date:   2016-06-22 00:00:00 +0530
categories: Server Architecture
tags: [Jupyter, Python, Nginx, Websocket, DataScience, Upstart, Ubuntu]
---

What is Jupyter?


As Mentioned in the official Page : The Jupyter Notebook is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. Uses include: data cleaning and transformation, numerical simulation, statistical modeling, machine learning and much more.

Jupyter project had a long history of development, It started with the Ipython project which provides a rich set of tools for computing and visualization with Python at it's core. In the recent years the Ipython project broke into small components and the Kernal is the core of Jupyter.

Jupyter supports multiple programming languages.

For more information [click here](http://jupyter.org/)



Jupyter Installation


I would suggest installing from continuum anaconda project. It provides a seemless package management and virtual env setup tool. And also provides a rich set of libraries bundled with the setup. You can find the instruction [here](https://www.continuum.io/downloads)



Setting Up a Notebook Server


You can start the notebook server as: 

{% highlight bash linenos %}

jupyter notebook
#for all the args
jupyter notebook --help-all
{% endhighlight %}

The Notebook is a tornado Server which serves the Terminal and kernal UI.


Demonizing the Notebook Server For Ubuntu

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
    --NotebookApp.allow_origin='*' --notebook-dir='/pathtojupyter_workspace'

end script

pre-stop script
    rm /var/run/jupyter.pid
end script
{% endhighlight %}



 









