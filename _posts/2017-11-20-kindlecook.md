---
layout: post
title: 一个从互联网上生成电子书的工具 - Kindle Cook
categories: create
comments: true
share: false
image:
  feature:

modified:
---

{% include _toc.html %}

[项目地址](https://github.com/SaulLawliet/kindlecook)

## 依赖
- [KindleGen](https://www.amazon.com/gp/feature.html?docId=1000765211)
- [ImageMagick](https://www.imagemagick.org)

## 使用
进入项目目录，然后运行`ruby -Ilib recipes/xxx.rb`  
再次运行的时候，默认会使用已经保存好文件，如果想重新生成，在命令的最后加上`-c`

## 如何制作 recipe
主要实现以下几个方法，其中`prepare`必须要实现，具体可以参考[recipe/sicp.rb](https://github.com/SaulLawliet/kindlecook/blob/master/recipes/sicp.rb)
- `prepare`：返回图书的目录结构，同时通过调用`save_article`将网页的`body`保存下来
- `root_url`：当页面或图片的路径为相对路径时，会需要通过这个转换成绝对路径
- `document`：设置图书的元信息，默认为空
- `slug`：图书的唯一标示，默认为类名

## 制作好的图书
- [Drive](https://drive.google.com/drive/folders/1zrSwnKffuSPfLzn_oWv_HDLqCBJqAs33)
