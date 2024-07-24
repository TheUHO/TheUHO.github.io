---
title: 基于github与hexo的个人博客搭建教程
date: 2024-07-24 09:08:53
tags:
    - github
    - hexo
    - 博客
    - 学习
    - 教程
    - 网站
categories:
    - 博客
keywords: "hexo, github, 学习, 教程, Windows系统, 博客搭建"
description: "基于github与hexo的简易个人博客搭建教程，使用github pages进行托管，使用hexo进行博客管理，使用butterfly主题进行美化，并利用Picgo配置图床提高访问速度。"

top_img: https://gitee.com/TheUHO/blog/raw/master/images/202407212255288.jpg
cover: https://gitee.com/TheUHO/blog/raw/master/images/202407241217735.jpg
---

**尚在施工**

### 前言：跨出成为CS人的重要一步
- 当我们从头开始迈入CS学习的大门时，都必然会参考学习网络上丰富的各类资源。无论你是习惯于查阅CSDN、知乎，还是在浏览器中直接搜索，都一定会找到许多前人之鉴。很多个人博客文章，都能给予小白莫大的帮助。
- 然而，随着CS学习的深入，我们可能会发现，许多博客文章也许并不正确，亦或我们自己也找到一些很好的解决方法。这时，我们可能会萌生自己搭建一个博客的想法，以便于记录自己的学习过程，分享自己的心得体会，甚至与志同道合的人交流。
- 因此，本教程将简要介绍如何使用GitHub Pages和Hexo搭建一个Window系统下的简易个人博客，并使用Butterfly主题进行美化，同时配置Picgo作为图床以提高访问速度。通过本教程，你可以快速搭建一个属于自己的博客，并享受写作和分享的乐趣。
> 本教程面向的是和我一样的CS小白，也会提供一些我遇上的bug我解决思路。并且我需要强调的是，如果你有更多的精力和资源，完全可以选择购买云服务器，甚至可以自己从头开始写一个博客网站。但如果你像我一样，既想有一个自己的博客，又不想投入太多学习成本，那么本教程将是一个很好的选择。

### 准备工作
<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5);box-sizing: border-box">
<img src="https://gitee.com/TheUHO/blog/raw/master/images/202407241217735.jpg" /></div>
<p>

1. **GitHub账号**：首先，你需要有一个GitHub账号，用于在[Github pages](https://pages.github.com/)在线部署博客，在Github仓库托管和发布自己的静态网站页面。如果没有，请先注册一个[Github账号](https://github.com/)。
2. **Node.js和npm**：Hexo是基于Node.js的静态博客框架，因此你需要安装Node.js和npm。我们可以从[Node.js官网](https://nodejs.org/)下载并安装。
3. **Git**：
Git是一个版本控制工具，用于管理代码的版本。我们可以从[Git官网](https://git-scm.com/)下载并安装。

3. **PicGo**：PicGo是一个用于快速上传图片并生成图片链接的工具，我们将使用它来配置图床。我们可以从[PicGo官网](https://picgo.github.io/PicGo-Doc/)下载并安装。

### 搭建步骤

#### 环境搭建
#### 1. 创建GitHub Pages仓库
1. 登录GitHub，点击右上角的“+”号，选择“New repository”。
2. 在“Repository name”中输入你的用户名，例如`yourusername.github.io`。
3. 选择“Public”作为仓库的可见性。
4. 勾选“Initialize this repository with a README”。
5. 点击“Create repository”按钮。

#### 2. 安装Hexo
1. 打开终端，输入以下命令安装Hexo：
    ```bash
    npm install -g hexo-cli
    ```
2. 创建一个新的Hexo博客文件夹，并进入该文件夹：
    ```bash
    mkdir myblog
    cd myblog
    ```
3. 初始化Hexo博客：
    ```bash
    hexo init
    ```
4. 安装Hexo的依赖：
    ```bash
    npm install
    ```

#### 3. 配置Hexo
1. 打开Hexo博客文件夹，找到`_config.yml`文件，使用文本编辑器打开。
2. 修改以下配置：
    ```yaml
    # Site
    title: Your Blog Title
    subtitle: Your Blog Subtitle
    description: Your Blog Description
    author: Your Name
    language: en
    timezone: Asia/Shanghai

    # URL
    url: https://yourusername.github.io

    # Deployment
    deploy:
      type: git
      repo: https://github.com/yourusername/yourusername.github.io.git
      branch: master
    ```
3. 保存并关闭`_config.yml`文件。

#### 4. 安装Butterfly主题
1. 在终端中输入以下命令安装Butterfly主题：
    ```bash
    git clone https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
    ```
2. 打开Hexo博客文件夹，找到`_config.yml`文件，使用文本编辑器打开。
3. 修改以下配置：
    ```yaml
    theme: butterfly
    ```
4. 保存并关闭`_config.yml`文件。

#### 5. 配置PicGo
1. 打开PicGo，点击“图床设置”。
2. 选择“GitHub图床”，点击“确定”。
3. 输入GitHub的Access Token，可以在GitHub的Settings -> Developer settings -> Personal access tokens中生成。
4. 输入GitHub的仓库名称，格式为`yourusername/yourrepository`。
5. 输入分支名称，一般为`master`。
6. 输入存储路径，一般为`img`。
7. 输入自定义域名，一般为`https://cdn.jsdelivr.net/gh/yourusername/yourrepository`。
8. 点击“确定”保存配置。

### 6. 创建博客文章
1. 在终端中输入以下命令创建新的博客文章：
    ```bash
    hexo new post "Your Blog Post Title"
    ```
2. 进入生成的文章文件夹，使用文本编辑器打开`source/_posts/Your Blog Post Title.md`文件。
3. 编辑文章内容，可以使用Markdown语法。
4. 保存并关闭文章文件。

### 7. 部署博客
1. 在终端中输入以下命令生成静态文件：
    ```bash
    hexo generate
    ```
2. 在终端中输入以下命令部署博客：
    ```bash
    hexo deploy
    ```
3. 等待部署完成，打开浏览器，访问`https://yourusername.github.io`即可查看你的博客。

## 结语

以上还是草稿