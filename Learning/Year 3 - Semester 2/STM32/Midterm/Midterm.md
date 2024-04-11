---
_filters: []
_contexts: []
_links: []
_sort:
  field: rank
  asc: false
  group: false
---
# GPIOs
STM32 nhóm các chân GPIOs thành các Port A, B, C, D, ... Mỗi Port chứa 16 chân GPIOs đánh số từ 0 đến 15.
Ví dụ: PA0 -> PA15

### Các thanh ghi của ngoại vi GPIOs:
- 4 thanh ghi thiết lập (32-bit configuration registers):
	GPIOx_MODER, GPIOx_OTYPER, GPIOx_OSPEEDR, GPIOx_PUPDR.
- 2 thanh ghi dữ liệu (32-bit data registers):
	GPIOx_IDR: Phụ trách Input.
	GPIOx_ODR: Phụ trách Output.
- 1 thanh ghi set/reset (32-bit): GPIOx_BSRR.
- 1 thanh ghi locking (32-bit): GPIOx_LCKR.
- 2 thanh ghi alternate function selection (32-bit):
	GPIOx_AFRH  và GPIOx_AFRL.

#### Đối với thanh ghi bit set/reset:
Thanh ghi BSRR có độ lớn gấp đôi thanh ghi ODR, được dùng để set hoặc reset các bit tương ứng trên thanh ghi ODR.

![[Screenshot_20240328_193028.png]]

>[!note]
>Lí do cần sử dụng thanh ghi BSRR: Nếu muốn thay đổi một bit trên thanh ghi ODR, phải thực thi các thao tác: Read -> Modify -> Write.
>-> Chậm và không an toàn.
>BSRR cho phép set hoặc reset các bit trên thanh ghi ODR một cách trực tiếp và nhanh chóng.

### Sơ đồ và nguyên lý hoạt động:
![[Screenshot_20240328_193330.png]]

##### Khi GPIO được cấu hình là input:
- Chức năng output sẽ bị khóa lại.
- Tín hiệu được đưa vào từ I/O pin, việc sử dụng trở kéo lên hay kéo xuống tùy người dùng quy định. Tín hiệu sau đó đi qua khối *TTL Schmitt Trigger*, khối này có tác dụng tăng ngưỡng điện áp so sánh tương ứng với logic 0 và 1, qua đó tăng độ chính xác khi quy đổi. Tín hiệu cuối cùng được đưa vào bit tương ứng trên thanh ghi IDR, sau đó được đọc ra để lấy giá trị input.

##### Khi GPIO được cấu hình là output:
- Ghi giá trị logic vào thanh ghi ODR (có thể thông qua BSRR hoặc không).
- Bit tương ứng trên thanh ghi khi đi qua khối Output control sẽ hoạt động theo một trong hai chế độ:
	- Push-pull mode: 
		Giá trị **0** tương ứng trên ODR sẽ làm n-mos dẫn, p-mos ngắt. Lúc này đầu ra có giá trị **0**.
		Giá trị **1** trên ODR: tương tự.
	- Open drain mode:
		Giá trị **0**: Tương tự push-pull mode.
		Giá trị **1**: Làm ngưng dẫn cả n-mos lẫn p-mos, cho ra trạng thái trở kháng cao.

### Cấu hình chân GPIO:
- Chọn chân GPIO -> Chọn GPIO_Input hoặc GPIO_Output.
- System Core -> GPIO -> Chọn vào chân GPIO vừa cấu hình.
	Tiếp tục chọn trở kéo lên hoặc kéo xuống nếu cần thiết (chỉ dành cho input).

### Một số hàm cần nhớ:
```cpp
HAL_GPIO_ReadPin(GPIOx, GPIO_Pin); // Đọc giá trị chân GPIO;
HAL_GPIO_WritePin(GPIOx, GPIO_Pin, PinState); //Ghi giá trị vào chân GPIO;
```

---
### EXTERNAL INTERRUPT:
Với interrupt, các chương trình phục vụ ngắt sẽ được thực thi khi các sự kiện tương ứng đã được khai báo trước xảy ra, tốc độ đáp ứng nhanh hơn, vi xử lí được sử dụng hiệu quả hơn.

### Sơ đồ và nguyên lý hoạt động:

![[Screenshot_20240328_194735.png]]

#### Nguyên lý hoạt động:
- Để tạo ngắt, line ngắt cần được cấu hình để chọn sườn ngắt thông qua 2 thanh ghi *Falling trigger selection* và *Rising trigger selection*. Sau đó set bit tương ứng của line ngắt trong Interrupt Mask cho phép tạo yêu cầu ngắt.
- Khi có sự thay đổi sườn tín hiệu, một yêu cầu ngắt được tạo ra. Lúc này bit tương ứng của line ngắt trên thanh ghi Pending Request được set lên 1 cho đến khi khối NVIC chấp nhận thực thi hàm callback.

