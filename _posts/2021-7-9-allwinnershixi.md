---
layout: post
title:  "珠海allwinner实习日记"
date:   2021-07-09 20：01
categories: 灌水
tags: 灌水
excerpt: 来到公司每天的打工日程
---

* content
{:toc}

# day1 2021-7-9 来到珠海的第一天  解决住房问题
    今天kirin亲自来到车站接我，路途向我介绍了到公司的相关情况，还给我指了公司的位置。

    行李放到了家里之后，就去看房子了，知寓直接就断货了  直接没有房子   

    去看看附近的房子  个人认为优先距离最短  然后就是公司公交车
    确实十分感谢kirin  以及公司的款待  直接给我安排上了5点的酒店住宿

    一番体验下来  还是感觉十分不错的

# day2 2021-7-10 第二天  看房子 
    计划早上去看 金发苑的房子  下午去看  唐家湾附近的房子  

    中午吃饭  在酒店附近找找饭吃 
    
### 看房情况
    珠海个人租户一般都是自己出租加委托代理出租  ，初来乍到没有 认识的人和渠道   
    所以只能找到代理    
    代理会收取一个月房租的一半 作为中介费 
    虽然会有点略贵 对于我这个实习生来说  实在是不太友好，但是也没有什么好的办法。 就只能租这个了。

## 一点点小想法
    适配opencv 做全景照片    车辆倒车镜优化    --基于nezha
        全志IC读数用于多媒体业务，什么智能音箱，显示器等的方案。   暂时想到一个 摄像头的方案   

### 个人吐槽
    自己来带的钱就不多，所以租完房子，付完房租真的就么得钱了。。。。。。
    呜呜呜，我太惨了


# day3 今天就要搬去租的房子了 7-11 
    瑶哥今天帮我搬行李，美滋滋，嘿嘿。。。。
    

### 今天早上看到的好东西
    推理框架各家厂商都有各家厂商的东西，还有开源的框架等等，感触颇丰，但是目前基本上所有的工作都是在arm上或者gpu上专门进行的优化处理。
    今天还看到了 fpga 和 riscv 的一本书 基于riscv和fpga的嵌入式应用开发，想要，等发了工资我就奖励自己一本书。

    今天早上的 知识总结： 能够将业务落地，使用框架加速  包括Opencv也可以加速   这也是一个可以注意的点
    
    海思的NNIE框架目前正在使用，也在做相关的东西，这块也学习一下，IVE视频加速框架，这些都是使用c语言实现的。我猜测这应该是像裸机一样，将摄像头不作为一个linux的通用设备，而是一个可执行文件，在运行的过程中加载及初始化，可能会有相关的硬件如FIFO加速技术，底层没有太过研究。  总之还是感触深刻呀！

### 中午搬了过来 
    收拾了两个小时，现在房间里没有可以喝的水，还好我带了一杯，感觉不错，喝水问题还有待解决，与此同时，桌子上没有椅子， 房东说周一买椅子给我，顺便看一下有没有电磁炉 给我用。



# day 4 已经把房子基本收拾好了，房子里面基本正常。 7-12
    床已经收拾好了，房子也基本收拾好了，所以现在基本没什么事情，等待入职中。。。。。。
    房东提供了 煤气灶一个  电脑椅 一个  挺好用的   体验不错。。。。。。。
    
    
# day5 天气太热了  出去 汗如雨下   
    还好今天快递比较给力  ，嘿嘿  比较专业  啥事没有
    假期基本呆在家里没事   顺便开发  查阅一下资料   搞搞摄像头

    准备一下明天入职的资料   身份证  学生证   还有记得拿上钥匙

    明天开始工作， 先查找相关方向的资料  及  文献

# day6 入职第一天 
    学习开发环境  公司 内部权限管理  申请流程 及部署流程

# day7
    完成了heloword demo开发并上传了文档
# day8
    完成了摄像头的demo开发，并上传了文档
# day9 今天晕哥来公司啦
    编译了opencv 终于可以用了！！！
    仅仅记录任务完成情况啦~！
    希望自己继续加油加油!!!
    向晕哥讨了块芯片，希望自己可以加油完成工作  输出文档和demo 

    今天研究了io口的demo 和 按键的demo    目前使用轮询的方法可以驱动按键，知道了按键还可以是哟个 pull 的方法来进行使用，希望自己自己可以专业一点  抽抽空搞了！

    今天晚上跑了Tina的wifi连接 好像可以直接连接网络   有待开发  尝试尝试 哈哈哈   可以试试直接从服务器获取数据  adb 获取可以不用啦
    明天预计跑出摄像头摄影的demo  然后就准备制作数据集啦！

# day10 其实我是有想法自己diy一块核心板？
    自己diy一块核心板  可以做自己的服务器  有没有道理？ 讲道理 其实开源也挺好玩的  哈哈哈
    分析一下全志的开发板  研究研究原理图  看能不能diy一块出来·


# day11 
    晕哥给寄的东西到了，这边尝试一下，明天把外壳给拆了。

# day12 7-26号
    今天早上就开始研究如何拍视频。由于刚开始我读取摄像头的数据格式为JPEG，通过查阅资料，发现了使用MJPEG 来进行编码该图片，但是我并没有找到相关的方法。
    然后就使用YUV来进行输出。YUV输出了image，由于自己电脑的问题无法查看YUV图片，所以无法产看图片的有效，但是图片的大小经过计算是对的。、
    然后就使用 yuv 来直接保存 yuv 视频，视频文件没有打开  宣告失败。 但是经过查看  视频文件的 大小是真的 确实是 存在的。 但是我就是不知道是怎么回事。。
    

# day13-day15
    这两天是疲劳的两天，问题多多。好在老板能够满族几乎所有的要求。IT部门还相对比较给力嗷。
    V4L2框架的变编程 已经下载来了几个工程 还需要继续琢磨  跑通对应的demo

## 今天开会感悟
    不是所有的芯片都是完美的，芯片的IP也是需要更新。而且芯片的Bug一旦出现，影响后果就会很严重。
    我们公司的项目都是有人做的，不同的人在不同的产品上负责不同的项目。每周的开会同事们都会交流这周的项目成果。以及出现的bug，和完成的东西。
    具体细节先不做透漏。大概bug 是什么FIFO溢出  UART 等问题
    还有启动 功耗等问题

## 明天希望能把训练环境搞出来  争取训练个模型出来 然后跑一下检测
    嘻嘻嘻