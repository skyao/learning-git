# 更新fork的仓库

在 github 上 fork 了一些仓库, 需要更新到最新版本, 记录方法和过程.

## 前言

需要将自己 fork 的 github 项目更新, google 了一下方法, 记录下来.

参考资料:

- [Pull new updates from original Github repository into forked Github repository](http://stackoverflow.com/questions/3903817/pull-new-updates-from-original-github-repository-into-forked-github-repository)
- [How to update a GitHub forked repository?](http://stackoverflow.com/questions/7244321/how-to-update-a-github-forked-repository)
- [HOW TO GITHUB: FORK, BRANCH, TRACK, SQUASH AND PULL REQUEST](https://gun.io/blog/how-to-github-fork-branch-and-pull-request/)

## 更新过程

按照下面的步骤:

git@github.com:netty/netty.git

1. 为本地仓库增加一个remote, 命名为"upstream":

	> git remote add upstream git://github.com/netty/netty.git

	也有人推荐下面的多了--track参数的的方式:

	> git remote add --track master upstream git://github.com/netty/netty.git

2. fetch 这个upstream远程的所有分支到remote-tracking分支, 例如upstream/master

	> git fetch upstream

3. 确认当前分支是master分支, 如果不是checkout到master分支

	> git branch
	> git checkout master

4. 同步upstream的修改到本地, 可以选择rebase或者merge

	> git rebase upstream/master
	> git merge upstream/master

	注: 还是推荐用merge.

5. 将更新之后的版本推送到自己fork的仓库

	> git push -f origin master


