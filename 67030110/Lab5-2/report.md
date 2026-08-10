# ใบงานที่ 5.2: การยืนยันตัวตน การสถาปนาการเชื่อมต่อ และการรับหมายเลข IP Address (Wi-Fi Connection & IP Assignment)
---
## 6. ตารางบันทึกผลการทดลอง (Experiment Results)

ให้นักศึกษาบันทึกผลลัพธ์จากการสังเกตใน Serial Console ลงในตารางต่อไปนี้:

### 6.1 ตารางสรุปเปรียบเทียบผลการทดลองทั้ง 3 สถานการณ์

| ข้อการทดลอง | สถานการณ์ทดสอบ | Event สุดท้ายที่ได้รับ | ผลลัพธ์ (Passed/Failed) | Reason Code (Decimal / Hex) | คำอธิบาย Reason Code |
| :---: | :--- | :---: | :---: | :---: | :--- |
| **5.2.1** | SSID และ Password ถูกต้อง |IP_EVENT_STA_GOT_IP |Passed |N/A (0) | เชื่อมต่อสำเร็จและได้รับ IP|
| **5.2.2** | ระบุ SSID ผิด (ไม่มีในระบบ) |WIFI_EVENT_STA_DISCONNECTED | Failed|8 / 0x08 |WIFI_REASON_NO_AP_FOUND |
| **5.2.3** | ระบุ SSID ถูกต้อง แต่ Password ผิด |WIFI_EVENT_STA_DISCONNECTED |Failed |2 / 0x02 |WIFI_REASON_NO_AP_FOUND |

### 6.2 บันทึกข้อมูลเครือข่ายจากการเชื่อมต่อสำเร็จ (ข้อ 5.2.1)

| พารามิเตอร์เครือข่าย | ค่าที่ได้รับจริงจาก DHCP |
| :--- | :--- |
| **SSID** |แมว |
| **BSSID (MAC Address)** |FA:85:88:3A:DA:64 |
| **Channel** |6 |
| **IP Address** |172.20.10.3 |
| **Subnet Mask** |255.255.255.240 |
| **Default Gateway** |172.20.10.1 |

---

## 7. คำถามท้ายการทดลอง (Post-Lab Questions)

1. เหตุใดการระบุ SSID ผิด (ข้อ 5.2.2) จึงส่งผลให้เกิด Disconnect Event ด้วย Reason Code `201` (`WIFI_REASON_NO_AP_FOUND`) ตั้งแต่เฟส Scan?
~~~
เพราะ ในขั้นเริ่มต้น ESP32 จะทำการสแกนหา Access Point (AP) ตามชื่อ SSID ที่ตั้งไว้
ถ้าป้อน SSID ผิด ESP32 จะไม่พบ AP ที่มีชื่อตรงกันในช่องสัญญาณ ทำให้ไม่สามารถเริ่มขั้นตอน Authenticate ได้ และแจ้ง Disconnect ทันทีด้วย WIFI_REASON_NO_AP_FOUND (Code 201)
~~~
2. เหตุใดการพิมพ์ Password ผิด (ข้อ 5.2.3) จึงผ่านเฟส Auth และ Assoc มาได้ แต่มาล้มเหลวในเฟส 4-Way Handshake (Reason Code `15` หรือ `204`)?
~~~
เฟส Auth & Assoc: เป็นการสร้างข้อตกลงและจับคู่ในระดับฮาร์ดแวร์ยังไม่มีการตรวจรหัสผ่าน
เฟส 4-Way Handshake: เป็นขั้นตอนยืนยันรหัสผ่านจริงผ่านการคำนวณค่า MIC (Message Integrity Code)
หากใส่รหัสผ่านผิด ค่า MIC จะไม่ตรงกัน ทำให้ Handshake ล้มเหลวและหลุดด้วย Reason Code 15 หรือ 204
(HANDSHAKE_TIMEOUT)
~~~
3. ลำดับการเกิด Event ระหว่าง **`WIFI_EVENT_STA_CONNECTED`** กับ **`IP_EVENT_STA_GOT_IP`** Event ใดเกิดขึ้นก่อนกัน และมีความหมายทางกายภาพของ Layer Network ต่างกันอย่างไร?
~~~
WIFI_EVENT_STA_CONNECTED เกิดก่อน IP_EVENT_STA_GOT_IP
ความหมายทาง Layer
WIFI_EVENT_STA_CONNECTED (Layer 2 - Data Link) อุปกรณ์เกาะสัญญาณไร้สายกับ Router ได้สำเร็จ
แต่ยังไม่มี IP Address (ยังส่งข้อมูลผ่านอินเทอร์เน็ตไม่ได้)
IP_EVENT_STA_GOT_IP (Layer 3 - Network) ได้รับการแจกหมายเลข IP Address จาก DHCP Server
เรียบร้อยแล้ว พร้อมส่ง/รับข้อมูลสื่อสารจริง
~~~
4. สมาชิกตัวแปร `reason` ในโครงสร้าง `wifi_event_sta_disconnected_t` มีประโยชน์อย่างไรต่อการออกแบบระบบค้นหาสาเหตุและกู้คืนการเชื่อมต่อ (Auto-Reconnection Mechanism) ในแอปพลิเคชัน IoT?
~~~
ช่วยให้ระบบตัดสินใจแก้ไขปัญหาตาม สาเหตุที่แท้จริง ได้อย่างเหมาะสม เช่น
- หากเกิดจากปัญหาชั่วคราว (เช่น สัญญาณหลุด BEACON_TIMEOUT หรือ NO_AP_FOUND ชั่วคราว): ระบบจะสั่ง พยายามเชื่อมต่อใหม่ (Retry)
- หากเกิดจากรหัสผ่านผิด (HANDSHAKE_TIMEOUT): ระบบจะ หยุด Retry แล้วเข้าสู่โหมดตั้งค่าใหม่ (SmartConfig / Provisioning) เพื่อป้องกันไม่ให้บอร์ดรันลูปพยายามต่อซ้ำๆ โดยไม่เกิดประโยชน์
~~~
