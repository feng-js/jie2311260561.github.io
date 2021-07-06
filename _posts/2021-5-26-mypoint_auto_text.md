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
在另一个线程中创建的 VIDEO_FRAME_INFO_S 好像没有传递过来 转后之后 没有正确处理  
使用直接创建变量的方法 
使用malloc 进行内存分配的方法   
```
   Mat image;
     frame2Mat(srcFrm, image);
     if (image.size != 0){
        LOGE("frame to mat success\n");
     }
```
直接使用这种方法是可以的

通过逐步加判断的方式将错误定位在  
s32Ret = HI_MPI_IVE_CSC(&hIveHandle, &pstSrc, &pstDst, &stCscCtrl, bInstant);  
这一句，但是看不多这句是干什么用的    比较遗憾。。。。    没有转化成功

但是这这一句 的参数意思是   Handle 的头   ps str 的地址   DSt 的纸质  C特人了
的地址   最后不知道放在那里  可以 干什么


 但是这句 如果不成功就会 free 掉刚才 变量的地址空间  如果成功了就转到 下一句  下一句是干什么的也不是很清晰 明白  


 这块转换过程中的问题  不是很清楚式什么问题  

使用  在主程序里    使用这两个结构体  进行传输 
typedef struct tagIPC_IMAGE{
    HI_U64 u64PhyAddr;
    HI_U64 u64VirAddr;
    HI_U32 u32Width;
    HI_U32 u32Height;
} IPC_IMAGE;

typedef struct hiIVE_IMAGE_S {
    HI_U64 au64PhyAddr[3];   /* RW;The physical address of the image */
    HI_U64 au64VirAddr[3];   /* RW;The virtual address of the image */
    HI_U32 au32Stride[3];    /* RW;The stride of the image */
    HI_U32 u32Width;         /* RW;The width of the image */
    HI_U32 u32Height;        /* RW;The height of the image */
    IVE_IMAGE_TYPE_E enType; /* RW;The type of the image */
} IVE_IMAGE_S;


 传这个东西 没有实现 现在改成传文件名  然后打开文件名的方式



最后放弃 直接传图片的形式  采用保存文件传文件名的形式

/**
    读取完整消息.
*/
int FdReadMsg(int fd, void* msgBuf, int msgSize);

/**
    写入完整消息.
*/
int FdWriteMsg(int fd, const void* msgData, int msgLen);




在taurus_adapt.c中  591行 有对于当前结构体的定义   static LcdAic g_lcd; 所有的操作都是基于当前封装的结构体


目前注释掉了  在 adapt 中的按键 响应函数和 按键  处理及回调函数


按键处理函数使用 扫描或者回调的方法   个人觉得扫描的方法 好像不是很好用 使用添加fd回调的方法 试试
在回调中要将fd中的所有内容全部抛出   确保不会重复按下异常
