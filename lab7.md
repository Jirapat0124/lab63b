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
[04 run example 4](https://youtu.be/nFqoZT26U5k)



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
  	pinMode(1, INPUT);     #เพิ่มinput 1 และoutput 3
	pinMode(2, OUTPUT);
  	pinMode(3, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
  	int a = digitalRead(1);
  Serial.printf("======= read %d\n", val);
	if(val==1) and (a==1) {
		digitalWrite(2, LOW);
    		digitalWrite(3, HIGH);
	} else {
		digitalWrite(2, HIGH);
    		digitalWrite(3, LOW);
	}
  
  	for cnt in range(1,2+1);
  	Serial.printf("PATTANI :%d\n",cnt);
  	int b = cnt ;
  	int d = b * 1000;
	delay(d);
}



## การบันทึกผลการทดลอง

## อภิปรายผลการทดลอง

## คำถามหลังการทดลอง
