---
title: Docker学习笔记(1)
cover: /images/docker.png
updated: 2022-05-20 10:40:22
id: 000001
categories:
- docker
tags:
- 运维
---
Docker学习笔记 - 命令

<!-- more -->

<!-- {% codeblock "ElasticsearchConfig.java" lang:java %}
{% endcodeblock %} -->

![image](/images/docker-cli1.png)
docker volume [COMMAND]

- create			创建一个数据卷
- inspect          显示一个或多个数据卷（volume）的详细信息
- ls                     列出所有volume
- prune             删除目前没人使用的数据卷volume
- rm                   删除指定volume

代码块测试：
{% codeblock "HelloWord.java" lang:java %}
public static void main(String[] args) {
    System.out.println("Hello World!")
}
{% endcodeblock %}