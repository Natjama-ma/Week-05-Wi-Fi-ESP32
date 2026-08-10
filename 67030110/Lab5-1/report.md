# ใบงานที่ 5.1: การเชื่อมต่อ Wi-Fi และการค้นหาสัญญาณรอบข้าง (Wi-Fi Connection and Scanning)
---

~~~
I (29) boot: ESP-IDF v5.5.1 2nd stage bootloader
I (29) boot: compile time Aug  4 2026 11:20:41
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
I (81) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=19b74h (105332) map
I (124) esp_image: segment 1: paddr=00029b9c vaddr=3ffb0000 size=03eech ( 16108) load
I (130) esp_image: segment 2: paddr=0002da90 vaddr=40080000 size=02588h (  9608) load
I (134) esp_image: segment 3: paddr=00030020 vaddr=400d0020 size=86364h (549732) map
I (323) esp_image: segment 4: paddr=000b638c vaddr=40082588 size=15884h ( 88196) load
I (358) esp_image: segment 5: paddr=000cbc18 vaddr=50000000 size=00020h (    32) load
I (370) boot: Loaded app from partition at offset 0x10000
I (370) boot: Disabling RNG early entropy source...
I (380) cpu_start: Multicore app
I (389) cpu_start: Pro cpu start user code
I (389) cpu_start: cpu freq: 160000000 Hz
I (389) app_init: Application information:
I (389) app_init: Project name:     wifi_scan_phase
I (393) app_init: App version:      218e85e-dirty
I (398) app_init: Compile time:     Aug  4 2026 11:19:48
I (403) app_init: ELF file SHA256:  5f86962b2...
I (407) app_init: ESP-IDF:          v5.5.1
I (411) efuse_init: Min chip rev:     v0.0
I (415) efuse_init: Max chip rev:     v3.99 
I (419) efuse_init: Chip rev:         v3.1
I (423) heap_init: Initializing. RAM available for dynamic allocation:
I (429) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (434) heap_init: At 3FFB7FC8 len 00028038 (160 KiB): DRAM
I (439) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (445) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (450) heap_init: At 40097E0C len 000081F4 (32 KiB): IRAM
W (457) spi_flash: Detected boya flash chip but using generic driver. For optimal functionality, enable `SPI_FLASH_SUPPORT_BOYA_CHIP` in menuconfig
I (468) spi_flash: detected chip: generic
I (472) spi_flash: flash io: dio
W (475) spi_flash: Detected size(4096k) larger than the size in the binary image header(2048k). Using the size in the binary image header.
I (488) main_task: Started on CPU0
I (498) main_task: Calling app_main()
I (498) LAB_WIFI_SCAN: [FORENSIC]: Call nvs_flash_init()
I (508) LAB_WIFI_SCAN: [FORENSIC]: nvs_flash_init() returned ESP_OK (0x0)
I (508) LAB_WIFI_SCAN: [FORENSIC]: Call esp_netif_init()
I (508) LAB_WIFI_SCAN: [FORENSIC]: esp_netif_init() returned ESP_OK (0x0)
I (508) LAB_WIFI_SCAN: [FORENSIC]: Call esp_event_loop_create_default()
I (518) LAB_WIFI_SCAN: [FORENSIC]: esp_event_loop_create_default() returned ESP_OK (0x0)
I (528) LAB_WIFI_SCAN: [FORENSIC]: Call esp_netif_create_default_wifi_sta()
I (538) LAB_WIFI_SCAN: [FORENSIC]: esp_netif_create_default_wifi_sta() returned pointer 0x3ffbd808
I (538) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_init(&cfg)
I (558) wifi:wifi driver task: 3ffbfef4, prio:23, stack:6656, core=0
I (558) wifi:wifi firmware version: 14da9b7
I (558) wifi:wifi certification version: v7.0
I (558) wifi:config NVS flash: enabled
I (568) wifi:config nano formatting: disabled
I (568) wifi:Init data frame dynamic rx buffer num: 32
I (578) wifi:Init static rx mgmt buffer num: 5
I (578) wifi:Init management short buffer num: 32
I (578) wifi:Init dynamic tx buffer num: 32
I (588) wifi:Init static rx buffer size: 1600
I (588) wifi:Init static rx buffer num: 10
I (598) wifi:Init dynamic rx buffer num: 32
I (598) wifi_init: rx ba win: 6
I (598) wifi_init: accept mbox: 6
I (608) wifi_init: tcpip mbox: 32
I (608) wifi_init: udp mbox: 6
I (608) wifi_init: tcp mbox: 6
I (608) wifi_init: tcp tx win: 5760
I (618) wifi_init: tcp rx win: 5760
I (618) wifi_init: tcp mss: 1440
I (618) wifi_init: WiFi IRAM OP enabled
I (628) wifi_init: WiFi RX IRAM OP enabled
I (628) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_init() returned ESP_OK (0x0)
I (638) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_set_mode(WIFI_MODE_STA)
I (638) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_set_mode() returned ESP_OK (0x0)
I (648) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_start()
I (658) phy_init: phy_version 4861,b71b5ad,Aug  5 2025,11:16:06
I (738) phy_init: Saving new calibration data due to checksum failure or outdated calibration data, mode(0)
I (798) wifi:mode : sta (14:08:08:a4:c7:bc)
I (798) wifi:enable tsf
I (798) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_start() returned ESP_OK (0x0)
I (798) LAB_WIFI_SCAN: ==================================================================
I (808) LAB_WIFI_SCAN:   Lab 5.1: Wi-Fi Connection and Scanning Phase (ESP-IDF Forensic)
I (818) LAB_WIFI_SCAN: ==================================================================
I (828) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (828) LAB_WIFI_SCAN: >>> Experiment 5.1.1: General AP Scan (All Channels)
I (838) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (848) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (3358) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 2499 ms]
I (3358) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_num(&ap_count)
I (3358) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=12
I (3368) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS
I (3368) LAB_WIFI_SCAN: [AP COUNT]: 12 network(s) found
I (3378) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_records(&number, ap_info)
I (3388) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_records() returned ESP_OK (0x0), records=12

