# Chapter 0: Foreword, Reading Guide, and Study Plan / 序言、导读与学习计划

> 中文版本在前, English version follows. 
>
> The Chinese and English versions cover the same ideas.

>  本笔记是《程序员的自我修养：链接、装载与库》的学习总纲，用于整理本书的核心问题、学习路线、代码实验、Java 对照、Android/OS 联系、补充资料和阶段计划。
>
> This note is a stud roadmap for *The Self-Cultivation of Programmers: Linking, Loading and Libraries*. It is used to organize the book's core questions, learning path, code experiments, Java comparisions, connections with Android/OS development, supplementary materials, and staged study plan.

---

## 中文版

### 1. 核心问题

这本书围绕一个核心问题展开：

> 一个程序是如何从源代码变成正在操作系统中运行的进程的？

围绕这个问题，本书进一步讨论：

- 源代码如何被编译成目标文件；
- 目标文件中保存了什么内容；
- 链接器如何把多个目标文件和库文件组合起来；
- 可执行文件如何被操作系统装载到内存；
- 动态链接为什么存在，以及它如何工作；
- C/C++ 运行库在程序启动和运行过程中做了什么；
- 应用程序如何通过系统调用请求操作系统服务。

这本书不是单纯讲C/C++语法，或者操作系统，而是把编译、链接、装载、运行库、动态链接和系统调用串联起来。

---

### 2. 整体理解

一个普通程序看起来是从`main`函数开始执行的，但这只是用户代码层面的入口。在`main`之前，操作系统和运行库已经完成了很多准备工作，例如：

- 创建进程；
- 为进程建立地址空间；
- 装载可执行文件；
- 映射代码段、数据段等内容到内存；
- 加载需要的动态库；
- 初始化 C/C++ 运行库环境；
- 处理全局变量和全局对象的初始化；
- 最后才调用用户写的`main`函数。

`main`是用户代码的入口，不是整个程序执行过程的真正起点。

这本书的价值在于帮助理解程序背后的稳定机制。即使以后主要写 Java、Web、数据库、Android 或应用层代码，这些底层知识也能帮助更好地理解 JVM、内存、文件系统、性能优化、程序崩溃、依赖问题和系统调用。

---























