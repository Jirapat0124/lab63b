# การทดลองที่4 การเขียนโปรแกรมอินพุทสัญญาณดิจิทัล

## วัตถุประสงค์
* เพื่อที่จะเข้าใจก่ีเขียนโปรแกรมอินพุทสัญญาณดิจิทัล โดยใช้ไมโครคอนโทรเลอร์

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์(ESP-01)
2. สายต่อ USB
3. USB to sereal
4. adapter
5. หลอดไฟ LED
6. censor รับแสง
7. คอมพิวเตอร์

## ศึกษาข้อมูลเบื้องต้น
[04 run example 4](https://youtu.be/nFqoZT26U5k)


## วิธีการทำการทดลอง
1. นำAdapter ต่อกับ USB to Serial
2. นำไมโครคอนโทรเลอร์ต่อเข้ากับพอร์ท
3. เปิด Comand Prompt เข้าโฟลเดอร์D
4. เปิดโปรแกรมตัวอย่างโดยพิมพ์คำสั่ง **cd pattani**
5. เลือกตัวอย่างโปรแกรมคำสั่ง **cd 04_Input-Port**
6. พิมพ์ vi src/maim.cpp เพื่อดูเนื้อหาโปรแกรม จะได้ดังนี้ (พอร์ท 0 เป็นinput พอร์ท 2 เป็นoutput)
```c
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, INPUT);
	pinMode(2, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
	Serial.printf("======= read %d\n", val);
	if(val==1) {
		digitalWrite(2, LOW);
	} else {
		digitalWrite(2, HIGH);
	}
	delay(100);
}
```
7. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์โดยใช้คำสั่ง pio run -t upload พร้อมทั้งกดปุ่มสีดำค้างไว้เพื่ออัพโหลด จะขึ้นหน้าจอแบบนี้ 
<img width="776" alt="image" src="https://user-images.githubusercontent.com/80879598/111982887-1580e700-8b3c-11eb-8a8a-170b929ae8c4.png">


## การบันทึกผลการทดลอง

## อภิปรายผลการทดลอง

## คำถามหลังการทดลอง
