# 模拟输出


#### Description 介绍 {#description}

Writes an analog value ([PWM wave](http://arduino.cc/en/Tutorial/PWM)) to a pin. Can be used to light a LED at varying brightnesses or drive a motor at various speeds. After a call to **analogWrite()**, the pin will generate a steady square wave of the specified duty cycle until the next call to **analogWrite()** (or a call to **digitalRead()** or **digitalWrite()** on the same pin). The frequency of the PWM signal is approximately 490 Hz.

将模拟值（PWM波）输出到管脚。可用于在不同的光线亮度调节发光二极管亮度或以不同的速度驱动马达。调用analogWrite()后，该引脚将产生一个指定占空比的稳定方波，直到下一次调用analogWrite()（或在同一引脚调用digitalRead()或digitalWrite()）。 PWM的信号频率约为490赫兹。

On most Arduino boards (those with the ATmega168 or ATmega328), this function works on pins 3, 5, 6, 9, 10, and 11\. On the Arduino Mega, it works on pins 2 through 13\. Older Arduino boards with an ATmega8 only support analogWrite() on pins 9, 10, and 11\. You do not need to call pinMode() to set the pin as an output before calling analogWrite().

在大多数Arduino板（带有ATmega168或ATmega328），这个函数工作在引脚3，5，6，9，10和11。在ArduinoMega，它适用于2-13号引脚。老的带有ATmega8的Arduino板只支持9，10，11引脚上使用。你并不需要在调用analogWrite()之前为设置输入引脚而调用pinMode()。

The analogWrite function has nothing whatsoever to do with the analog pins or the analogRead function.

这个analogWrite方法与模拟引脚或者analogRead方法毫不相干

#### Syntax 语法 {#syntax}

analogWrite(pin, value)

#### Parameters 参数 {#parameters}

pin: the pin to write to.

pin：输出的引脚号

value: the duty cycle: between 0 (always off) and 255 (always on).

value：占用空：从0（常关）到255（常开）

#### Returns 返回值 {#returns}

nothing

#### Notes and Known Issues 备注和已知问题 {#notes-and-known-issues}

The PWM outputs generated on pins 5 and 6 will have higher-than-expected duty cycles. This is because of interactions with the millis() and delay() functions, which share the same internal timer used to generate those PWM outputs. This will be noticed mostly on low duty-cycle settings (e.g 0 - 10) and may result in a value of 0 not fully turning off the output on pins 5 and 6.

引脚5和6的PWM输出将产生高于预期的占空比。这是因为millis()和delay()函数，它们共享同一个内部定时器用于产生PWM输出所产生的相互作用。这提醒我们引脚5和6在多数低占空比的设置（如0- 10）的情况下0数值的结果并没有完全关闭。

#### Example 例子 {#example}

Sets the output to the LED proportional to the value read from the potentiometer.

int ledPin = 9; // LED connected to digital pin 9

int analogPin = 3; // potentiometer connected to analog pin 3

int val = 0; // variable to store the read value

void setup()

{

pinMode(ledPin, OUTPUT); // sets the pin as output

}

void loop()

{

val = analogRead(analogPin); // read the input pin

analogWrite(ledPin, val / 4); // analogRead values go from 0 to 1023, analogWrite values from 0 to 255