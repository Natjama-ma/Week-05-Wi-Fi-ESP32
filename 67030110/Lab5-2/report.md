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

~~~
I (29) boot: ESP-IDF v5.5.1 2nd stage bootloader
I (29) boot: compile time Aug  8 2026 13:19:54
I (29) boot: Multicore bootloader
I (31) boot: chip revision: v3.1
I (33) boot.esp32: SPI Speed      : 40MHz
I (37) boot.esp32: SPI Mode       : DIO
I (41) boot.esp32: SPI Flash Size : 2MB
I (44) boot: Enabling RNG early entropy source...
I (49) boot: Partition Table:
I (51) boot: ## Label            Usage          Type ST Offset   Length
I (58) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (64) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (71) boot:  2 factory          factory app      00 00 00010000 00100000
I (77) boot: End of partition table
I (81) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=19e38h (106040) map
I (124) esp_image: segment 1: paddr=00029e60 vaddr=3ffb0000 size=03eech ( 16108) load
I (130) esp_image: segment 2: paddr=0002dd54 vaddr=40080000 size=022c4h (  8900) load
I (134) esp_image: segment 3: paddr=00030020 vaddr=400d0020 size=861fch (549372) map
I (323) esp_image: segment 4: paddr=000b6224 vaddr=400822c4 size=15b48h ( 88904) load
I (358) esp_image: segment 5: paddr=000cbd74 vaddr=50000000 size=00020h (    32) load
I (370) boot: Loaded app from partition at offset 0x10000
I (370) boot: Disabling RNG early entropy source...
I (381) cpu_start: Multicore app
I (389) cpu_start: Pro cpu start user code
I (389) cpu_start: cpu freq: 160000000 Hz
I (389) app_init: Application information:
I (389) app_init: Project name:     wifi_connection_phase
I (394) app_init: App version:      218e85e-dirty
I (399) app_init: Compile time:     Aug  8 2026 13:19:22
I (404) app_init: ELF file SHA256:  fd6e4e72a...
I (408) app_init: ESP-IDF:          v5.5.1
I (412) efuse_init: Min chip rev:     v0.0
I (416) efuse_init: Max chip rev:     v3.99 
I (420) efuse_init: Chip rev:         v3.1
I (424) heap_init: Initializing. RAM available for dynamic allocation:
I (430) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (435) heap_init: At 3FFB7FD0 len 00028030 (160 KiB): DRAM
I (440) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (446) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (451) heap_init: At 40097E0C len 000081F4 (32 KiB): IRAM
W (458) spi_flash: Detected boya flash chip but using generic driver. For optimal functionality, enable `SPI_FLASH_SUPPORT_BOYA_CHIP` in menuconfig
I (469) spi_flash: detected chip: generic
I (473) spi_flash: flash io: dio
W (476) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the size in the binary image header.
I (489) main_task: Started on CPU0
I (499) main_task: Calling app_main()
I (499) LAB_WIFI_CONN: [FORENSIC]: Call nvs_flash_init()
I (509) LAB_WIFI_CONN: [FORENSIC]: nvs_flash_init() returned ESP_OK (0x0)
I (509) LAB_WIFI_CONN: [FORENSIC]: Call esp_netif_init()
I (509) LAB_WIFI_CONN: [FORENSIC]: Call esp_event_loop_create_default()
I (509) LAB_WIFI_CONN: [FORENSIC]: Call esp_netif_create_default_wifi_sta()
I (519) LAB_WIFI_CONN: [FORENSIC]: esp_netif_create_default_wifi_sta() returned 0x3ffbd838
I (529) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_init(&cfg)
I (539) wifi:wifi driver task: 3ffbff24, prio:23, stack:6656, core=0
I (549) wifi:wifi firmware version: 14da9b7
I (549) wifi:wifi certification version: v7.0
I (549) wifi:config NVS flash: enabled
I (549) wifi:config nano formatting: disabled
I (559) wifi:Init data frame dynamic rx buffer num: 32
I (559) wifi:Init static rx mgmt buffer num: 5
I (559) wifi:Init management short buffer num: 32
I (569) wifi:Init dynamic tx buffer num: 32
I (569) wifi:Init static rx buffer size: 1600
I (579) wifi:Init static rx buffer num: 10
I (579) wifi:Init dynamic rx buffer num: 32
I (589) wifi_init: rx ba win: 6
I (589) wifi_init: accept mbox: 6
I (589) wifi_init: tcpip mbox: 32
I (589) wifi_init: udp mbox: 6
I (599) wifi_init: tcp mbox: 6
I (599) wifi_init: tcp tx win: 5760
I (599) wifi_init: tcp rx win: 5760
I (609) wifi_init: tcp mss: 1440
I (609) wifi_init: WiFi IRAM OP enabled
I (609) wifi_init: WiFi RX IRAM OP enabled
I (619) LAB_WIFI_CONN: [FORENSIC]: Call esp_event_handler_instance_register(WIFI_EVENT)
I (619) LAB_WIFI_CONN: [FORENSIC]: Call esp_event_handler_instance_register(IP_EVENT)
I (629) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_set_mode(WIFI_MODE_STA)
I (639) LAB_WIFI_CONN: ==================================================================
I (649) LAB_WIFI_CONN:   Lab 5.2: Wi-Fi Connection & IP Assignment (ESP-IDF Forensic)
I (649) LAB_WIFI_CONN: ==================================================================
I (659) LAB_WIFI_CONN: 

