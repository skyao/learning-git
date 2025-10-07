---
title: "tag命令用法"
linkTitle: "tag命令用法"
weight: 341
date: 2021-01-20
description: >
  tag命令介绍
---

记录git中tag命令的用法。

## tag命令用法

### 列出已有tag

	git tag
	git tag -l 'v1.4.2.*'

### 添加tag

添加轻量级标签：

	git tag -a v1.4

添加含附注类型的标签：

	git tag -a v1.4 -m 'my version 1.4'

推送到远程：

	git push origin v1.4

或者--tags推送全部：

	git push --tags

### 删除tag

删除本地tag：

	git tag -d v1.0.0

删除远程tag：

	git push origin :refs/tags/v1.0.0

## 资料

### git官方资料

中英文两个版本：

- [2.6 Git Basics - Tagging](http://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [2.6 Git 基础 - 打标签](http://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE)
