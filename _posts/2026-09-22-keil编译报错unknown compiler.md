---
title: keil编译报错unkonwn compiler
date: 2026-09-22 
categories: [技术]
tags: [博客]
---

### 一、问题

移植一个新的 Keil 工程（HC32F460），编译时遇到报错。作为对比，手头另一个工程用同样的 Keil、同样选 CMSIS 6.1.0，却能正常编译。

### 二、现象
1、使用version 5 编译器，遇到问题（原工程使用也是AC5
```c
D:\keil\Arm\Pack\ARM\CMSIS\6.1.0\CMSIS\Core\Include\cmsis_compiler.h(287): error:  #35: #error directive: Unknown compiler.
    #error Unknown compiler.
```
2、改成ARM Compiler 6.22
```c
compiling TransformFunctionsF16.c...
armclang: error: unknown argument: '--diag_suppress=186,66'
```
### 三、排查过程
查找网络说是CMSIS 6.1.0不支持Compiler V5.06了。但实际上，我有两个工程文件，一个能编译一个不能，二者在RTE里面CMSIS都选择的6.1.0.产生矛盾。

由于两个工程使用不用的芯片，查找资料后得知芯片型号决定绑定的DFP（设备支持包），DFP对CMSIS路径有优先级更高的绑定；怀疑DFP的配置“覆盖”了RTE里选择的 CMSIS 版本。

### 四、解决问题
下载更低版本的CMSIS如5.9.0
https://forum.anfulai.cn/forum.php?mod=viewthread&tid=96992
下载CMSIS后双击安装，然后在keil里进入Pack Installer，移除6.1.0。
![](/assets/img/keil_unknownCompiler/image-1.png)
接下来检查RTE里CMSIS的版本
![alt text](/assets/img/keil_unknownCompiler/image.png)

以上完成后可正常编译。