#编程  #Shell
## 第一章 Shell 概述

### 1. Shell 和 Shell 脚本

首先，shell 和 shell script 是两个不同的概念。通常平常所说的 shell 通常都是指 shell 脚本。

- shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。Ken Thompson 的 sh 是第一种 Unix Shell，Windows Explorer 是一个典型的图形界面 Shell。
- shell 脚本（shell script），是一种为 shell 编写的脚本程序。

### 2. 常见 Shell

sh (全称 Bourne Shell): 是 UNIX 最初使用的 shell，而且在每种 UNIX 上都可以使用。

Bourne Shell 在 shell 编程方面相当优秀，但在处理与用户的交互方面做得不如其他几种 shell。

bash（全称 Bourne Again Shell）: LinuxOS 默认的，它是 Bourne Shell 的扩展。与 Bourne Shell 完全兼容，并且在 Bourne Shell 的基础上增加了很多特性。可以提供命令补全，命令编辑和命令历史等功能。它还包含了很多 C Shell 和 Korn Shell 中的优点，有灵活和强大的编辑接口，同时又很友好的用户界面。

- csh (全称 C Shell): 是一种比 Bourne Shell 更适合的变种 Shell，它的语法与 C 语言很相似。

- Tcsh: 是 Linux 提供的 C Shell 的一个扩展版本。

- Tcsh 包括命令行编辑，可编程单词补全，拼写校正，历史命令替换，作业控制和类似 C 语言的语法，他不仅和 Bash Shell 提示符兼容，而且还提供比 Bash Shell 更多的提示符参数。

- ksh (全称 Korn Shell): 集合了 C Shell 和 Bourne Shell 的优点并且和 Bourne Shell 完全兼容。

- pdksh: 是 Linux 系统提供的 ksh 的扩展。

- pdksh 支持人物控制，可以在命令行上挂起，后台执行，唤醒或终止程序。

- Bash 在日常工作中被广泛使用。同时，Bash 也是大多数 Linux 系统默认的 Shell。

> 在一般情况下，人们并不区分 Bourne Shell 和 Bourne Again Shell，所以，像 #!/bin/sh，它同样也可以改为 #!/bin/bash。

## 第二章 Shell 解析器

### 1. 什么是解析器 ？

**Shell** 是 Linux 操作系统下的命令行解析器，是用户和 Linux 内核交互的工具，其实 Shell 担任着类似翻译官的角色，如下图所示：

![[Shell解析器.png]]

从上图可以看到，解析器起名为 Shell（外壳）也是有原因的，整个操作系统其实是一层层包起来的，是一层层的抽象，抽象程度越高越方便用户操作，这就类似于编程语言，汇编程序更接近于底层，再就是 C 语言抽象程度比汇编语言高，Java 语言抽象程度更高。

那么，第一个 Unix Shell 是谁发明的呢？

肯·汤普逊在写第一版 UNIX 的时候开发了 Shell，仿效 Multics 上的 Shell 所实现出来的。

### 2. Linux 中都有哪些解析器 ？

Linux 解析器有如下几种：

```bash
[ root@localhost ~]# cat /etc/shells
/bin/sh
/bin/bash
/usr/bin/sh
/usr/bin/bash
/bin/tcsh
/bin/csh
```

在 CentOS  7 中默认使用 /bin/bash，如下所示：

```bash
[ root@localhost ~]# cat /etc/redhat-release 
CentOS Linux release 7.6.1810 (Core) 
[ root@localhost ~]# echo $SHELL
/bin/bash
[ root@localhost ~]#
```

#### 2 .1 /bin/bash 和 /usr/bin/bash

> Bash，Unix shell 的一种，在 1987 年由布莱恩·福克斯为了 GNU 计划而编写。1989 年发布第一个正式版本，原先是计划用在 GNU 操作系统上，但能运行于大多数类 Unix 系统的操作系统之上，包括 Linux 与 Mac OS X v10.4 起至 macOS Mojave 都将它作为默认 shell，而自 macOS Catalina，默认 Shell 以 zsh 取代。    ------ 维基百科

#### 2 .2 /bin/sh 和 /usr/bin/sh

如下所示，/bin/sh 和 /usr/bin/sh 是 bash 的一个软连接。

```bash
[ root@localhost ~]# ls -l /bin/sh
lrwxrwxrwx. 1 root root 4 9 月  24 01:40 /bin/sh -> bash
[ root@localhost ~]# ls -l /usr/bin/sh
lrwxrwxrwx. 1 root root 4 9 月  24 01:40 /usr/bin/sh -> bash
[ root@localhost ~]#
```

#### 2 .3 /bin/tcsh

tcsh 是一个向下兼容 c shell 的 Unix shell。它本质上是为 c shell 增加命令补完，命令编辑等其他功能。目前作为 FreeBSD 和其延伸发行版的默认 shell。                  ------ 维基百科

#### 2 .4 /bin/csh

> C shell 是 Unix shell 的一种，由比尔·乔伊在 BSD 系统上开发。C shell 脱胎于 Unix 第六版的/bin/sh，也是 Bourne shell 的前身。这种 shell 的语法类似于 C 语言，与 Bourne shell 相比，C shell 有不少特别的功能，比如 aliases（别名）、command history（命令的历史）。目前 C shell 已不再被广泛使用，后继者包括 Tenex C shell（tcsh）、Korn shell（ksh）、GNU Bourne-Again shell（bash）。         ------ 维基百科

