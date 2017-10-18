---
title: "Typing Unicode Characters in Ubuntu"
author: Sahil Ahuja
date: 2017-08-27T23:20:16+05:30
tags: [ "ubuntu", "webstorm", "unicode", "shortcuts" ]
categories: [ "guide" ]
---

Ever since I decided that <code>&#96;</code> was he best means to toggle Yakuake (which has been my lifeline for an integral part of the way I work for a long time now), typing <code>&#96;</code> whenever I needed it has been hell.

After going through a great deal and self doubt, the final outcome deserves being documented.

The way to type a backtick without using the backtick key is through its unicode. The following are the ways to type unicode:

### For General Use

`Shift + Ctrol + U` follow by the unicode and a `space` or `enter`.
Eg:  `Shift + Ctrol + U` 0060 `enter` converts to a ``` ` ```

*Reference:* https://help.ubuntu.com/community/GtkComposeTable 

### In Webstorm

Unfortunately the above methods don't work in Jetbrain IDEs. There's a great Jetbrains plugin to solve this problem: https://plugins.jetbrains.com/plugin/2162-string-manipulation

After installing this plugin, type `\u0060`, select it, and then `Alt + M`, `1`, `D` to convert it to ``` ` ```

#### Important unicode characters:
| Name        | Unicode | Character |
| ------------- |:-------------:| -----:|
| Backtick      |  ```0060```  | ``` ` ``` |
| Degrees       |  ```00b0```  | ``` ° ``` |
| Tick      |  ```2714```  | ``` ✔ ``` |
| Wrong      |  ```2715```  | ``` ✕ ``` |
