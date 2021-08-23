---
layout: default
title:  "Security Shell(SSH) with GitHub"
date:   2021-08-23 08:41:39 +0300
categories: jekyll update
---

# Why opt for SSH Key?
1. Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username and personal access token at each visit.
2. Recently, GitHub phased out authentication usng email and password from the commandline, GitBash inclusive. This is why we need to set up SSH and be able to continue using our terminals to access Github.
3. Let us look at how to set up SSH.

# Steps to set up SSH keys
## Check for existing SSH key
1. Open your terminal and run this command:
{% highlight ruby %}
ls -al ~/.ssh
{% endhighlight %}
If there files in you .ssh directory, they will be listed. Public keys usually have a *.pub* extension. If you have existing keys, you need to add them to an ssh-agent. An ssh-agent is a background program that handles passwords for SSH private keys.

## Generate new SSH key
1. In your terminal, run this command using your github email 
{% highlight ruby %}
ssh-keygen -t ed25519 -C "your_email@example.com"
{% endhighlight %}
This email will create a new key that a new key using the provided email.
2. You will be asked to enter a directory in which to save the key. You are advised to use the default location by  pressing Enter.
3. Next, you will be asked to enter a passphrase that will substitute the email and password.
{% highlight ruby %}
>Enter passphrase (empty for no passphrase): [Type a passphrase]
>Enter same passphrase again: [Type passphrase again]
{% endhighlight %}

## Add the SSH key to your ssh-agent
1. If you don't want to reenter your passphrase every time you use your SSH key, you can add your key to the SSH agent, which manages your SSH keys and remembers your passphrase.
2. Now that you have a key generated, let's add it to the ssh-agent.
* Start the ssh-agent in the background
{% highlight ruby %}
eval "$(ssh-agent -s)"
#which will return this
Agent pid 59566
{% endhighlight %}
* Add your SSH private key to the ssh-agent. If your key has a different name, replace id_ed25519 with the name of your private key file.
{% highlight ruby %}
ssh-add ~/.ssh/id_ed255196
{% endhighlight %}
That is done, now we have to add the key to the GitHub account to be able to use it.

## Adding the key to your GitHub account.
Now that we have created a new key and added it to the ssh-agent, we must add the SSH key to the associated account on GitHub before you use the key to authenticate.
1. Copy the public key to your clip board. Locate the hidden *.ssh* folder, open the file and copy its contents.
2. Go to your GitHub account, click on your icon and go to settings. Then select SSH and GPG keys and Add a new key.
3. In the "Title" field, add a descriptive label for the new key.
4. Paste your key into the "Key" field.
5. Click Add SSH key.
6. If prompted, confirm your GitHub password.

## Changing the remote repository URL from HTTPS to SSH
The *git remote set-url* command changes an existing remote repository URL. The URLs are in this format:
{% highlight ruby %}
#HHTPS
https://github.com/USERNAME/REPOSITORY.git
#SSH
git@github.com:USERNAME/REPOSITORY.git
{% endhighlight %}
To change the existing remotes;
* List all the existing remotes:
{% highlight ruby %}
git remote -v
{% endhighlight %}
* Change the remote from HTTPS to SSH
{% highlight ruby %}
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
{% endhighlight %}
* List the remotes again to verify that it has been changed sucessfully.

There you have it! Now you can clone, pull, push and many others without using email and password for authentication.