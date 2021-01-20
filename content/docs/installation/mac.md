---
title: "MacOS安装"
date: 2021-01-20
weight: 220
description: >
  在MacOS上安装Git
---


### 下载

在 [git官网](https://git-scm.com/)的下载页面找到mac版本

https://git-scm.com/download/mac

下载得到安装包，如 `git-2.19.0-intel-universal-mavericks.dmg`

### 安装

安装过程基本按照默认设置，一路next就好了。

### 修复

有些在升级macos的版本之后，再使用git时会报错如下：

```bash
$ git version
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

此时需要重新安装 `xcode command line`:

```bash
$ xcode-select --install
```

参考资料：

- [解决MacOS升级后出现xcrun: error: invalid active developer path, missing xcrun的问题](https://www.jianshu.com/p/50b6771eb853)