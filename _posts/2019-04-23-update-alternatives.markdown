---
layout: post
title: update-alternatives
---

Debian系发行版提供`update-alternatives`来管理程序多版本共存和切换问题。

假设将java8安装在`/usr/local/java`目录下，目录结构如下

```
-> tree /usr/local/java -L 2

/usr/local/java
└── jdk1.8.0_212
    ├── bin
    ├── COPYRIGHT
    ├── include
    ├── javafx-src.zip
    ├── jre
    ├── lib
    ├── LICENSE
    ├── man
    ├── README.html
    ├── release
    ├── src.zip
    ├── THIRDPARTYLICENSEREADME-JAVAFX.txt
    └── THIRDPARTYLICENSEREADME.txt

6 directories, 8 files
```



* 将该版本的java作为默认版本

    ```

    # update-alternatives --install link name real-path priority
    # link: 系统命令的链接，命令的统一入口，指向真正版本的可执行文件，更改版本其实就是更改该link的指向
    # name: 配置名称，用来在update-alternatives命令中查询
    # real-path: 真正的可执行程序路径
    # priority: 该条配置的优先级，数值越大，优先级越高。默认情况下，update-alternatives 工作在auto mode，选择优先级最高的版本。
    sudo update-alternatives --install /usr/bin/java java /usr/local/java/jdk1.8.0_212/bin/java 100
    sudo update-alternatives --install /usr/bin/javac javac /usr/local/java/jdk1.8.0_212/bin/javac 100
    ```

* 查看机器上所有的java版本

    ```
    update-alternatives --display java
    ```

* 选择指定的java版本

    ```
    update-alternatives --config java
    ```

