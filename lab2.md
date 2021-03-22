# การทดลองที่2:การเขียนโปรแกรมค้นหาไวไฟ

## วัตถุประสงค์
* เพื่อค้นหาไวไฟโดยใช้ ไมโครคอนโทรเลอร์

## อุปกรณ์ที่ใช้
1. สาย USB
2. ซีเรียล
3. ไมโครคอนโทรเลอร์(ESP-01)
4. คอมพิวเตอร์

## ศึกษาข้อมูลเบื้องต้น
* [02 run example 2](https://youtu.be/yBjab0UNuB8)

## วิธีการทำการทดลอง
1. ต่อไมโครคอนโทรเลอร์เข้ากับซีเรียล เข้าสาย USB
2. เข้า command prompt เข้าไดรฟ์ D จากคำสั่ง **D:**
3. เข้าโปรแกรมตัวอย่างโดยพิมพ์คำสั่ง **cd pattani**
4. เลือกโปรแกรมคำสั่ง **cd 02_Scan-Wifi** 
5. พิมพ์ vi src/maim.cpp เพื่อrunโปรแกรม
```c
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);
	Serial.println("\n\n\n");
}

void loop()
{
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("NO NETWORK FOUND");
	} else {
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			delay(10);
		}
	}
	Serial.println("\n\n");
}
```
6. อัพโหลดโปรแกรมลงในไมโครคอนโทรนเลอร์ด้วยคำสั่ง **pio run -t upload** พร้อมทั้งกดปุ่มสีดำค้างเพื่อให้ดาวโหลด และกดปุ่ทสีแดง1ครั้งเพื่อรีเซ็ทคำสั่งเก่า
7. จากนั้นใช้คำสั่ง**pio device monitor** เพื่อดูผลลัพธ์บนคอมพิวเตอร์


## การบันทึกผลการทดลอง
เมื่อรันโปรแกรม ไมโครคอนโทรเลอร์จะรับสัญญานไวไฟแล้วนำมาแสดงผลบนหน้าต่าง
![image](https://i.imgur.com/kvlzGVI.jpg)
## อภิปรายผลการทดลอง
จากการทดลองเขียนโปรแกรมบนไมโครคอนโทรเลอร์ เมื่อเขียนโค๊ดลงไมโครคอนโทรเลอร์แล้วใช้คำสั่ง **pio device monitor** จะขึ้นหน้าจอแสดงผลไวไฟที่ตรวจจับได้
## คำถามหลังการทดลอง