--------------------------------------------------------------------------------------------------
No.  | SSID                     | MAC Address (BSSID) | RSSI   | Chan | Encryption Type     
--------------------------------------------------------------------------------------------------
1    | KMITL-WIFI               | 78:17:BE:C0:7D:A1 | -51  dBm | 1    | OPEN (No Password)  
2    | Cs.WiFi                  | 4E:9D:3A:DC:4C:B6 | -53  dBm | 11   | WPA2_WPA3_PSK       
3    | KMITL-Legacy             | 78:17:BE:C0:7D:A0 | -54  dBm | 1    | WPA2_ENTERPRISE     
4    | KMITL-IoT                | 78:17:BE:C0:7D:A2 | -55  dBm | 1    | WPA2_PSK            
5    | Thanutorn                | D6:65:F4:32:83:9C | -63  dBm | 6    | WPA2_PSK            
6    | Zenny                    | A6:27:B2:9B:5C:04 | -65  dBm | 6    | WPA2_PSK            
7    | Snowfake                 | A2:FA:D0:08:08:0C | -66  dBm | 6    | WPA2_PSK            
8    | I Bew                    | 4A:39:B6:6E:0A:29 | -79  dBm | 6    | WPA2_PSK            
9    | KMITL-Legacy             | 78:17:BE:C0:66:60 | -81  dBm | 11   | WPA2_ENTERPRISE     
10   | KMITL-IoT                | 78:17:BE:C0:66:62 | -81  dBm | 11   | WPA2_PSK            
11   | KMITL-WIFI               | 78:17:BE:C0:66:61 | -87  dBm | 11   | OPEN (No Password)  
12   | dlink                    | C4:A8:1D:93:89:30 | -92  dBm | 11   | OPEN (No Password)  
--------------------------------------------------------------------------------------------------

I (4528) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (4528) LAB_WIFI_SCAN: >>> Experiment 5.1.2: Channel-Specific Scan (Channel 1)
I (4528) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (4538) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (4748) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 200 ms]
I (4748) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_num(&ap_count)
I (4748) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=5
I (4758) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS
I (4758) LAB_WIFI_SCAN: [AP COUNT]: 5 network(s) found
I (4768) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_records(&number, ap_info)
I (4778) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_records() returned ESP_OK (0x0), records=5

