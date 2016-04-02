# arduino学习笔记13 Arduino的模拟输入 {#arduino-13-arduino}

#### Description 介绍 {#description}

Reads the value from the specified analog pin. The Arduino board contains a 6 channel (8 channels on the Mini and Nano, 16 on the Mega), 10-bit analog to digital converter. This means that it will map input voltages between 0 and 5 volts into integer values between 0 and 1023\. This yields a resolution between readings of: 5 volts / 1024 units or, .0049 volts (4.9 mV) per unit. The input range and resolution can be changed using [analogReference](http://arduino.cc/en/Reference/AnalogReference)().

It takes about 100 microseconds (0.0001 s) to read an analog input, so the maximum reading rate is about 10,000 times a second.

从指定的模拟引脚读取值。Arduino主板有6个通道（Mini和Nano有8个，Mega有16个），10位AD（模数）转换器。这意味着输入电压0-5伏对应0-1023的整数值。这就是说读取精度为：5伏/1024个单位，约等于每个单位0.049伏（4.9毫伏）。输入范围和进度可以通过[analogReference](http://arduino.cc/en/Reference/AnalogReference)()进行修改。

模拟输入的读取周期为100微秒（0.0001秒），所以最大读取速度为每秒10,000次。

#### Syntax 语法 {#syntax}

analogRead(pin)

#### Parameters 参数 {#parameters}

pin: the number of the analog input pin to read from (0 to 5 on most boards, 0 to 7 on the Mini and Nano, 0 to 15 on the Mega)

pin：读取的模拟输入引脚号（大多数主板是0-5，Mini和Nano是0-7，Mega是0-15）

#### Returns 返回值 {#returns}

int (0 to 1023)

整数型  int（0到1023）

#### Note 备注 {#note}

If the analog input pin is not connected to anything, the value returned by analogRead() will fluctuate based on a number of factors (e.g. the values of the other analog inputs, how close your hand is to the board, etc.).

如果模拟输入引脚没有连接到任何地方，analogRead()的返回值也会因为某些因素而波动（如其他模拟输入，你的手与主板靠的太近）

#### Example 例子 {#example}

int analogPin = 3; // potentiometer wiper (middle terminal) connected to analog pin 3

// outside leads to ground and +5V

int val = 0; // variable to store the value read

void setup()

{

Serial.begin(9600); // setup serial

}

void loop()

{

val = analogRead(analogPin); // read the input pin

Serial.println(val); // debug value

}