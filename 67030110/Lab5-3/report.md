# ใบงานที่ 5.3: การยืนยันตัวตนและการผูกสัมพันธ์ในระดับ Link Layer (Authentication & Association Phase)
---
### 6.1 ตารางสรุปเปรียบเทียบผลการทดลองในระดับ Link Layer

| ข้อการทดลอง | สถานการณ์ทดสอบ | Event ที่ได้รับ | ผลการผูกสัมพันธ์ Link Layer | ค่า Association ID (AID) ที่ได้ | Reason Code (ถ้ามี) |
| :---: | :--- | :---: | :---: | :---: | :--- |
| **5.3.1** | ร้องขอ Auth & Assoc กับ AP มีอยู่จริง | WIFI_EVENT_STA_CONNECTED|สำเร็จ (Passed)  |3 | -|
| **5.3.2** | ร้องขอ Auth & Assoc กับ AP ไม่มีอยู่จริง |WIFI_EVENT_STA_DISCONNECTED |ไม่สำเร็จ (Failed) |. |201 (WIFI_REASON_NO_AP_FOUND) |

### 6.2 บันทึกข้อมูล Link Layer จาก Event `WIFI_EVENT_STA_CONNECTED` (ข้อ 5.3.1)

| พารามิเตอร์ Link Layer | ค่าที่อ่านได้จริงจาก Forensic Log |
| :--- | :--- |
| **SSID** |แมว |
| **BSSID (MAC Address)** |D2:B9:E2:05:E2:70 |
| **Channel** |6 |
| **Auth Mode Enum** |3 (WIFI_AUTH_WPA2_PSK)|
| **Association ID (AID)** |3 |

---

## 7. คำถามท้ายการทดลอง (Post-Lab Questions)

1. **Association ID (AID)** คืออะไร มีบทบาทอย่างไรใน Phase 3 และส่งคืนมาในโครงสร้างข้อมูลตัวแปรใด?
~~~
คือ หมายเลขประจำตัวชั่วคราวที่ AP ออกให้ ESP32 ใน Phase 3 (Association) เพื่อใช้อ้างอิงตัวตนอุปกรณ์อย่างรวดเร็ว จัดลำดับการส่งรับข้อมูล และใช้จัดการโหมดประหยัดพลังงาน (Power Save)
ส่งคืนมาในโครงสร้างตัวแปร: สมาชิก aid ในโครงสร้างข้อมูล wifi_event_sta_connected_t (เมื่อเกิด Event WIFI_EVENT_STA_CONNECTED)
~~~

2. เหตุใดการเชื่อมต่อ Wi-Fi ความปลอดภัยแบบ WPA2-PSK จึงสามารถผ่าน Phase 2 (Authentication) และ Phase 3 (Association) จนเกิด Event `WIFI_EVENT_STA_CONNECTED` ได้สำเร็จ แม้ผู้ใช้จะป้อนรหัสผ่าน (Password) ผิด?
~~~
เพราะ Phase 2 (Authentication) และ Phase 3 (Association) เป็นเพียงกระบวนการ เชื่อมต่อและลงทะเบียนทางกายภาพ (Link-Layer) เท่านั้น
~~~
3. หาก Router มีการตั้งค่า **MAC Address Filtering** (อนุญาตเฉพาะ MAC ที่ลงทะเบียน) ESP32 จะล้มเหลวในเฟสใด และจะส่ง Disconnect Reason Code ใดออกมา?
~~~
เฟสที่ล้มเหลว: Phase 2 (Authentication) หรือ Phase 3 (Association)เพราะ Router ตรวจพบว่า MAC Address ไม่ได้ลงทะเบียนไว้ จึงปฏิเสธคำขอ
Reason Code: WIFI_REASON_NOT_AUTHED (Code 6), WIFI_REASON_NOT_ASSOCED (Code 7) หรือ WIFI_REASON_UNSPECIFIED (Code 1)
~~~

4. สรุปความแตกต่างสำคัญระหว่างจุดสิ้นสุดของ **Phase 3 (Link-Layer Connected)** กับจุดสิ้นสุดของ **Phase 5 (IP Address Assigned)**
~~~
สิ้นสุด Phase 3 (Link-Layer Connected / WIFI_EVENT_STA_CONNECTED)
อุปกรณ์เกาะสัญญาณไร้สายกับ Router สำเร็จยังไม่มี IP Address และยังไม่ได้ยืนยันรหัสผ่าน (ถ้าเป็น WPA2)
ส่งข้อมูลออกอินเทอร์เน็ตไม่ได้สิ้นสุด
Phase 5 (IP Address Assigned / IP_EVENT_STA_GOT_IP)
ผ่านการยืนยันรหัสผ่าน และได้รับหมายเลข IP Address จาก DHCP Server เรียบร้อยแล้ว
พร้อมใช้งานเครือข่ายเต็มรูปแบบ สามารถส่งข้อมูลไปยังเว็บเซิร์ฟเวอร์ภายนอกได้ทันที
~~~
