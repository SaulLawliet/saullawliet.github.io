---
layout: post
title: 解决 Mercurial 中文路径字符编码的问题
categories: essay
comments: true
share: false
image:
  feature:

modified:
date: 2018-09-03T16:46:49+08:00
---

1. Mercurial 的路径字符编码使用提交者电脑的字符编码
1. 当 Windows 用户提交时, 路径字符编码是 GBK, 此时 Linux/Mac 用户更新的时, 会出现路径乱码情况

带着这个问题, 在网上搜索了一番, 解决思路都是修改提交者的配置,
而团队只有我使用非 Windows 系统, 让其他人都修改不太现实,
所以只能从自己这边解决问题, 幸好使用中文路径的仓库不需要我提交,
于是一个脚本, 很暴力的解决该问题

``` bash
cd /path/to/project

# 清空本地修改
hg update -C
hg purge --all

# 更新
hg pull
hg update

# 转换文件名的字符编码
convmv -f gbk -t utf-8 -r --notest .
```
