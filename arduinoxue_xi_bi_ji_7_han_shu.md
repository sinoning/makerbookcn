# arduino学习笔记7函数 {#arduino-7}

输入输出函数

Arduino 内含了一些处理输出与输入的切换功能，相信已经从书中程式范例略知一二。

pinMode(pin, mode)

将数位脚位(digital pin)指定为输入或输出。

范例 :

pinMode(7,INPUT); // 将脚位 7 设定为输入模式

digitalWrite(pin, value)

将数位脚位指定为开或关。脚位必须先透过pinMode明示为输入或输出模式digitalWrite才能生效。

范例 :

digitalWrite(8,HIGH); //将脚位 8设定输出高电位

int digitalRead(pin)

将输入脚位的值读出，当感测到脚位处于高电位时时回传HIGH，否则回传LOW。

范例 :

val = digitalRead(7); // 读出脚位 7 的值并指定给 val

int analogRead(pin)

读出类比脚位的电压并回传一个 0到1023 的数值表示相对应的0到5的电压值。

范例 :

val = analogRead(0); //读出类比脚位 0 的值并指定给 val变数

analogWrite(pin, value)

改变PWM脚位的输出电压值，脚位通常会在3、5、6、9、10与11。Value变数范围0-255，例如：输出电压2.5伏特（V），该值大约是128。

范例 :

analogWrite(9,128); // 输出电压约2.5伏特（V）

unsigned long pulseIn(pin, value)

设定读取脚位状态的持续时间，例如使用红外线、加速度感测器测得某一项数值时，在时间单位内不会改变状态。

范例 :

time = pulsein(7,HIGH); // 设定脚位7的状态在时间单位内保持为HIGH

shiftOut(dataPin, clockPin, bitOrder, value)

把资料传给用来延伸数位输出的暂存器，函式使用一个脚位表示资料、一个脚位表示时脉。bitOrder用来表示位元间移动的方式（LSBFIRST最低有效位元或是MSBFIRST最高有效位元），最后value会以byte形式输出。此函式通常使用在延伸数位的输出。

范例 :

shiftOut(dataPin, clockPin, LSBFIRST, 255);

时间函数

控制与计算晶片执行期间的时间

unsigned long millis()

回传晶片开始执行到目前的毫秒

范例:

duration = millis()-lastTime; // 表示自"lastTime"至当下的时间

delay(ms)

暂停晶片执行多少毫秒

范例:

delay(500); //暂停半秒（500毫秒）

delay Microseconds(us)

暂停晶片执行多少微秒

范例:

delayMicroseconds(1000); //暂停1豪秒

数学函式

三角函数以及基本的数学运算

min(x, y)

回传两数之间较小者

范例：

val = min(10,20); // 回传10

max(x, y)

回传两数之间较大者

范例：

val = max(10,20); // 回传20

abs(x)

回传该数的绝对值，可以将负数转正数。

范例：

val = abs(-5); // 回传5

constrain(x, a, b)

判断x变数位于a与b之间的状态。x若小于a回传a；介于a与b之间回传x本身；大于b回传b

范例：

val = constrain(analogRead(0), 0, 255); // 忽略大于255的数

map(value, fromLow, fromHigh, toLow, toHigh)

将value变数依照fromLow与fromHigh范围，对等转换至toLow与toHigh范围。时常使用于读取类比讯号，转换至程式所需要的范围值。

例如：

val = map(analogRead(0),0,1023,100, 200); // 将analog0 所读取到的讯号对等转换至100 – 200之间的数值。

double pow(base, exponent)

回传一个数(base)的指数(exponent)值。

范例：

double x = pow(y, 32); // 设定x为y的32次方

double sqrt(x)

回传double型态的取平方根值。

范例：

double a = sqrt(1138); // 回传1138平方根的近似值 33.73425674438

double sin(rad)

回传角度（radians）的三角函数sine值。

范例：

double sine = sin(2); // 近似值 0.90929737091

double cos(rad)

回传角度（radians）的三角函数cosine值。

范例：

double cosine = cos(2); //近似值-0.41614685058

double tan(rad)

回传角度（radians）的三角函数tangent值。

范例：

double tangent = tan(2); //近似值-2.18503975868

乱数函式

产生乱数

randomSeed(seed)

事实上在Arduino里的乱数是可以被预知的。所以如果需要一个真正的乱数，可以呼叫此函式重新设定产生乱数种子。你可以使用乱数当作乱数的种子，以确保数字以随机的方式出现，通常会使用类比输入当作乱数种子，藉此可以产生与环境有关的乱数（例如：无线电波、宇宙雷射线、电话和萤光灯发出的电磁波等）。

范例：

randomSeed(analogRead(5)); // 使用类比输入当作乱数种子

long random(max)

long random(min, max)

回传指定区间的乱数，型态为long。如果没有指定最小值，预设为0。

范例：

long randnum = random(0, 100); // 回传0 – 99 之间的数字

long randnum = random(11);     // 回传 0 -10之间的数字

序列通讯

你可以在第五章看见一些使用序列埠与电脑交换讯息的范例，以下是函式解释。

Serial.begin(speed)

你可以指定Arduino从电脑交换讯息的速率，通常我们使用9600 bps。当然也可以使用其他的速度，但是通常不会超过115,200 bps（每秒位元组）。

范例：

Serial.begin(9600);

Serial.print(data)

Serial.print(data, encoding)

经序列埠传送资料，提供编码方式的选项。如果没有指定，预设以一般文字传送。

范例：

Serial.print(75);       // 列印出 "75"

Serial.print(75, DEC); //列印出 "75"

Serial.print(75, HEX); // "4B" (75 的十六进位)

Serial.print(75, OCT); // "113" (75 in的八进位)

Serial.print(75, BIN); // "1001011" (75的二进位)

Serial.print(75, BYTE); // "K" (以byte进行传送，显示以ASCII编码方式)

Serial.println(data)

Serial.println(data, encoding)

与Serial.print()相同，但会在资料尾端加上换行字元（ ）。意思如同你在键盘上打了一些资料后按下Enter。

范例：

Serial.println(75);       //列印出"75 "

Serial.println(75, DEC); //列印出"75 "

Serial.println(75, HEX); // "4B "

Serial.println(75, OCT); // "113 "

Serial.println(75, BIN); // "1001011 "

Serial.println(75, BYTE); // "K "

int Serial.available()

回传有多少位元组（bytes）的资料尚未被read()函式读取，如果回传值是0代表所有序列埠上资料都已经被read()函式读取。

范例：

int count = Serial.available();

int Serial.read()

读取1byte的序列资料

范例：

int data = Serial.read();

Serial.flush()

有时候因为资料速度太快，超过程式处理资料的速度，你可以使用此函式清除缓冲区内的资料。经过此函式可以确保缓冲区(buffer)内的资料都是最新的。

范例：

Serial.flush();