I (659) LAB_WIFI_CONN: ------------------------------------------------------------------
I (669) LAB_WIFI_CONN: >>> Experiment 5.2.1: Connection Test - Correct Credentials
I (679) LAB_WIFI_CONN: ------------------------------------------------------------------
I (689) LAB_WIFI_CONN:   Target SSID: "MY_SSID"
I (689) LAB_WIFI_CONN:   Target Password: "MY_PASSWORD"
I (699) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_stop()
I (699) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_set_config(WIFI_IF_STA, &wifi_config)
I (739) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_set_config() returned ESP_OK (0x0)
I (739) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_start()
I (739) phy_init: phy_version 4861,b71b5ad,Aug  5 2025,11:16:06
I (829) phy_init: Saving new calibration data due to checksum failure or outdated calibration data, mode(0)
I (889) wifi:mode : sta (14:08:08:a4:c7:bc)
I (889) wifi:enable tsf
I (889) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT ID 43 received
I (899) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_start() returned ESP_OK (0x0)
I (899) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_START received
I (909) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
I (909) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_connect() returned ESP_OK (0x0)
W (3329) LAB_WIFI_CONN: =======================================================
W (3329) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (3329) LAB_WIFI_CONN:   -> Target SSID          : MY_SSID
W (3329) LAB_WIFI_CONN:   -> Reason Code (Decimal): 201
W (3339) LAB_WIFI_CONN:   -> Reason Code (Hex)    : 0xC9
W (3339) LAB_WIFI_CONN:   -> Reason Description   : WIFI_REASON_NO_AP_FOUND (201)
W (3349) LAB_WIFI_CONN: =======================================================
W (3359) LAB_WIFI_CONN: [RESULT]: TEST FAILED - Disconnected event captured.
I (5369) LAB_WIFI_CONN: 

I (5369) LAB_WIFI_CONN: ------------------------------------------------------------------
I (5369) LAB_WIFI_CONN: >>> Experiment 5.2.2: Connection Test - Wrong SSID (No AP Found)
I (5369) LAB_WIFI_CONN: ------------------------------------------------------------------
I (5379) LAB_WIFI_CONN:   Target SSID: "NON_EXISTENT_SSID_9999"
I (5389) LAB_WIFI_CONN:   Target Password: "12345678"
I (5389) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_stop()
I (5399) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT ID 3 received
I (5399) wifi:flush txq
I (5399) wifi:stop sw txq
I (5409) wifi:lmac stop hw txq
I (5409) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_set_config(WIFI_IF_STA, &wifi_config)
I (5459) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_set_config() returned ESP_OK (0x0)
I (5459) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_start()
I (5469) wifi:mode : sta (14:08:08:a4:c7:bc)
I (5469) wifi:enable tsf
I (5469) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_START received
I (5479) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
I (5479) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_connect() returned ESP_OK (0x0)
I (5469) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_start() returned ESP_OK (0x0)
W (7899) LAB_WIFI_CONN: =======================================================
W (7899) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (7899) LAB_WIFI_CONN:   -> Target SSID          : NON_EXISTENT_SSID_9999
W (7909) LAB_WIFI_CONN:   -> Reason Code (Decimal): 201
W (7909) LAB_WIFI_CONN:   -> Reason Code (Hex)    : 0xC9
W (7919) LAB_WIFI_CONN:   -> Reason Description   : WIFI_REASON_NO_AP_FOUND (201)
W (7919) LAB_WIFI_CONN: =======================================================
W (7929) LAB_WIFI_CONN: [RESULT]: TEST FAILED - Disconnected event captured.
I (9939) LAB_WIFI_CONN: 

