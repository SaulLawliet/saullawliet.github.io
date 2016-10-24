---
layout: post
title: "Ubuntu 使用心得"
category: share
comments: true
share: false
image:
  feature:

modified: 2015-07-26
---
{% include _toc.html %}

# 分区

| 目录  | 大小                                                                     |
|:------+:-------------------------------------------------------------------------|
| /     | 30GB                                                                     |
| ----  |                                                                          |
| swap  | <small>4GB of RAM requires a minimum of 2GB of swap space                |
|       | <small>4GB to 16GB RAM requires a minimum of 4GB of swap space           |
|       | <small>16GB to 64GB of RAM requires a minimum of 8GB of swap space       |
|       | <small>64GB to 256GB of RAM requires a minimum of 16GB of swap space[^1] |
| ----  |                                                                          |
| /data | 硬盘余下空间                                                             |
{: rules="groups"}

# 常用配置文件

配置文件尽量都放在`/data`分区，然后通过创建软链接的方式访问，这样在重新安装系统的时候，只需要再创建一轮软连接即可。<br>
如果要在多个电脑保证配置文件的同步性，推荐使用[Dropbox](https://db.tt/vM77VZfZ)[^2]，虽然在大陆无法访问，但总有办法，不是么?

# 终端

先说快捷键吧，熟练掌握后绝对提升效率，[要看详细戳这](http://www.bigsmoke.us/readline/shortcuts)

| 快捷键 | 含义                            |
|:-------+:--------------------------------|
| C^P    | 上                              |
| C^N    | 下                              |
| C^A    | 行首                            |
| C^E    | 行尾                            |
| C^W    | 删除上一个单词                  |
| C^R    | 历史命令搜索，效率比history要高 |
{: rules="groups"}

使用`zsh`配合`oh-my-zsh`的方式来代替默认的`bash`，好处是什么呢？

- `tab`自动纠错，比如`cd down`，按下`tab`后，此时命令行可能变为`cd Downloads`
- 命令补全时可以通过方向键选择的
- `C^L`等价于`clear`，那么`M^L`呢？在这里等价于`ls`
- 阅读配置文件`~/.zshrc`，根据注释说明，定制自己的配置
- 多种主题可以选择，文件在`~/.oh-my-zsh/themes`，数十种，很难挑选。<br>
  可以修改配置文件，找到`ZSH-THEME`，修改成`ZSH-THEME="rondom"`。这样每次重新打开一个窗口的时候就会随机一个主题。
- 多种插件可以选择，个人觉得必装的一个是`command-not-found`，其他的到`~/.oh-my-zsh/plugins`慢慢发现吧。基本上常用的命令行工具都会有插件来帮助你更快的输入参数（因为有Tab补全或其他）。

在终端执行命令的时候，网络超时或拒绝怎么办？如果身处中国，不用怀疑90%挂代理吧。<br>
在原命令前输入`http_proxy=ip:port` 或 `https_proxy=ip:port`，这样代理只对此命令有效。<br>
如：`https_proxy=127.0.0.1:8888 bundle install`<br>
或者把`alias P="http_proxy=127.0.0.1:8888 https_proxy=127.0.0.1:8888"`加入你的`bashrc`文件中，这样每次使用的时候就可以直接`P bundle install`

# 编辑器的快捷键

写代码时的快捷键，个人觉得要分三个版本，标准版，Vim版，Emacs版

| 类别    | 说明                                                                        |
|---------+-----------------------------------------------------------------------------|
| 标准版  | 最通用版本，但是移动光标要移动手腕，用不得（虽然本人用HHKB，但也有点麻烦）  |
| Emacs版 | 貌似只有Emacs跟终端支持，毕竟现在主要图形化，`Ctrl + `的方式容易冲突        |
| Vim版   | 通过Esc来切换模式，编辑文本功能强大，基本流行的编辑器都可以通过插件来使用它 |
{: rules="groups"}

所以推荐使用Vim版的快捷键，一旦掌握，受益终生。

# 常用软件

| 名称                                            | 用途                   |
|:------------------------------------------------+:-----------------------|
| terminator                                      | 终端分屏，支持拖拽布局 |
| aria2                                           | 命令行下载             |
| tree                                            | 展示目录结构           |
| [Xmind](http://www.xmind.net/)                  | 思维导图               |
| [bashmarks](https://github.com/huyng/bashmarks) | Bash下的书签           |
{: rules="groups"}


[^1]: [Adding and Managing RHEL 6 Swap Space](http://www.techotopia.com/index.php/Adding_and_Managing_RHEL_6_Swap_Space)
[^2]: 通过此链接注册会为我增加500MB的空间;)
