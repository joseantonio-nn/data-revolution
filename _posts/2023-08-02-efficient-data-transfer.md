---
layout: post
title:  "Efficient Data Transfer for Data Science"
subtitle: "Get to know the SCP command!"
date:   2023-08-02 11:50:27 +0200
categories: misc
---

## Introduction

At some point in your professional data science career, sooner than later, you will face the following problem: you have just generated a massive dataset (> 50 GB) that you need to move from one cloud server to another in order to continue working with it, for either structural or organizational reasons within your company/department. 

Given this situation, you have two options; either you rely on the office Wi-Fi to download it to your local machine and re-upload it later, using WinSCP (please don't do this, it will be the longest coffee break ever) or you become the ultimate data-transfer-hacker taking advantage of `SCP (Secure Copy Protocol)` command for transferring big data files between servers securely and quickly (this sounds much more exciting imho). In this post, we will cover the benefits of using SCP for data transfer and provide step-by-step commands for transferring big data files between servers.
<br>
<br>

## Why Choose SCP for Data Transfer?

~~Why not? As if there were many more options lol~~. Anyway, for the sake of the post and SEO dictatorship, these are the main strenghts of this protocol:

- **Security**: SCP utilizes `SSH (Secure Shell)` for data transfer. This means that your data is encrypted during transmission, making it an ideal choice for sensitive data.

- **Efficiency**: as expected, SCP is designed for efficient file transfer, and it can handle large files quickly and reliably.

- **Simplicity**: SCP is easy to use, with a syntax similar to the traditional UNIX `cp` command. It allows for seamless data transfer with just a single command.

- **Cross-platform Support**: SCP is supported on various operating systems, including Linux, macOS, and Windows (with third-party tools like WinSCP).

But the most important, underlying super-secret knowledge, which probably makes this technology a transfer protocol on steroids for you, is the fact that, the servers you are working on are most likely **very close** to each other \*and\* the network used to transfer files is Microsoft's, Amazon's or whatever provider your wise and always-willing-to-help IT department chose. That means that you don't have to rely on your ~~crappy~~ office Wi-Fi for high speeds. I personally find it very useful.
<br>
<br>

## Step-by-Step Guide: Transferring Big Data Files with SCP

### Transfer files between Two Remote Servers:
Okay, enough talking. I give what I promise. Here you are the command to copy a big data file from one remote server to another:

{% highlight ruby %}
scp username@origin_server_ip:/path/to/file username@destination_server_ip:/path/to/destination/
{% endhighlight %}

I'd do this if I had a user in both machines called "chatgptwrotethis":

{% highlight ruby %}
scp chatgptwrotethis@203.0.113.10:/home/chatgptwrotethis/data/data.csv chatgptwrotethis@198.51.100.5:/home/chatgptwrotethis/backups/
{% endhighlight %}

Note that you can also use the server's name instead of its ip, like this:

{% highlight ruby %}
scp chatgptwrotethis@server1:/home/chatgptwrotethis/data/data.csv chatgptwrotethis@server2:/home/chatgptwrotethis/backups/
{% endhighlight %}

How to retrieve the server's name? Just type one of the following commands (they both output the same information):
{% highlight ruby %}
uname -n
{% endhighlight %}

or

{% highlight ruby %}
hostname
{% endhighlight %}
<br>

### Transfer files from Local to Remote Server:
Because it's free and almost effortless, I'll teach you how to copy data files from your local machine to a remote server and viceversa. Use the following command for the first case:

{% highlight ruby %}
scp /path/to/local/file username@remote_server:/path/to/destination/
{% endhighlight %}

Example:

{% highlight ruby %}
scp final_dataset_ofc.csv chatgptwrotethis@203.0.113.10:/home/chatgptwrotethis/data/
{% endhighlight %}
<br>

### Transfer files from Remote to Local Server:
To copy a big data file from a remote server to your local machine, use the following command:

{% highlight ruby %}
scp username@remote_server:/path/to/remote/file /path/to/destination/
{% endhighlight %}

Example:

{% highlight ruby %}
scp chatgptwrotethis@203.0.113.10:/home/chatgptwrotethis/data/final_dataset_ofc.csv /Users/chatgptwrotethis/Documents/
{% endhighlight %}
<br>

## Optimizing Data Transfers for Data Science Projects

Before you go, there are some more settings you might consider to smooth the whole process if you are struggling with freaking big data files.

- **Compression**: you can compress your data files before transferring them to reduce transfer time and bandwidth usage. Use tools like `gzip` or `tar` to create compressed archives.

- **Parallel Transfers**: for even faster data transfer, consider using parallel SCP tools like `pscp` or `parallel-scp` which utilize multiple connections to transfer files simultaneously.

- **Bandwidth Control**: SCP does not provide native bandwidth control, so if for whatever reason you need to limit SCP's data transfer rate, you can use external tools like `trickle`.
<br>
<br>

## Conclusion

The SCP command is a powerful tool that simplifies and secures the transfer of big data files between servers, making it an indispensable asset for data science professionals. I hope you enhanced your productivity and streamline for your data science projects reading this post. Continue your data revolution, see you soon!

## TL;DR

{% highlight ruby %}
scp /path/to/local/file username@remote_server:/path/to/destination/
{% endhighlight %}