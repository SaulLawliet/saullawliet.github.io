---
layout: post
title: 一个 Bash 下的书签管理工具 - bashJ
categories: create
comments: true
share: false
image:
  feature:

modified:
date: 2017-04-10T21:32:38+08:00
---

{% include _toc.html %}

# 介绍

[项目地址](https://github.com/SaulLawliet/bashJ)  
一个 `Bash` 下的书签管理工具，仅用一个命令（实际是函数）`J`（可以更改）就可以完成书签增删查、目录跳转。
这是 [oh-my-zsh jump](https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/jump/jump.plugin.zsh) 的改进版，
使用起来会更方便，同时支持多种 `shell` ，原理是把数据以软链接的方式存在 `~/marks` 目录下。  
具体用法见下：

~~~
$ J -h
Usage:
  J           - Lists all marks
  J <mark>    - Goes (cd) to the directory associated with <mark>
  J -s <mark> - Saves the current directory as <mark>
  J -d <mark> - Deletes the <mark>
~~~

# 使用说明
1. `git clone https://github.com/SaulLawliet/bashJ.git`
1. 默认命令是 `J` ，你可以打开 `bashJ.sh` ，把 `J` 改成任意你喜欢的命令
1. 将 `source <dir>/bashJ.sh` 加入你的 `~/.bash_profile` 或 `~/.bashrc` 或 `~/.zshrc`

# 为什么写这个？
- [autojump](https://github.com/wting/autojump)  
  在使用过程中统计目录频率，然后进行跳转目录，但有些我不想保存的目录也会被保存。
- [bashmarks](https://github.com/huyng/bashmarks)  
  可以自己添加书签，然后跳转目录，但默认的命令是单字母的，容易产生冲突。
- [oh-my-zsh jump](https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/jump/jump.plugin.zsh)  
  与 `bashmarks` 类似，但默认命令不够友好。
  
