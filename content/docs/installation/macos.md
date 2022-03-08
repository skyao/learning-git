---
title: "MacOS安装"
date: 2021-01-20
weight: 20
description: >
  在MacOS上安装Git
---

## 手工安装

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

## brew安装

参考 https://git-scm.com/download/mac 页面的说明。


```bash
$ brew install git
……
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.
zsh completions and functions have been installed to:
 /opt/homebrew/share/zsh/site-functions
Emacs Lisp files have been installed to:
 /opt/homebrew/share/emacs/site-lisp/git
==> **Summary**
🍺 /opt/homebrew/Cellar/git/2.35.1: 1,523 files, 43.5MB
==> **Running `brew cleanup git`...**
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> **Caveats**
==> **git**
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.
zsh completions and functions have been installed to:
 /opt/homebrew/share/zsh/site-functions
Emacs Lisp files have been installed to:
/opt/homebrew/share/emacs/site-lisp/git
```

验证安装：

```bash
git --version
git version 2.32.0 (Apple Git-132)
```
