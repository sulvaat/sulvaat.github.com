---
layout: post
title: "Using dwm Continued"
date: 2012-03-16 08:20
comments: true
categories: [Arch, dwm, Linux] 
---
In my last guide, I quickly skimmed over the basics of getting dwm going in an arch linux machine. Now lets get some post-install configureation to get something that looks nice as well as works nice.

<h2>Urxvt</h2>
We told dwm to use dwm last time so lets get the stuff most users are looking for in a terminal - mainly transparency. Configuration for urxvt is done via the <code>.Xdefaults</code> file which it lookds for in <code>$HOME</code>.

```
URxvt*termName: rxvt

## borderless and no scrollbar
 URxvt*scrollBar_right: false
 URxvt*scrollBar: false
 URxvt*borderLess: false

## teh transparency stuff
 URxvt*inheritPixmap: true
 URxvt*tintColor: white
 URxvt*shading: 40

## change default colors
 URxvt*background: #000000
 URxvt*foreground: #3300ff
 URxvt*color0: #000000
 URxvt*color1: #A80000
 URxvt*color2: #00A800
 URxvt*color3: #A85400
 URxvt*color4: #0000A8
 URxvt*color5: #A800A8
 URxvt*color6: #00A8A8
 URxvt*color7: #A8A8A8
 URxvt*color8: #545054
 URxvt*color9: #F85450
 URxvt*color10: #50FC50
 URxvt*color11: #F2FC50
 URxvt*color12: #5054F8
 URxvt*color13: #F854F8
 URxvt*color14: #50FCF8
 URxvt*color15: #F8FCF8
```

My <code>.Xdefaults</code> is a good start but by far not all the things urxvt can do.
<h2>Getting around dwm</h2>

A quick list of the most used hotkeys in dwm

<ul>
<li>alt+q - Bails out of dwm and brings you back to the command prompt.</li>
<li>alt+shift+c - Simply closes the current window.</li>
<li>alt+1-5 - Switches your desktop, holding shift while doing this moves the current window to that desktop.</li>
<li>alt+shift+enter - Spawns a terminal window.</li>
</ul>

Thats all for now, going off to D.C later to the Japan Association to meet a friend!

