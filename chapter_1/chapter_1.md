###第一章绪论

[TOC]

####1.1 什么是操作系统

操作系统（Operating System，简称OS）是管理和控制计算机硬件与软件资源的计算机程序，是直接运行在“裸机”上的最基本的系统软件，任何其他软件都必须在操作系统的支持下才能运行。（来自度娘）

#####操作系统在计算机系统中的地位：

|计算机组成部分|面向的研究、适用人群|
|---|---|
|应用软件|应用用户|
|系统工具|应用开发人员|
|操作系统|应用开发人员|
|计算机硬件|操作系统开发人员|

#####操作系统目标：

有效性（系统管理人员的观点）
>管理和分配硬件、软件资源，合理地组织计算机的工作流程。

方便性（用户的观点）
>提供良好的、一致的用户接口，弥补硬件系统的类型和数量差别。

可拓展性（开放的观点）
>硬件的类型和规模、操作系统本身的功能和管理策略、多个系统之间的资源共享和互操作。

#####OS是计算机资源管理器：

管理对象：
>CPU、存储器、外部设备、信息（数据和软件）

管理内容：
>资源当前状态（数量和使用状态）、资源的分配、回收和访问的操作、相应管理策略（包括用户策略）

#####OS是拓展机：

在裸机上添加：设备管理、文件管理、存储管理（针对内存和外存）、处理器管理（针对CPU）

屏蔽异构的计算机硬件，提供统一的抽象接口。
>例如：Windows不像Macos一样预装了很多硬件设备的驱动，但是Windows也因此比较轻巧。

#####OS是用户使用系统的接口：

系统命令：
>命令行、菜单式、命令脚本式、图形用户接口GUI

系统调用：
>形式上类似于过程调用，在应用编程中使用。

#####操作系统举例：

MS OS
>MS DOS, MS Windows 3.x, Windows 95,$\cdots$，Windows 10，$\cdots$

类UNIX
>BSD, SRV4, Mac OS X，Linux，Android，Minix，$\cdots$
（p.s.:Minix是其中唯一一个微内核的操作系统，其他都为宏内核。）

实时OS
>交换机、工控计算机，例如：VxWorks，pSoS，Nucleus
（对时间的精度要求很高）

######需求推动发展：

器件的发展：
>CPU处理能力、内存容量和速度、$\cdots$
 CPU能耗上无法做到摩尔定律，Intel要活路，走多线程多核的路，~~以此为自己续上几秒~~。(@Loveall Wang非要我改成“续上几年”。) )

提高资源的利用率和系统性能;
>多道系统、分时系统、线程、虚拟化技术。

方便用户：
>文本终端、图形界面、网络服务，$\cdots$

####1.2 操作系统发展历史

#####电子管时代（1945-1955）

工作方式
>用户既是程序员，又是操作员，是计算机专业人员。
>编程语言为机器语言
>输入输出为纸带或卡片

计算机工作特点：
>用户独占全机：不出现资源被其他用户占用，资源利用率低。
>CPU等待用户：计算前，手工装入纸袋或卡片；计算完成后，手工卸去纸带或卡片；CPU利用率低。

#####晶体管时代（1955-1965）

利用磁带把若干个作业分类编成作业执行序列，每批作业由一个专门的监督程序（Monitor）自动一次处理。可使用汇编语言开发。

批处理中的作业组成：
>用户处理
>数据
>作业说明书（作业控制语言）

批：
>供一次加载的磁带或磁盘，通常由若干个作业组装成，在处理中使用一组相同的系统软件（系统带）

#####集成电路时代（1965-1980）

多道批处理的运行特征：
>多道：内存中同时存放几个作业
>宏观上并行运行：都处于运行状态，但都未运行完
>微观上串行运行：各作业交替使用CPU

多道批处理系统的特点

优点：
>资源利用率高：CPU和内存利用率高
>作业吞吐量大：单位时间内完成的工作总量大

缺点;
>用户交互性差：整个作业完成后或中间出错时，才和用户交互，不利于调试和修改
>作业平均周转时间长：短时间的周转时间显著增强

######分时系统（time-sharing system）

分时是指多个用户分享使用同一台计算机，多个程序分时共享硬件和软件资源。
>多个用户分时共享：单个用户使用计算机效率低，因而允许多个应用程序同时在内存中，分别服务于不同的用户
>前台和后台程序（foreground & background）分时：后台程序不占用终端输入输出，不与用户交互
>通常按时间片（time slice）分配：各个程序在CPU上执行的轮换时间

例如：MULTICS - Unix的“前辈”

#####微处理器时代（1980-）



######网络/分布式操作系统

Network Operating System(NOS):
>provides mainly file sharing
>Each computer runs independently from other computers on the network.
>(p.s.:every thing you send by third-party system can be viewed by their operators.pay attention to your message security)

Distributed Operating System(DOS):
>gives the impression there is a single operating syetem controlling the network.
>network is mostly transparent - it's a powerful vritual machine.

######集群系统/网络系统

Clustered Systems
>Clustering allows two or more systems to share external storage and balance CPU load.
>>*Asymmetric clustering.* one server runs the application while other server standby.
>>*Symmetric clustering.* all N hosts are running the application.

Closely coupled system:
>processors also have their own external memory
>communication takes place through high-speed channels
>Provides high reliability.

实例：
>Kerrighed, OpenSSI,openMosix

Grid Computing System
>建立在Internet技术、web技术、高性能计算等技术之上的综合软硬件的基础设施，采用开放标准，为动态参与的多个机构所构成组成的虚拟组织协同完成某类科学、工程或工业上的应用提供可拓展的、安全的、一致的、普及的、高效的大规模资源有效共享
>共享主要不在于文件交换，而在于对计算机、软件、数据和其他资源的直接接入使用，这是工业界、科学界中大量出现的协同解决问题和资源代理策略的需要
>这种共享必须被高度控制，资源提供者和消费者要清晰和详细的定义哪些资源可被共享，谁可享用这些资源，及共享发生的条件。

######虚拟化技术

相当于一个操作系统就是一个程序，有其他的操作系统运行着。

#####MINIX 历史

Tenny Bob等编写了一个在用户看来与UNIX完全兼容，然而内核全新的操作系统
>名字由来： mini UNIX
>1987年发布第一版
>不受任何商业许可证的限制，适用于教学
>内核代码量：4000
>比UNIX晚出现十年，并且其代码采用了一种更加模块化的组织方法
>是LINUX的“前辈”

目前的版本：MINIX 3
>本课程以MINIX 3为例子

####1.3 操作系统基本概念

####1.4 操作系统系统调用

####1.5 操作系统组织结构

####1.6 常用操作系统简介
