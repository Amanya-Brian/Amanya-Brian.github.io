---
layout: post
title:  "An overview of Git"
description: "Git and GitHub"
date:   2021-03-24 12:03:42 +0300
categories: jekyll update
---
## What is Git?
Git is software for tracking changes in different files, usually used for coordinating work among programmers and teams collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows. It makes sure that there are no conflicts in the code of the developers.

### Main features of Git
* Git is a content tracker and can be used to store content. This makes it a good control system.
* The content that is stored keeps changing as more code is added. As a versiono control system, it keeps a history of what changes have been made as some developers work in parallel. It uses features like merging and branching that will be discussed later.
* Git has a remote repository that is stored on the server and a local repository that is stored on the computers of the various developers. This makes the same code available to all the computers of the developers. This  makes Git a distributed 
version control system.

## Let's get started with Git
To start, ensure that Git is installed on your machine. Check if Git is installed on your machine by running:
{% highlight ruby %}
git --version
{% endhighlight %}
It is important to declare yourself to Git using youor email and password before doing any operation. Use these commands to declare:
{% highlight ruby %}
git config --global user.name "Your Name Comes Here"
git config --global user.email you@yourdomain.example.com
{% endhighlight %}
* Create a simple project on your machine and *cd* into the directory.
* Add a local git repository using this command:
{% highlight ruby %}
git init
{% endhighlight %}
* Create a file in that repository and add some code into it.

### Staging and commiting code
Staging is the process of adding code to a "waiting area" called the staging area where we keep track of the files that need to be committed. To add the file into the staging area, use this command to add all changed files:
{% highlight ruby %}
git add .
{% endhighlight %}

### Committing code
Committing is the process of adding the staged files into the local repository. Commits are made with a message to indicate what changes have been made to the files. Use this command to commit the changes to the file:
{% highlight ruby %}
git commit -m "commit-message"
{% endhighlight %}

### Git status and Git log
* These commands are used to show which changes have been made in our projects. The difference is that *Git status* shows which files have been added to the staging area and those that haven't been added. In the current directory, make a change in the file and run this command in the terminal:
{% highlight ruby %}
git status
{% endhighlight %}
* In our case, it will show that the file has been edited but not added to the staging area. 
* Add the file to the staging area and commit the file. athen run git status and see that the file has been commited.
* Git log however shows all the commits that have been made up to now. It includes details of the author of the commit, date of the commit and the commit message. Run this command in your terminal to confirm:
{% highlight ruby %}
git log
{% endhighlight %}

## Branching using Git
