---
layout: post
title: "Easily Switch To USB Audio Output in Arch"
date: 2012-03-13 23:36
comments: true
categories: [Arch, Audio] 
---
Lets face it, switching audio outputs is a pain on linux. I made a quick script that you can place in /bin to make life easier. 

You will need to get asoundconf out of the AUR first, once thats ready to go:

```
$ asoundconf is-active
$ asoundconf list
```
```
sanae@MORIYA> asoundconf list
Names of available soundcards:
Intel 
CODEC // This is my USB DAC
```

This will print all the cards in your system. Remember them since you will make a script for each one now:

```
#!/bin/sh

asoundconf is-active
asoundconf list
asoundconf set-default-card Intel
```
```
#!/bin/sh

asoundconf is-active
asoundconf list
asoundconf set-default-card CODEC
```
Simple.

Now, move them to /bin so all you need to do is type intel or codec (in this case) to switch.

Enjoy.
