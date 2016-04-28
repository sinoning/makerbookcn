# Arduino程序烧录

##一、	所需材料：
1：一块可以正常上传Arduino程序的开发板（Nano、UNO、各种Atmega168/328的板都可以）
**arduino uno**
 ![](http://pic2.haibucuo.com/img/2016/04/1.jpg)
 **arduino Nano**
 ![](http://pic2.haibucuo.com/img/2016/04/2.jpg)
##二、	软件：
Arduino1.6.6中文版（这里使用的是这个版本，win7/64位系统，使用其它软件版本肯定也可以实现本文的功能，只是对应的菜单可能有所变化）
[Arduino下载地址](http://www.chuang-ke.com/a/downloads/Arduino/2015/1205/211.html)
##三、	步骤：
1、	连接可以正常上传程序的开发板，在菜单“工具”中选择对应的开发板类型和端口。一般自动识别

2、	在菜单“文件”中选择“示例”->“01.Basics>Blink”。
![](http://pic2.haibucuo.com/img/2016/04/QQ截图20160428190653.jpg)

 
3、先`验证`一下，就是那个√那个图标，验证通过了，电机`上传`，当下面显示上传成功，就完成了烧录。

**如果是自己的程序，可以复制，粘贴到上面的空白处，再验证，然后上传即可。**

常见问题：
1. arduino 代码验证失败


  没有安装必要的驱动库

2.无法烧录Arduino代码


驱动安装不正确，用驱动精灵检测并修复即可


