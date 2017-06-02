## The Data Link Layer

> Tài liệu: The Data Link Layer
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **02/06/2017**

### Mục lục

[1. Lớp Data Link](#lopdatalink)

[2. Các vấn đề thiết kế Lớp Data Link](#cacvandethietkelopdatalink)
- [2.1. Frame](#frame)
- [2.2. Các dịch vụ có thể có](#cacdichvucotheco)
- [2.3. Cách thức đóng frame](#cachthucdongframe)
	+ [2.3.1. Bộ đếm Byte](#bodembyte)
	+ [2.3.2. Cơ chế Byte Stuffing](#cochebytestuffing)
	+ [2.3.3. Cơ chế Bit Stuffing](#cochebitstuffing)		
- [2.4. Kiểm soát lỗi](#kiemsoatloi)
- [2.5. Kiểm soát luồng](#kiemsoatluồng)
	
[3. Phát hiện lỗi và Sửa lỗi](#phathienloivasualoi)

[4. Các giao thức Data Link sơ cấp](#cacgiaothucdatalinksocap)

[5. Giao thức Sliding Window](#giaothucslidingwindow)

[6. Các giao thức Data Link ví dụ](#cacgiaothucdatalinkvidu)

---

<a name="lopdatalink"></a>
### Lớp Data Link

![data-link-layer-1](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/data-link-layer-1.png)

* Chịu trách nhiệm vận chuyển các frame thông tin qua một đường kết nối duy nhất.
	- Xử lý các lỗi truyền dẫn và điều chỉnh luồng dữ liệu.

![data-link-layer-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/data-link-layer-2.png)

<a name="cacvandethietkelopdatalink"></a>
### 2. Các vấn đề thiết kế Lớp Data Link
* Frame
* Các dịch vụ có thể có
* Cách thức đóng Frame
* Kiểm soát Lỗi.
* Kiểm soát luồng

![bit-transmission](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/bit-transmission.png)

<a name="frame"></a>
#### 2.1. Frame
* Lớp Data Link nhận các gói tin (**packet**) từ lớp Network, và đóng gói chúng thành các Frame và gửi chúng đi bằng cách sử dụng lớp Physical; Quá trình nhận thì ngược lại.

![frame](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/frame.png)

<a name="cacdichvucotheco"></a>
#### 2.2. Các dịch vụ có thể có
* Dịch vụ vô hướng không có thông báo nhận (Unacknowledged connectionless service)
	- Frame được gửi mà không tồn tại kết nối/phục hồi Lỗi.
	- Ví dụ là Ethernet.
* Dịch vụ vố hướng có thông báo nhận (Acknowledged connectionless service)
	- Frame được gửi đi, có thể truyền lại nếu cần.
	- Ví dụ là 802.11
* Dịch vụ kết nối có hướng có thông báo nhận (Acknowledged connection-oriented service)
	- Kết nối được thiết lập
	- Hiếm

<a name="cachthucdongframe"></a>
#### 2.3. Cách thức đóng Frame
* Bộ đếm Byte.
* Các byte cờ với cơ chế **Byte Stuffing**.
* Các bit cờ với cơ chế **Bit Stuffing**.
* Các vi phạm mã hóa lớp Physical.
	- Sử dụng ký hiệu không phải là dữ liệu (non-data) để biễu diễn frame.

<a name="bodembyte"></a>	
##### 2.3.1. Bộ đếm Byte	
* Frame bắt đầu với bộ đếm số lượng các byte trong nó.
	- Đơn giản, nhưng khó tái đồng bộ sau khi bị lỗi.
	
	![byte-count](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/byte-count.png)

<a name="cochebytestuffing"></a>		
##### 2.3.2. Cơ chế Byte Stuffing
* Các byte cờ đặc biệt phân tách frame; sự xuất hiện của các cờ trong dữ liệu cần phải nhét (escaped).
	- Dài hơn, nhưng dễ dàng tái đồng bộ sau khi lỗi.
	
	![byte-stuffing](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/byte-stuffing.png)

<a name="cochebitstuffing"></a>		
##### 2.3.3. Cơ chế Bit Stuffing	
* Cơ chế Stuffing được thực hiện ở múc bit:
	- Cờ Frame có 6 bit 1 liên tiếp (không hiển thị).
	- Khi truyền, sau 5 bit 1 trong dữ liệu, một bit 0 được thêm vào.
	- Khi nhận, một bit 0 sau 5 bit 1 sẽ bị xóa.
	
	![bit-stuffing](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/bit-stuffing.png)

<a name="kiemsoatloi"></a>			
#### 2.4. Kiểm soát lỗi
* Kiểm soát lỗi sửa chữa các frame nhận được có lỗi.
	- Yêu cầu các lỗi được phất hiện ở máy nhận.
	- Thường được truyền lại các frame không thông báo nhận.
	- Bộ đếm thời gian bảo vệ các thông báo nhận bị mất.
	
<a name="kiemsoatluong"></a>			
#### 2.5. Kiểm soát luồng
* Ngăn máy gửi nhanh gửi nhanh hơn máy nhận chậm.
	- Máy nhận gửi phản hồi về dữ liệu mà nó có thể chấp nhận.
	- Ít có ở lớp Physical vì NIC chạy ở "tốc độ dây".
		+ Máy nhận có thể lấy dữ liệu nhanh như nó được gửi đi.


---

### Tài liệu tham khảo:

[1] The Data Link Layer. http://scisweb.ulster.ac.uk/~kevin/com320/slides/Chapter3-DataLinkLayer.pptx

---

### Hết
