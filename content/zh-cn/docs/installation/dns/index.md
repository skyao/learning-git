---
title: "DNS污染"
date: 2022-03-08
weight: 140
description: >
  配置DNS以避免DNS污染
---

github 和一些相关的域名，经常被污染，导致无法解析从而造成 git clone 失败。

解决的方式除了使用避开了 DNS 污染的干净的 DNS 代理服务器外，还有一个方式就是在本地 hosts 文件中直接设置相关的 host，避开 DNS 污染。

### linux 下设置 hosts

在 linux 下，修改 `/etc/hosts` 文件：

```bash
sudo vi /etc/hosts
```

加入以下记录：

```properties
199.232.68.133 raw.githubusercontent.com
20.205.243.166 github.com
```

linux 下这个修改可以即时生效，无需重启或者注销。

### windows 下设置 hosts

类似的修改 `C:\Windows\System32\drivers\etc` 文件。不过这个文件很可能是被设置为了"只读"，因此修改前要先去除"只读"属性，可以在修改完成之后再恢复为"只读"。设置的方式和 linux 下是一样的：

```properties
199.232.68.133 raw.githubusercontent.com
20.205.243.166 github.com
```

重启，或者手工刷新dns缓存。打开cmd命令行，输入以下命令：

```bash
ipconfig /flushdns
```

