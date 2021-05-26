---
layout: post
title:  "项目实现算法架构"
date:   2021-5-26
categories: OpenCV Hispark SDK硬件平台适配
tags: Using makefile
excerpt: 使用Opencv进行仪表识别的架构的实现方式
--- 
# 使用SDK的具体思路  
首先默认加载出来模型默认返回值要为1，即告诉框架模型加载成功。

在进行Load模型加载的过程中，同时开辟出来响应的通讯管道，音频处理的线程，我在这里需要使用  可能尽可能多的线程，其中Load中包括 按键的初始化程序  这边还需要LED的开关



二、在指定的触发条件下跑算法