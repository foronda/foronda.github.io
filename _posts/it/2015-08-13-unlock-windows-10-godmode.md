---
layout: post
title: "How to Unlock Windows 10 'GodMode'"
headline: GodMode!?
description: Shortcut to a list of every configurable items in windows 10
categories: IT
tags: how-to, windows10
published: true
---

### Windows 10 God Mode

Found this article [^1] online regarding some 'GodMode' configuration in Windows 10. Curious to what it was, I went ahead and unlocked it via an easy hack.

### Unlock God Mode You Ask?

#### Step 1: Create a new folder on your desktop

Right Click on Desktop > New folder (or CTRL + SHIFT + N).

#### Step 2: Rename the folder.

Name this folder the following, 

```
GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}
``` 

Actually, you can name the string before the **.** anything you want. For example

```
HelloWorld.{ED7BA470-8E54-465E-825C-99712043E01C}
```

Step 3: Open the new 'GodMode Shortcut'

The folder icon is replaced by an icon similar to a Control Panel icon immediately after renaming.

![Desktop Folder](https://dl.dropboxusercontent.com/u/33327425/images/it/godmode.png)

The list of configurable items that can be accessed in one 'GodMode' shortcut.

![Settings](https://dl.dropboxusercontent.com/u/33327425/images/it/godmode2.png)


While this may be convenient shortcut, I do not see myself using it as a way of accessing windows configurations. Maybe because I have become accostumed to the  Win + Q, Win + X shortcuts in finding specifically what controls I need without the touch of the mouse. Given that I manage an Active Direcoty domain at work, I would rather have a working Windows RSAT tools. Microsoft, I am patiently waiting. Having to remote into the domain controller to manage AD objects and users is so "time consuming"! :) 

##### References:

[^1]:http://www.thinkcomputers.org/how-to-unlock-windows-10-god-mode/

