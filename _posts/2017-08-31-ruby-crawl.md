---
layout: post
title: 使用 Ruby 抓取网页数据
categories: ruby
comments: true
share: false
image:
  feature:

modified:
date: 2017-08-31T15:26:31+08:00
---

{% include _toc.html %}

# 打开页面

## 使用 OpenURI

[OpenURI 文档](https://docs.ruby-lang.org/en/trunk/OpenURI.html)

~~~ ruby
require "open-uri"

# 直接
html = open(link).read
# 使用 User-Agent
html = open(link, "User-Agent" => "Mozilla/5.0 ...").read
# 使用 代理
html = open(link, "proxy" => "http://127.0.0.1:8001").read
# 如果有编码问题, 用二进制方式
html = open(link, "r:binary").read.encode("utf-8", uri.charset, invalid: :replace, undef: :replace)
~~~

## 使用 Socks 代理

[socksify-ruby 项目](https://github.com/astro/socksify-ruby)

~~~ ruby
require "socksify/http"

html = Net::HTTP::SOCKSProxy("127.0.0.1", 8002).get(URI(link))
~~~

# 解析页面

[Nokogiri 项目](https://github.com/sparklemotion/nokogiri)


~~~ ruby
# !!! Copy from: https://github.com/sparklemotion/nokogiri#synopsis

require 'nokogiri'
require 'open-uri'

# Fetch and parse HTML document
doc = Nokogiri::HTML(open('http://www.nokogiri.org/tutorials/installing_nokogiri.html'))

puts "### Search for nodes by css"
doc.css('nav ul.menu li a', 'article h2').each do |link|
  puts link.content
end

puts "### Search for nodes by xpath"
doc.xpath('//nav//ul//li/a', '//article//h2').each do |link|
  puts link.content
end

puts "### Or mix and match."
doc.search('nav ul.menu li a', '//article//h2').each do |link|
  puts link.content
end
~~~

# 小结
因为每次抓页面的时候, 总是要搜索一遍如何去写, 所以在这里做一个总结.  
以上差不多包含了日常的使用需求.
