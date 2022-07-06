---
title: Spring Boot 使用outlook发送邮件
cover: /covers/GOSTBLADE3.jpg
updated: 2022-07-06 13:17:32
id: 000004
categories:
- java
tags:
- springboot
toc: true
---

就突发奇想，想写一个邮件验证码的功能。这里就先记录一下我的代码（就单纯发个邮件）

<!-- more -->

既然是要用到springboot的email组件，那就需要先用maven导入jar包：

{% codeblock "pom.xml" lang:xml %}
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
{% endcodeblock %}

倒入完我们就来编写一下配置文件（核心）：

{% codeblock "application.yaml" lang:yaml %}
spring:
  mail:
    # 微软outlook的smtp服务器
    host: smtp.office365.com
    username: ********@outlook.com
    # 由于这里使用微软的outlook，所以password就只需要输入你微软账号(上面的********@outlook.com)的密码就好了
    password: ********
    # 端口
    port: 587
    # 细节配置
    properties:
      mail.smtp.auth: true
      mail.smtp.starttls.enable: true
      mail.smtp.starttls.required: true
{% endcodeblock %}

接下来编写接口，这里就直接写一个get请求的接口用来测试。先写服务层

{% codeblock "MailService.java" lang:java %}
@Service
public class MailService {

    @Autowired
    JavaMailSender sender;

    /**
     * 发送邮件
     * @param from 发件人
     * @param to 收件人
     * @param subject 邮件主题，标题
     * @param text 邮件内容
     */
    public void sendMail(String from, String to, String subject, String text) {
        SimpleMailMessage simpleMailMessage = new SimpleMailMessage();
        simpleMailMessage.setFrom(from);
        simpleMailMessage.setTo(to);
        simpleMailMessage.setSubject(subject);
        simpleMailMessage.setText(text);

        sender.send(simpleMailMessage);
    }

}
{% endcodeblock %}

接下来编写控制器层

{% codeblock "MailService.java" lang:java %}
@RestController
public class MailController {

    @Autowired
    MailService service;

    @GetMapping("/send")
    public String send() {
        service.sendMail(
                "******@outlook.com",
                "******@qq.com", 
                "Test",
                "testtesttest"
        );
        return "success";
    }

}
{% endcodeblock %}

接下来运行测试，进入浏览器访问`http://localhost:8080/send`擦看结果：

![请求成功](/images/spring-mail-success.png)

我们查看收件箱

![邮件内容](/images/mail-success-1.png)

结束，很简单吧。
