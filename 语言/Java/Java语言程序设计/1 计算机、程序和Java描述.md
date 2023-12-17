[TOC]

# 1 计算机、程序和Java描述

## 1.7 一个简单的Java程序

-   类
-   主方法 main method
-   保留字 reserved word
    class public static void
-   关键字 keyword
-   注释 comment 
    -   行注释 line comment //
    -   块注释 block comment /* */
-   块 block 
    -   类块 class block
    -   方法块 method block

## 1.8 创建、编译和执行Java程序

Java源程序保存为.java文件，被编译器(complier)编译为.class文件(字节码文件)。.class文件被Java虚拟机(JVM)执行

源文件文件名与公共类名完全相同，后缀为.java

Java字节码可以在不同的硬件平台和操作系统上运行

![image-20200801002432959](1%20%E8%AE%A1%E7%AE%97%E6%9C%BA%E3%80%81%E7%A8%8B%E5%BA%8F%E5%92%8CJava%E6%8F%8F%E8%BF%B0.assets/image-20200801002432959.png)

>   执行过程：
>
>   1.  JVM先使用类加载器(class loader)程序将类字节码加载到内存中
>   2.  如果有用到其它类，类加载器会在需要前动态加载
>       1.  JVM使用字节码校验器(bytecode verifier)程序校验字节码的合法性

## 1.8 创建、编译和执行Java程序

