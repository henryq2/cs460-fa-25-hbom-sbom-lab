### 1) ESP32-S3FN8 (Dual-core Xtensa LX7, up to 240 MHz)

- **Manufacturer:** Espressif Systems.
- **Part / Family:** ESP32-S3 series; variant **ESP32-S3FN8** (8 MB external flash). Dual-core Xtensa LX7 MCU up to 240 MHz, Wi-Fi 2.4 GHz + BLE 5, ~512 KB SRAM (plus external PSRAM/flash options).
- **Known vulnerabilities / operational risk:**
  - **CVE-2024-45798**: A pipeline-execution issue in the Arduino-ESP32 repository CI. Since the cardputer uses Arduino, this would affect the model given the repository is used. It has been fixed upstream, and users should verify artifacts.
  - **CVE-2023-35818**: Electromagnetic fault injection on “ESP32_rev300 (ECO3)” can force entry to ROM download mode regardless of Secure Boot/Flash Encryption, enabling plaintext flash read or stub execution. It may not be an issue on Cardputer since the ESP32 revision is different, but in general fault injection is a category of prevalent attack on embedded systems, so attention is needed to prevent this in operation.
  - **Operational notes:** As a Wi-Fi/BLE SoC, there are many attack surfaces including over-the-air attack surface, insecure OTA/update pipelines, and insecure peripheral buses to sensors/displays.

---

### 2) ST7789V2 TFT-LCD controller/driver

- **Manufacturer:** Sitronix Technology Corp.
- **Part / Family:** **ST7789V2** is a single-chip 262K-color TFT-LCD controller/driver
- **Known vulnerabilities / operational risk:**
  - No NVD-listed CVEs specific to ST7789V2 were found. The related risks are mostly on the render path: if the microcontroller firmware or the display bus is compromised, attackers can spoof UI and display falsify warnings/values, or leak screen content by man-in-the-middle attack to the data bus.

---

### 3) SIT3088EEUA (SIT3088E) RS-485 transceiver

- **Manufacturer: SIT 芯力特
- **Part / Family:** SIT3088E is a half-duplex RS-485 transceiver
- **Known vulnerabilities / operational risk:**
  - Protocols commonly carried over RS-485 like Modbus are typically insecure, as they do not include authentication or integrity check. This enables spoofing, tampering, and eavesdropping if attackers gain bus access.

---

### Summarize how hardware dependencies can influence firmware/software risk

 - Hardware plays a pivotal role in systems security, as it runs one layer below software, and is almost always implicitly trusted by the software, so the security mitigations applied to software usually are not very effective to hardware. For example, if we were to compromise the sensors, communication channels, or displays, we could lead the system/user to believe in false data, and deny them access to critical subsystems. Likewise, fault-injection attacks, as seen in older ESP32 revisions, demonstrate that hardware can be physically coerced to bypass security features if tamper resistance is weak. In addition, even if a microcontroller or peripheral chip is functionally sound, its associated SDKs, drivers, and build tools can introduce vulnerabilities, as we've seen in CVE-2024-45798. Collectively, these factors show that firmware security cannot be isolated from the hardware it runs on—resilience requires both secure hardware roots and a controlled, transparent supply chain.