### Các thanh ghi cần lưu ý:
- Interrupt Mask Register: Cho phép có yêu cầu ngắt trên line tương ứng.
- Rising trigger selection register: Được dùng để chọn sườn lên làm tín hiệu kích hoạt ngắt.
- Falling trigger selection register: Được dùng để chọn sườn xuống làm tín hiệu kích hoạt ngắt.
- Pending register: Thanh ghi chờ xử lý ngắt, khi có yêu cầu ngắt được tạo ra trên một line ngắt thì bit tương ứng với line ngắt đó sẽ được set lên 1.

### Các line ngắt:
Ví dụ:
- Line 0 sẽ chung cho tất cả chân Px0 ở tất cả các Port.
- Line 0 nếu đã chọn chân PA0 làm chân ngắt thì tất cả các chân 0 ở các Port khác không được khai báo làm chân ngắt ngoài nữa.

### Mức độ ưu tiên ngắt NVIC:
Có 2 loại ưu tiên ngắt khác nhau là Preemption Priorities và Sub Priorities.
> Giá trị ưu tiên càng thấp -> Mức độ ưu tiên càng cao.

- Mặc định thì ngắt nào có PP cao hơn thì thực hiện trước.
- Cùng PP thì SP cao hơn sẽ thực hiện trước.
- 2 ngắt cùng mức PP lẫn SP thì ngắt nào đến trước sẽ được thực hiện trước.

### Cấu hình:
- Chọn chân GPIO -> Chọn GPIO_EXTI_Pin
- System Core -> GPIO -> Chọn vào chân GPIO vừa cấu hình.
	Ở mục *GPIO mode*: Có thể cấu hình chọn kích hoạt ngắt bằng sườn lên, sườn xuống hoặc cả 2.
	Cấu hình trở kéo lên hoặc kéo xuống nếu cần thiết.
- Chuyển qua tab NVIC, tick vào ô enable để chấp nhận thực thi callback trên interrupt line.

### Một số hàm cần nhớ:
```cpp
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin); // Hàm callback sẽ được gọi khi interrupt xảy ra, cần tái định nghĩa lại trong chương trình chính.
__HAL_GPIO_EXTI_CLEAR_FLAG(GPIO_Pin); //Clear bit trên thanh ghi Pending, loại bỏ việc thực thi lại hàm call back khi interrupt xảy ra lần nữa.
while(HAL_GPIO_ReadPin(GPIOF, GPIO_PIN_15))
	if (HAL_GetTick() - tpre > 5000)
		break;
// Dùng để tránh kẹt nút.
```

---
### SAR ADC
### Sơ đồ khối và nguyên lý hoạt động
![[Pasted image 20240328201142.png]]

#### Nguyên lý hoạt động:
- Tín hiệu analog sẽ được lấy mẫu thông qua tụ, sau đó đưa vào đầu dương của mạch OpAmp.
- Đầu tiên khối SAR Control Circuit sẽ set bit có trọng số lớn nhất của chuỗi bit đầu ra lên 1, sau đó chuyển đổi thành mức điện áp thông qua khối DAC, đưa mức điện áp đó vào đầu âm của mạch OpAmp. 
- Mạch OpAmp sẽ thực hiện phép so sánh 2 giá trị điện áp:
	- Nếu điện áp đầu vào < điện áp chuyển đổi: Set bit ở vị trí tương ứng trong chuỗi bit đầu ra thành 0.
	- Nếu điện áp đầu vào > điện áp chuyển đổi: Set bit ở vị trí tương ứng trong chuỗi bit đầu ra lên 1.
- Tiếp tục với các bit ở vị trí tiếp theo.

Ví dụ điện áp đầu vào là 0.425 V và điện áp tham chiếu (voltage reference) là 1 V, độ phân giải (resolution) của chuỗi bit đầu ra là 8bit. Chuỗi bit đầu ra có thể được tính như sau:
1. Set bit đầu tiên của 8 bit output lên 1 (1000 0000), output qua DAC sẽ là 0.5V.
2. Vì 0.425 < 0.5, set bit đầu tiên của output thành 0 (0000 0000).
3. Set bit tiếp theo lên 1 (0100 0000), output qua DAC sẽ là 0.25V.
4. 0.45 > 0.25, bit tiếp theo của chuỗi bit đầu ra là 1 (0100 000).
5. Set bit tiếp theo lên 1 (0110 0000), output qua DAC sẽ là 0.375V.
4. 0.45 > 0.375, bit tiếp theo của chuỗi bit đầu ra là 1 (0110 000).

Tương tự cho đến bit thứ 8 (cuối cùng), ta được 01101100
#### Một số thuật ngữ:
- V reference: Mức điện áp tham chiếu, tương ứng với giá trị lớn nhất của chuỗi bit đầu ra.
- Resolution: Độ phân giải, dộ lớn của chuỗi bit dầu ra.

### Các chế độ chuyển đổi:
- Single channel, single conversion:
	Kênh đầu vào được lựa chọn chuyển đổi 1 lần, lưu vào thanh ghi kết quả, cờ báo kết thúc quá trình chuyển đổi được bật lên, yêu cầu ngắt sẽ được sinh ra nếu người dùng cho phép ngắt.
	![[Screenshot_20240328_201948.png]]
	
