---
layout: post
title: offline pip
date: 2018-06-10 20:27:00 +08:00
tags: pip
---

# pip离线安装 #

`pip install --download`命令在pip 10之后被弃用，改为`pip download`。


`pip download`可以将指定的第三方库及其依赖下载到指定目录，提供给离线环境安装。

## 下载库 ##

基本用法

    pip download -r requirements.txt


针对特定平台、版本的库

`--platform`, `--python-version`, `--implementation`, `--abi`指定库的适用平台和版本。

    pip download --only-binary=:all: \
                 --platform linux_x86_64 \
                 --python-version 36 \
                 --implementation cp \
                 -d /path/of/package \
                 -r requirements.txt


## 离线安装 ##

    pip install --no-index --find-links=/path/of/packages -r requirements.txt


`--no-index`和`--find-links`配合使用，后者指定package安装包所在的目录。