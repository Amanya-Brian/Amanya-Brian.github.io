---
layout: default
title:  "Contributing To Projects"
date:   2022-01-22 08:41:39 +0300
categories: jekyll update
---

# How To Contribute To Projects
There are many projects on GitHub and GitLab, some of which we would like to contribute to or we have been invited to contribute.

* Fork the Project
    - Go to the pproject you would like to contribute to and fork it.
    - Choose where to fork it to.

* Clone the forked repo to your machine
    - Use this command to clone the forked repo:
    {% highlight ruby %}
    git clone git@github.com:Username/ProjectName.git
    {% endhighlight %}

* Add the original Repository to the remotes of your cloned repo
{% highlight ruby %}
git remote add upstream url-to-original-repo
{% endhighlight %}
- Check if upstream url has been added to remotes
{% highlight ruby %}
git remote -v
{% endhighlight %}

* Create a new branch to make your changes
{% highlight ruby %}
git checkout -b branch_name
{% endhighlight %}

* Make the changes intended

* Stage the changes
{% highlight ruby %}
git add .
{% endhighlight %}

* Commit the changes
{% highlight ruby %}
git commit -m "suitable commit message"
{% endhighlight %}

* Push the changes to the remote repo
{% highlight ruby %}
git push origin branch_name
{% endhighlight %}

* Create a Pull Request
- Go to your forked repo and open a Pull Request

And that is it for your first time contribution!

# Submitting more changes on the same project
Assuming your Pull Request was approved and you want to continue contributing, you don't need to fork again.

* Go to the master branch of your forked repo
{% highlight ruby %}
git checkout master
{% endhighlight %}

* Get the changes from the Original repo's master to your local repo's master
{% highlight ruby %}
git fetch upstream
{% endhighlight %}

* Update the local master with the changes from the main repo
{% highlight ruby %}
git merge --ff upstream/master
{% endhighlight %}

* Checkout the new branch where to make changes
{% highlight ruby %}
git checkout -b new-branch
{% endhighlight %}

* Stage, commit and push the changes as before.

* Make a Pull Request for your changes to be reviewed.

**With this, you are able to contribute to a project.**