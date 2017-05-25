##The Physical Layer

> Tài liệu: The Physical Layer
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **25/05/2017**

### Mục lục

[1. Cơ sở lý thuyết về truyền thông dữ liệu](#cosolythuyettruyenthongdulieu)
- [1.1. Tầng Vật lý](#tangvatly)
- [1.1. Tốc độ dữ liệu cực đại của một kênh](#tocdodulieucucdaicuamotkenh)

[2. Phương tiện truyền dẫn có hướng](#phuongtientruyendancohuong)
- [2.1. Dây dẫn](#daydan)
	+ [2.1.1. Cáp xoắn đôi](#capxoandoi)
	+ [2.1.2. Thuật ngữ kết nối](#thuatnguketnoi)
	+ [2.1.3. Cáp đồng trục](#capdongtruc)
	+ [2.1.4. Dây dẫn điện](#daydandien)
	+ [2.1.5. Cáp quang](#capquang)
	
[3. Truyền dẫn không dây]

[4. Vệ tinh truyền thông]

[5. Điều chế số và Ghép kênh]

[6. Mạng điện thoại chuyển mạch công cộng]

[6. Hệ thống điện thoại di động]

[7. Truyền hình cáp]

---


<a name="cosolythuyettruyenthongdulieu"></a>
#### 1. Cơ sở lý thuyết về truyền thông dữ liệu

<a name="tangvatly"></a>
##### 1.1. Tầng Vật lý
* Là nền tảng để xây dựng các tầng khác. 
	- Các đặc tính của dây dẫn, sợi quang, giới hạn không dây mà mạng có thể làm.

![model](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/model.png)	

* Vấn đề chính là gửi cấc bit (số) mà chỉ sử dụng tín hiệu (tương tự).
	- Gọi là điều chế.

![osi-model](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/osi-model.png)	

<a name="tocdodulieucucdaicuamotkenh"></a>
##### 1.2. Tốc độ dữ liệu cực đại của một Kênh
* Định lý Nyquist liên hệ tốc độ dữ liệu với băng thông (B) và số mức tín hiệu (V):

![nyquist](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/nyquist.png)	

* Định lý Shanon liên hệ tốc độ dữ liệu với băng thông (B), cường độ tín hiệu (S) so với độ nhiễu (N):

![shannon](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/shannon.png)	

<a name="phuongtientruyendancohuong"></a>
#### 2. Phương tiện truyền dẫn có hướng

<a name="daydan"></a>
##### 2.1. Dây dẫn

<a name="capxoandoi"></a>
###### 2.1.1. Cáp xoắn đôi

* Rất phổ biến; được sử dụng trong LAN, đường dây điện thoại.
	- Xoắn giảm thiểu tín hiệu bức xạ (nhiễu).
	
![twisted-pair](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/twisted-pair.png)

![utp](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/utp.png)

<a name="thuatnguketnoi"></a>
###### 2.1.2. Thuật ngữ kết nối

* Kết nối **Full-duplex**
	- Được sử dụng trong truyền dẫn cả hai hướng cùng một lúc.
	- Ví dụ: sử dụng cáp xoắn đôi cho mỗi hướng.
* Kết nối **Half-duplex**
	- Cả hai hướng, nhưng không cùng lúc.
	- Ví dụ: người gửi luân phiên nhau trên một Kênh không dây.
* Kết nối **Simplex**
	- Chỉ có một hướng cố định tại mọi thời điểm; không phổ biến.
	
<a name="capdongtruc"></a>
###### 2.1.3. Cáp Đồng trục ("Co-ax")
* Cũng phỗ biến. Được bao bọc tốt hơn và băng thông rộng hơn cho khoảng cách xa hơn và tốc độ cao hơn cáp xoắn đôi.

![coaxial-cable](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/coaxial-cable.png)

<a name="daydandien"></a>
###### 2.1.4. Dây dẫn điện
* Dây dẫn điện là một ví dụ khác về dây dẫn.
	- Tiện lợi khi sử dụng, nhưng khủng khiếp để gửi dữ liệu.
	
![power-lines](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/power-lines.png)

<a name="capquang"></a>
###### 2.1.5. Cáp quang
* Được sử dụng phổ biến cho tốc độ cao và khoảng cách xa.
	- Đường kết nối các ISP với khoảng cách xa, Fiber-to-the-Home.
	- Ánh sáng được truyền trong sợi thủy tinh rất dài, mỏng.
	
![optical-trans-system](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/optical-trans-system.png)

* Một hệ thống truyền dẫn quang có ba thành phần chính:
	- Nguồn phát ánh sáng.
	- Phương tiện truyền dẫn.
	- Bộ tách sóng quang.
* Bản chất quang học của sợi quang.

![fiber-optics](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/fiber-optics.png)

	- (a) Ba ví dụ về một tia ánh sáng từ một sợi silic chiếu đến ranh giới không khí/silic ở các góc khác nhau.
	- (b) Ánh sáng bị giữ lại bởi phản xạ toàn phần trong.

* Sợi quang có băng thông khổng lồ (THz) và hao hụt tín hiệu thấp - nên có tốc độ cao trên khoảng cách dài.

![chart](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/chart.png)

* Single-mode
	- Lõi rất hẹp (10µm) thậm chí ánh sáng không thể dội ra xung quanh.
	- Được sử dụng với laser trong khoảng cách xa, ví dụ 100km.
	
![single-mode](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/single-mode.png)

* Multi-mode
	- Nhiều loại sợi quang khác.
	- Ánh sáng có thể dội lại (lõi 50µm).
	- Được sử dụng với LED cho những đường truyền ngắn và rẻ hơn.
	
![multi-mode](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/multi-mode.png)

* So sánh việc dùng Điốt bán dẫn và LED làm nguồn sáng.

|**Item**|**LED**|**Laser bán dẫn**|
|---|---|---|
|Tốc độ dữ liệu|Thấp|Cao|
|Loại sợi quang|Multi-mode|Multi-mode hoặc Single-mode|
|Khoảng cách|Ngắn|Dài|
|Thời gian tồn tại|Dài|Ngắn|
|Độ nhạy nhiệt độ|Nhỏ|Đáng kể|
|Giá thành|Thấp|Đắt|

* Trong sợi cáp quang, nếu đường kính của sợi bị giảm xuống đến một vài bước sóng ánh sáng, sợi sẽ hoạt động giống như một ống dẫn sóng (wave guide) và ánh sáng chỉ có thể truyền theo đường thẳng mà không bị dội, tạo một sợi single-mode.

	

### Tài liệu tham khảo:

[1] http://scisweb.ulster.ac.uk/~kevin/com320/notes.htm

[2] Lepture 2: Physical Layer. http://scisweb.ulster.ac.uk/~kevin/com320/slides/Chapter2-PhysicalLayer.pptx

---

### Hết
