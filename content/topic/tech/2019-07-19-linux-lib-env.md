---
title: Linux 下的动态库、静态库与环境变量
type: post
topic/tags: ["Linux", "运维"]
date: 2019-07-19T02:22:00.000Z
category: 运维
published: true
---

最近这几天在处理集群软件的过程中，遇到各种各样的库和环境变量的问题，被虐的不清！趁此机会，整理了一下 Linux 下静态库、动态库（共享库）和环境变量的一些知识，与大家共享一下。



# 库的种类

Linux 下的库有两种：**静态库**和**动态库**（共享库）。

静态库的代码在**编译过程中**已经被载入可执行程序，因此生成的可执行程序体积较大。静态用 `.a` 为后缀， 例如： `libhello.a` 。

动态库（共享库）的代码是在可执行**程序运行时**才载入内存的，在编译过程中仅简单的引用，因此生成的可执行程序代码体积较小。动态库通常用 `.so` 为后缀， 例如： `libhello.so` 。

为了在同一系统中使用不同版本的库，可以在库文件名后加上版本号为后缀,例如： `libhello.so.1.0` ，由于程序连接默认以 `.so` 为文件后缀名。所以为了使用这些库，通常使用建立符号连接的方式。



# 库的环境变量

**LIBRARY_PATH**
环境变量：指定程序静态链接库文件搜索路径。

**LD_LIBRARY_PATH**
环境变量：指定程序动态链接库文件搜索路径。



# 库的搜索顺序

**动态库链接时搜索路径的顺序：**

1. 编译目标代码时指定的动态库搜索路径；
1. 环境变量
**LD_LIBRARY_PATH** 指定动态库搜索路径，它指定程序动态链接库文件搜索路径；
1. 配置文件
**/etc/ld.so.conf** 中指定的动态库搜索路径；
1. 默认的动态库搜索路径
**/lib**；
1. 默认的动态库搜索路径
**/usr/lib**。

**静态库链接时搜索路径的顺序：**

1. ld 会去找 `gcc` / `g++`  命令中的参数 `-L` ；
1. 再找 gcc 的环境变量 **LIBRARY_PATH**，它指定程序静态链接库文件搜索路径；
1. 再找默认库目录 `/lib` ， `/usr/lib` ， `/usr/local/lib` ，这是当初 compile gcc 时写在程序内的。


# 环境变量文件加载顺序

正常登录配置文件顺序加载过程，所谓正常登录指用户通过输入用户名和密码登录的状态。

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1566551259962-56a823c2-f6f6-4e64-bd75-4dc0e27f4e28.png#align=left&display=inline&height=244&name=image.png&originHeight=244&originWidth=845&size=19821&status=done&width=845)

在 CentOS 7，我们测试一下：
```bash
# /etc/profile
$ sudo sed -i '1 iecho "/etc/profile goes start"\n' /etc/profile;head -n 3 /etc/profile
echo "/etc/profile goes start"

# /etc/bashrc
$ sudo sed -i '1 iecho "/etc/bashrc goes start"\n' /etc/bashrc;head -n 3 /etc/bashrc
echo "/etc/bashrc goes start"

# .bash_profile
$ sed -i '1 iecho "~/.bash_profile goes start"\n' ~/.bash_profile;head -n 3 ~/.bash_profile
echo "~/.bash_profile goes start"

# .bashrc
$ sed -i '1 iecho "~/.bashrc goes start"\n' ~/.bashrc;head -n 3 ~/.bashrc
echo "~/.bashrc goes start"

$ sudo echo "echo '/etc/profile.d/test.sh goes'" >/etc/profile.d/test.sh;cat /etc/profile.d/test.sh
echo '/etc/profile.d/test.sh goes'

$ sudo sed -i '1 iecho "/etc/profile goes start"\n' /etc/profile;head -n 3 /etc/profile
echo "/etc/profile goes start"
```

重新登录终端，可以看到各个环境变量文件的启动顺序：

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1563507266576-43dcd960-e475-4305-80d6-1c81b023ab4d.png#align=left&display=inline&height=327&name=image.png&originHeight=327&originWidth=772&size=42121&status=done&width=772)


当我们不正常启动（su 命令切换用户），环境变量文件加载顺序如下：

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1563513885037-271bd3eb-80e8-4d48-b871-387cf23ea70e.png#align=left&display=inline&height=291&name=image.png&originHeight=291&originWidth=723&size=20899&status=done&width=723)

![](https://qiniu.bioinit.com/yuque/0/2019/png/126032/1563514034328-0b7fdc31-638d-4c3a-8681-bce631eac7d4.png#align=left&display=inline&height=456&name=image.png&originHeight=456&originWidth=840&size=51052&status=done&width=840)



# 常用环境变量

我们可以使用 `env` 命令查看当前用户的所有环境变量设置：
```bash
$ env
MANPATH=/usr/local/software/texlive/2018/texmf-dist/doc/man:/usr/local/auto-devops/ansible/docs/man:
XDG_SESSION_ID=61
HOSTNAME=ecs-steven
TERM=xterm
SHELL=/bin/bash
HISTSIZE=3000
......
LESSOPEN=||/usr/bin/lesspipe.sh %s
INFOPATH=/usr/local/software/texlive/2018/texmf-dist/doc/info:
XDG_RUNTIME_DIR=/run/user/1000
DISPLAY=localhost:16.0
HISTTIMEFORMAT=%F %T
_=/usr/bin/env
```



# **用户环境变量常用设置方法**


## 系统级别设置

- /etc/profile：

全局的系统环境变量设置。适用于多个 shell，比如 bash, sh, zsh 之类。

- /etc/bashrc：

bash shell 全局环境变量。



## 用户级别设置

- ~/.bashrc：

包含专用于当前用户 bash
shell 的 bash 信息，当登录时以及每次打开新的 shell
时，该文件被读取。每开一个 shell，这个文件会读取一次。

- ~/.bash_profile：

每个用户都可使用该文件输入专用于自己使用的 shell 信息，当用户使用 login
shell 模式登陆时，该文件仅仅执行一次。



## **用户临时（当前 shell 对话框）环境变量设置**

export
命令：用于/bin/bash shell类型


## 用户级别 .bashrc 示例

```bash
# User Specific Alias
alias ll='ls -lht'
alias le='less -S'

# Custom History setting
HISTFILESIZE=3000000
HISTSIZE=3000
export HISTTIMEFORMAT='%F %T '
HISTCONTROL=ignoredups
PROMPT_COMMAND="history -a“

# Login Style
PS1='\033[35;1m\u@\h \[\e[m\]\t \[\033[36;1m\]$(pwd) \n$ \[\e[m\]'
clear;

# Shortcut Commands
bcl_fq='/Bioinfo/Project/BCL_fastq‘

# Custom Path
ANACONDA2_PATH='/Bioinfo/Pipeline/SoftWare/Anaconda2/bin'
PERL_PATH='/Bioinfo/Pipeline/SoftWare/Perl-5.26/bin‘
export PATH="$ANACONDA2_PATH:$ANACONDA3_PATH:$hdf5_PATH:$PERL_PATH:$PATH"

export LD_LIBRARY_PATH="……: $LD_LIBRARY_PATH"
export PYTHONPATH="……: $PYTHONPATH"
```

