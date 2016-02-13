<!--
author:ivan 
date: 2016-02-11
title: 利用ssh反向隧道访问内网-赚钱宝折腾 
tags: ssh,赚钱宝 
category: 赚钱宝折腾 
status: publish
summary: 赚钱宝折腾，利用ssh反向隧道从外网访问内网。从而实现远程调度。
-->
***
  **迅雷赚钱宝**root后真是一切都自由了！

  关于root，原来是序列号的后8位，后来迅雷官方修改规则了，特别是pro，完全进不去。没办法，只能在某宝上找了一个算号的算出来密码进去了。

ROOT后首先是要创建一个自己的root权限用户，并配置entWare环境。这部分会在之后的文章中整理出来，今天先说一下ssh反向隧道。

##一、为什么要反向隧道呢?
 1.上网环境做不了端口映射。

 2.自己搞不定root后的配置，需要别人远程帮忙设置的。

##二、如何建立反向隧道？
```
ssh -R 19999:localhost:22 远程用户名@远程ip -p 远程端口
```

  这样就实现了把本地的22端口映射到远程的19999端口上了.
  这时候在远程ip的主机里，连接19999就可以访问内网里的赚钱宝了：
```
ssh localhost -p 19999
```

* 如果安装了autossh的话，可以这样：

```
autossh  -M 5678 -R 19999:localhost:22 远程用户名@远程ip -p 远程端口
```
  其中，-M后的端口号可以随便，这是为在本地建立一个监听端口，只要别端口冲突就行。

  可以用screen来让它保持在后台运行。

>  *关于autossh和screen的安装，参见entWare环境配置，里面会提到如何安装软件*