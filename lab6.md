# การทดลองที่6 # การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

## วัตถุประสงค์
* เพื่อศึกษาการรันโปรแกรมสร้างไวไฟของไมโครคอนโทรเลอร์

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์
2. สายUSB
3. USB to serial
4. คอมพิวเตอร์

## ศึกษาข้อมูลเบื้องต้น
[06 run wiri AP](https://www.youtube.com/watch?v=T26DVHePlTs)


## วิธีการทำการทดลอง
1. เปิด command prompt
2. เปิดโปรแกรมตัวอย่างโดยพิมพ์คำสั่ง cd pattani
3. เลือกตัวอย่างโปรแกรมคำสั่ง cd 06_Wifi-AP-Web-Server
4. พิมพ์ vi src/maim.cpp เพื่อดูเนื้อหาโปรแกรม จะได้ดังนี้
```c
#include <ESP8266WiFi.h>
#include <ESP8266WebServer.h>

const char* ssid = "TUENG-ESP-WIFI";
const char* password = "choompol";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, geteway, subnet);
	delay(100);

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain",msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
	server.handleClient();
  ```
  5. ต่อUSBกับซีเรียล และต่อซีเรียลกับไมโครคอนโทรเลอร์ แล้วใช้คำสั่ง pio run -t upload เพื่ออัพโหลดโปรแกรมลงไมโครคอนโทรเลอร์โดยกดปุ่มสีดำค้างเพื่ออัพโหลด และกดปุ่มสีแดงเพื่อรีเซ็ท
  <img width="1112" alt="image" src="https://user-images.githubusercontent.com/80879598/112306722-b0132e80-8cd2-11eb-9d09-8f8cdfb768dd.png">

  6. พิมพ์คำสั่ง pio device monitor เพื่อดูผลลัพธ์
  <img width="1112" alt="image" src="https://user-images.githubusercontent.com/80879598/112306921-f072ac80-8cd2-11eb-8c29-874e6eb051a7.png">



## การบันทึกผลการทดลอง
* สามารถใช้ไมโครคอนโทรเลอร์สร้างเครือข่ายไวไฟขึ้นมาได้ ซึ่งกำหนดได้ทั้งชื่อและพาสเวิส
<img width="1112" alt="image" src="https://user-images.githubusercontent.com/80879598/112306999-01bbb900-8cd3-11eb-8e61-ad629bc0b9c0.png">


## อภิปรายผลการทดลอง
จากการรันโปแกรมลงไมโครคอนโทรเลอร์สามารถทำได้จริงซึ่งสามารถใช้งานwifiได้

## คำถามหลังการทดลอง
ประโยชน์ของwifi APคือ
* เราสามารถนำอุปกรณ์รับสัญญาณ wireless ไปใช้ตรงที่มี wifi APได้

