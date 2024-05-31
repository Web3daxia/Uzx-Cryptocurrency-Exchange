UZX 数字加密货币交易系统
本源码仅限于交流学习，凡涉及到法律问题与本人无关
#  最近有不法分子，通过我们的项目进行倒卖，请大家擦亮眼睛，不要上当受骗，我们也会保留我们相应的法律权利，请大家准守当地法律！
#  任何使用本源码从事商业活动，对别人和自己造成损失的，本人概不负责！
#  本系统持续长期更新 功能详细看文件夹内的图片
=====================================
- ## [English](README-EN.md)
---
### 提问和建议
- 欢迎咨询：Telegram:https://t.me/liuyuehi

#### UZX 是一个数字货币交易系统，它使用目前最流行的Java框架和相关技术开发而成。

## 愿景
    我们的使命是用Java开发世界上最好的、高性能的、安全的、开源的（重点）数字货币交易系统

## 警告(自行脑补FBI warning 画面)

1. 运营一家交易所是非常不容易的.

    UZX 可以使你很容易的建立一套数字货币交易系统，但是，它远远比搭建一个网站要难的多得多.不要以为简单的就是点击下一步，下一步即可完成。整个体系架构分为了很多的组件，需要专业的知识或者团队才能运行成功，好在有我们，可以随时联系我们。

2. 系统安全知识.

    UZX 框架不能保护你的数字资产安全，也不能保证你的系统运行安全。在部署过程中，需要注意网络安全的设置，如果你不在行的话，可以找一个专业的运维人员。

3. 法律风险

- 法律风险第一条：不要触犯中华人民共和国的法律条例。
- 技术无罪，请在法律范围内使用UZX框架。
- 如果你想使用UZX作为商业应用，最好请个律师，确保你的商业应用在法律允许的范围内。一切用于商业化项目所带来的法律和经济问题，概不负责。

4. 你需要知道的基本知识

- 法律知识（安全第一条，法律最重要）
- Java知识（主要是spring）
- linux知识（CentOS、Ubuntu等等）
- 安全知识

### 主要技术

- 后端：Spring、SpringMVC、SpringData、SpringCloud、SpringBoot
- 数据库：Mysql、Mongodb
- 其他：redis、kafka、OSS
- 前端：Vue、iView、less

### 测试环境
- 这里为防止玩坏，不提供测试环境，参考图片即可

##  重点业务介绍

    后端框架的核心模块为 exchange,market模块。

    其中exhcnge模块完全采用Java内存处理队列,大大加快处理逻辑,中间不牵涉数据库操作,保证处理速度快,其中项目启动后采用继承ApplicationListener方式，自动运行；

    启动后自动加载未处理的订单,重新加载到JVM中，从而保证数据的准确，exchange将订单处理后，将成交记录发送到market;

    market模块主要都是数据库操作，将用户变化信息持久化到数据库中。主要难点在于和前端交互socket推送，socket推送采用两种方式，web端socket采用SpringSocket，移动端采用Netty推送,其中netty推送通过定时任务处理。

## 环境搭建
- Centos 7.6+
- MySQL 5.7.16+
- Redis 6.2.7
- Mongodb 4.0+
- kafka_2.11-2.2.1
- nginx-1.16.0+
- JRE 8u241
- JDK 1.8
- Vue

## 服务部署准备

1. 项目用了Lombok插件，无论用什么IDE工具，请务必先安装Lombok插件
2. 项目用了QueryDsl，如果遇见以Q开头的类找不到，请先编译一下对应的core模块，例如core、exchange-core、xxx-core这种模块
3. 找不到的jar包在项目jar文件夹下
4. jdk版本1.8以上
5. 初始化sql在sql文件夹中配置文件
配置文件打开这个设置会自动建表
#jpa
spring.jpa.hibernate.ddl-auto=update

## 修改服务配置文件
请根据服务实际部署情况修改以下配置。配置文件位置如下，如果配置文件中没有某一项配置，说明该模块未使用到该项功能，无需添加：

```
各个模块/src/main/resources/dev/application.properties
```

mysql数据库:

```
spring.datasource.**
```

reids

```
redis.**
```

mongodb(主要存储K线图相关数据)

```
spring.data.mongodb.uri
```

kafka

```
spring.kafka.bootstrap-servers
```

阿里云OSS，图片资源上传

```
aliyun.**
```

短信配置

```
sms.**
```

邮件认证

```
spring.mail.**
```

腾讯防水校验

```
water.proof.app.**
```

### 服务启动
 1. maven构建打包服务

 2. 将各个模块target文件夹下的XX.jar上传到自己的服务器

 3. 先启动cloud模块，再启动market，exchange模块，剩下的没有顺序。

 4. 启动服务

    例：

    ```
    nohup  java  -jar  /自己的jar包路径/cloud.jar  >/dev/null 2>&1 &
    ```
    
    ```
    nohup  java  -jar  /web/app/cloud.jar  >/dev/null 2>&1 &
    nohup  java  -jar  /web/app/exchange.jar  >/dev/null 2>&1 &
    nohup  java  -jar  /web/app/market.jar  >/dev/null 2>&1 &
    nohup  java  -jar  /web/app/exchange-api.jar  >/dev/null 2>&1 &
    nohup  java  -jar  /web/app/ucenter-api.jar  >/dev/null 2>&1 &
    nohup  java  -jar  /web/app/otc-api.jar  >/dev/null 2>&1 & 
    nohup  java  -jar  /web/app/chat.jar  >/dev/null 2>&1 & 
    nohup  java  -jar  /web/app/wallet.jar  >/dev/null 2>&1 & 
    nohup  java  -jar  /web/app/admin.jar  >/dev/null 2>&1 &
    ```
    持续更新
