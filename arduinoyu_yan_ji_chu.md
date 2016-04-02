# Arduino语言基础

**arduino语言**

*   Arduino语言是建立在C/C++基础上的，其实也就是基础的C语言，Arduino语言只不过把AVR单片机（微控制器）相关的一些参数设置都函数化，不用我们去了解他的底层，让我们不了解AVR单片机（微控制器）的朋友也能轻松上手。

在与Arduino DIYER接触的这段时间里，发现有些朋友对Arduino语言还是比较难入手，那么这里我就简单的注释一下Arduino语言（本人也是半罐子水，有错的地方还请各位指正）。

/*************基础C语言*************/

#### 关键字：

*   [**if**](http://arduino.cc/en/Reference/If)
*   [**if...else**](http://arduino.cc/en/Reference/Else)
*   [**for**](http://arduino.cc/en/Reference/For)
*   [**switch case**](http://arduino.cc/en/Reference/SwitchCase)
*   [**while**](http://arduino.cc/en/Reference/While)
*   [**do... while**](http://arduino.cc/en/Reference/DoWhile)
*   [**break**](http://arduino.cc/en/Reference/Break)
*   [**continue**](http://arduino.cc/en/Reference/Continue)
*   [**return**](http://arduino.cc/en/Reference/Return)
*   [**goto**](http://arduino.cc/en/Reference/Goto)

#### 语法符号： {#-0}

*   [**;**](http://arduino.cc/en/Reference/SemiColon)
*   [**{}**](http://arduino.cc/en/Reference/Braces)
*   [**//**](http://arduino.cc/en/Reference/Comments)
*   [**/* */**](http://arduino.cc/en/Reference/Comments)

#### 运算符： {#-1}

*   =
*   +
*   -
*   *
*   /
*   %
*   [**==**](http://arduino.cc/en/Reference/If)
*   [**!=**](http://arduino.cc/en/Reference/If)
*   [**<**](http://arduino.cc/en/Reference/If)
*   [**>**](http://arduino.cc/en/Reference/If)
*   [**<=**](http://arduino.cc/en/Reference/If)
*   [**>=**](http://arduino.cc/en/Reference/If)
*   [**&&**](http://arduino.cc/en/Reference/Boolean)
*   [**||**](http://arduino.cc/en/Reference/Boolean)
*   [**!**](http://arduino.cc/en/Reference/Boolean)
*   [**++**](http://arduino.cc/en/Reference/Increment)
*   [**--**](http://arduino.cc/en/Reference/Increment)
*   [**+=**](http://arduino.cc/en/Reference/IncrementCompound)
*   [**-=**](http://arduino.cc/en/Reference/IncrementCompound)
*   [***=**](http://arduino.cc/en/Reference/IncrementCompound)
*   [**/=**](http://arduino.cc/en/Reference/IncrementCompound)

#### 数据类型： {#-2}

*   [**boolean**](http://arduino.cc/en/Reference/BooleanVariables) 布尔类型
*   [**char**](http://arduino.cc/en/Reference/Char)
*   [**byte**](http://arduino.cc/en/Reference/Byte) 字节类型
*   [**int**](http://arduino.cc/en/Reference/Int)
*   [**unsigned int**](http://arduino.cc/en/Reference/UnsignedInt)
*   [**long**](http://arduino.cc/en/Reference/Long)
*   [**unsigned long**](http://arduino.cc/en/Reference/UnsignedLong)
*   [**float**](http://arduino.cc/en/Reference/Float)
*   [**double**](http://arduino.cc/en/Reference/Double)
*   [**string**](http://arduino.cc/en/Reference/String)
*   [**array**](http://arduino.cc/en/Reference/Array)
*   [**void**](http://arduino.cc/en/Reference/Void)

#### 数据类型转换： {#-3}

*   [**char()**](http://arduino.cc/en/Reference/CharCast)
*   [**byte()**](http://arduino.cc/en/Reference/ByteCast)
*   [**int()**](http://arduino.cc/en/Reference/IntCast)
*   [**long()**](http://arduino.cc/en/Reference/LongCast)
*   [**float()**](http://arduino.cc/en/Reference/FloatCast)

#### 常量： {#-4}

*   [**HIGH**](http://arduino.cc/en/Reference/Constants) | [**LOW**](http://arduino.cc/en/Reference/Constants)     表示数字IO口的电平，[**HIGH**](http://arduino.cc/en/Reference/Constants) 表示高电平（1），[**LOW**](http://arduino.cc/en/Reference/Constants) 表示低电平（0）。
*   [**INPUT**](http://arduino.cc/en/Reference/Constants) | [**OUTPUT**](http://arduino.cc/en/Reference/Constants) 表示数字IO口的方向，[**INPUT**](http://arduino.cc/en/Reference/Constants) 表示输入（高阻态），[**OUTPUT**](http://arduino.cc/en/Reference/Constants)   表示输出（AVR能提供5V电压 40mA电流）。
*   [**true**](http://arduino.cc/en/Reference/Constants) | [**false**](http://arduino.cc/en/Reference/Constants)   [**true**](http://arduino.cc/en/Reference/Constants) 表示真（1），[**false**](http://arduino.cc/en/Reference/Constants)表示假（0）。

/******************************************/

       以上为基础c语言的关键字和符号，有c语言基础的都应该了解其含义，这里也不作过多的解释。


## Arduino 语言


### 结构
* void setup()   初始化变量，管脚模式，调用库函数等 
* void loop() 连续执行函数内的语句 

### 数字 I/O
* **pinMode**(pin, mode)    数字IO口输入输出模式定义函数，pin表示为0～13， mode表示为INPUT或OUTPUT。 
* 	digitalWrite(pin, value)   数字IO口输出电平定义函数，pin表示为0～13，value表示为HIGH或LOW。比如定义HIGH可以驱动LED
* int digitalRead(pin)    数字IO口读输入电平函数，pin表示为0～13，value表示为HIGH或LOW。比如可以读数字传感器。

### 模拟 I/O
•	int analogRead(pin)    模拟IO口读函数，pin表示为0～5（Arduino Diecimila为0～5，Arduino nano为0～7）。比如可以读模拟传感器（10位AD，0～5V表示为0～1023）。 

•	analogWrite(pin, value) - PWM     数字IO口PWM输出函数，Arduino数字IO口标注了PWM的IO口可使用该函数，pin表示3, 5, 6, 9, 10, 11，value表示为0～255。比如可用于电机PWM调速或音乐播放。

### 扩展 I/O
•	shiftOut(dataPin, clockPin, bitOrder, value)    SPI外部IO扩展函数，通常使用带SPI接口的74HC595做8个IO扩展，dataPin为数据口，clockPin为时钟口，bitOrder为数据传输方向（MSBFIRST高位在前，LSBFIRST低位在前），value表示所要传送的数据（0～255），另外还需要一个IO口做74HC595的使能控制。 

•	unsigned long pulseIn(pin, value)    脉冲长度记录函数，返回时间参数（us），pin表示为0～13，value为HIGH或LOW。比如value为HIGH，那么当pin输入为高电平时，开始计时，当pin输入为低电平时，停止计时，然后返回该时间。

### 时间函数


•	unsigned long millis()   返回时间函数（单位ms），该函数是指，当程序运行就开始计时并返回记录的参数，该参数溢出大概需要50天时间。 

•	delay(ms)    延时函数（单位ms）。 

•	delayMicroseconds(us)    延时函数（单位us）。 
数学函数

•	min(x, y) 求最小值 

•	max(x, y) 求最大值 

•	abs(x)   计算绝对值 

•	constrain(x, a, b) 约束函数，下限a，上限b，x必须在ab之间才能返回。 

•	map(value, fromLow, fromHigh, toLow, toHigh)    约束函数，value必须在fromLow与toLow之间和fromHigh与toHigh之间。 

•	pow(base, exponent) 开方函数，base的exponent次方。

•	sq(x)     平方 

•	sqrt(x)   开根号 


### 三角函数


•	sin(rad) 
•	cos(rad) 
•	tan(rad) 

### 随机数函数


•	randomSeed(seed)   随机数端口定义函数，seed表示读模拟口analogRead(pin)函数 。 

•	long random(max)   随机数函数，返回数据大于等于0，小于max。 

•	long random(min, max)   随机数函数，返回数据大于等于min，小于max。 


### 外部中断函数


•	attachInterrupt(interrupt, , mode)     外部中断只能用到数字IO口2和3，interrupt表示中断口初始0或1，表示一个功能函数，mode：LOW低电平中断，CHANGE有变化就中断，RISING上升沿中断，FALLING 下降沿中断。 

•	detachInterrupt(interrupt)    中断开关，interrupt=1 开，interrupt=0 关。 
中断使能函数

•	interrupts() 使能中断 

•	noInterrupts() 禁止中断 

### 串口收发函数


•	Serial.begin(speed) 串口定义波特率函数，speed表示波特率，如9600，19200等。 
•	int Serial.available() 判断缓冲器状态。 
•	int Serial.read()   读串口并返回收到参数。 
•	Serial.flush()    清空缓冲器。 
•	Serial.print(data) 串口输出数据。 
•	Serial.println(data)   串口输出数据并带回车符。 
/**********************************/
/************Arduino语言库文件*************/

### 官方库文件


•	EEPROM - EEPROM读写程序库 
•	Ethernet - 以太网控制器程序库 
•	LiquidCrystal - LCD控制程序库 
•	Servo - 舵机控制程序库 
•	SoftwareSerial - 任何数字IO口模拟串口程序库 
•	Stepper - 步进电机控制程序库 
•	Wire - TWI/I2C总线程序库 
•	Matrix - LED矩阵控制程序库 
•	Sprite - LED矩阵图象处理控制程序库 

### 非官方库文件


•	DateTime - a library for keeping track of the current date and time in software. 
•	Debounce - for reading noisy digital inputs (e.g. from buttons) 
•	Firmata - for communicating with applications on the computer using a standard serial protocol. 
•	GLCD - graphics routines for LCD based on the KS0108 or equivalent chipset. 
•	LCD - control LCDs (using 8 data lines) 
•	LCD 4 Bit - control LCDs (using 4 data lines) 
•	LedControl - for controlling LED matrices or seven-segment displays with a MAX7221 or MAX7219. 
•	LedControl - an alternative to the Matrix library for driving multiple LEDs with Maxim chips. 
•	Messenger - for processing text-based messages from the computer 
•	Metro - help you time actions at regular intervals 
•	MsTimer2 - uses the timer 2 interrupt to trigger an action every N milliseconds. 
•	OneWire - control devices (from Dallas Semiconductor) that use the One Wire protocol. 
•	PS2Keyboard - read characters from a PS2 keyboard. 
•	Servo - provides software support for Servo motors on any pins. 
•	Servotimer1 - provides hardware support for Servo motors on pins 9 and 10 
•	Simple Message System - send messages between Arduino and the computer 
•	SSerial2Mobile - send text messages or emails using a cell phone (via AT commands over software serial) 
•	TextString - handle strings 
•	TLC5940 - 16 channel 12 bit PWM controller. 
•	X10 - Sending X10 signals over AC power lines 
/****************************************/
 
### 数据类型


有多种类型的变量，如下所述
boolean   布尔
char        字符
byte        字节
int          整数
unsigned int 无符号整数
long        长整数
unsigned long 无符号长整数
float        浮点
double     双字节浮点
string      字符串
array       数组


### Arduuino复合运算符


+= , -= , *= , /= 
Description描述
Perform a mathematical operation on a variable with another constant or variable. The += (et al) operators are just a convenient shorthand for the expanded syntax, listed below. 
对一个变量和另一个参数或变量完成一个数学运算。+=（以及其他）可以缩短语法长度。
Syntax语法
x += y;   // equivalent to the expression x = x + y;          // 等价于 x = x + y;
x -= y;   // equivalent to the expression x = x - y;           // 等价于 x = x - y;
x *= y;   // equivalent to the expression x = x * y;           // 等价于 x = x * y;
x /= y;   // equivalent to the expression x = x / y;           // 等价于 x = x / y;
Parameters参数
x: any variable type 
x：任何变量类型
y: any variable type or constant 
y：任何变量类型或常数
Examples范例
x = 2;
x += 4;      // x now contains 6             // x现在为6
x -= 3;      // x now contains 3             // x现在为3
x *= 10;     // x now contains 30             // x现在为30
x /= 2;      // x now contains 15             // x现在为15


### Syntax语法


x++; // increment x by one and returns the old value of x
      // 将x的值加1并返回原来的x的值。    ++x; // increment x by one and returns the new value of x      // 将x的值加1并返回现在的x的值。   
x-- ;   // decrement x by one and returns the old value of x       // 将x的值减1并返回原来的x的值。   
--x ;   // decrement x by one and returns the new value of x        // 将x的值减1并返回现在的x的值。
Parameters参数
x: an integer or long (possibly unsigned) 
x：一个整数或长整数（可以无符号）
Returns返回
The original or newly incremented / decremented value of the variable. 
返回变量原始值或增加/消耗后的新值。
Examples范例
x = 2;
y = ++x;      // x now contains 3, y contains 3              // x现在为3，y为3
y = x--;      // x contains 2 again, y still contains 3              // x现在仍然为2，y将为3









