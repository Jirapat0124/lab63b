# การทดลองที่7 : การประยุกต์การใช้โปรแกรม

## วัตถุประสงค์
* เพื่อศึกษาวิธีการประยุกต์ใช้โปรแกรมให้มีความซับซ้อนมากขึ้น
* เพื่อให้เข้าใจการทำงานโดยรวมของโปรแกรมที่รันลงไปใน ไมโครคอนโทรเลอร์ (ESP-01)


## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์ (ESP-01)
2. Adapter
3. USB to Serial
4. คอมพิวเตอร์
5. หลอดไฟ LED
6. censor รับแสง
7. สวิทซ์ ON-OFF


## ศึกษาข้อมูลเบื้องต้น
[04 run example 4](https://www.youtube.com/watch?v=nFqoZT26U5k&t=88s)


## วิธีการทำการทดลอง
1. เชื่อมต่อ Adapter และ USB to serial เข้าด้วยกัน
2. ต่อไมโครคอนโทรลเลอร์หเข้ากับซีเรียลพอร์ทเปิด 
3. ต่อcensorรับแสงเข้าที่port0 และเชื่อมกับสายสีแดง5V
4. ต่อสวิทซ์ON-OFFเข้ากับ port1
5. command prompt รันโปรแกรมตัวอย่าง
```c
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, INPUT);
	pinMode(1, INPUT);     //เชื่อมกับสวิทซ์
	pinMode(2, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
	int x = digitalRead(1)
	if(x==0) {
		Serial.printf("======The program is ready ======")
		Serial.printf("======= read %d\n", val);
		if(val==1) {
			digitalWrite(2, LOW);
		} else {
			digitalWrite(2, HIGH);
		}
	} else {
		Serial.printf("======The program is not ready ======")
	}
	delay(1000);
}
	
```
6. อัพโหลดโปรแกรมลงในไมโครคอนโทรนเลอร์ โดยพิมพ์คำสั่ง pio run -t upload แล้วกด Enter ในขณะที่รับโปรแกรมใหม่เข้าไปให้กดปุ่มสีดำค้างไว้ แล้วกดปุ่มแดง 1 ครั้ง เพื่อเป็นการ reset คำสั่งเก่า
7. เมื่อทำการลงโปรแกรมเสร็จแล้ว พิมพ์คำสั่ง pio device monitor แล้วกด Enter เพื่อดูผลลัพธ์ที่ได้บนหน้าจอคอมพิวเตอร์



## การบันทึกผลการทดลอง
เมื่อ

## อภิปรายผลการทดลอง

## คำถามหลังการทดลอง
