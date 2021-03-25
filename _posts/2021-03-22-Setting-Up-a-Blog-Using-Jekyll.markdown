---
layout: post
title:  "Setting Up a Blog Using Jekyll"
description: "Setting up a blog using jekyll"
date:   2021-03-22 12:03:42 +0300
categories: jekyll update
excerpt_separator: <!--more-->
---

I tried setting up a blog using jekyll on both Windows Operating System and Ubuntu Operating system. 
<!-- more -->

Personally, it was easier for me to set it up on Ubuntu(20.04 to be specific) than on windows.
* When it comes to Ubuntu, we open the terminal and run:
{% highlight ruby %}
sudo apt-get install ruby-full build-essential zlib1g-dev
{% endhighlight %}
to install ruby and all its packages.

* Then we run: 
{% highlight ruby %}
gem install jekyll bundler
{% endhighlight %}
to install jekyll and bundler gems from Ruby.

* To confirm if Jekyll has been installed, run
{% highlight ruby %}
jekyll -v
{% endhighlight %}

* Then you're good to go!

The next challenge is start the blog app.
* For this, we open the terminal and run
{% highlight ruby %}
jekyll new <site_name>
{% endhighlight %}

We have now successfully set up a blog site using Jekyll, Congratulations! The next hurdle is to get the site 
running on our localhost.

* Change directory into the site directory
{% highlight ruby %}
cd <site_name>
{% endhighlight %}

* Then we run the jekyll serve command using the bundle gem
{% highlight ruby %}
bundle exec jekyll serve
{% endhighlight %}

From here, go to your browser and search 127.0.0.1:4000