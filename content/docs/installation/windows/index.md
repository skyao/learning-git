---
title: "windows安装"
date: 2021-01-20
weight: 30
description: >
  在windows上安装Git
---


## 下载

在 [git官网](https://git-scm.com/)的下载页面找到windows版本的下载页面：

https://git-scm.com/download/win

下载最新版本：

https://github.com/git-for-windows/git/releases/download/v2.47.0.windows.2/Git-2.47.0.2-64-bit.exe

下载得到安装包，如 Git-2.47.0.2-64-bit.exe。

## 安装

安装路径选择 `C:\Users\sky\work\soft\git` 或者 `D:\sky\work\soft\git`

安装过程基本按照默认设置，一路next就好了。

## 配置

### 修改启动后的默认路径

安装完成之后，桌面的 Git Bash 快捷方式打开之后，默认进入当前用户的home目录。

如果需要修改，比如我个人习惯直接进入代码存放路径如 `C:\work\code` 或者 `D:\sky\work\code`，则需要修改快捷方式的属性。

编辑快捷方式的属性：

![](images/windows-link.jpg)

目标中删除 `--cd-to-home`， 然后将起始位置从默认的 `%HOMEDRIVE%%HOMEPATH%` 修改为 `C:\work\code`。

### 修改控制台字体

Git Bash 控制台默认的字体如果不合适（通常字体偏小），可以修改。

1. 点下图中红色箭头处，下拉菜单中选择"Options"

	![](images/setting-options.jpg)

2. 在 "Text" 中可以选择字体和大小

	![](images/setting-fonts.jpg)


##  安装配置 zsh

这些工作是 windows 工作环境配置的一部分，具体请见 https://skyao.io/learning-windows11/docs/develop/zsh/