--------------------------------------------------------------------------------------------------
No.  | SSID                     | MAC Address (BSSID) | RSSI   | Chan | Encryption Type     
--------------------------------------------------------------------------------------------------
1    | KMITL-Legacy             | 78:17:BE:C0:7D:A0 | -51  dBm | 1    | WPA2_ENTERPRISE     
2    | KMITL-IoT                | 78:17:BE:C0:7D:A2 | -51  dBm | 1    | WPA2_PSK            
3    | KMITL-WIFI               | 78:17:BE:C0:7D:A1 | -52  dBm | 1    | OPEN (No Password)  
4    | KMITL-WIFI               | 78:17:BE:C0:66:21 | -83  dBm | 1    | OPEN (No Password)  
5    | KMITL-Legacy             | 78:17:BE:C0:66:20 | -86  dBm | 1    | WPA2_ENTERPRISE     
--------------------------------------------------------------------------------------------------

I (5858) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (5858) LAB_WIFI_SCAN: >>> Experiment 5.1.3: Targeted SSID Scan - Existing ("KMITL-WIFI")
I (5858) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (5868) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (8378) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 2499 ms]
I (8378) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_num(&ap_count)
I (8378) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=4
I (8388) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS
I (8388) LAB_WIFI_SCAN: [AP COUNT]: 4 network(s) found
I (8398) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_records(&number, ap_info)
I (8408) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_records() returned ESP_OK (0x0), records=4

--------------------------------------------------------------------------------------------------
No.  | SSID                     | MAC Address (BSSID) | RSSI   | Chan | Encryption Type     
--------------------------------------------------------------------------------------------------
1    | KMITL-WIFI               | 78:17:BE:C0:7D:A1 | -50  dBm | 1    | OPEN (No Password)  
2    | KMITL-WIFI               | 78:17:BE:A9:94:E1 | -83  dBm | 6    | OPEN (No Password)  
3    | KMITL-WIFI               | 78:17:BE:C0:72:61 | -83  dBm | 11   | OPEN (No Password)  
4    | KMITL-WIFI               | 78:17:BE:C0:66:61 | -85  dBm | 11   | OPEN (No Password)  
--------------------------------------------------------------------------------------------------

I (9478) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (9478) LAB_WIFI_SCAN: >>> Experiment 5.1.4: Targeted SSID Scan - Non-Existent ("NON_EXISTENT_AP_9999")
I (9478) LAB_WIFI_SCAN: ------------------------------------------------------------------
I (9488) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_start(scan_config, block=true)
I (11998) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_start() returned ESP_OK (0x0) [Duration: 2498 ms]
I (11998) LAB_WIFI_SCAN: [FORENSIC]: Call esp_wifi_scan_get_ap_num(&ap_count)
I (11998) LAB_WIFI_SCAN: [FORENSIC]: esp_wifi_scan_get_ap_num() returned ESP_OK (0x0), ap_count=0
I (12008) LAB_WIFI_SCAN: [STATUS]: Scan SUCCESS
I (12008) LAB_WIFI_SCAN: [AP COUNT]: 0 network(s) found
W (12018) LAB_WIFI_SCAN: [NOTE]: No Access Point found matching the criteria.
I (12018) LAB_WIFI_SCAN: ==================================================================
I (12028) LAB_WIFI_SCAN:   [Phase 1 Completed: Wi-Fi Scan Finished]
I (12038) LAB_WIFI_SCAN:   Program stopped after scanning. Auth/Assoc Phase not started.
I (12048) LAB_WIFI_SCAN: ==================================================================
I (12048) main_task: Returned from app_main()
~~~

## 6. ตารางบันทึกผลการทดลอง (Experiment Results)
ให้นักศึกษาบันทึกผลลัพธ์จากการสังเกตใน Serial Console ลงในตารางต่อไปนี้:

### 6.1 ตารางสรุปเปรียบเทียบการสแกนทั้ง 4 กรณี
| ข้อการทดลอง | เงื่อนไขการสแกน | สถานะ (Success/Error Code) | จำนวน AP ที่พบ (เครือข่าย) | เวลาที่ใช้ในการสแกน (ms) |
| :---: | :--- | :---: | :---: | :---: |
| **5.1.1** | สแกนทั่วไปทุก Channel |ESP_OK (0x0) |12 |2499 ms |
| **5.1.2** | กำหนดสแกนเฉพาะ Channel 1 |ESP_OK (0x0) |5 |200 ms |
| **5.1.3** | กำหนดสแกน SSID ที่มีจริง |ESP_OK (0x0) |4 |2499 ms |
| **5.1.4** | กำหนดสแกน SSID ที่ไม่มีจริง | ESP_OK (0x0)|0 |2498 ms |

