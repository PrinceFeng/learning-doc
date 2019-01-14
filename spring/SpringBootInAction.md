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











