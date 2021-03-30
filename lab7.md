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


## ศึกษาข้อมูลเบื้องต้น
[04 run example 4](https://www.youtube.com/watch?v=nFqoZT26U5k&t=88s)


## วิธีการทำการทดลอง
1. เชื่อมต่อ Adapter และ USB to serial เข้าด้วยกัน
2. ต่อไมโครคอนโทรลเลอร์หเข้ากับซีเรียลพอร์ท
3. เปิด command prompt รันโปรแกรมตัวอย่าง
```c
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, INPUT);
	pinMode(1, INPUT);
	pinMode(2, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
	int x = digitalRead(1)
	if(x==1) {
		Serial.printf("======The program is ready ======")
		Serial.printf("======= read %d\n", val);
		if(val==1) {
			digitalWrite(2, LOW);
		} else {
			digitalWrite(2, HIGH);
		}
		}
	delay(1000);
}
	
```


## การบันทึกผลการทดลอง

## อภิปรายผลการทดลอง

## คำถามหลังการทดลอง
