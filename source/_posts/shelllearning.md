---
title: shell学习笔记
date: 2024-03-14 20:42:19
tags:
    - 工具
    - 学习
    - 教程
categories:
    - 学习
    - 工具
top_img: 
cover: https://gitee.com/TheUHO/blog/raw/master/images/202407212255288.jpg
---
## shell
+ 课程来源：[b站浙大竺院辅学](https://www.bilibili.com/video/BV1ry4y1A7qo/?p=2&spm_id_from=pageDriver&vd_source=ad387bf24e3219fa7c16fce8832f4c21)

+ 工具：WSL,Ubuntu,zsh
+ 插件及主题：[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md),[powerlevel10k](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#installation),[zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/tree/master)
*参看[鹤翔万里的shell备忘](https://note.tonycrane.cc/cs/tools/shell/)* <br/>
<!--more-->

+ 基础shell指令记录
   1. `pwd`获取当前路径(print working directory)
    2. `cd`切换路径(change directory)

        - `~`代表home，`.`代表当前路径，`..`代表上一级路径

    3. `ls`列出当前路径下的文件和目录  `ls -a` 列出所有文件和目录，包括隐藏文件, 
    `ls -l`列出详细信息(文件权限，大小，修改时间，...)
    `ls -al`上述功能
    4. `touch`创建一个文件
        - 如`touch 0.c`
    5. `mkdir`创建一个目录
        - 如`mkdir learning`
    6. `cp` *src* *dst*复制文件或目录(`cp -r`)
        - 如`cp 0.c 00.c`,`cp -r learning learning.0`
    7. `mv` *src* *dst*移动文件或目录(重命名)
    8. `rm`删除文件(`-r`递归删除目录；`-f`强制删除)
        - 如`rm 0.c`
    9. `find` *path* `-name` *pattern*在 path 下查找文件名匹配 pattern 的文件
        - 如`find . 0.c`, `find . '*.c'`
    10. `cat`输出与拼接文件(`-n`：带行号输出)
        ```c
            ❯ cat a.c
            #include<stdio.h>
            #include<string.h>
            #include<stdlib.h>
            #include<math.h>
            int main()
            {

                system("pause");
                return 0;
            }%

            ❯ cat -n a.c
            1  #include<stdio.h>
            2  #include<string.h>
            3  #include<stdlib.h>
            4  #include<math.h>
            5  int main()
            6  {
            7
            8      system("pause");
            9      return 0;
            10  }%
        ```
        - 如`cat a.c b.c`将两个文件拼接起来
    11. `head` *file* 输出 *file* 前 10 行`head file -n` *lines*  输出 *lines* 行
        `tail` *file* 输出 *file* 后10行 `tail file -n` *lines*   输出后 *lines* 行
    12. `more`/`less` *file* 分页输出 *file* 内容，空格翻页，回车下一行，q退出
    13. `hexdump` *file* 以十六进制输出文件内容(`-C`并排输出十六进制与 ASCII, `-n` N输出前 N 个字节)
    14. `man`：查看命令文档（manual）
`echo`：输出字符串（常配合重定向 / 管道使用）
`whoami`：获取当前用户
`whereis/which/whence`：查找命令所在位置
`clear`：清屏
`chmod`：更改文件权限
`ps`：显示进程信息
`date`：获取当前日期时间
`kill`：杀死进程（向进程发送信号）
`grep`：搜索文件内容（常配合重定向 / 管道使用）
`diff`：比较文件 / 目录内容
`curl`：发送 HTTP 请求；`wget`：下载文件
未完待续...