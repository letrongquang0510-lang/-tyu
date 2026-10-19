# Yêu cầu đầu ra
## Báo cáo phân tích (I/O) : Định nghĩa rõ Input (văn bản thô) và Output (giao diện render chuyên nghiệp).
  -   **Input (Văn bản thô / Yêu cầu ban đầu):**
    -   Yêu cầu xây dựng tài liệu kỹ thuật cài đặt cảm biến độ ẩm trang trại Lan.
          -   Yêu cầu định dạng: Sử dụng Inline Code cho biến/lệnh ngắn, Code Block có Highlight cho đoạn code Python điều khiển máy bơm, Bảng (Table) so sánh cảm biến, Danh sách công việc (Task List) và xử lý ký tự đặc biệt bằng ký tự thoát (Escape).
-   **Output (Giao diện render chuyên nghiệp):**
    -   Tài liệu Markdown có cấu trúc rõ ràng với các đề mục chuẩn (`#`, `##`).      
    -   Các khối mã nguồn trực quan, dễ phân biệt giữa dòng lệnh Terminal và văn bản hướng dẫn thông thường.      
    -   Dữ liệu dạng bảng mạch lạc giúp so sánh thiết bị nhanh chóng.
    -   Checklist công việc dưới dạng danh sách tương tác (`- [ ]`, `- [x]`).
       -   Đảm bảo hiển thị chính xác các ký tự đặc biệt thông qua ký tự escape
## Source code : Một file .md chứa đầy đủ: Khối code Python, Bảng so sánh và Task List kiểm tra thiết bị.
### 1. Khối code Python Điều khiển Máy bơm
- **cập nhập hệ thống**
sudo apt update && sudo apt upgrade -y
- **Cài đặt thư viện cho cảm biến DHT22**
sudo apt install -y git python3-pip sudo pip3 install Adafruit_DHT
- **kích hoạt giao tiếp 1-wire**
sudo raspi-config # Chọn: Interface Options > # 1-Wire > Enable
- **kiểm tra module đã nhận được**
ls /sys/bus/w1/devices/ # Kết quả có dạng 28-xxxxxxx
- **chạy thử chương trình đọc cảm biến**
git clone https://github.com/adafruit/Adafruit_Python_DHT.git cd Adafruit_Python_DHT/examples python3 AdafruitDHT.py 22 4 # 22: DHT22, 4: GPIO pin # Nhận kết quả độ ẩm và nhiệt độ
- **tự dộng chạy khi khởi dộng**
crontab -e # Thêm dòng (ví dụ mỗi 5 phút): */5 * * * * python3 /home/pi/read_dht22.py
- **kết quả**
```
Temp=28.4°C   Humidity=67.1%
pi@farm:~ $

```
### 2. Bảng So sánh Cảm biến

|**Tiêu chí**|**Cảm biến cũ**|**Cảm biến mới**|
|:---|:---|:---|
|Độ chính xác|$\pm 5\%$|$\pm 1\%$|
|Giao tiếp|Analog|Digital (I2C)|
|Biến mã|sensor_old|sensor_v2|
### 3. Task List Kiểm tra Thiết bị
-   [x] Kiểm tra sơ đồ đấu nối chân `VCC`, `GND`, `Data`    
-   [ ] Cài đặt thư viện `adafruit-circuitpython-dht`
-   [ ] Kiểm tra phản hồi tín hiệu cảm biến `#sensor_v2`




