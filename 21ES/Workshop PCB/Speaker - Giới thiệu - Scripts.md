### Nội dung chính:
Hôm nay chúng mình sẽ đưa đến các bạn các nội dung chính như sau:
- Đầu tiên, chúng ta sẽ cần hiểu được một số khái niệm cơ bản về PCB như nó **là gì**, tại sao PCB lại là loại mạch ưu tiên và được ứng dụng rộng rãi trong hầu hết các thiết bị và linh kiện điện tử, cấu trúc cơ bản của một PCB là như thế nào.
- Phần tiếp theo là làm thế nào để có thể thiết kế được một chiếc mạch PCB đơn giản? Các bạn sẽ được làm quen với phần mềm KiCad và hiểu rõ quy trình thiết kế từ đầu đến cuối. Vì đây là nội dung trọng tâm của workshop ngày hôm nay nên tất cả mọi người sẽ được hướng dẫn thực hành chi tiết bởi diễn giả Nguyễn Đức Hưng.
- Sau khi đã thiết kế thành công, gia công sẽ là giai đoạn cuối cùng để khiến chiếc mạch của bạn có thể đem vào sử dụng. Diễn giả Đặng Tuấn Anh sẽ giới thiệu chi tiết về các bước đem một chiếc mạch in đến với thực tế và các phương pháp gia công mà bạn có thể lựa chọn.

### PCB là gì ?
PCB viết tắt cho Printed Circuit Board, được dịch ra là bảng mạch in, hay bo mạch in, hay chỉ đơn giản và thông dụng như **mạch in**.
Đây là một tấm vật liệu cách điện, thường được làm từ sợi thủy tinh, phủ lên một lớp kim loại dẫn điện như đồng. Trên bề mặt của lớp kim loại này sẽ được “in” các đường dẫn điện và các vị trí để gắn các linh kiện điện tử.
Như các bạn có thể thấy trên hình, con trở tại đây có một chân được nối đến chiếc tụ gốm bên cạnh, một lát nữa thôi các bạn sẽ hiểu được cách mà chúng ta có thể tạo ra các đường nối gọn gàng như vậy trong quá trình thực hành.

### Tại sao lại là mạch in?
Chúng ta sẽ so sánh một chút với mạch Breadboard, một loại mạch mà gần như không ai trong các bạn là không biết.

- Cấu trúc: PCB có cấu trúc như đã nêu ra ở phần khái niệm, còn breadboard là bo mạch có chứa các lỗ được nối dẫn điện, chúng hoàn toàn khác nhau về mặt cấu trúc.
- PCB yêu cầu hàn để tạo kết nối giữa các linh kiện với bo mạch, còn breadboard được sinh ra để dùng dây cắm vì cấu trúc có các lỗ dẫn điện.
- PCB cho chúng ta khả năng tạo ra những loại mạch có độ phức tạp và tính chính xác cao, trong khi đó Breadboard chỉ phù hợp với các dự án đơn giản.
- Vì các linh kiện được hàn chắc vào mạch nên PCB cho ta sự kết nối an toàn và ổn định, trong khi đó nếu các bạn đã từng thực hành trên breadboard, chắc chắn đã từng ít nhất một lần gặp trường hợp dây cắm bị lỏng khiến cho tín hiệu và sự kết nối bị chập chờn.

Tất cả những lý do trên cho ta thấy được PCB chiếm ưu thế trong các dự án dài hạn hoặc cần độ tin cậy cao vì nó mang lại độ bền, độ nhỏ gọn và tính ổn định hiệu quả. Ngoài ra, PCB còn cung cấp cho ta khả năng thiết kế và điều chỉnh cấu trúc mạch một cách chính xác, khiến chúng phù hợp với các dự án phức tạp.

### Ứng dụng
Vì các ưu điểm vượt trội trên, PCB được ứng dụng rất rộng rãi trong mọi lĩnh vực có liên quan đến điện tử.
- Điện tử dân dụng: Đây là lĩnh vực đễ dàng liên hệ nhất vì nó phổ biến và có ở xung quanh chúng ta. Từ các thiết bị di động như điện thoại, radio cầm tay, cho đến máy tính bàn, laptop. Cả các thiết bị giải trí như loa cũng cần có các bo mạch xử lý.
- Công nghiệp: Lĩnh vưc này yêu cầu các bo mạch có khả năng hỗ trợ các thiết bị công suất cao và bền bỉ, PCB là lựa chọn tốt nhất cho điều này. Bao gồm Máy lắp ráp, bộ nguồn, thiết bị đo lường, ...
- Y tế: Đây là nhóm ngành yêu cầu các bo mạch có tiêu chuẩn và độ tin cậy cao do ảnh hưởng đến sức khỏe. Bao gồm máy chụp X-quang, máy đo đường huyết, đo nhịp tim, máy phẫu thuật, ...
- Sản xuất ô tô: Môi trường mà các bo mạch này hoạt động sẽ có yêu cầu về khả năng chịu được độ rung cao. Cần sử dụng một số chất liệu đặc biệt để tạo nên các PCB dùng trong các hệ thống điều khiển và xử lý tuyến đường, hệ thống tự lái, hệ thống định vị, ...

### Cấu tạo:
![[Pasted image 20240509155144.png]]
- Đây là hình vẽ mô phỏng cấu trúc của một mạch in cơ bản, bao gồm 2 lớp đồng ở mặt trên và mặt dưới
- Lớp nền: Chất liệu cơ bản, thường là sợi thủy tinh, cung cấp độ cứng và hỗ trợ cho các lớp khác.
- Lớp đồng: Lớp kim loại dẫn điện, tạo thành các đường dẫn và các điểm hàn cho linh kiện.
- Lớp che phủ: Chất liệu cách điện, bảo vệ các đường dẫn và linh kiện khỏi bụi bẩn, hơi ẩm và các tác nhân bên ngoài. Thường là nhựa thông pha xăng thơm.
- Lỗ khoan: Sử dụng để gắn vít, định vị linh kiện hoặc tạo kết nối giữa các lớp.
- Silk screen: Đánh dấu các đường dẫn và vị trí cần gắn linh kiện.