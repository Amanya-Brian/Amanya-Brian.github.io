---
layout: default
title:  "SSH Login without Password"
date:   2022-09-27 16:02:39 +0300
categories: jekyll update
---

# How to use SSH Login Without a Password
* You can login to a remote server without entering password in 3 simple steps using ssh-keygen and ssh-copy-id as explained in this article.

* ssh-keygen creates the public and private keys. ssh-copy-id copies the local-host’s public key to the remote-host’s authorized_keys file. ssh-copy-id also assigns proper permission to the remote-host’s home, ~/.ssh, and ~/.ssh/authorized_keys.

## Step 1: Create public and private keys using ssh-key-gen on local-host
{% highlight ruby %}
amanya@local-host$ [Note: You are on local-host here]

amanya@local-host$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/amanya/.ssh/id_rsa):[Enter key]
Enter passphrase (empty for no passphrase): [Press enter key]
Enter same passphrase again: [Press enter key]
Your identification has been saved in /home/amanya/.ssh/id_rsa.
Your public key has been saved in /home/amanya/.ssh/id_rsa.pub.
The key fingerprint is:
33:b3:fe:af:95:95:18:11:31:d5:de:96:2f:f2:35:f9 amanya@local-host
{% endhighlight %}

## Step 2: Copy the public key to remote-host using ssh-copy-id
{% highlight ruby %}
amanya@local-host$ ssh-copy-id -i ~/.ssh/id_rsa.pub remote-host
amanya@remote-host's password:
Now try logging into the machine, with "ssh 'remote-host'", and check in:

.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.
{% endhighlight %}

## Step 3: Login to remote-host without entering the password
{% highlight ruby %}
amanya@local-host$ ssh remote-host
Last login: Sun Nov 16 17:22:33 2008 from 192.168.1.2
[Note: SSH did not ask for password.]

amanya@remote-host$ [Note: You are on remote-host here]
{% endhighlight %}

**These steps did for me. They will also do the trick for you.**