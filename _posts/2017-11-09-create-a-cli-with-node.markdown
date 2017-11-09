---
layout: post
title:  "Creating a CLI with Node.js"
date:   2017-11-09 16:52:00 -0500
categories: node.js cli tutorial
---

When you find yourself repeating the same tasks over and over again, it's often tempting to want to automate that task as a script or command line tool. Today I'm going to explain creating a command line tool with JavaScript and NPM. Why? JavaScript / Node.js has a robust ecosystem with a huge number of open source packages that are very handy in scripting. Also, because JavaScript is so ubiquitous these days, your tool is just an `npm install` away for most developers. The multitude of packages plus the distribution of NPM makes JavaScript an attractive scripting language.

I'm going to explore this topic by explaining how I created my own command line tool called `webgate`. `webgate` is a productivity tool I created to block or unblock certain websites by editing my `etc/hosts` file. It makes for a good example project because it accomplishes a very specific task, and editing some strings in a file is trivial enough that we can focus on the CLI itself.

Blocking a website with your hosts file is simple enough, you simply map the domain to your loopback IP address 127.0.0.1. For example, to block Facebook, we would add the following line to `/etc/hosts`:

`127.0.0.1 www.facebook.com`

This tells the OS to redirect any URL requests with the host `www.facebook.com` to the IP address `127.0.0.1`, which does not serve traffic and will fail to load. It will work across all browsers and users across the machine. It's mentioning that it's easily circumventable by using a proxy server, so don't attempt to use this as a content filtering tool or enterprise firewall system. It is, however, enough work to change that I often lose motivation if I try to knee-jerk visit my favorite social media sites.
