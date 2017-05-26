##The Physical Layer

> Tài liệu: The Physical Layer
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **26/05/2017**

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
	
[3. Truyền dẫn không dây](#truyendankhongday)
- [3.1. Phổ điện từ](#phodientu)
- [3.2. Truyền dẫn vô tuyến](#truyendanvotuyen)
- [3.3. Truyền dẫn vi sóng](#truyendanvisong)
- [3.4. Truyền dẫn ánh sáng](#truyendananhsang)
- [3.5. Không dây vs Có dây/Cáp Quang](#khongdayvscoday)

[4. Vệ tinh liên lạc](#vetinhlienlac)
- [4.1. Các loại vệ tinh](#cacloaivetinh)
- [4.2. Vệ tinh Địa tĩnh (GEO)](#vetinhdiatinh)
- [4.3. Vệ tinh quỹ đạo thấp](#vetinhquydaothap)
- [4.4. Vệ tinh và cáp quang](#vetinhvacapquang)

[5. Điều chế số và Ghép kênh]

[6. Mạng điện thoại chuyển mạch công cộng]

[7. Hệ thống điện thoại di động]

[8. Truyền hình cáp]

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

* Mạng sợi quang.
	- Một vòng sợi quang với nhiều repeater hoạt động.
	
![fiber-optic-network](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/fiber-optic-network.png)

* So sánh các thuộc tính của dây dẫn và cáp quang.

|**Thuộc tính**|**Dây dẫn**|**Cáp quang**|
|---|---|---|
|Khoảng cách|Ngắn (vài trăm mét)|Dài (Vài chục km)|
|Băng thông|Trung bình|Rất cao|
|Giá thành|Không đắt|Không rẻ|
|Độ tiện lợi|Dễ sử dụng|Ít dễ hơn|
|Bảo mật|Dễ bị nghe lén|Khó bị nghe lén|

* Cáp quang dưới nước.
	- Những loại cáp quang này chỉ dày khoảng 3 inch.
	- Chỉ chứa một vài sợi quang, và có tổng dung lượng truyền từ 40Gbps đến 10Tbps, và độ trễ gần đến tốc độ ánh sáng và chỉ trong một mili giây.
	- Một số cáp có khả năng gửi 40Gbps trên một sợi quang duy nhất.
	- Các Switch quang Graphene mở rộng tổng dung lượng của cáp ngầm (và các Router đầu cuối) lên khoảng petabit và exabit mỗi giây.
	
	![under-water-fiber-cable](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/under-water-fiber-cable.png)
	 
	- Trong hình trên:
		+ (1): polyethylene
		+ (2): băng lụa
		+ (3): dây thép dẹt
		+ (4): lớp nhôm chống thấm nước
		+ (5): polycarbonate
		+ (6): ống đồng hoặc nhôm
		+ (7): sáp xăng dầu
		+ (8): sợi quang

* Hệ thống cáp dưới nước.

![under-water-cables](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/under-water-cables.png)

* DDOS ở thời gian thực.

![ddos](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/ddos.png)

<a name="truyendankhongday"></a>
#### 3. Truyền dẫn không dây

<a name="phodientu"></a>
##### 3.1. Phổ điện từ
* Các dải sóng khác nhau sẽ có cách sử dụng khác nhau.
	- Sóng vô tuyến (Radio): phát sóng diện rộng.
	- Hồng ngoại/Ánh sáng: đường ngắm.
	- Vi sóng (Microwave): LAN và 3G/4G.

![electromagnetic-spectrum](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/electromagnetic-spectrum.png)

* Để quản lý giao thoa, phổ được phân chia cẩn thận, và việc sử dụng nó được quản lý và cấp phép, ví dụ, được bán đấu giá.

![frequency-allocations](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/frequency-allocations.png)

* May mắn thay, cũng những dải tần không cấp phép ("ISM"):
	- Miễn phí sử dụng ở công suất thấp: các thiết bị quản lý nhiễu.
	- Sử dụng rộng rãi cho mạng: WiFi, Bluetooth,Zigbee,vv.

![ism-band](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/ism-band.png)

<a name="truyendanvotuyen"></a>
##### 3.2. Truyền dẫn vô tuyến
* Tín hiệu vô tuyến xuyên qua các tòa nhà tốt và lan truyền trong khoảng cách dài với sự hao hụt trên đường dẫn.
* Trong các dải tần VLF, LF và MF, sóng vô tuyến truyền theo độ cong của Trái Đất.

![vlf-lf-mf](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/vlf-lf-mf.png)

* Trong dải tần HF, sóng vô tuyến phóng lên khỏi tầng điện ly.

![hf](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/hf.png)

* Khi các electron di chuyển, chúng tạo ra các sóng điện từ có thể truyền qua không gian (kể cả trong chân không). Số lần dao động trong 1 giây của một sóng gọi là tần số của nó, f, và được đo bằng Hertz (Hz).
* Trong truyền dẫn không dây, một số sóng bị khúc xạ ở tầng không khí thấp và truyền đi lâu hơn sóng có hướng.
* Những sóng trễ có thể vượt qua khỏi pha với sóng có hướng và có thể gây hủy tín hiệu. Hiện tượng này gọi là **multipath fading**.

![reflected-path](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/reflected-path.png)

<a name="truyendanvisong"></a>
##### 3.3. Truyền dẫn vi sóng
* Vi sóng có nhiều băng thông và được sử dụng rộng rãi trong nhà (WiFi) và ngoài trời (3G, vệ tinh).
	- Tín hiệu bị suy giảm/phản xạ bởi các vật thể hàng ngày.
	- Cường độ khác nhau tùy vào khác khả năng di động do multipath fading.
	
![microwave-transmission](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/microwave-transmission.png)

<a name="truyendananhsang"></a>
##### 3.4. Truyền dẫn ánh sáng
* Ánh sáng nhìn thấy (không dùng sợi quang) có thể được sử dụng cho kết nối.
	- Ánh sáng có tính định hướng cao, cao nhiều băng thông.
	- Dùng trong LED/máy ảnh và laser/bộ dò ánh sáng.

![light-transmission](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/light-transmission.png)
	
<a name="khongdayvscoday"></a>
##### 3.5. Không dây vs Có dây/Cáp Quang
* Không dây:
	- Ưu:
		+ Dễ sử dụng và không đắt để triển khai.
		+ Hỗ trợ khả năng di động.
		+ Hỗ trợ khả năng phát sóng.
	-Hạn chế:
		+ Truyền tải có sự can thiệp và chịu sự quản lý.
		+ Do cường độ tín hiệu nên tốc độ dữ liệu thay đổi đáng kể.
* Có dây/Cáp quang:
	- Ưu:
		+ Dễ dàng lắp đặt một tốc độ dữ liệu cố định qua những đường kết nối điểm-điểm (point-to-point).
	- Hạn chế:
		+ Có thể đắt để triển khai, đặc biệt là qua những khoảng cách xa.
		+ Không sẵn sàng hỗ trợ khả năng di động hay phát sóng.

<a name="vetinhlienlac"></a>
#### 4. Vệ tinh liên lạc
* Vệ tinh có hiệu quả trong phân phối phát sóng và liên lạc mọi lúc/mọi nơi.

![satellites-1](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/satellites-1.png)

* Một vệ tinh liên lạc có thể xem là một repeater vi sóng cỡ lớn trên bầu trời. Có chứa vài *Transponder* , mỗi cái có thể lắng nghe một phần của phổ, khuếch đại tín hiệu đến và phát sóng lại nó ở tần số khác để tránh nhiễu với tín hiệu đến.
* Việc tiếp nhận và truyền lại sóng được thực hiện bởi một Transponder. Một Transponder trên một vệ tinh Địa tĩnh có khả năng xử lý khoảng 5000 kênh thoại hoặc dữ liệu cùng một lúc. Một vệ tinh điển hình có 32 Transponder.
* Transponder hoạt động trên một bước sóng hoặc dải tần số cụ thể. Vệ tinh liên lạc hoạt động trên 3 dài tần chính: C, Ku và Ka. C là dải tần đầu tiên được sử dụng, có bước sóng dài, và đòi hỏi phải có một anten lớn. Ku là dải tần được sử dụng trong hầu hết các hệ thống VSAT hiện tại. Ka là dải tần mới được chỉ định nhưng chưa được sử dụng rộng rãi. Trong ba dải tần thì nó có bước sóng nhỏ nhất và sử dụng anten nhỏ nhất.

![satellites-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/satellites-2.png)

* Những dải tần chính của vệ tinh.

|**Dải tần**|**Tần số dưới**|**Tần số trên**|**Băng thông**|**Hạn chế**|
|---|---|---|---|---|
|L|1.5 GHz|1.6 GHz|15 MHz|Băng thông thấp; chật|
|S|1.9 GHz|2.2 GHz|70 MHz|Băng thông thấp; chật|
|C|4.0 GHz|6.0 GHz|500 MHz|Nhiễu trên mặt đất|
|Ku|11 GHz|14 GHz|500 MHz|Mưa|
|Ka|20 GHz|30 GHz|3500 MHz|Mưa;Giá thành thiết bị|

<a name="cacloaivetinh"></a>
##### 4.1. Các loại vệ tinh
* Vệ tinh và các thuộc tính của chúng thay đổi theo độ cao:
	- Địa tĩnh - Geostationary (GEO).
	- Quỹ đạo trung bình - Medium-Earth Orbit (MEO).
	- Quỹ đạo thấp - Low-Earth Orbit (LEO).

![kinds-of-satellites](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/kinds-of-satellites.png)

<a name="vetinhdiatinh"></a>	
##### 4.2. Vệ tinh Địa tĩnh (GEO)
- [4.3. Vệ tinh quỹ đạo thấp](#vetinhquydaothap)
- [4.4. Vệ tinh và cáp quang](#vetinhvacapquang)



		
### Tài liệu tham khảo:

[1] http://scisweb.ulster.ac.uk/~kevin/com320/notes.htm

[2] Lepture 2: Physical Layer. http://scisweb.ulster.ac.uk/~kevin/com320/slides/Chapter2-PhysicalLayer.pptx

---

### Hết
