# merge 时冲突

## 准备工作

我们先从 master 分支拉出一个 develop 分支

![](images/conflict-merge/new-branch.jpg)

然后我们修改 a.txt 文件，内容如下：

```bash
aaaaaaaaaa10 - changed by myself and others
aaaaaaaaaa20
aaaaaaaaaa30 - changed in develop branch
aaaaaaaaaa50
aaaaaaaaaa60
```

内容修改如下

- 修改了第三行的内容
- 删除了原来的第四行
- 在最后增加了一行

提交并push到远程仓库，然后 checkout 回 master branch，继续修改 a.txt 的内容：

```bash
aaaaaaaaaa10 - changed by myself and others
aaaaaaaaaa20
aaaaaaaaaa30 - changed in master branch
aaaaaaaaaa40
aaaaaaaaaa50
```

这里我们故意修改第三行，以便造成文件冲突。

![](images/conflict-merge/before-merge.jpg)

## 开始 merge

保持当前之分为 master，然后右键点 develop 分支，选择 "Merge develop into current branch":

![](images/conflict-merge/merge-operation.jpg)

提示冲突：

![](images/conflict-merge/merge-confilicts.jpg)

此时 a.txt 文件的内容如下，包含 merge 冲突内容：

```bash
aaaaaaaaaa10 - changed by myself and others
aaaaaaaaaa20
<<<<<<< HEAD
aaaaaaaaaa30 - changed in master branch
aaaaaaaaaa40
aaaaaaaaaa50
=======
aaaaaaaaaa30 - changed in develop branch
aaaaaaaaaa50
aaaaaaaaaa60
>>>>>>> develop
```

后面的操作和pull 时重复的处理一致。

