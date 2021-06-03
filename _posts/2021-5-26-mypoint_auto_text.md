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




# python源码 执行流程
1、使用及sensor显示   完成 imshow 及  使用Q拍照的功能  Q 拍照之后 保存在  target 中  的 target.jpg 表示当前需要处理的 图片    
这里转化为  表示 通过触发之后 当前需要处理的帧  然后传进 main / (run.py)


main中 判断当前执行的模式（默认为0  当然还有1   或者其他有效模式  这是一个有趣的接口）  在  mode 0  中进行 检测 


1 mathFeatures 函数 匹配特征  匹配cut_circle_img 的图片
- 创建两个dict 用老进行 FannBaseMastcher 匹配 
- colorfil_target 读取 pathCircle = cut_circle_img\\cut_circle_img.jpg 用来存放 指针表盘切割后存放的路径  同时进行错误判断
- target = 将都进来的赌片转化成 GRAY 像素空间
- sift = xfeatures2d.SiFT_creat  创建了提取算子
- target_des = sift.detectAndCompute (target)   特征提取   
- 文件排列 
- 在所有的文件中分别调用 fun 进行匹配 将匹配结果放进 distance list 中


# 实现了使用SIFT算子检测特征点及特征匹配



# 新的问题 算力不够  不可能针对每张图片提取特征点
将找好的特征点保存到 文件中



# 加时间戳  一分半 送一帧   主处理函数不变  