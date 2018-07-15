---
layout: post
title: git submodule
date: 2018-06-10 20:24:00 +08:00
tags: git
---


# subtree #

`git subtree`用来解决嵌套项目版本管理的问题。

## Usage ##

```
# 添加子项目，拉取子项目到指定目录
git subtree add --prefix path/of/local/dir subproject-git-address branch --squash

# 拉取子项目更新
git subtree pull -prefix path/of/local/dir branch --squash
```
> `--squash`表示将子项目的提交记录压缩为一条，否则保留全部子项目的`commit log`。

----

先将`subproject-address`设置为一个`remote`,此时子项目只是被`fetch`到本地的一个`detach HEAD`。
添加子项目后，子项目才被`merge`到本地项目中。

```
# 设置远程repo
git remote add -f remote-repo subproject-git-address

# 添加子项目
git subtree add --prefix path/of/local/dir remote-repo branch --squash

# 拉取子项目更新
git fetch remote-repo
git subtree pull --prefix path/of/local/dir remote-repo branch --squash
```

---

将子项目修改推送到子项目`remote repo`

```
git remote add remote-preo subproject-git-address
git subtree push --prefix path/of/local/dir remote-repo branch
```

