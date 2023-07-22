---
title: How to Build My Blog Using GitHub Pages and Jekyll
layout: post
post-image: "https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/thumb-1920-994659.jpg"
description: 非常细致全面的搭建博客指南
tags:
- jekyll
- blog
- tech
---


> **声明：**
>
> 纯前端小白，只学了一点点 html，CSS 和 JS 一点没学，所以只写了如何利用模板建立网站，大佬们多多指导 (因为不是这个方向的，只是想建个自己喜欢的博客，拥有一个属于自己的博客不帅吗[doge])



## 第一步 找主题

1. 记得拥有一个 GitHub 账号 (提醒一下而已

2. 在使用 Jekyll 主题的网站找到一款喜欢的主题，如 <http://jekyllthemes.org/>，点开该主题的 GitHub 主页并 `Fork`。

   > 我用的是 <https://jekyll-themes.com/> 主题网站

2. 点开刚刚 fork 到自己的 repo ，点击 settings ，改名为 username.github.io ( username 为你的 GitHub 昵称)，点击 `rename`

   > 必须改为这个名字（我也不知道为啥

3. 还是 settings 中，在左边栏你能看到 `Pages` 项，点进去，更改 source 。Source 分为 `Branch` 和 `folder`，选的时候我是看 _config.yml 啊、CNAME 啊之类的文件在哪个 `Brance` 以及 `folder` 下就选哪个

   > 一般是在 `Master` - `Root `下，但也不排除别的，看清楚

4. 这里 `Choose a theme` 就不用点了

5. (这一条建议在博客搭建好之后最后再弄) Custom domain 填写自己的域名，如果你有现成的想用来搭建博客的域名就直接填上，然后在域名服务商给域名添加 CNAME 解析，值为 username.github.io (点击确认后服务商会自动在值后加个点，不用理会)，最后勾选 `Ensure HTTPS`

   > 如果还没有域名或者以上步骤没有看懂，可以看我的另一篇博客《域名注册指导》(自我推广



## 第二步 安装必要项 (不会起名了

1. Gitbash

   Gitbash 的作用是方便我们在本地管理 GitHub，例如在本地修改好仓库文件直接 push 到 GitHub 比在网页中一个一个改方便多了

   - 首先下载 Gitbash

     <https://gitforwindows.org/>

     点击 `Download`，下载速度慢的话就[doge] (意会)

     ~~我电脑还蛮大的，~~下载好就直接安装~~，安装了就关机，没问题的~~，安装位置任意，按照默认步骤安装即可

   - 然后把 GitHub 账号和 GitBash 联系起来

     打开 Git Bash (按 Win/点击菜单 - 所有应用 - Git - Git Bash)，输入以下命令行：

     ```bash
     git config --global user.name “github_username”
     git config --global user.email "email@useremail"
     ```

     > github_username 改为 GitHub 的名字
     >
     > email@useremail 改为注册 GitHub 用的邮箱

   - 选择一个位置建立保管我们博客文件的本地仓库，我是在F盘新建了个 blog 文件夹。进入此文件夹，右键点击 `Git Bash Here`，在Git Bash程序中输入：`git init` (初始化仓库的意思)

   至此 Git Bash 就安装好了

2. Ruby

   因为我们现在用的是 Jekyll ，它是使用 Ruby 语言编写的，也需要用到 gem 命令，所以需要安装

   > gem 安装，即为使用 RubyGems——Ruby 的包管理器的命令进行安装，类似于 Ubuntu 的 apt-get，Centos 的 yum，Python 的 pip。到目前为止我没有用到 RubyGems，所以暂时只安装了 Ruby 没安装 RubyGems

   - 因为是 Windows 系统，我是使用 RubyInstaller 进行安装的。首先打开 RubyInstaller 网站 <https://rubyinstaller.org/>，点击最上方的 `Download`，我推荐选择 WITH DEVKIT 下最新的安装包进行下载。(注意 x64 代表64位，x86 代表32位，不会下错吧...算了还是提醒一下[doge]

   - 下载好就开始安装，安装时注意几个点：

     1. 记得勾选 “Add Ruby executables to your PATH”
     2. 安装后打开 cmd.exe，输入 `ruby -v` 测试 Ruby，若正常显示版本号等信息，则为安装成功
     3. (安装成功忽略此条) 若没能正常显示，则考虑为没能配置环境变量导致没有安装成功，这时需要找到计算机系统设置中的环境变量，将 ruby 目录下的 bin 目录的路径添加上去 (没懂怎么做的话可以自行查找 Windows 如何配置环境变量)

   - 还要注意一点

     Ruby3.0 之后不不会再自带 webrick，所以待会配置 Jekyll 时可能会出错，下面会介绍到解决方法，别急

   至此 Ruby 就安装好了

3. Jekyll

   安装 Jekyll

   - 刚刚说的小问题现在需要解决一下，打开保管我们博客文件的本地仓库文件夹，右键`Git Bash Here`，输入：

     `bundle add webrick`

     > 运行这条命令时建议断开 [doge] (意会，否则可能运行失败

   - 打开保管我们博客文件的本地仓库文件夹，右键 `在终端打开`，或打开 cmd.exe 并 cd 到该文件夹，输入:

     ```bash
     gem install bundler jekyll  #Install bundler? Is it same with 'bundle install'?
     jekyll new my-awesome-site
     cd my-awesome-site
     bundle exec jekyll serve  #Host WhatATheme locally
     ```

     上面命令行中两个 my-awesome-site 指的是新建一个和你博客域名同名的文件夹 (比如我的是 www.Alpss.tech)
     
     > 1. 运行这条命令时建议断开 [doge] (意会，否则可能运行失败
     >
     > 2. 有个小问题，我不知道Bundler需不需要和 Ruby 安装在同一个文件夹，也不知道我在终端中 cd 到该文件夹中运行`install` 命令是不是把应用安装在该文件夹中了，有大佬知道的教教我！

   至此，Jekyll就安装好了，所有必要安装项也安装好了

4. 最后将Repo克隆到本地仓库

   打开 my-awesome-site 文件夹，右键点击 `Git Bash Here`，输入：

   ```bash
   git clone https://github.com/username/username.github.io.git
   bundle install  #I'm not sure whether it is repetitive, but there is no error up to now so...just do it
   ```

   这样仓库就克隆到本地了，你可以在本地修改好文件直接 push 到 GitHub，或在 GitHub 修改文件后更新到本地。具体的Git最基本操作一会会说到



## 第三步 个性化设置该主题

我们可以根据个人喜好来改变这个主题。

1. _config.yml

   我把常用的一些设置列了出来，可以参考着意思改一改 (懒得打中文了)。需要注意的是书写规范，比如冒号后面必须有一个空格等等，照着人家原来的格式改

   ```yaml
   # Change markdown
   markdown: kramdown
   
   # URL of the Site
   url: ''
   # Base URL of the Site (i.e., Name of the Repository in which the Site is hosted)
   baseurl: 
   
   # Title of the Site
   title: 
   # Description of the Site
   description: 
   # URL of Image of the Site
   site-image: 
   # Keywords of the Site
   site-keywords: 
   # URL for the Image of custom Favicon
   favicon-url: 
   
   # URL of the Image of Custom Hero Image (i.e., the image in the background of the very first section of the Homepage)
   heroimage: 
   
   ```

2. 404.md

   修改自己喜欢的404样式，用markdown语言书写

3. 更改 html，CSS，JS 文件

   如果你还想更改该主题或者说模板的更多东西，可以学习下 html，CSS，JS 等的基本语法来进行更改，这里不赘述 (因为我也一知半解，随便改了改 html 文件



## 第四步 书写博客

很简单，有手就行[doge]

博客需要放到 _post 文件夹中





## Git最基础操作

更多请阅读 <https://www.runoob.com/git/git-basic-operations.html>

1. 将在本地写好的博客或是对其他文件做出的更改同步到 GitHub：

   更改了什么文件夹中的文件就打开该文件夹，更改了不同文件夹中文件的话就打开 my-awesome-site 文件夹。打开后右键点击 `Git Bash Here`，输入：

   ```bash
   git add .  #注意是空格加点。意义为添加文件到暂存区，点的意义是添加当前目录下的所有文件到暂存区
   git commit -m “blog1”  #引号中的是对本次同步的说明。意义为将暂存区内容添加到仓库
   git push -u origin master  #意义为将本地的 master 分支推送到 origin 主机的 master 分支，同时指定 origin 为默认主机
   # 第一次需要使用 -u 命令，之后直接 'git push' 就好了
   # git push --force origin master  #当推送失败可以试试这个，意义为强制推送
   ```

   这样就将更改同步到 GitHub 以及博客网站了

2. 将 GitHub 的更改同步到本地仓库

   打开想同步的文件夹，输入：

   ```bash
   git pull origin
   ```

   这样就同步到本地仓库了





**好耶，写完了~**

**有能帮我解决文章中提到的问题的大佬吗，帮帮我帮帮我！весьма благодарить！**



