# การทดลองที่5 การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

## วัตถุประสงค์
* เพื่อศึกษาวิธีการใช้ไมโครคอนโทรเลอร์สร้างเว็บเซอร์เวอร์จากไวไฟ

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์
2. สายต่อUSB
3. USB to serial
4. คอมพิวเตอร์

## ศึกษาข้อมูลเบื้องต้น
[05 run wifi](https://youtu.be/VX-QNQcO-b4 "05 run wifi")

## วิธีการทำการทดลอง
1. เปิด command prompt
2. เปิดโปรแกรมตัวอย่างโดยพิมพ์คำสั่ง cd pattani
3. เลือกตัวอย่างโปรแกรมคำสั่ง cd 05_Wifi-Web-Server
4. พิมพ์ vi src/maim.cpp เพื่อดูเนื้อหาโปรแกรม จะได้ดังนี้
```c
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "HI_BMFWIFI_2.4G";   #พิมพ์ชื่อไวไฟและรหัสผ่าน
const char* password = "0819110933";

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(500);
		Serial.print(".");
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}
```
5. ต่อไมโครคอนโทรเลอร์กับUSB to Serial แล้วอัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์โดยใช้คำสั่ง pio run -t upload พร้อมทั้งกดปุ่มสีดำค้างไว้เพื่ออัพโหลด และรีเว็นโดยการกดปุ่มสีแดง
6. พิมพ์คำสั่ง pio device monitor เพื่อดูผลลัพธ์ ซึ่งจะแสดงผล ip address
7. ให้ copy ip address ไปที่บราวเซอร์ในการทดสอบ



## การบันทึกผลการทดลอง


## อภิปรายผลการทดลอง


## คำถามหลังการทดลอง



