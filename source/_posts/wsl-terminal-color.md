---
title: WIN10 WSL VIM颜色调整
date: 2019-9-1 14:27:45
tags: [Windows,WSL]
categories: 教程
---

# 问题

在win10上装了bash on ubuntu，自配的颜色真是看不清，看到知乎上推荐的molokai配色挺不错的，我们来记录一下解决的过程

# 教程

打开bash on ubuntu，运行下面的命令，进入vim的配置文件夹

```
cd /etc/vim
```

从github上clone下molokai的配色方案

```
git clone https://github.com/tomasr/molokai.git
```

clone完毕后会得到一个molokai，然后运行下面的命令，将colors文件夹拷贝出来，然后就可以删除molokai文件夹了

```
cp -rf molokai/colors/ ./colors
rm -rf molokai
```

之后通过编辑vimrc文件

```
vi vimrc
```

添加

```
colorscheme molokai
```

然后保存退出就可以了

# 附件

相关链接

* https://blog.csdn.net/zycdsg/article/details/79057698