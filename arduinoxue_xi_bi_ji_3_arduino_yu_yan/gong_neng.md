## 功能

**数字 I/O**

*   [**pinMode**](http://arduino.cc/en/Reference/PinMode)(pin, mode)    数字IO口输入输出模式定义函数，pin表示为0～13， mode表示为INPUT或OUTPUT。
*   [**digitalWrite**](http://arduino.cc/en/Reference/DigitalWrite)(pin, value)   数字IO口输出电平定义函数，pin表示为0～13，value表示为HIGH或LOW。比如定义HIGH可以驱动LED。
*   int [**digitalRead**](http://arduino.cc/en/Reference/DigitalRead)(pin)    数字IO口读输入电平函数，pin表示为0～13，value表示为HIGH或LOW。比如可以读数字传感器。

**模拟 I/O**

*   int [**analogRead**](http://arduino.cc/en/Reference/AnalogRead)(pin)    模拟IO口读函数，pin表示为0～5（Arduino Diecimila为0～5，Arduino nano为0～7）。比如可以读模拟传感器（10位AD，0～5V表示为0～1023）。
*   [**analogWrite**](http://arduino.cc/en/Reference/AnalogWrite)(pin, value) - PWM     数字IO口PWM输出函数，Arduino数字IO口标注了PWM的IO口可使用该函数，pin表示3, 5, 6, 9, 10, 11，value表示为0～255。比如可用于电机PWM调速或音乐播放。

**扩展 I/O**

*   [**shiftOut**](http://arduino.cc/en/Reference/ShiftOut)(dataPin, clockPin, bitOrder, value)    SPI外部IO扩展函数，通常使用带SPI接口的74HC595做8个IO扩展，dataPin为数据口，clockPin为时钟口，bitOrder为数据传输方向（**MSBFIRST**高位在前，**LSBFIRST**低位在前），value表示所要传送的数据（0～255），另外还需要一个IO口做74HC595的使能控制。
*   unsigned long [**pulseIn**](http://arduino.cc/en/Reference/PulseIn)(pin, value)    脉冲长度记录函数，返回时间参数（us），pin表示为0～13，value为HIGH或LOW。比如value为HIGH，那么当pin输入为高电平时，开始计时，当pin输入为低电平时，停止计时，然后返回该时间。

**时间函数**

*   unsigned long [**millis**](http://arduino.cc/en/Reference/Millis)()   返回时间函数（单位ms），该函数是指，当程序运行就开始计时并返回记录的参数，该参数溢出大概需要50天时间。
*   [**delay**](http://arduino.cc/en/Reference/Delay)(ms)    延时函数（单位ms）。
*   [**delayMicroseconds**](http://arduino.cc/en/Reference/DelayMicroseconds)(us)    延时函数（单位us）。

**数学函数**

*   [**min**](http://arduino.cc/en/Reference/Min)(x, y) 求最小值
*   [**max**](http://arduino.cc/en/Reference/Max)(x, y) 求最大值
*   [**abs**](http://arduino.cc/en/Reference/Abs)(x)   计算绝对值
*   [**constrain**](http://arduino.cc/en/Reference/Constrain)(x, a, b) 约束函数，下限a，上限b，x必须在ab之间才能返回。
*   [**map**](http://arduino.cc/en/Reference/Map)(value, fromLow, fromHigh, toLow, toHigh)    约束函数，value必须在fromLow与toLow之间和fromHigh与toHigh之间。
*   [**pow**](http://arduino.cc/en/Reference/Pow)(base, exponent) 开方函数，base的exponent次方。
*   [**sq**](http://arduino.cc/en/Reference/Sq)(x)     平方
*   [**sqrt**](http://arduino.cc/en/Reference/Sqrt)(x)   开根号

**三角函数**

*   [**sin**](http://arduino.cc/en/Reference/Sin)(rad)
*   [**cos**](http://arduino.cc/en/Reference/Cos)(rad)
*   [**tan**](http://arduino.cc/en/Reference/Tan)(rad)

**随机数函数**

*   [**randomSeed**](http://arduino.cc/en/Reference/RandomSeed)(seed)   随机数端口定义函数，seed表示读模拟口analogRead(pin)函数 。
*   long [**random**](http://arduino.cc/en/Reference/Random)(max)   随机数函数，返回数据大于等于0，小于max。
*   long [**random**](http://arduino.cc/en/Reference/Random)(min, max)   随机数函数，返回数据大于等于min，小于max。

**外部中断函数**

*   [**attachInterrupt**](http://arduino.cc/en/Reference/AttachInterrupt)(interrupt, , mode)     外部中断只能用到数字IO口2和3，interrupt表示中断口初始0或1，表示一个功能函数，mode：**LOW**低电平中断，**CHANGE**有变化就中断，**RISING**上升沿中断，**FALLING** 下降沿中断。
*   [**detachInterrupt**](http://arduino.cc/en/Reference/DetachInterrupt)(interrupt)    中断开关，interrupt=1 开，interrupt=0 关。

**中断使能函数**

*   [**interrupts**](http://arduino.cc/en/Reference/Interrupts)() 使能中断
*   [**noInterrupts**](http://arduino.cc/en/Reference/NoInterrupts)() 禁止中断

**串口收发函数**

*   [**Serial.begin**](http://arduino.cc/en/Serial/Begin)(speed) 串口定义波特率函数，speed表示波特率，如9600，19200等。
*   int [**Serial.available**](http://arduino.cc/en/Serial/Available)() 判断缓冲器状态。
*   int [**Serial.read**](http://arduino.cc/en/Serial/Read)()   读串口并返回收到参数。
*   [**Serial.flush**](http://arduino.cc/en/Serial/Flush)()    清空缓冲器。
*   [**Serial.print**](http://arduino.cc/en/Serial/Print)(data) 串口输出数据。
*   [**Serial.println**](http://arduino.cc/en/Serial/Println)(data)   串口输出数据并带回车符。

/**********************************/

/************Arduino语言库文件*************/

### 官方库文件 {#-0}

*   [**EEPROM**](http://arduino.cc/en/Reference/EEPROM) - EEPROM读写程序库
*   [**Ethernet**](http://arduino.cc/en/Reference/Ethernet) - 以太网控制器程序库
*   [**LiquidCrystal**](http://arduino.cc/en/Reference/LiquidCrystal) - LCD控制程序库
*   [**Servo**](http://arduino.cc/en/Reference/Servo) - 舵机控制程序库
*   [**SoftwareSerial**](http://arduino.cc/en/Reference/SoftwareSerial) - 任何数字IO口模拟串口程序库
*   [**Stepper**](http://arduino.cc/en/Reference/Stepper) - 步进电机控制程序库
*   [**Wire**](http://arduino.cc/en/Reference/Wire) - TWI/I2C总线程序库
*   [**Matrix**](http://wiring.org.co/reference/libraries/Matrix/index.html) - LED矩阵控制程序库
*   [**Sprite**](http://wiring.org.co/reference/libraries/Sprite/index.html) - LED矩阵图象处理控制程序库

### 非官方库文件 {#-1}

*   [**DateTime**](http://www.arduino.cc/playground/Code/DateTime) - a library for keeping track of the current date and time in software.
*   [**Debounce**](http://www.arduino.cc/playground/Code/Debounce) - for reading noisy digital inputs (e.g. from buttons)
*   [**Firmata**](http://www.arduino.cc/playground/ComponentLib/Firmata) - for communicating with applications on the computer using a standard serial protocol.
*   [**GLCD**](http://www.arduino.cc/playground/Code/GLCDks0108) - graphics routines for LCD based on the KS0108 or equivalent chipset.
*   [**LCD**](http://www.arduino.cc/en/Tutorial/LCDLibrary) - control LCDs (using 8 data lines)
*   [**LCD 4 Bit**](http://www.arduino.cc/playground/Code/LCD4BitLibrary) - control LCDs (using 4 data lines)
*   [**LedControl**](http://www.arduino.cc/playground/Main/LedControl) - for controlling LED matrices or seven-segment displays with a MAX7221 or MAX7219\.
*   [**LedControl**](http://www.wayoda.org/arduino/ledcontrol/index.html) - an alternative to the Matrix library for driving multiple LEDs with Maxim chips.
*   [**Messenger**](http://www.arduino.cc/playground/Code/Messenger) - for processing text-based messages from the computer
*   [**Metro**](http://www.arduino.cc/playground/Code/Metro) - help you time actions at regular intervals
*   [**MsTimer2**](http://www.arduino.cc/playground/Main/MsTimer2) - uses the timer 2 interrupt to trigger an action every N milliseconds.
*   [**OneWire**](http://www.arduino.cc/playground/Learning/OneWire) - control devices (from Dallas Semiconductor) that use the One Wire protocol.
*   [**PS2Keyboard**](http://www.arduino.cc/playground/Main/PS2Keyboard) - read characters from a PS2 keyboard.
*   [**Servo**](http://www.arduino.cc/playground/ComponentLib/Servo) - provides software support for Servo motors on any pins.
*   [**Servotimer1**](http://www.arduino.cc/playground/ComponentLib/Servotimer1) - provides hardware support for Servo motors on pins 9 and 10
*   [**Simple Message System**](http://www.arduino.cc/playground/Code/SimpleMessageSystem) - send messages between Arduino and the computer
*   [**SSerial2Mobile**](http://code.google.com/p/sserial2mobile/) - send text messages or emails using a cell phone (via AT commands over software serial)
*   [**TextString**](http://arduino.cc/en/Tutorial/TextString) - handle strings
*   [**TLC5940**](http://www.arduino.cc/playground/Learning/TLC5940) - 16 channel 12 bit PWM controller.
*   [**X10**](http://arduino.cc/en/Tutorial/X10) - Sending X10 signals over AC power lines

/****************************************/