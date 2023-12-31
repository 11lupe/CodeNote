## Kuberneters 介绍

[TOC]

### 1. 发展历程

#### 单体应用 vs 微服务

>   大型单体应用：由很多个组件组成，这些组件紧密耦合在 起；以单个进程或几个进程的方式，运行在几台服务器之上
>
>   微服务：小的、可独立运行的组件
>
>   每个微服务 以独立的进程（ 见图 1.1 ）运行，并通过简单且定义良好的接口（ API)与其他的微服务通信。
>
>   服务之间可以通过类似 HTTP 这样的同步协议通信，或者通过像 AMQP 这样的异步协议通信 这些协议能够被大多数开发者所理解，并且并不局限于某种编程语言。这意味着任何 个微服务，都可以用最适合的开发语言来实现

![单体应用和微服务](Kubernetes%20%E4%BB%8B%E7%BB%8D.assets/单体服务和微服务.png)

单体应用：

-   发布时间长
-   迭代不频繁
-   运维人员处理部署、监控
-   开发、部署、管理在同一实体进行
-   一处修改，重新部署整个应用
-   需要一台高性能服务器，提升只能垂直扩展(增加CPU、内存或其它系统资源)或水平扩展(增加更多服务器)；任何一部分不能扩展，则整个应用不能扩张
-   扩容：针对整个应用

微服务：

-   彼此解耦，可独立开发、部署、升级、伸缩
-   实现快速迭代
-   扩容：只针对单个服务
-   (问题) 组件部署要求越来越高——组件增多、数据中心增长，手动不太适用
-   (问题) 跨进程、跨机器，使调试、定位问题变得困难；解决：分布式定位系统，如Zipkin

解决微服务手动问题：自动化措施实现自动调度、配置、监管和故障处理。--> kuberetes

### 开发趋势

-   为应用程序提供一个一致的环境
-   DevOps 和 NoOps
    -   DevOps: 同一个团队参与应用的开发、部署和运维的整个生命周期
    -   NoOps： 开发者是部署程序本身， 不需要知道硬件基础设施的任何情况，也不需要和运维团队交涉
    -   优点：
        -   开发者在生产环境中运行应用

### kubernetes特点

-   可自主部署应用，控制部署频率，脱离运维团队
-   系统管理员：从监管应用到监管kubernetes，以及剩余的系统资源

>   Kubemetes 抽象了数据中心的硬件基础设施，使得对外暴露的只是 个巨大的
>
>   资源地 它让我们在部署和运行组件时，不用关注底层的服务器。使用 Kubemetes
>
>   部署多组件应用时，它会为每个组件都选择 个合适的服务器，部署之后它能够保
>
>   证每个组件可以轻易地发现其他组件，并彼此之间实现通信。