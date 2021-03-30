---
layout: post
title:  "An overview of Git"
description: "Git and GitHub"
date:   2021-03-29 11:03:42 +0300
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
It is important to declare yourself to Git using your email and password before doing any operation. Use these commands to declare:
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

## Branching and Merging using Git
Git provides very powerful features called branching and merging. Branching is used to support parallel developments and gives a lot of flexibility in workflow. Merging helps to combine the changes of the parallel developments made in the separate branches.

### Creating a new branch in the loacl repository
You can create a new branch in the local repository called trial by running:
{% highlight ruby %}
git checkout -b trial
# you can also use
git branch trial
{% endhighlight %}

Switch to the new branch using:
{% highlight ruby %}
git checkout trial
{% endhighlight %}

To find out the branches in your repository and which ones you are working on, use:
{% highlight ruby %}
git branch
{% endhighlight %}

### Committing to the new branch
Now that we have changed to the trial branch, let's make some changes to our file and commit to the trial branch. Follow the *git add* and *git commit* commands as discussed earlier to commit to the new branch. In order to confirm that the commit, use *git log* as also discussed earlier.

### Merging branches in Git
Merging is done when we want to combine changes made in different branches on the repository. This cane however develop conflicts in the process, if there are some parts of the files with different information.
For our project, the trial branch is ahead of the master branch by one commit. The changes in the trial branch can be implemented in the master branch by first switching to the master branch, then doing the merge:
{% highlight ruby %}
# switch to master branch
git checkout master
# merge changes into master
git merge trial
{% endhighlight %}

## The remote reopsitory
* For now we have been working on the remote repository and we are going to look at working on the remote repository. In case of collaborations, other developers can only see the code on the remote repository.
![remote repo demo](/assets/images/remote.jpeg)
* We are going to use GitHub for the remote repository. Visit [GitHub](https://github.com) to create your account if you don't have one yet. 
* When this is done, create a repository and give it a name. On opening the repository, you will find a screen like this, highlighting the link to the repository.
![remote repo link](/assets/images/remote_link.png)
* To set up this remote repo with your local repo, use the following command:
{% highlight ruby %}
git remote add origin [url]
{% endhighlight %}

### Pushing changes from the local repository
We can now push changes committed from the local repository to the remote repository using the *git push* command:
{% highlight ruby %}
git push -u origin [branch name]
{% endhighlight %}
This will push changes from the current branch in the local repository to the same branch in the remote repository.

## Conclusion
Thank you for following through to the end. These are the most basic commands of Git. There are more advanced features that you will have to explore and can visit the [GitHub documentation reference](https://git-scm.com/doc). With this, you can work with Git on simple projects.