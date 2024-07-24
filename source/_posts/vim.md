---
title: Vscode x vim，实现高效开发
date: 2024-07-20 13:12:23
tags:
    - vim
    - vscode
    - 工具
    - 编辑器
    - 学习
    - 笔记
    - 教程

categories:
    - 学习
    - 工具
keywords: "vim, 学习, 教程, 工具, 编辑器, vscode插件"
description: "vim编辑器，高效开发必备工具，本教程将介绍Vscode中vim插件的安装、配置及使用，快速上手vim，提升开发效率。"
top_img: http://gitee.com/TheUHO/blog/raw/master/images/202407212255291.jpg
cover: https://gitee.com/TheUHO/blog/raw/master/images/202407221045233.png
---
| 目录跳转 |
| --- |
|[1. vim简要介绍](#section1)|
|[2. 为什么是vim](#section2)|
|[3. vim插件下载及配置](#section3)|
|[4. vim相关说明](#section4)|
|[5. vim基本操作](#section5)|
|[6. easymotion模式](#section6)|
|[7. vim-surround插件easymotion模式](#section7)|
### 前言：关于vim，你需要知道的

#### vim简要介绍
<a id="section1"></a>
- vim 是一款经典的文本编辑器，最初是 Unix 系统上的一个工具，现在所有的类 Unix 系统（Linux、Mac）都安装了vim。它具有强大的文本编辑功能，可直接通过终端操作文本。
- vim 是一个**高度可定制**的编辑器，我们可以通过修改配置文件来适应自己的使用习惯和需求。它支持多种编程语言和文件格式，可以方便地进行代码编辑和调试，有效 ~~使自己看上去更像一个CS人~~ 提升开发效率。
- vim 是一个开源软件，可以在多种操作系统上运行，包括 Linux、Windows、Mac等。它可能是Linux用户最熟悉的软件之一。vim也能通过丰富的插件和扩展进一步增强其功能，也能基于其他编辑器（如Vscode）内的Vim插件辅助开发。
<a id="section2"></a>
#### 为什么是vim

- vim 是一款轻量级的编辑器，不需要图形界面，可以在终端中运行，适合在服务器上使用。
- vim 能够省略频繁的鼠标操作，在不离开键盘热区的情况下，通过键盘快捷键进行操作，提高开发效率。
- vim 方便学习，它的上下限区别很大，可以满足不同用户的需求，从简单的文本编辑到复杂的代码编辑，都可以通过vim实现。你可以只掌握简单的`i`、`:wq`、`dd`、`ESC`便在日常开发中使用，也可以通过更多的快捷键和操作，摆脱鼠标的束缚。

### Vscode x vim插件

- 在Vscode中安装Vim插件，可以方便地使用vim的快捷键进行日常开发，提升个人效率。
- 在Vscode中配置vim插件，可以更好地平衡自己的使用习惯和需求，个性化配置vim，提升个人开发体验。
- 很多人认为vim的学习曲线高，学习成本大，需要记忆非常多的快捷键和操作，但是我最近体验下来，实际只需要掌握一些使用频率较高的快捷键，其余的可以自己制作一个速查表方便随时查阅。
<a id="section3"></a>
#### vim插件下载及配置
- 官网：<https://github.com/VSCodeVim/Vim>

<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5);box-sizing: border-box">
<img src="https://gitee.com/TheUHO/blog/raw/master/images/202407221042770.png" /></div>
<p>

- 直接打开Vscode拓展搜索vim点击安装，Windows用户可以**直接使用**，Mac用户需要根据拓展说明在命令行执行对应语句。
```
$ defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false              # For VS Code
$ defaults write com.microsoft.VSCodeInsiders ApplePressAndHoldEnabled -bool false      # For VS Code Insider
$ defaults write com.vscodium ApplePressAndHoldEnabled -bool false                      # For VS Codium
$ defaults write com.microsoft.VSCodeExploration ApplePressAndHoldEnabled -bool false   # For VS Codium Exploration users
$ defaults delete -g ApplePressAndHoldEnabled                                           # If necessary, reset global default
```
- 拷贝拓展说明中的配置文件到Vscode的配置文件中

<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5);box-sizing: border-box"><img src="https://gitee.com/TheUHO/blog/raw/master/images/202407231736736.png"/></div> <p>


<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5); box-sizing: border-box">
<img src="https://gitee.com/TheUHO/blog/raw/master/images/202407231734848.png" /></div> </p>

- 或者拷贝下面的配置文件到settings.json
    > 这是我的个人配置，包含一些更改，比如保留了Vscode的`Ctrl`热键，`j` `k`替换`Esc`使用，仅供参考
```json
{
    "vim.easymotion": true,
        "vim.incsearch": true,
        "vim.useSystemClipboard": true,
        "vim.useCtrlKeys": true,
        "vim.hlsearch": true,
        "vim.insertModeKeyBindings": [
          {
            "before": ["j", "k"],
            "after": ["<Esc>"]
          },
          {
            "before": ["<Ctrl>", "c"],
            "after": ["y"]
          }
        ],
        "vim.normalModeKeyBindingsNonRecursive": [
          {
            "before": ["<leader>", "d"],
            "after": ["d", "d"]
          },
          {
            "before": ["<C-n>"],
            "commands": [":nohl"]
          },
          {
            "before": ["K"],
            "commands": ["lineBreakInsert"],
            "silent": true
          }
        ],
        "vim.leader": "<space>",
        "vim.handleKeys": {
            "<C-a>": false,
            "<C-c>": false,
            "<C-x>": false,
            "<C-f>": false,
            "<C-h>": false,
            "<C-s>": false,
            "<C-z>": false,
            "<C-y>": false,
        },
      
        "// To improve performance",
        "extensions.experimental.affinity": {
          "vscodevim.vim": 1
        }
 }
```
<a id="section4"></a>
### vim相关说明
- 模式mode：vim中有四种常用的模式
    - normal模式：默认模式，用于移动光标、删除文本等操作；
    - insert模式：用于插入文本；
    - visual模式：用于选择文本；
    - command-line模式：用于执行命令。
- 操作符operator：用于对文本进行操作，例如`d`删除、`y`复制、`p`粘贴等。
- 动作motion：用于指定操作的范围，例如`h` `j` `k` `l`移动光标、选择文本等。
### 学习资源
- vim安装后自带的教程vimtutor，在终端执行`vimtutot`即可进入。
- b站视频[指尖飞舞：vscode + vim 高效开发](https://www.bilibili.com/video/BV1z541177Jy?p=4&spm_id_from=pageDriver&vd_source=ad387bf24e3219fa7c16fce8832f4c21)
- [CS自学指南](https://csdiy.wiki/%E5%BF%85%E5%AD%A6%E5%B7%A5%E5%85%B7/Vim/)
- 博客[vim入门笔记](https://imageslr.com/2021/vim)
<a id="section5"></a>
### vim基本操作
- **模式相关操作**
    - `i` 进入插入模式, 光标在当前字符前
    - `I` 进入插入模式，光标在当前行开头
    - `a` 进入插入模式，光标在当前字符后 
    - `A` 进入插入模式，光标在当前行结尾
    - `o` 进入插入模式，光标在当前行下方
    - `O` 进入插入模式，光标在当前行上方
    - `Esc`或`Ctrl`+`[` 退出插入模式，进入normal模式,也可用设置的快捷键 *(我设置的是`j` `k`,理由是因为`Esc`距离键盘热区较远)*
    - `:` 普通模式下进入命令模式，按`Esc`退出命令模式
    - `:wq` 保存并退出
    - `:q!` 不保存退出
    - `:w` 保存
    - `:q` 退出
- **光标移动相关操作**
    - `h` `j` `k` `l` ← ↓ ↑ →移动光标
    - `w` 向后移动一个单词，到下一个单词的开头
    - `b` 向前移动一个单词，到本单词或上一个单词开头
    - `e` 向后移动一个单词，到本单词或下一个单词结尾
    - `ge` 向前移动一个单词，到本单词或上一个单词结尾
    - `W` 向后移动一个单词，到下一个单词的开头，忽略标点符号
    - `B` 向前移动一个单词，到本单词或上一个单词开头，忽略标点符号
    - `E` 向后移动一个单词，到本单词或下一个单词结尾，忽略标点符号
    - `gE` 向前移动一个单词，到本单词或上一个单词结尾，忽略标点符号
    - `0` 移动到当前行开头
    - `$` 移动到当前行结尾
    - `^` 移动到当前行开头第一个非空字符
    - `gg` 移动到文件开头
    - `G` 移动到文件结尾
    - `H` 移动到屏幕顶部
    - `M` 移动到屏幕中间
    - `L` 移动到屏幕底部
    - `f 字符` 光标移动到下一个字符所在位置
    - `F 字符` 光标反向移动到上一个字符所在位置
    - `t 字符` 光标移动到下一个字符之前的位置
    - `T 字符` 光标反向移动到上一个字符之后的位置
    - `;` 重复上一次的`f/F/t/T`操作
    - `,` 反向重复上一次的`f/F/t/T`操作
    - `%` 跳转到匹配的括号
    - `n` 跳转到下一个匹配的字符
    - `N` 跳转到上一个匹配的字符
    - `Ctrl + d` `Ctrl + u` 向下向上翻页
    - `Ctrl + f` `Ctrl + b` 向下向上翻页
    - `Ctrl + e` `Ctrl + y` 向下向上滚动一行
    - `Ctrl + g` 显示当前行号和文件信息

- **动作motion相关操作(需结合操作符使用)**

    - `i` 表示inner，内部，表示操作对象是字符的内部
    - `a` 表示around，周围，表示操作对象是字符的周围
> 如`diw`删除当前单词，`ciw` 修改当前单词，`yiw` 复制当前单词，`viw` 选择当前单词，也可用`i(`或`ib`、`i"`、`i{`或`iB`、`it`等表示特殊符号包含的内容；而`daw`删除当前单词及之前的空格，`a(`或`ab`、`a"`、`a{`或`aB`、`at`等表示特殊符号本身及包含的内容
- **操作符operator**

    - `d` 删除delete
    - `c` 修改(删除并进入插入模式)change
    - `r` 替换replace
    - `y` 复制yank
    - `p` 粘贴put
    - `u` 撤销
    - `v` 选择(选中并进入visual模式)
    - `~` 切换当前字母大小写 `n~`切换光标位置开始的n个字母大小写
    - `g~` 切换当前行字母大小写
    - `gu` 切换为小写，后接动作motion，如`guu`将当前行字母改为小写，`guiw`将光标所在单词改为小写等
    - `gU` 切换为大写，后接动作motion，如`gUU`将当前行字母改为大写，`guiw`将光标所在单词改为大写等
    - `>` 增加缩进
    - `<` 减少缩进
    - `=` 自动缩进
- **其他操作**

    - `gd` 跳转到定义go to definition
    - `gD` 跳转到全局定义
    - `Ctrl o`退出定义
    - `g h` 悬浮显示定义
    - `g t` 跳转下一个标签页，`n g t` 跳转到向后第n个标签页
    - `g T` 跳转上一个标签页，`n g T` 跳转到向前第n个标签页
    - `Ctrl 0` 将光标移动到侧边栏
    - `Ctrl 1` 将光标移动到编辑器/将光标移动到组1
    - `Space`或`Enter` 展开或进入文件夹/打开文件
    - `Ctrl n` 打开组n/将光标移动到组n
    - `:noh` 取消高亮
    - `:set number` 显示行号
    - `:set nonumber` 取消显示行号
    - `:set hlsearch` 高亮搜索结果
    - `:set nohlsearch` 取消高亮搜索结果
    - `:set ignorecase` 忽略大小写

<a id="section6"></a>

### easymotion模式
- [vim-easymotion](https://github.com/easymotion/vim-easymotion)插件

|Motion Command|Description|
|:--|:--|
|`<leader> <leader> s <char>`|搜索指定的字符
|`<leader><leader> f <char>`|	向前查找指定的字符
|`<leader><leader> F <char>`|	向后查找指定的字符
|`<leader><leader> t <char>`|	向前查找直到指定的字符
|`<leader><leader> T <char>`|	向后查找直到指定的字符
|`<leader><leader> w`|	向前移动到单词的开头
|`<leader><leader> b`|	向后移动到单词的开头
|`<leader><leader> l`|	匹配单词的开始和结束，驼峰命名法，在 `_` 后，在 `#` 后向前
|`<leader><leader> h`|	匹配单词的开始和结束，驼峰命名法，在 `_` 后，在 `#` 后向后
|`<leader><leader> e`|	向前移动到单词的结尾
|`<leader><leader> ge`|	向后移动到单词的结尾
|`<leader><leader> j`|	向前移动到行的开头
|`<leader><leader> k`|	向后移动到行的开头
|`<leader><leader> / <char>... <CR>`|	搜索n个字符
|`<leader><leader><leader> bdt`|	向前移动到指定的字符
|`<leader><leader><leader> bdw`|	向前移动到单词的开头
|`<leader><leader><leader> bde`|	向前移动到单词的结尾
|`<leader><leader><leader> bdjk`|	向前移动到行的开头
|`<leader><leader><leader> j`|	JumpToAnywhere 动作；默认行为匹配单词的开始和结束，驼峰命名法，在 `_` 后，在 `#` 后向前
- 在Vscode配置文件`settings.json`中将`<leader>`设置为`<space>`，两次空格进入easymotion模式
```json
"vim.leader": "<space>",
```
<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5); box-sizing: border-box">
<img src="https://gitee.com/TheUHO/blog/raw/master/images/202407232204348.png" /></div> </p>

<a id="section1"></a>

### vim-surround插件
<div style="box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5); box-sizing: border-box">
<img src="https://gitee.com/TheUHO/blog/raw/master/images/202407232208576.png" /></div> </p>

例如，对于下面的代码

```c
    printf(hello world);
```
在normal模式下，输入`ysi("`，就可以将`hello world`用括号括起来，变成

```c
    printf("hello world");
```
在normal模式下，输入`ds"`，就可以将`"hello world"`中的双引号删除，变成

```c
    printf(hello world);
```
在normal模式下，输入`cs"<char>`，就可以将`"hello world"`中的双引号替换成指定的字符，例如`<char>`为`'`，就可以将双引号替换成单引号，变成

```c
    printf('hello world');
```

### 结语
 **最后我想说的是，学习vim最需要的不是记忆这些快捷键，而是尝试干掉鼠标。忘记是在哪里看到的一句话，程序员需要做的，就是尽可能减少双手离开键盘的时间。**