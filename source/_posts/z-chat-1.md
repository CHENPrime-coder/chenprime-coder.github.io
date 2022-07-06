---
title: Z-Chat项目笔记(一)
cover: /covers/GOSTBLADE2.png
updated: 2022-06-30 09:50:22
id: 000003
categories:
- project
tags:
- 项目
toc: true
---
暑假了，想给自己找点事情干。所以就计划开发一个类似于微信的程序（swing，springboot，mybatis，vue-element-admin）。

<!-- more -->

此项目未单人开发，锻炼个人能力。

# 需求分析

首先是需求分析。
![需求分析](/images/z-chat-1-demand.png)
这里分成了5个模块，根据这些需求。决定使用以下技术栈：`springboot，mybatis，redis，mysql，springdata，vue-element-admin，java-swing`

**redis**是为了实现未读消息的数量，方便高频读写。而**mysql**就是传统的用法，**swing**用来作桌面端应用程序，**vue-element-admin**是用于web管理页面。其他的就不解释了。
