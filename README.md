UZX Digital Cryptocurrency Trading System
This source code is for communication and learning only, and any legal issues related to it are not my responsibility

#  Recently, there have been illegal elements who resell through our project. Please keep your eyes open and do not fall for scams. We will also reserve our corresponding legal rights. Please abide by local laws!
#  I am not responsible for any losses caused to others or myself by using this source code for commercial activities!
#  This system is continuously updated for a long time
- ## [中文](README-CN.md)
=====================================

#### Questions and suggestions

- Telegram: https://t.me/coinshuai
#### UZX is a digital currency trading system developed using the most popular Java framework and related technologies.。

## vision
   Our mission is to develop the world's best, high-performance, secure, and open-source (key) digital currency trading system using Java

## Warning (self brain supplementing FBI warning screen)
Running an exchange is very difficult

UZX can make it easy for you to establish a digital currency trading system, but it is much more difficult than building a website. Don't think it's just a matter of clicking Next to complete it. The entire architecture is divided into many components that require professional knowledge or a team to run successfully. Fortunately, with us, you can always contact us.

2. System security knowledge

The UZX framework cannot protect the security of your digital assets, nor can it guarantee the safe operation of your system. During the deployment process, attention should be paid to network security settings. If you are not proficient, you can find a professional operation and maintenance personnel.

3. Legal risks

-Article 1 of Legal Risks:
-Technically innocent, please use the UZX framework within the legal framework.
-If you want to use UZX as a commercial application, it is best to hire a lawyer to ensure that your commercial application is within the legal limits. We are not responsible for any legal or economic issues arising from commercial projects.

4. Basic knowledge you need to know
-Legal knowledge (safety first, law is the most important)
-Java knowledge (mainly spring)
-Linux knowledge (CentOS, Ubuntu, etc.)
-Safety knowledge

### Main technologies
- Backend: Spring, SpringMVC, SpringData, SpringCloud, SpringBoot
- Database: MySQL, Mongodb
- Other: Redis, Kafka, OSS
- Front end: Vue, iView, less
  
### testing environment
- To prevent spoilage, a testing environment is not provided here. Please refer to the pictures for reference

## Key Business Introduction
The core modules of the backend framework are the exchange and market modules.

The exhcnge module fully utilizes Java memory processing queues, greatly speeding up processing logic without involving database operations, ensuring fast processing speed. After the project starts, it inherits the Application Listener method and runs automatically;

Automatically load unprocessed orders after startup and reload them into the JVM to ensure data accuracy. Exchange processes the orders and sends transaction records to the market;

The market module mainly involves database operations, persisting user change information into the database. The main difficulty lies in interacting with the front-end for socket push. Socket push adopts two methods: SpringSocket on the web end and Netty push on the mobile end. Netty push is processed through scheduled tasks.
## Environmental construction
- Centos 7.6+
- MySQL 5.7.16+
- Redis 6.2.7
- Mongodb 4.0+
- kafka_2.11-2.2.1
- nginx-1.16.0+
- JRE 8u241
- JDK 1.8
- Vue
## Service deployment preparation
1. The project uses the Lombok plugin. Regardless of the IDE tool used, please make sure to install the Lombok plugin first
2. The project uses QueryDsl. If you encounter a class starting with Q that cannot be found, please compile the corresponding core module first, such as core, exchange core, xxx core modules
3. The jar package that cannot be found is located in the project jar folder
4. JDK version 1.8 or above
5. Initialize SQL and configure files in the SQL folder
Opening this configuration file will automatically create a table
#JPA
Spring. jpa. hibernate. ddl auto=update
