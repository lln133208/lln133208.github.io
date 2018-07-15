---
layout: post
title: git useful command
date: 2018-07-14 20:33:00 +08:00
tags: git
---

# Git useful command #

1. search commits contains a log message

    ```
    git log --all --grep "something"
    ```

2. rename tag

    ```
    git tag -m new old
    git tag -d old
    git push origin :refs/tags/old
    git push --tags
    ```

3. rename branch

    ```
    git branch -m old new
    ```
