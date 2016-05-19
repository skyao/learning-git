CentOS 6.5 上安装git
===================

# 前言

CentOS 6.5 上默认安装的git版本为 1.7.1, 版本太低, 报错如下:

    using .gitcredentials to set credentials
    [WARNING] Installed git version too old for credentials support

因此必须升级到新版本.

# 安装方式

## yum安装

依次执行以下命令:

    rpm -i http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
    yum --enablerepo=rpmforge-extras update
    yum --enablerepo=rpmforge-extras provides git

在列出的版本列表中选择最新的一个版本, 如:

    git-1.7.12.4-1.el6.rfx.x86_64 : Git core and tools
    Repo        : rpmforge-extras
    Matched from:

执行安装命令:

	yum --enablerepo=rpmforge-extras install git-1.7.12.4-1.el6.rfx.x86_64

安装结束之后, 通过"git version" 命令可以查看更新之后的版本信息:

    git version 1.7.12.4

# 资料参考

- [CentOS 6.x 升级 Git](https://segmentfault.com/a/1190000002729908): 主要参考这个文章, 除了安装git那里命令有错-:)