# Spring Boot 实战 读书笔记

## 第一章 概述

Spring Boot最重要的核心：

* 自动配置：针对很多Spring应用程序常见的应用功能，Spring Boot能自动的提供相关配置
* 起步依赖：告诉Spring Boot 需要什么功能，就能引入需要的库
* 命令行界面：可选特性，只需专注代码编写，无需传统项目构建
* Actuator：能够深入运行中的Spring Boot应用程序，一探究竟

## 第二章 开启Hello World之旅

启动引导Spring

* 注解@SpringBootApplication开启组件扫描和自动配置，他相当于以下三个注解的合体
  1. Spring的@Configuration：表明该类使用Spring基于java的配置
  2. Sprig的@ComponentScan：启动组件扫描，这样web控制器类和其他组件才能被自动发现并注册为Spring应用程序上下文里的Bean
  3. Spring Boot的@EnableAutoConfiguration：这个小注解也可以称为@Abracadabra，它开启了Spring Boot自动配置的魔力，使得我们不用再写成片的配置了
* 如果应用程序需要Spring Boot自动配置以外的其他Spring的配置，一般来说最好把它写到一个单独的@Configuration标注的类里
* 起步依赖本质上是一个maven项目对象模型，定义了对其他库的传递依赖，这些东西加在一起支持某项功能
* 起步依赖的版本是由使用的Spring Boot的版本决定的

## 第三章 自定义配置

覆盖Spring Boot的自动配置：

* 编写一个显示的配置，即可覆盖Spring Boot的自动配置
* Spring Boot的默认错误也为error.xx

## 第四章 测试

* 模拟Spring MVC

  Spring的Mock MVC框架模拟了Spring MVC的很多功能

## 第六章 Spring Boot 与 Grails

## 第七章 Actuator

Spring Boot Actuator的关键特性是在应用程序里提供众多web端点，通过他们可以了解应用程序运行时的内部状况

* 配置

  ```xml
  </dependency>
    <groupId>org.springframework.boot</groupId> 
    <artifactId>spring-boot-starter-actuator</artifactId> 
  </dependency>
  ```

* 端点分为三大类：配置端点、度量端点、其他端点

* 查看配置明细

  * /beans(本地访问地址：http://localhost:8080/actuator/beans)，返回json文档，描述上下文每个Bean的情况，包括其java类型以及注入的其他Bean
  * /env 会生成应用程序可用的所有环境属性列表，包括环境变量、JVM属性、命令行参数，以及application.yml文件提供的属性
  * /mappings 生成端点到控制器的映射

## 第八章 部署

* 部署war包

  由于应用没有启用Spring MVC DispatcherServlet的web.xml文件或者Servlet初始化类，所以在打war包之前需要配置，此时就需要Spring Boot出马了，它提供的SpringBootServletInitializer是一个支持Spring Boot的Spring WebApplicationInitializer实现，除了配置Spring的DispatcherServlet，它还会在Spring应用程序上下文里查找Filter、Servlet或ServletContextInitializer类型的Bean，把它们绑定到Servlet容器里

* 配置

  要使用SpringBootServletInitializer，只需要创建一个子类，覆盖configure()方法来指定Spring配置类

  ```java
  import org.springframework.boot.builder.SpringApplicationBuilder; 
  import org.springframework.boot.context.web.SpringBootServletInitializer; 
  public class ReadingListServletInitializer 
   extends SpringBootServletInitializer { 
       @Override 
       protected SpringApplicationBuilder configure( 
       SpringApplicationBuilder builder) { 
       	return builder.sources(Application.class);
       }
  }
  ```

  这里configure()方法传入一个SpringApplicationBuilder参数，并将其作为返回，期间它调用了sources()方法注册了一个Spring配置类。这里只注册了一个Application类，这个Application类既是启动类（带有main方法），也是一个Spring配置类

* 打包：mvn package

* 值得注意：war包一方面可以直接部署在服务器，也可以直接运行（如果你没有删除Application里的main方法）

  ```java
  java -jar demo.war
  ```

  



