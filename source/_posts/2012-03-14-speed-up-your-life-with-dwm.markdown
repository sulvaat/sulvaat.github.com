---
layout: post
title: "Speed Up Your Life With dwm"
date: 2012-03-14 11:57
comments: true
categories: [Arch, Linux, dwm] 
---
Good X window managers make life good. Unless you're into bloated desktop enviroments a simple X window manager is plenty sufficiant. Here is how to setup a slightly less basic dwm. This is mostly taken from the <a href="https://wiki.archlinux.org/index.php/Dwm#Customizing_config.h">ArchWiki</a> with a few added comments. Some steps have been simplified but helper applications like conky and dmenu have been split up.

First get what we need to install dwm:
```
# pacman -S abs dmenu
```
If you diddn't already have base-devel selected at install, add it now.

Now copy the scipts from the dwm community:
``` 
# abs community/dwm
$ cp -r /var/abs/community/dwm ~/dwm && cd ~/dwm
```
Now that we have a bare copy of dwm in our user directory, lets configure. dwm is mainly configured through its <code>config.h</code> file. 
```
/* appearance */
static const char font[]            = "-*-terminus-medium-r-*-*-16-*-*-*-*-*-*-*";
static const char normbordercolor[] = "#444444";
static const char normbgcolor[]     = "#333333";
static const char normfgcolor[]     = "#bbbbbb";
static const char selbordercolor[]  = "#005577";
static const char selbgcolor[]      = "#333333";
static const char selfgcolor[]      = "#3300ff";
static const unsigned int borderpx  = 1;        /* border pixel of windows */
static const unsigned int snap      = 32;       /* snap pixel */
static const Bool showbar           = True;     /* False means no bar */
static const Bool topbar            = True;     /* False means bottom bar */
```
Most of it is self explanitory here

For:
<ul>
<li><code>normbgcolor[]</code> I like dark since it is easy to contrast with...but not black so #333333
<li><code>normfgcolor[]</code> I picked a nice shade of blue from a list of web colors (easy to google for) #bbbbbb
<li> also not that I made <code>selbgcolor[]</code> and <code>selfgcolor[]</code> go with the same dark theme.
</ul>

Now lets set a good terminal emulator. I like urxvt just because it was the easiest to make look pretty. 
```
# pacman -S rxvt-unicode
```
Now lets set dwm to use it when e press <code>alt+shift+enter</code>
```
/* commands */
static const char *dmenucmd[] = { "dmenu_run", "-fn", font, "-nb", normbgcolor, "-nf", normfgcolor, "-sb", selbgcolor, "-sf", selfgcolor, NULL };
static const char *termcmd[]  = { "urxvt", NULL };
```
For the most part you just need to change the line above with urxvt, the rest tells dwm about how to theme dmenu, same as above.

Now lets install (whew!)
```
$ makepkg -g >> PKGBUILD
$ makepkg -efi --skipinteg
```
Now lets get conky and set it up for our status bar!
```
# pacman -S conky
```
Conky needs to have it's output sent to the status bar <code>xsetroot -name</code>. Add this to your <code>~/.xinitrc</code>
```
conky | while read -r; do xsetroot -name "$REPLY"; done &
exec dwm
```
Save and close that, then open up your conkyrc or <code>/etc/conky/conky.conf</code>. Below is a snipt from mine which is set up for a dual core cpu and wlan0 as the network to display stats from.
```
out_to_console yes
out_to_x no
background no
update_interval 2
total_run_times 0
use_spacer none

TEXT
${cpu cpu1}% | ${cpu cpu2}% :: ${acpitemp}c :: ${downspeed wlan0}D | ${upspeed wlan0}U :: ${time %a %b %d %I:%M%P}
```
We are finally finished! Enjoy you're new dwm desktop. I will make another post shortly with the kep combinations and other ways that I have found to speed up workflow.
