---
title: "更新fork仓库"
linkTitle: "更新fork仓库"
weight: 331
date: 2021-01-20
description: >
  更新github上fork的仓库
---

## 背景

- 在github上fork了某项目
- 原仓库有新的改动
- 想将原仓库的改动更新到自己fork的仓库

## 操作过程

### 同步代码

以netty为例：

- 源地址：git@github.com:netty/netty.git
- 我fork的： git@github.com:skyao/netty.git

按照下面的步骤:

1. 为本地仓库增加一个remote, 命名为"upstream":

	```bash
	git remote add upstream git://github.com/dapr/dapr.git
	# 或者
	git remote add upstream git@github.com:dapr/dapr.git
	```

	也有人推荐下面的多了--track参数的的方式:

	```bash
	git remote add --track master upstream git://github.com/dapr/dapr.git
   ```

2. fetch 这个upstream远程的所有分支到remote-tracking分支, 例如upstream/master

	```bash
	git fetch upstream
   ```

3. 确认当前分支是master分支, 如果不是checkout到master分支

	```bash
	git branch
	git checkout master
   ```

4. 同步upstream的修改到本地, 可以选择rebase或者merge

	```bash
	git rebase upstream/master
	git merge upstream/master
   ```

	注: 推荐用merge.

5. 将更新之后的版本推送到自己fork的仓库

	```bash
	git push -f origin master
   ```

### 同步tag

```bash
git fetch upstream --tags

git push --tags
```

## 参考资料

- [Pull new updates from original Github repository into forked Github repository](http://stackoverflow.com/questions/3903817/pull-new-updates-from-original-github-repository-into-forked-github-repository)
- [How to update a GitHub forked repository?](http://stackoverflow.com/questions/7244321/how-to-update-a-github-forked-repository)
- [HOW TO GITHUB: FORK, BRANCH, TRACK, SQUASH AND PULL REQUEST](https://gun.io/blog/how-to-github-fork-branch-and-pull-request/)
