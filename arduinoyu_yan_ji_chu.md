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








