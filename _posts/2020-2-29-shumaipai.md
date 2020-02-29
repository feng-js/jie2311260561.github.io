---
layout: post
title:  "树莓派的入门配置，包括ftp 远程桌面，中问输入法，语音模块配置"
date:   2020-03-29 12:47
categories: 树莓派，API，语音识别
tags: Using Python
excerpt: 树莓派的入门配置，包括ftp 远程桌面，中问输入法，语音模块配置
---
#  第一次开机！！
从树莓派的[官方网站](https://www.raspberrypi.org/downloads/raspbian/)下载树莓派的系统![在这里插入图片描述](https://img-blog.csdnimg.cn/20191107184524435.png)
推荐下载第二个空间小，功能全！
##  第二步 格式化sd卡  ！
一定要使用sd的官方软件：[SD Card Formatter ](https://sourceforge.net/projects/win32diskimager/)
选择磁盘，然后点击格式化即可。
##  第三步 安装系统镜像！
使用  [win32diskimager](https://sourceforge.net/projects/win32diskimager/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191107185409283.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU0NDU4OA==,size_16,color_FFFFFF,t_70)
选中镜像文件 写入 即可（等待大约 10min  根据内存卡读写速度而定）
写入成功后一定不要  选择格式化内存卡！
#  树莓派的ftp配置

```c
sudo apt-get install vsftpd
sudo service vsftpd start
sudo nano /etc/vsftpd.conf
#修改文件如下
```

```c
1.	anonymous_enable=NO   //不允许匿名访问
2.	
3.	local_enable=YES        //允许本地用户访问
4.	
5.	write_enable=YES        //允许写
6.	
7.	local_umask=022         //设定上传后文件权限掩码

```

```c
sudo service vsftpd restart #重启
```
ftp 配置完成

接下来可以使用
  Ifconfig 查看树莓派的ip  然后在电脑上使用软件FileZilla Client 输入树莓派的ip 账户名称时pi 密码为初次登录树莓派时设置的密码。
#  树莓派远程桌面配置
首先打开树莓派的vnc  可以使用  提供的两种方法打开 


 1. 开始
 2. 首选项
 3. Respberry Pi configuration
 4. Interface
 5. 勾选spi开启即可
 当然需要开启其他设置也可以来这里
 
•	也有其他方法：sudo raspi-config;
•	选择 "Interfacing Options";
•	选择 "SPI";
•	选择 “Yes”
•	选择 “Yes”
•	选择 “OK”
•	选择 “Finish”

```c
	sudo apt-get install tightvncserver
	sudo apt-get install xrdp
	sudo service xrdp restart
	sudo ufw allow 3389
	sudo service ufw restart
	sudo service xrdp restart

```
	接下来重启即可使用
#  树莓派中文输入法的安装
**强调！！！中文输入法尽量只安装一种，否则就会引文冲突而不能使用！！！**

```c
sudo apt-get install ibus ibus-pinyin
```
然后重启
#  最后一个就是安装语音模块驱动
树莓派软件源切换：

```c
  pi@raspberrypi ~ $ sudo nano /etc/apt/sources.list
```

用#注释掉原文件内容，用以下内容取代：

```c
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ stretch main non-free contrib
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ stretch main non-free contrib

```

```c

sudo apt-get update
sudo apt-get upgrade
git clone https://github.com/respeaker/seeed-voicecard.git
cd seeed-voicecard #下载声卡驱动

sudo ./install.sh #安装声卡驱动    此处可能比较慢，也可能安装失败，切换网络重新试试
reboot  #重启

```
检查声卡名称是否与源代码seeed-voicecard相匹配.

```c
Cd seeed-voicecard  #切换到文件目录
pi@raspberrypi:~/seeed-voicecard $ arecord -L
null
    Discard all samples (playback) or generate zero samples (capture)
playback
capture
dmixed
array
ac108
default:CARD=seeed4micvoicec
    seeed-4mic-voicecard,
    Default Audio Device
sysdefault:CARD=seeed4micvoicec
    seeed-4mic-voicecard,
    Default Audio Device
dmix:CARD=seeed4micvoicec,DEV=0
    seeed-4mic-voicecard,
    Direct sample mixing device
dsnoop:CARD=seeed4micvoicec,DEV=0
    seeed-4mic-voicecard,
    Direct sample snooping device
hw:CARD=seeed4micvoicec,DEV=0
    seeed-4mic-voicecard,
    Direct hardware device without any conversions
plughw:CARD=seeed4micvoicec,DEV=0
    seeed-4mic-voicecard,
    Hardware device with all software conversions
```

如果和上面的一样说明驱动安装成功。

```c
$ sudo apt update
$ sudo apt install audacity
$ audacity                      // 运行 audacity

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191107195633570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU0NDU4OA==,size_16,color_FFFFFF,t_70)运行声卡检！！！！下面安装使用模块的功能时需要重新将源切换到树莓派的官方源！！！
  

```c
pi@raspberrypi ~ $ sudo nano /etc/apt/sources.list
```

把修改过的用#注释掉，打开之前注释过的内容
测软件，测试录音，和是否有相应的麦克风数量。
模块的led 需要开启硬件spi

推荐点击左下角开始 首选项Respberry Pi configurationInterface勾选spi开启即可，

当然需要开启其他设置也可以来这里
现在就可以运行led 示例：

```c
pi@raspberrypi:~ $ cd /home/pi
pi@raspberrypi:~ $ git clone https://github.com/respeaker/4mics_hat.git
pi@raspberrypi:~ $ cd /home/pi/4mics_hat
pi@raspberrypi:~ $ sudo apt install python-virtualenv          # 安装 python 虚拟环境
pi@raspberrypi:~ $ virtualenv --system-site-packages ~/env     # 创建 python 虚拟环境
pi@raspberrypi:~ $ source ~/env/bin/activate                   # 激活 python 虚拟环境
(env) pi@raspberrypi:~ $ pip install spidev gpiozero           # 安装 spidev 和 gpiozero
```
•	在虚拟环境下运行 python pixels.py, 你可以看到LED像Google Assistant灯光一样闪烁。

```c
•	Alexa SDK 和 DuerOs SDK
•	pi@raspberrypi:~ $ source ~/env/bin/activate                    # 激活Python虚拟环境, 如果已经激活，调到下一步。
•	(env) pi@raspberrypi:~ $ cd ~/4mics_hat
•	(env) pi@raspberrypi:~/4mics_hat $ sudo apt install libatlas-base-dev     # 安装 snowboy dependencies
•	(env) pi@raspberrypi:~/4mics_hat $ sudo apt install python-pyaudio        #安装pyaudio音频处理包
•	(env) pi@raspberrypi:~/4mics_hat $ pip install ./snowboy*.whl             # 安装 snowboy for KWS
•	(env) pi@raspberrypi:~/4mics_hat $ pip install ./webrtc*.whl              # 安装 webrtc for DoA
•	(env) pi@raspberrypi:~ $ cd ~/
•	(env) pi@raspberrypi:~ $ git clone https://github.com/voice-engine/voice-engine #write by seeed
•	(env) pi@raspberrypi:~ $ cd voice-engine/
•	(env) pi@raspberrypi:~ $ python setup.py install
•	(env) pi@raspberrypi:~ $ cd examples
```
在虚拟环境下运行 python kws_doa.py。请用 snowboy 来唤醒，我们就可以看到方位的信息。

```c
pi@raspberrypi:~ $ source ~/env/bin/activate                    # activate the virtual, if we have already activated, skip this step
(env) pi@raspberrypi:~ $ cd ~/
(env) pi@raspberrypi:~ $ git clone https://github.com/respeaker/avs
(env) pi@raspberrypi:~ $ cd avs                                 # install Requirements
(env) pi@raspberrypi:~ $ python setup.py install                               
(env) pi@raspberrypi:~/avs $ sudo apt install gstreamer1.0
(env) pi@raspberrypi:~/avs $ sudo apt install gstreamer1.0-plugins-good
(env) pi@raspberrypi:~/avs $ sudo apt install gstreamer1.0-plugins-ugly
(env) pi@raspberrypi:~/avs $ sudo apt install python-gi gir1.2-gstreamer-1.0
(env) pi@raspberrypi:~/avs $ pip install tornado
```
step 2. 取得授权
在终端运行 alexa-auth ，然后登陆获取alexa的授权， 或者运行 dueros-auth 获取百度的授权。 授权的文件保存在/home/pi/.avs.json。
现在请在虚拟环境下运行 python ns_kws_doa_alexa.py , 我们会在终端看到很多 debug 的消息. 当我们看到 status code: 204 的时候, 请说 snowboy 来唤醒 respeaker。接下来 respeaker 上的 led 灯亮起来, 我们可以跟他对话, 比如问，"谁是最帅的?" 或者 "播放刘德华的男人哭吧哭吧不是罪"。小伙伴，尽情的 High 起来吧。
树莓派的语音模块配置到这里就结束了