## 第三章 Shell 脚本入门

### 1. 脚本格式

脚本以 `#!/bin/bash` 开头 (指定解析器)

### 2. 第一个 Shell 脚本：Hello World

> 需求：创建一个 Shell 脚本，输出 helloworld

```bash
# 创建脚本 
[linux@localhost datas]$ cat helloworld.sh 
#!/bin/bash echo "hello huangxb" 

# 执行脚本方式1 
[linux@localhost datas]$ bash helloworld.sh hello huangxb 

# 执行脚本方式2 
[linux@localhost datas]$ ./helloworld.sh
-bash: ./helloworld.sh: 权限不够
```

- 方式 1，本质是 bash 解析器帮你执行脚本，所以脚本本身不需要执行权限；
- 方式 2，本质是脚本自己需要执行，所以需要执行权限

### 3. 多命令处理

> 需求：在/home/hogg/目录下创建一个 banzhang. txt，在文件中添加“I Love cls”。

```bash
#!/bin/bash
cd /home/linux/
touch banzhang.txt
echo "I LOVE YOU" >> banzhang.txt
```

## 第四章 Shell 中的变量

### 1. 常用系统变量

- $HOME 家目录，即/home/user/(~) 下
- $PWD 当前的目录
- $SHELL 当前默认的解析器
- $USER 当前的用户名

### 2. 自定义变量

#### 2.1 基本语法
1.  定义变量：变量=值 _等号两边不能留有空格_
2.  撤销变量：unset 变量
3.  输出变量：echo $变量
4.  声明静态变量： readonly (只读) 变量，注意：不能 unset

```bash
[linux@localhost datas]$ A=2
[linux@localhost datas]$ echo $A
2
[linux@localhost datas]$ unset A # 撤销变量
```


#### 2.2 变量定义规则

1.  变量名称可以由字母，数字和下划线组成，不能以数字开头，环境变量名建议大写
2.  等号两侧不能有空格
3.  在bash中，变量默认类型都是字符串类型，无法直接进行数值运算
4.  变量的值如果有空格，需要使用双引号或单引号括起来
5. 可把变量提升为全局变量，可供其他 shell 程序使用 export 变量

### 3. 特殊变量

#### 3.1 $n

##### 3.1.1 基本语法

$n （描述：n 为数字，$0 代表脚本名称，10 以内参数用$1-9 表示， 10 以上的需要用大括号包含， 9 表示，10 以上的需要用大括号包含，9 表示，10 以上的需要用大括号包含，{10}）

##### 3.1.2 案例实操

```bash
[linux@localhost datas]$ vim text.sh
echo "$0$1$2$3"

[linux@localhost datas]$ bash text.sh 1 2 3 4 
text.sh 1 2 3
```

#### 3.2 $#.

##### 3.2.1 基本语法

$# (功能描述：获取所有输入参数个数，常用于循环)

##### 3.2.2 案例实操

```bash
!/bin/bash 
echo "$0 $1 $2 $3" 
echo $#
```

### 3.3   $ * 和 $ @

-   $* （描述：代表命令行中所有的参数，把所有参数看成一个整体）
-   $@ （描述：也代表命令行中所有的参数，不过把每个参数区分对待）

### 3.4 $?

$? （描述：最后一次执行命令的状态，0：正确执行）

## 第五章 运算符
### 1. 基本语法

1.  $((运算式)) 或 $[运算式]
2.  expr +,-,\*,/,% 加减乘除取余
> _expr 运算符间要有空格_

### 2. 实操案例

```bash
# 计算2+3
[linux@localhost datas]$ expr 2 + 3
5

# 计算（2+3）*4
## 方式1
[linux@localhost datas]$ expr `expr 2 + 3` \* 4
20

## 方式2
[linux@localhost datas]$ s=$[(2+3)*4]
[linux@localhost datas]$ echo $s
20
```

## 第六章 条件判断

### 1. 基本语法

`[ condition ]`（注意 condition 前后要有空格)

### 2. 常用判断条件

#### 2.1 两个整数之间比较

| 符号 | 描述                      |
| ---- | ------------------------- |
| -lt  | (less than) 小于          |
| -le  | (less equal) 小于等于     |
| -eq  | (equal) 等于              |
| -gt  | (greater than) 大于       |
| -ge  | （greater equal）大于等于 |
| -ne  | (not equal) 不等于        |

#### 2.2 文件权限判断

-   -r 有读的权限
-   -w 有写的权限
-   -x 有执行的权限

#### 2.3 文件类型判断

-   -f 文件存在并且是一个常规文件
-   -e 文件存在
-   -d 文件存在并且是一个目录

```bash
# 判断23是否大于2
[linux@localhost datas]$ [ 23 -gt 2 ]
[linux@localhost datas]$ echo $?
0

# 判断helloworld.sh是否有写入权限
[linux@localhost datas]$ [ -w hellowrld.sh ]
[linux@localhost datas]$ echo $?
1

# 判断目录中文件是否存在
[linux@localhost datas]$ [ -e /home/linux/datas ]
[linux@localhost datas]$ echo $?
0
```

