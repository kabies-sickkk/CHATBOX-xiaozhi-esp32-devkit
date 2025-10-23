
```bash
idf.py set-target esp32
```

**打开 menuconfig：**

```bash
idf.py menuconfig
```

**选择板子：**

```
Xiaozhi Assistant -> Board Type -> ESP32 CGC 144
```

**编译：**

```bash
idf.py build
```
xóa dữ liệu Build
```bash
idf.py fullclean
```
# thay COM5 bằng cổng thực tế
```bash
idf.py -p COM5 flash
```
# Cấu hình phần cứng (Board Configuration)


<img width="800" height="581" alt="image" src="https://github.com/user-attachments/assets/37683826-03ae-4d9c-bb50-71cebc37cfe3" />


Microphone (I²S)

## Sử dụng microphone kỹ thuật số I²S loại INMP441 / SPH0645 / ICS-43434.
Kết nối như sau:

VCC → 3V3

GND → GND

WS / LRCK → GPIO25 (I²S word select)

SCK / BCLK → GPIO26 (I²S bit clock)

SD / DOUT → GPIO32 (dữ liệu từ mic đến ESP32)

L/R → GND (chọn kênh ghi bên trái, nếu nối 3V3 thì là bên phải)

**Loa khuếch đại MAX98357A (I²S)**

Sử dụng module MAX98357A I²S amplifier để phát âm thanh ra loa.
Kết nối như sau:

LRC / WS → GPIO27 (I²S left-right clock)

BCLK → GPIO14 (I²S bit clock)

DIN → GPIO33 (dữ liệu âm thanh từ ESP32)

GAIN → GND (hoặc 3V3 để tăng độ khuếch đại)

SD → 3V3 (giữ chip luôn hoạt động)

VCC → 5V (nguồn cho module khuếch đại)

GND → GND

**Màn hình TFT LCD ST7789 (SPI)**

Sử dụng màn hình SPI ST7789 (128×128 hoặc 240×240).
Kết nối với ESP32 như sau:

SCLK / CLK → GPIO18 (SPI clock)

MOSI / SDA / DIN → GPIO23 (SPI data)

CS → GPIO5 (chip select)

DC → GPIO2 (chọn giữa lệnh và dữ liệu)

RESET → Nối 3V3 (vì chân reset không sử dụng – GPIO_NC)

BL / LED → GPIO4 (điều khiển đèn nền)

VCC → 3V3

GND → GND

Tốc độ SPI: 20 MHz
Loại hiển thị: ST7789 serial, hỗ trợ đảo màu, lật trục X/Y tùy cấu hình.

Nút nhấn và đèn

Các nút và đèn được cấu hình cho thao tác cơ bản:

BOOT Button → GPIO0 (dùng để flash / nạp code)

ASR Button → GPIO13 (nút kích hoạt chức năng ví dụ nhận dạng giọng nói)

Lamp Control → GPIO12 (điều khiển bật/tắt đèn hoặc relay test)

Tóm tắt giao thức sử dụng

I²S (input) → microphone kỹ thuật số

I²S (output) → khuếch đại MAX98357A

SPI → màn hình ST7789

GPIO → nút nhấn và đèn báo

---

Link tham khảo: 
https://www.wdmomo.fun:81/doc/index.html?file=001_%E8%AE%BE%E8%AE%A1%E9%A1%B9%E7%9B%AE/0001_%E5%B0%8F%E6%99%BAAI/002_ESP32-CGC%E5%BC%80%E5%8F%91%E6%9D%BF%E5%B0%8F%E6%99%BAAI

https://xiaozhi.me/