### 6.2 ตารางรายละเอียด AP ที่พบจากการสแกนทั่วไป (ข้อ 5.1.1)

| ลำดับ | ชื่อเครือข่าย (SSID) | MAC Address (BSSID) | ความแรงสัญญาณ (RSSI: dBm) | ช่องความถี่ (Channel) | ประเภทการเข้ารหัส (Encryption Type) |
| :---: | :--- | :--- | :---: | :---: | :--- |
| 1 |KMITL-WIFI |78:17:BE:C0:7D:A1 |-51 dBm |1 |OPEN (No Password) |
| 2 |Cs.WiFi |4E:9D:3A:DC:4C:B6 |-53 dBm | 11|WPA2_WPA3_PSK |
| 3 |KMITL-Legacy |78:17:BE:C0:7D:A0 |-54 dBm |1 |WPA2_ENTERPRISE |
| 4 |KMITL-IoT |78:17:BE:C0:7D:A2 |-55 dBm | 1| WPA2_PSK|
| 5 |Thanutorn |D6:65:F4:32:83:9C |-63 dBm |6 |WPA2_PSK |

---

## 7. คำถามท้ายการทดลอง (Post-Lab Questions)

1. การกำหนดค่าในโครงสร้าง `wifi_scan_config_t` สำหรับสแกนเจาะจงเฉพาะช่องความถี่ (ข้อ 5.1.2) ช่วยลดเวลาในการสแกนเมื่อเทียบกับการสแกนทุกช่องความถี่ (ข้อ 5.1.1) อย่างไร และมีข้อจำกัดอย่างไร?
~~~
ESP32 จะฟังสัญญาณเฉพาะช่องสัญญาณ (Channel) ที่ระบุเท่านั้น ไม่เสียเวลาไล่สแกนและรอ dwell time ทีละช่องจนครบ 1–13 ช่อง ทำให้สแกนเสร็จเร็วขึ้นมาก
ข้อจำกัด หาก AP/Router ย้ายไปใช้ช่องสัญญาณอื่น หรือเปลี่ยนช่องแบบอัตโนมัติ (Auto Channel) ESP32 จะสแกนไม่พบ AP นั้นเลย
~~~

2. เมื่อสังเกตผล Forensic Log ในข้อ 5.1.4 (สแกนหา SSID ที่ไม่มีอยู่จริง) ฟังก์ชัน `esp_wifi_scan_start()`, `esp_wifi_scan_get_ap_num()` และ `esp_wifi_scan_get_ap_records()` ส่งคืนค่าอย่างไร?
~~~
esp_wifi_scan_start(): ส่งคืนค่า ESP_OK (ฟังก์ชั่นสั่งสแกนทำงานสำเร็จปกติ)
esp_wifi_scan_get_ap_num(): ส่งคืนจำนวน 0 (ไม่พบ AP ที่ตรงตามเงื่อนไข)
esp_wifi_scan_get_ap_records(): ส่งคืนค่า ESP_OK แต่โครงสร้างข้อมูลในบัฟเฟอร์จะว่างเปล่า (ไม่มี Record ใดๆ)
~~~
3. ค่าระดับความแรงสัญญาณ (RSSI) ที่แสดงเป็นตัวเลขติดลบ (เช่น -45 dBm กับ -80 dBm) ค่าใดแสดงถึงสัญญาณที่มีความแรงและความเสถียรมากกว่ากัน?
~~~
-45 dBm แรงและเสถียรกว่าเพราะค่า RSSI เป็นหน่วยติดลบ ยิ่งเข้าใกล้ 0 มากเท่าไหร่ แสดงว่าสัญญาณยิ่งแรง ( -45 dBm สัญญาณแรงมาก / -80 dBm สัญญาณอ่อนและอาจหลุดง่าย
~~~
4. เหตุใดการดึงค่า `authmode` (`wifi_auth_mode_t`) จากโครงสร้าง `wifi_ap_record_t` จึงมีความสำคัญต่อการเตรียมการในเฟสถัดไป (Authentication & Association Phase)?
~~~
เพื่อให้ ESP32 รู้ว่า Router เป้าหมายใช้ระบบความปลอดภัยแบบใด (เช่น Open, WPA2-PSK, WPA3-PSK)
~~~
