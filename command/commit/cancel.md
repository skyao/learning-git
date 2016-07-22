# 撤销commit

## 背景

- 代码修改后已经执行了commit和push
- 希望撤销这次commit，回到到这个commit之前的状态：包括本地和远程仓库

## 操作

1. 先 `git log` 找出提交的历史记录

	比如下面有四个commit记录：

	```bash
    $ git log
    commit 87dabb290ae1a4e620512b7cd81d2161747c6ec9
    Author: Sky Ao <aoxiaojian@gmail.com>
    Date:   Thu Jul 21 16:36:26 2016 +0800

        add cliet builder and wrap native api; setup integration test; add first unit test case and integration test case

    commit 6899dd19dbe58da6ae65fd157a791151967c16b2
    Author: Sky Ao <aoxiaojian@gmail.com>
    Date:   Thu Jul 21 15:17:00 2016 +0800

        rollback package name to etcdserverpb, otherwise etcd server will reject the request

    commit 18d034b3a1e20e81ece3d2f6ba9919e8bdb3dfd4
    Author: Sky Ao <aoxiaojian@gmail.com>
    Date:   Thu Jul 21 14:37:19 2016 +0800

        change java version to 1.7

    commit 4beef3ce6557a41e657c2ee4e19c6156eabd759b
    Author: Sky Ao <aoxiaojian@gmail.com>
    Date:   Wed Jul 20 18:40:18 2016 +0800
	```

	现在需要撤销最新的这一次 `87dabb290ae1a4e620512b7cd81d2161747c6ec9` 提交， 回退到它的上一次 `6899dd19dbe58da6ae65fd157a791151967c16b2`。

2. 执行 reset 命令

	```bash
    git reset --hard 6899dd19dbe58da6ae65fd157a791151967c16b2
    HEAD 现在位于 6899dd1 rollback package name to etcdserverpb, otherwise etcd server will reject the request
	```

	注意 commitid 是要撤销的commit的前一次commit的id，也就是说 reset 命令是将提交 **重置** 到要撤销的前一次。

    reset命令执行完成后，本地仓库就重置，相当于撤销了 `6899dd1` 之前的所有commit。

3. 执行 push 命令

	```bash
    $ git push origin HEAD --force
    Total 0 (delta 0), reused 0 (delta 0)
    To git@github.com:skyao/jetcd.git
    + 87dabb2...6899dd1 HEAD -> master (forced update)
	```

	push命令执行完成，远程仓库也就重置了。

## 参考资料

- [git 删除错误提交的commit](https://www.douban.com/note/189603387/)