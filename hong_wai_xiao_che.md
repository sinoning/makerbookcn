# 红外小车

### 概述
  通过红外线采集实验，获取红外遥控的对应按钮的红外编码，再将对应红外编码在Arduino程序中定义相应的动作，使小车移动。当按下遥控器上对应的按钮，遥控器就会发送对应的编码，通过红外线接收管接收到信号，将对应的代码传递给Arduino，Arduino将向执行对应的动作


### 所用到的知识点
1. Arduino通过L298N电机模块驱动马达
2. 红外线接收
3. 红外线采集

### 线路连接
1.	电源插入Arduino电源圆形插口
2.	L298n in1-in4 接arduino2-5
3.	L298N GND接线柱连 Arduino GND,L298N 9+接线柱接Arduino 5+
4.	L298N两边各两个接线柱各接一个马达
5.	红外接收头黄色线接Arduino GND，红色线接Arduino 3.3+，蓝色线接Arduino AO


### 源代码

`#include <IRremote.h>  // 使用
//******红外遥控智能车程序*******
#include <IRremote.h>
int RECV_PIN = A0;
int pinLB=2;//定义I1接口
int pinLF=3;//定义I2接口
int pinRB=4;//定义I3接口
int pinRF=5;//定义I4接口
//******红外控制部分********
long advence = 0x00FF629D;
long back = 0x00FF02FD;
long stop = 0x00FFA25D;
long left = 0x00FF22DD;
long right = 0x00FFC23D;

IRrecv irrecv(RECV_PIN);
decode_results results;
void dump(decode_results *results) {
  int count = results->rawlen;
  if (results->decode_type == UNKNOWN) 
    {
     Serial.println("Could not decode message");
    } 
  else 
   {
    if (results->decode_type == NEC) 
      {
       Serial.print("Decoded NEC: ");
      } 
    else if (results->decode_type == SONY) 
      {
       Serial.print("Decoded SONY: ");
      } 
    else if (results->decode_type == RC5) 
      {
       Serial.print("Decoded RC5: ");
      } 
    else if (results->decode_type == RC6) 
      {
       Serial.print("Decoded RC6: ");
      }
     Serial.print(results->value, HEX);
     Serial.print(" (");
     Serial.print(results->bits, DEC);
     Serial.println(" bits)");
   }
     Serial.print("Raw (");
     Serial.print(count, DEC);
     Serial.print("): ");

  for (int i = 0; i < count; i++) 
     {
      if ((i % 2) == 1) {
      Serial.print(results->rawbuf[i]*USECPERTICK, DEC);
     } 
    else  
     {
      Serial.print(-(int)results->rawbuf[i]*USECPERTICK, DEC);
     }
    Serial.print(" ");
     }
      Serial.println("");
     }

void setup()
 {
  pinMode(RECV_PIN, INPUT);   
  pinMode(pinLB,OUTPUT);
  pinMode(pinLF,OUTPUT);
  
  pinMode(pinRB,OUTPUT);
  pinMode(pinRF,OUTPUT);
 
Serial.begin(9600);
  irrecv.enableIRIn(); // Start the receiver
 }

int on = 0;
unsigned long last = millis();

void loop() 
{
  if (irrecv.decode(&results)) 
   {
    // If it's been at least 1/4 second since the last
    // IR received, toggle the relay
    if (millis() - last > 250) 
      {
       on = !on;
//       digitalWrite(8, on ? HIGH : LOW);
       digitalWrite(13, on ? HIGH : LOW);
       dump(&results);
      }
    if (results.value == advence )
    {digitalWrite(pinRB,LOW);//使直流电机（右）GO
    digitalWrite(pinRF,HIGH);
    digitalWrite(pinLB,LOW);//使直流电机（左）GO
    digitalWrite(pinLF,HIGH);}

    if (results.value == back )
   

     {digitalWrite(pinRB,HIGH);//使直流电机（右）BACK
     digitalWrite(pinRF,LOW);
      digitalWrite(pinLB,HIGH);//使直流电机（左）BACK
    digitalWrite(pinLF,LOW);}
       

    if (results.value == left )
    { digitalWrite(pinRB,LOW);//使直流电机（右）GO
     digitalWrite(pinRF,HIGH);
     digitalWrite(pinLB,HIGH);//使直流电机（左）STOP
     digitalWrite(pinLF,HIGH);}


    if (results.value == right )
    { digitalWrite(pinRB,HIGH);//使直流电机（右）STOP
     digitalWrite(pinRF,HIGH);
     digitalWrite(pinLB,LOW);//使直流电机（左）GO
     digitalWrite(pinLF,HIGH);}

    if (results.value == stop )
      {
     digitalWrite(pinRB,HIGH);//使直流电机（右）STOP
     digitalWrite(pinRF,HIGH);
      digitalWrite(pinLB,HIGH);//使直流电机（左）STOP
     digitalWrite(pinLF,HIGH);
   
   } 
          
    last = millis();      
    irrecv.resume(); // Receive the next value
  }
}`


