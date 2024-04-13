# Thiết bị cảnh báo đi lạc.
---
## Hệ thống định vị (gọi chung là GNSS - Global Navigation Stateline System)
- **GPS** (General Positioning System): Hệ thống định vị toàn cầu, được Mỹ phát triển với khoảng hơn 30 vệ tinh đang hoạt động.
	> Đây sẽ là hệ thống định vị chính được sử dụng trong dự án lần này.
	
- GLONASS (Nga)
- Beidou (Trung Quốc)
- Galileo (EU)

## Các thành phần của GPS
Gồm có 3 thành phần chính:
- Phần không gian: Bao gồm các vệ tinh hoạt động trên 6 mặt phẳng quỹ đạo.
- Phần kiểm soát: Có chức năng đảm bảo vệ tinh di chuyển đúng quỹ đạo và truyền nhận thông tin chính xác.
- Các thiết bị nhận tín hiệu vệ tinh được người dùng sử dụng, được tích hợp các thuật toán ước tính và hoàn thiện kết quả đầu ra một cách chính xác.

## Cách thức hoạt động của GPS
Thiết bị nhận sẽ tính toán được khoảng thời gian kể từ khi vệ tinh bắt đầu phát tín hiệu cho đến khi nhận được tín hiệu, từ đó tính toán được độ dài quãng đường truyền nhận. 
Từ mỗi vệ tinh, ta vẽ được đường tròn tập hợp các điểm với khoảng cách đến vệ tinh là bằng nhau. Với 3 vệ tinh sẽ dễ dàng xác định được kinh độ và vĩ độ của thiết bị.
![[Pasted image 20240412002628.png]]

## Các module phổ biến trên thị trường

| Danh mục   | **Quectel L76X**                                                | **NEO-6M, NEO-7M**                   |
| ---------- | --------------------------------------------------------------- | ------------------------------------ |
| Hình ảnh   | ![[Pasted image 20240412131318.png]]                            | ![[Pasted image 20240412131103.png]] |
| Ưu điểm    | - Giá thành rẻ.<br>- Phổ biến, số lượng tài liệu tham khảo lớn. | Ổn định, bắt tín hiệu rất nhạy.      |
| Nhược điểm | - Nhiều hàng giả, hàng nhái.                                    | Giá thành cao.                       |
## Module Quectel L76X
Đây là module dùng để tiếp nhận dữ liệu từ vệ tinh và gửi trả tọa độ thiết bị.
>[!note]
>Module GPS Quectel L76X sử dụng NMEA (National Marine Electronics Association) làm định dạng dữ liệu tiêu chuẩn trong quá trình truyền tải. 
Cấu trúc của một chuỗi NMEA:
![[Pasted image 20240412222022.png]]
>- **GPGGA**: Header. Mỗi header tương ứng với mỗi output message. Ở đây GPGGA là header thông dụng có chứa tọa độ vị trí. Ngoài ra còn 13 loại header khác nhau.
>- **1891908.00**: Time stamp. Giờ UTC theo cấu trúc lần lượt là giờ, phút, giây.
>- **3403.7041778**: Vĩ độ.
>- **N**: Vĩ độ Bắc.
>- **07044.3966270**: Kinh độ.
>- **W**: Kinh độ Tây.
>- **4**: Chỉ số chất lượng.
>- **13**: Lượng vệ tinh sử dụng để xác định tọa độ.
>- **1.0**: HDOP - horizontal dilution of precision (độ pha loãng theo chiều ngang).
>- **495.144**: Độ cao (antenna).
>- **M**: Đơn vị độ cao.
>- **29.200**: Độ phân tách địa chất (dùng độ cao antenna trừ cho giá trị này để đạt được giá trị HAE - Height Above Ellipsoid).
>- **M**: Đơn vị đo cho độ phân tách địa chất.
>- **0.10**: Thời gian (giây) từ lần update cuối cùng của trạm tham chiếu.
>- **0000**: ID trạm tham chiếu.
>- **\*40**: Checksum
-40℃ ~ 85℃

- Kích thước 32.5 x 25.5 mm.
- Điện áp hoạt động: 5V / 3.3V.
- Dòng hoạt động: 11mA.
- Nhiệt độ hoạt động: -40℃ ~ 85℃.
- Module hỗ trợ nhiều hệ thống định vị: **GPS**, BDS và QZSS.
- Giao tiếp với bo mạch vi điều khiển thông qua UART (Baudrate mặc định là 9600).
- Có độ chính xác nhỏ hơn 2.5m. Thời gian đầu tiên nhận được dữ liệu sau Cold Start là < 15s, sau Warm starts là < 5s, sau Hot starts là < 1s.

Một số công nghệ đặc biệt 
- EASY™, công nghệ dự đoán tự theo dõi, giúp định vị nhanh chóng.
- AlwaysLocate™, bộ điều khiển thông minh hoạt động định kỳ để tiết kiệm năng lượng.
- Pin MS621FE, dùng để bảo quản ephemeris information và hot starts.
- 2x LEDs biểu thị trạng thái hoạt động của module.

![[Pasted image 20240413000247.png]]

1. **L76B module**
2. **RT9193-33:** power manager
3. **Rechargeable MS621FE Li battery**
4. **Ceramics active antenna**
5. **GPS status indicator**
6. **Power indicator**
7. **PH2.0 5PIN connector**
8. **GNSS antenna connector**
9. **Backup mode wakeup jumper:** Hàn nối để thoát backup mode.

## Module I2C và LCD
Module I2C PCF8754 được sử dụng để làm trung gian kết nối giữa MCU và LCD.
![[Pasted image 20240413000738.png]]

![[Pasted image 20240413001654.png]]
## Sơ đồ hệ thống
> Làm mạch in

![[GPS-device.drawio(4).svg]]