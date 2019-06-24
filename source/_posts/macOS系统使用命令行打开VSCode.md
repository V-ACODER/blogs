---
title: macOS系统使用命令行打开VSCode
date: 2019-06-24 14:51:54
tags: 操作系统
categories: 服务端
---

1, 进入官网下载VSCode，安装，打开软件。[官网地址](https://code.visualstudio.com/docs/setup/mac)

2, 方法一，但是这种方法对我来说像是临时的，每次重启电脑后又失效了。

> Open the Command Palette (⇧⌘P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.

3, 方法二，在.bash_profile文件里加入环境变量。

```
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```
由于我没有这个文件，自己touch了一个，修改后执行`source ~/.bash_profile`，接着恐怖的事情发生了，我所有的命令除了cd都失效了...

<!-- more -->

4, 找到解决方法，在控制台输入

```
export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/X11/bin"
```
在.bash_profile文件加入这句，发现并不起作用，网上也有说bashrc和zsh不同，编辑方式不一样，我的电脑应该是bashrc。

5, 终于找到正解，在.bash_profile里添加环境变量的应该是这句

```
code () { VSCODE_CWD="$PWD" open -n -b "com.microsoft.VSCode" --args $* ;}
```