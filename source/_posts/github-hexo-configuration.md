---
title: Github和Hexo配置
date: 2018-01-2 12:39:19
tags: [Hexo, GitHub]
categories: 教程
---

# 安装前提

安装 Hexo 相当简单。然而在安装前，您必须检查电脑中是否已安装下列应用程序：

  - [Node.js](https://nodejs.org/en/)
  - [Git](https://git-scm.com/)

如果您的电脑中已安装 Node.js , Git 的话，那么接下来就要用npm来安装Hexo了

## GitHub Pages 仓库

在自己的GitHub账号下创建一个新的仓库，命名为username.github.io（username是你的账号名)。

在这里，要知道，GitHub Pages有两种类型：User/Organization Pages 和 Project Pages，而我所使用的是User Pages。

简单来说，User Pages 与 Project Pages的区别是：

1. User Pages 是用来展示用户的，而 Project Pages 是用来展示项目的。
2. 用于存放 User Pages 的仓库必须使用username.github.io的命名规则，而 Project Pages 则没有特殊的要求。
3. User Pages 将使用仓库的 master 分支，而 Project Pages 将使用 gh-pages 分支。
4. User Pages 通过 http(s)://username.github.io 进行访问，而 Projects Pages通过 http(s)://username.github.io/projectname 进行访问。

## Git

### 配置name和email
当安装完Git应该做的第一件事情就是设置用户名称和邮件地址。这样做很重要，因为每一个Git的提交都会使用这些信息，并且它会写入你的每一次提交中，不可更改：
```
git config --global user.name "username"
git config --global user.email "username@example.com"
```

查看git配置可以使用 -l 参数(l 就是 list 的首字母,L的小写):
```
git config -l
```
在某个项目根路径下面可以设置单独的Email与姓名.
```
git config user.name "tiemaocsdn"
git config user.email "tiemaocsdn@qq.com"
```
### ssh配置
查看是否已经有了ssh密钥：cd ~/.ssh

如果没有密钥则不会有此文件夹，有则备份删除

生存密钥：
```
ssh-keygen -t rsa -C "username@example.com"
```
按3个回车，密码为空。

最后得到了两个文件：id_rsa和id_rsa.pub

添加密钥到ssh：ssh-add id_rsa

需要之前输入密码。

在github上添加ssh密钥，这要添加的是“id_rsa.pub”里面的公钥

git上进行测试
```
ssh git@github.com
```
返回结果
```
PTY allocation request failed on channel 0  
Hi username! You've successfully authenticated, but GitHub does not provide shell access.  
Connection to github.com closed.  
```

github ssh配置完毕


# Hexo安装

如果上述必备程序已完成，那么接下来即可使用npm完成Hexo的安装
```
npm install -g hexo-cli
```

# Hexo建站

安装Hexo完成后，Hexo需要在指定的文件夹init初始化，在你喜欢的文件夹内（例如D：\Hexo），点击鼠标右键选择Git bash，输入以下指令：
```
hexo init
```
接下来是安装依赖包，该命令会在当前文件夹内建立网站所需要的所有文件：
```
npm install
```
新建完成后，当前文件夹的目录如下：
```
.
├── _config.yml 网站的 配置 信息，您可以在此配置大部分的参数
├── package.json    应用程序的信息
├── scaffolds   模版文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件
├── source  资源文件夹是存放用户资源的地方
└── themes  主题文件夹。Hexo 会根据主题来生成静态页面。
```
现在可以通过下面的命令，搭建到本地预览一下
```
hexo generate
hexo server
```
然后在浏览器输入localhost:4000查看

这个博客只是本地的，别人是浏览不了的，之后需要部署到GitHub上。

# Hexo配置
您可以在 _config.yml 中修改大部份的配置

找到这一个部分
```
deploy:
  type:
```
然后在github上仓库的ssh地址复制过来，修改后
```
deploy:
  type: git
  repo: 对应仓库的SSH地址（可以在GitHub对应的仓库中复制）
  branch: 分支（User Pages为master，Project Pages为gh-pages）
```
为了能够使Hexo部署到GitHub上，需要安装一个插件：
```
npm install hexo-deployer-git --save
```
然后通过下面的命令发布到github的仓库上完成部署：
```
hexo generate
hexo deploy
```
# theme配置
如果想要使用其他主题，可以使用git clone将别人的主题拷贝到站点目录的\themes下，然后将_config.yml中的theme: landscape改为对应的主题名字

个人推荐一个不错的主题：[Next](https://github.com/iissnan/hexo-theme-next)

详细步骤可以参考[Next官网](http://theme-next.iissnan.com/)。

# 命令
常用命令
```
npm install -g hexo-cli
hexo init
npm install
hexo generate
hexo server
hexo clean
hexo deploy
```
其他命令
```
hexo new [layout] <title>
hexo publish [layout] <filename>
hexo render <file1> [file2] ...
hexo list <type>
hexo version
```