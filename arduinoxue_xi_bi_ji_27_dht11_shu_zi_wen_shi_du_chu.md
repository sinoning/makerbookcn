# arduino学习笔记27 DHT11数字温湿度传感器的使用 {#arduino-27-dht11}

**概述**

DHT11 数字温湿度传感器是一款含有已校准数字信号输出的温湿度复合传感器。它应用专用的数字模块采集技术

和温湿度传感技术，确保产品具有极高的可靠性与卓越的长期稳定性。传感器包括一个电阻式感湿元件和一个NTC 测

温元件，并与一个高性能8 位单片机相连接。因此该产品具有品质卓越、超快响应、抗干扰能力强、性价比极高等优

点。每个DHT11 传感器都在极为精确的湿度校验室中进行校准。校准系数以程序的形式储存在OTP 内存中，传感器内

部在检测信号的处理过程中要调用这些校准系数。单线制串行接口，使系统集成变得简易快捷。超小的体积、极低的

功耗，信号传输距离可达20 米以上，使其成为各类应用甚至最为苛刻的应用场合的最佳选则。

DHT11 数字温湿度传感器模块为3 针PH2.0 封装。连接方便。

**性能描述**

1． 供电电压：3-5.5V

2． 供电电流：最大2.5Ma

3． 温度范围：0-50℃ 误差±2℃

4． 湿度范围：20-90%RH 误差±5%RH

5． 响应时间: 1/e(63%) 6-30s

6． 测量分辨率分别为 8bit（温度）、8bit（湿度）

7． 采样周期间隔不得低于1 秒钟

8． 模块尺寸：30x20mm

**传感器的时序**

DATA 用于微处理器与 DHT11之间的通讯和同步,采用单总线数据格式,一次通讯时间4ms左右,数据分小数部分和

整数部分,具体格式在下面说明,当前小数部分用于以后扩展,现读出为零.操作流程如下:

一次完整的数据传输为40bit,高位先出。

数据格式:

8bit湿度整数数据+8bit湿度小数数据

+8bi温度整数数据+8bit温度小数数据

+8bit校验和

数据传送正确时校验和数据等于“**8bit湿度整数数据+8bit湿度小数数据+8bi温度整数数据+8bit温度小数数据**”所得结果的末8位。

用户MCU发送一次开始信号后,DHT11从低功耗模式转换到高速模式,等待主机开始信号结束后,DHT11发送响应信号,

送出40bit的数据,并触发一次信号采集,用户可选择读取部分数据.从模式下,DHT11接收到开始信号触发一次温湿度采集,如果没有接收到主机发送开始信号,DHT11不会主动进行温湿度采集.采集数据后转换到低速模式。

**模块的使用**

将 DHT11 模块接到Arduino 传感器扩展板的模拟口0

代码如下：

#define DHT11_PIN 0 // ADC0 接到模拟口0

byte read_dht11_dat()

{

byte i = 0;

byte result=0;

for(i=0; i< 8; i++){

while(!(PINC & _BV(DHT11_PIN))); // wait for 50us

delayMicroseconds(30);

if(PINC & _BV(DHT11_PIN))

result |=(1<<(7-i));

while((PINC & _BV(DHT11_PIN))); // wait '1' finish

}

return result;

}

void setup()

{

DDRC |= _BV(DHT11_PIN);

PORTC |= _BV(DHT11_PIN);

Serial.begin(19200);

Serial.println("Ready");

}

void loop()

{

byte dht11_dat[5];

byte dht11_in;

byte i;

// start condition

// 1\. pull-down i/o pin from 18ms

PORTC &= ~_BV(DHT11_PIN);

delay(18);

PORTC |= _BV(DHT11_PIN);

delayMicroseconds(40);

DDRC &= ~_BV(DHT11_PIN);

delayMicroseconds(40);

dht11_in= PINC & _BV(DHT11_PIN);

if(dht11_in){

Serial.println("dht11 start condition 1 not met");

return;

}

delayMicroseconds(80);

dht11_in = PINC & _BV(DHT11_PIN);

if(!dht11_in){

Serial.println("dht11 start condition 2 not met");

return;

}

delayMicroseconds(80);

// now ready for data reception

for (i=0; i<5; i++)

dht11_dat[i] = read_dht11_dat();

DDRC |= _BV(DHT11_PIN);

PORTC |= _BV(DHT11_PIN);

byte dht11_check_sum = dht11_dat[0]+dht11_dat[1]+dht11_dat[2]+dht11_dat[3];

// check check_sum

if(dht11_dat[4]!= dht11_check_sum)

{

Serial.println("DHT11 checksum error");

}

Serial.print("Current humdity = ");

Serial.print(dht11_dat[0], DEC);

Serial.print(".");

Serial.print(dht11_dat[1], DEC);

Serial.print("% ");

Serial.print("temperature = ");

Serial.print(dht11_dat[2], DEC);

Serial.print(".");

Serial.print(dht11_dat[3], DEC);

Serial.println("C ");

delay(2000);

}

编译代码后下载到Arduino 中，打开串口助手即可看见实际测量的温度与湿度。