- Single channel, continuos conversion:
	Ở chế độ này, kênh được chọn sẽ được chuyển đổi liên tục mà không cần sự can thiệp của cpu trong mỗi lần chuyển đổi.
	![[Screenshot_20240328_201948 1.png]]

### Cấu hình:
- Analog -> Chọn khối ADC (ADC1) -> Chọn interrupt line tương ứng với chân Analog cần sử dụng.
- Ở tab configuration, giữ các tham số mặc định, chỉ lưu ý một số tùy chọn như:
	- Continuous conversion mode: Enable để bật chế độ continuous conversion.
	- Rank -> Sampling time: Cầu hình thời gian lấy mẫu (càng lâu càng tốt).
- Chọn chân Analog -> chọn khối ADC đã được cấu hình.

### Một số hàm cần nhớ:
```cpp
HAL_ADC_Start(hadc); // Khởi động quá trình chuyển đổi ADC.
HAL_ADC_Stop(hadc); // Kết thúc quá trình chuyển đổi ADC;
AL_ADC_PollForConversion(hadc, Timeout); //Set timeout cho quá trình chuyển đổi ADC nếu thực thi quá lâu;

HAL_ADC_Start_IT(hadc); // Khởi động quá trình chuyển đổi ADC có interrupt;
HAL_ADC_Stop_IT(hadc); // Kết thúc quá trình chuyển đổi ADC có interrupt;

void HAL_ADC_ConvHalfCpltCallback(ADC_HandleTypeDef* hadc) // Hàm call back sẽ được gọi khi interrupt của khối ADC xảy ra;
HAL_ADC_GetValue(hadc); // Lấy giá trị chuyển đổi qua ADC;

```
 ---
# Timer
Timer là một loại ngoại vi được tích hợp trên hầu hết các vi điều khiển, cung cấp cho người dùng nhiều ứng dụng như xác định chính xác một khoảng thời gian, đo - đếm xung đầu vào, điều khiển dạng sóng đầu ra, băm xung...

### Sơ đồ khối và nguyên lý hoạt động:

![[Screenshot_20240328_205523.png]]

Thành phần chính của timer chính là bộ đếm - *CNT counter (16-bit)*, với ngưỡng giới hạn được thiết lập bởi thanh ghi *Auto reload (ARR)(16-bit)*. Counter có thể đếm lên hoặc đêm xuống.
> Người dùng có thể cấu hình cho các thanh ghi CNT, ARR và PSC.
#### Nguyên lý hoạt động:
- Xung clock khi đưa vào bộ đếm được chia bởi bộ chia tần (Prescaler). Xung tín hiệu sau đó tiếp tục được đưa vào bộ đếm CNT, bộ đếm này sẽ tăng hoặc giảm giá trị theo mỗi xung clock đầu vào. Lấy ví dụ trường hợp được cấu hình tăng giá trị, CNT sẽ đếm lên từ 0 (mặc định), hoặc một giá trị nào đó được người dùng cấu hình từ trước. CNT sẽ đếm lên cho đến giá trị của thanh ghi ARR, sau đó bắt đầu lại từ 0.
- Số lần đếm $\times$  chu kỳ của 1 clock cycle (CK_CNT) = Giá trị thời gian tương ứng.

Công thức tổng quát quy đổi:
$$t_{IT} = \frac{(ARR + 1)\times (PSC + 1)}{F_{CK\_PSC}}$$
> [!note]
> Giá trị ARR + 1 vì bộ đếm sẽ đếm từ giá trị ban đầu đến giá trị chặn, sau đó về lại giá trị ban đầu nên cộng thêm 1.
> Giá trị PSC + 1 vì bộ chia tần mặc định cộng thêm 1 vào giá trị trong thanh ghi (để khoảng giá trị khi chia tần số sẽ từ 1 - 65536 thay vì 0 - 65535).

#### Ví dụ:
Thiết kế giá trị PSC và ARR để đạt thời gian đầu ra là 100ms với tần số đầu vào của xung clock là 8MHz:
Chia tần số đầu vào cho 8000, ta được 1kHz, tương ứng với 1ms chu kỳ của xung clock sau khi chia tần.
Nhân thời gian chu kỳ xung clock cho 100, ta được 100ms. 
-> PSC: 7999.
-> ARR: 99.

### Cấu hình:
- Timers -> Chọn bộ Timer -> TIM2.
- Ở tab mode, mục Clock Source, chọn Internal Clock. Sau  đó chuyển sang menu Clock Configuration để kiểm tra gía trị nguồn Clock (thường là HSI).
- Quay lại menu Pinout & Configuration -> Timers -> TIM2 -> Tab configuration -> Parameter Settings. Điều chỉnh giá trị PSC, Counter Mode, Counter Period(ARR) tương ứng.
- Chuyển sang tab NVIC Settings -> Enable ngắt. Ngắt sẽ được gọi mỗi khi bộ đếm quy đổi thành công 1 giá trị thời gian.

### Một số hàm cần nhớ:
```cpp
HAL_TIM_Base_Start_IT(&htim2); // Khởi tạo bộ đếm timer với chế đọ interrupt ở TIM2.
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim); // Hàm call back được gọi mỗi khi bộ đếm quy đổi thành công 1 giá trị thời gian.
```