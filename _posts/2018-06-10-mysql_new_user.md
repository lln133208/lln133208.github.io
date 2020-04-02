---
layout: post
title: Mysql new user can not access
categories: [Database, Mysql]
---

# 在此page中记录一些平时遇到的Mysql问题的解决方案，以便日后查询。

## 新建用户无法登录问题
问题：使用PhpMyAdmin新建用户后，无法正常登录管理页面。
原因：Mysql默认存在一个用户名为空的账户，在Mysql服务器所在机器上不需要输入账号和密码就可以登录数据库，也正是因为这个账号的存在使得新建帐号无法正确登录数据库。
解决方法：使用PhpMyAdmin删除改账户，或是使用命令行删除，命令如下

    mysql -uroot -p
    use mysql;
    delete from user where User='';
    flush privileges;
    exit;

## 无法远程登录Mysql
问题：Mysql数据库运行在Linux服务器上，远程无法登录，
原因：Mysql服务器没有开启监听网络socket功能，或者是Linux服务器防火墙问题。
解决方法：查看Mysql的配置文件/etc/my.cnf，注释掉下列代码

    bind-address=127.0.0.1

修改防火墙规则，开放**3306**端口，最后重新启动Mysql服务。
