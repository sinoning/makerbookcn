# 蓝牙小车

![](http://pic2.haibucuo.com/img/2016/04/LOGO3-2.jpg)
购买地址：淘宝店 还不错商城 （送100下载金币）
## 概述

安卓手机通过APP客户端发送指令给蓝牙接收模块，蓝牙模块把命令发送给Arduino UNO,arduino经过事先变好的程序运算，发出指令给L298N电机驱动模块，电机驱动模块驱动电机，实现小车的运动。


## 材料

1. arduino UNO 开发板
2. L298N电机驱动板
3. hc-06蓝牙模块
4. 4电池和电池盒
5. 小车底盘或者坦克底盘
6. 导线螺丝若干

## 线路连接
[电路板安装视频教程](http://v.youku.com/v_show/id_XMTU1MTIwOTIzNg==.html)
![](http://pic2.haibucuo.com/img/2016/04/QQ%E5%9B%BE%E7%89%8720160428094310_%E5%89%AF%E6%9C%AC.jpg)
 **蓝牙链接**
 蓝牙上只需要接四条线就行了
 * RX-TX
 * TX-RX
 * VCC-3.3V
 * GND-GND


**L298N接线方法**
* IN1、IN2、IN3、IN4分别连接arduino的12、11、10、9接口
* 5V+接arduino的5V+
* GND接GND
* L298N上12V+接L298N上5v+
##步骤
1. 组装底盘（[三轮底盘安装视频](http://v.youku.com/v_show/id_XMTU0OTQ5NTIzMg==.html?from=y1.7-1.2)）
2. 调试电路板。先将电路板在底盘下面组装测试。
3. 测试成功以后，安装到底盘上面调试，马达正负极。手机连接蓝牙，发送f前进，b后退，l向左转，r向右转，来调试马达正负极。（注释：f，forward前进的意思；b，back后退的意思；l，left向左的意思；r，right向右的意思 ）[电路板安装视频](http://v.youku.com/v_show/id_XMTU1MTIwOTIzNg==.html)
4. 设置手机客户端，自定义按钮，便于操作。


### 手机app
[下载地址](http://www.chuang-ke.com/a/downloads/shoujiruanjian/2015/1022/155.html)（需要金币）
[安卓手机客户端操作演示](http://v.youku.com/v_show/id_XMTU1MTA1MjU5Ng==.html)

只能用于安卓手机
这个软件有几种模式，我们用到的就是2中模式
* 第一，命令模式。 连接蓝牙以后，向小车发送英文字母命令
* 第二，键盘模式，自定义每个按钮的意思和所发送的命令文本

操作方法
F 前进  B后退 L向左转 R向右转
输入f\b\l\r时，无论前往、后退、左转、右转，电机都是先停一下，再转，这样电机都流畅。


###室外演示
[室外效果简单演示](http://v.youku.com/v_show/id_XMTU1MTA3NzI0NA==.html)

## 代码
[代码下载](http://www.chuang-ke.com/a/downloads/Arduino/2015/1025/167.html)（需要金币）

![](http://pic2.haibucuo.com/img/2016/04/QQ图片20160428202144.jpg)



### 常见问题

* 发送前进命令，一个轮子前进，一个轮子后退。  

调换电机的正负极即可，直流电机，更换正负极即改变运动方向。
* 车轮走线不够直

任何马达都不可能转速完全一样，因此，走线轻微便宜问题不大。如果想彻底客服这个问题，就需要在马达左右安装测速码盘，时刻监控两边的速度，再通过程序控制调整两边PMW，使两边车速一样。这将是另外一个课题。




---


## 拓展练习


### 蓝牙模块测试实验
请移步http://bbs.haibucuo.com/forum.php?mod=viewthread&tid=63&highlight=%C0%B6%D1%C0
###烧录自己的程序
[程序烧录](http://www.makerbook.cn/arduinoban_ben.html)
###添加库文件
[库文件添加](http://www.makerbook.cn/arduinoku_wen_jian_zeng_jia.html)




