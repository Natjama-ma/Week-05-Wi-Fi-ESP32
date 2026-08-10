# ใบงานที่ 5.4: กระบวนการแลกเปลี่ยนคีย์ความปลอดภัยและการจัดสรรหมายเลข IP Address (4-Way Handshake & IP Assignment Phase)

---

### 6.1 ตารางสรุปเปรียบเทียบผลการทดลองใน Handshake & IP Phase

| ข้อการทดลอง | สถานการณ์ทดสอบ | Event `WIFI_EVENT_STA_CONNECTED` (เกิด/ไม่เกิด) | Event `IP_EVENT_STA_GOT_IP` (เกิด/ไม่เกิด) | ผลการทดลอง | Disconnect Reason Code (ถ้ามี) |
| :---: | :--- | :---: | :---: | :---: | :--- |
| **5.4.1** | Password ถูกต้อง |เกิด |เกิด | Passed|N/A (0) |
| **5.4.2** | Password ผิด |เกิด (หลังสั่ง Connect ใหม่) |ไม่เกิด |Failed |WIFI_REASON_AUTH_FAIL |

### 6.2 บันทึกข้อมูล IP Network จาก Event `IP_EVENT_STA_GOT_IP` (ข้อ 5.4.1)

| พารามิเตอร์ Network Layer | ค่าที่จัดสรรได้จริงจาก DHCP Server |
| :--- | :--- |
| **IP Address** | 172.20.10.3 |
| **Subnet Mask** |255.255.255.240 |
| **Default Gateway** |172.20.10.1 |

---

## 7. คำถามท้ายการทดลอง (Post-Lab Questions)

1. เหตุใดกระบวนการ **4-Way Handshake** จึงพิสูจน์ทราบรหัสผ่าน Wi-Fi ได้โดยไม่ต้องส่งรหัสผ่าน (Passphrase) ลอยไปในอากาศเลยแม้แต่แพ็กเกจเดียว?
~~~
เพราะทั้งสองฝั่ง (Router และ ESP32) รู้รหัสผ่านล่วงหน้าอยู่แล้ว และนำรหัสผ่านไปคำนวณสร้าง
เป็นคีย์ตั้งต้นไว้ฝั่งตนเอง ใน 4-Way Handshake จะส่งเพียงแค่ ค่าสุ่ม (Nonce) และค่าตรวจสอบ
ความถูกต้อง (MIC - Message Integrity Code) เพื่อพิสูจน์ว่าต่างฝ่ายต่างคำนวณคีย์จาก
รหัสผ่านเดียวกันได้ถูกต้อง โดยไม่ต้องส่งตัวรหัสผ่านจริงออกไปเลย
~~~
2. อธิบายบทบาทและที่มาของคีย์ **PMK (Pairwise Master Key)** และ **PTK (Pairwise Transient Key)** ว่ามีความสัมพันธ์กันอย่างไรในการเข้ารหัสเฟรมข้อมูล?
~~~
PMK (Pairwise Master Key): ได้มาจากการคำนวณรหัสผ่าน Wi-Fi (Passphrase) ร่วมกับชื่อเครือข่าย (SSID) เป็นคีย์แม่ที่ถูกสร้างไว้ล่วงหน้า

PTK (Pairwise Transient Key): นำ PMK มาผสมรวมกับค่าสุ่ม (ANonce, SNonce) และ MAC Address ของทั้งสองฝั่งในขั้นตอน 4-Way Handshake
เป็นคีย์ใช้งานจริงที่เปลี่ยนทุกครั้งในการเชื่อมต่อ ใช้ในการเข้ารหัส-ถอดรหัสเฟรมข้อมูล (Data Frames) ระหว่าง ESP32 กับ Router
~~~
3. เหตุใดเมื่อเราพิมพ์ Password ผิด (ข้อ 5.4.2) ESP32 จึงยังคงได้รับ Event **`WIFI_EVENT_STA_CONNECTED`** ก่อนที่จะเกิด Event **`WIFI_EVENT_STA_DISCONNECTED`** ตามมาในภายหลัง?
~~~
เพราะกระบวนการเกิดเรียงลำดับเฟสกัน
1. เฟส Auth & Assoc (Phase 2 & 3): เป็นการเชื่อมต่อทางกายภาพ/สายสัญญาณไร้สายสำเร็จ ระบบจึงส่ง Event WIFI_EVENT_STA_CONNECTED ออกมาก่อน
2. เฟส 4-Way Handshake (Phase 4): เพิ่งเริ่มเช็กรหัสผ่าน เมื่อรหัสผ่านผิด Handshake ล้มเหลว ระบบจึงสั่งตัดการเชื่อมต่อ และส่ง Event WIFI_EVENT_STA_DISCONNECTED ตามมาทีหลัง
~~~
4. หากเครือข่าย Wi-Fi ไม่มี DHCP Server (ไม่มีการแจก IP อัตโนมัติ) ผลการทดลองในข้อ 5.4.1 จะหยุดอยู่ที่ขั้นตอนใด และจะไม่เกิด Event ใดขึ้น?
~~~
หยุดอยู่ที่ขั้นตอน: DHCP Request / IP Acquisition Phase (ขั้นตอนขอรับหมายเลข IP Address)และจะไม่เกิด Event: IP_EVENT_STA_GOT_IP
(ทำให้ ESP32 ไม่ได้รับหมายเลข IP และไม่สามารถส่งข้อมูลออกอินเทอร์เน็ตได้ แม้ว่าจะต่อ Wi-Fi ติดแล้วก็ตาม)
~~~
