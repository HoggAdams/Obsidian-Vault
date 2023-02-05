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

## 