---
title: vim 使用的一些小技巧
type: post
tags: ["vim", "工具"]
date: 2019-05-18T12:47:11.000Z
category: 工具
published: true
---

- tab 分隔文件列对齐

```bash
:%!column -t
```

- vim 字体颜色看不清

```bash
# Ubuntu 中设置(在 /etc/vim/vimrc 中加入）
set background=dark

# CentOS 中设置(在 /etc/vimrc 最后一行加入)
hi Comment ctermfg = blue  //更改vi中注释内容字体颜色，可修改为：white、darkyellow、blue 等
```

修改前：

![ubuntu_vim_1.png](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1559372667519-27fbd607-668a-423d-8fd4-42e8d427976e.png#align=left&display=inline&height=292&name=ubuntu_vim_1.png&originHeight=292&originWidth=554&size=14789&status=done&width=554)

修改后：

![ubuntu_vim_2.png](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1559372686477-e552f700-3a76-483c-8b50-b12ff5d57127.png#align=left&display=inline&height=290&name=ubuntu_vim_2.png&originHeight=290&originWidth=559&size=14858&status=done&width=559)