I (9939) LAB_WIFI_CONN: ------------------------------------------------------------------
I (9939) LAB_WIFI_CONN: >>> Experiment 5.2.3: Connection Test - Wrong Password (Auth/Handshake Fail)
I (9939) LAB_WIFI_CONN: ------------------------------------------------------------------
I (9949) LAB_WIFI_CONN:   Target SSID: "MY_SSID"
I (9959) LAB_WIFI_CONN:   Target Password: "WRONG_PASS_9999"
I (9959) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_stop()
I (9969) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT ID 3 received
I (9969) wifi:flush txq
I (9969) wifi:stop sw txq
I (9979) wifi:lmac stop hw txq
I (9979) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_set_config(WIFI_IF_STA, &wifi_config)
I (10069) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_set_config() returned ESP_OK (0x0)
I (10069) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_start()
I (10079) wifi:mode : sta (14:08:08:a4:c7:bc)
I (10079) wifi:enable tsf
I (10079) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_START received
I (10089) LAB_WIFI_CONN: [FORENSIC]: Call esp_wifi_connect()
I (10089) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_connect() returned ESP_OK (0x0)
I (10079) LAB_WIFI_CONN: [FORENSIC]: esp_wifi_start() returned ESP_OK (0x0)
W (12509) LAB_WIFI_CONN: =======================================================
W (12509) LAB_WIFI_CONN: [EVENT FORENSIC]: WIFI_EVENT_STA_DISCONNECTED received!
W (12509) LAB_WIFI_CONN:   -> Target SSID          : MY_SSID
W (12509) LAB_WIFI_CONN:   -> Reason Code (Decimal): 201
W (12519) LAB_WIFI_CONN:   -> Reason Code (Hex)    : 0xC9
W (12519) LAB_WIFI_CONN:   -> Reason Description   : WIFI_REASON_NO_AP_FOUND (201)
W (12529) LAB_WIFI_CONN: =======================================================
W (12539) LAB_WIFI_CONN: [RESULT]: TEST FAILED - Disconnected event captured.
I (12549) LAB_WIFI_CONN: ==================================================================
I (12549) LAB_WIFI_CONN:   [Phase 2/3/4/5 Completed: Wi-Fi Connection Lab Finished]
I (12559) LAB_WIFI_CONN: ==================================================================
I (12569) main_task: Returned from app_main()

~~~

---

## 7. คำถามท้ายการทดลอง (Post-Lab Questions)

1. เหตุใดการระบุ SSID ผิด (ข้อ 5.2.2) จึงส่งผลให้เกิด Disconnect Event ด้วย Reason Code `201` (`WIFI_REASON_NO_AP_FOUND`) ตั้งแต่เฟส Scan?
2. เหตุใดการพิมพ์ Password ผิด (ข้อ 5.2.3) จึงผ่านเฟส Auth และ Assoc มาได้ แต่มาล้มเหลวในเฟส 4-Way Handshake (Reason Code `15` หรือ `204`)?
3. ลำดับการเกิด Event ระหว่าง **`WIFI_EVENT_STA_CONNECTED`** กับ **`IP_EVENT_STA_GOT_IP`** Event ใดเกิดขึ้นก่อนกัน และมีความหมายทางกายภาพของ Layer Network ต่างกันอย่างไร?
4. สมาชิกตัวแปร `reason` ในโครงสร้าง `wifi_event_sta_disconnected_t` มีประโยชน์อย่างไรต่อการออกแบบระบบค้นหาสาเหตุและกู้คืนการเชื่อมต่อ (Auto-Reconnection Mechanism) ในแอปพลิเคชัน IoT?
