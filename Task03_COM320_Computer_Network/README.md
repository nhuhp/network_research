## COM320 Computer Network

> Tài liệu: COM320 Computer Networks and Operating Systems
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **13/05/2017**
### Mục lục

[1. Mục đích của Mạng Máy Tính](#mucdichcuamang)
- [1.1. Ứng dụng thương mại](#ungdungthuongmai)
- [1.2. Ứng dụng tại gia](#ungdungtaigia)
- [1.3. Người dùng di động](#nguoidungdidong)
- [1.4. Những vấn đề xã hội](#nhungvandexahoi)
- [1.5. Tính bình đẳng của mạng](#tinhbinhdangcuamang)
[2. Phần cứng của Mạng](#phancung)
- [2.1. Personal Area Networks](#pan)
- [2.2. Local Area Networks](#lan)
- [2.3. Metropolitan Area Networks](#man)
- [2.4. Wide Area Networks](#wan)
[3. Phần mềm của Mạng](#phanmem)
[4. Mô hình tham chiếu](mohinhthamchieu)
[5. Ví dụ về Mạng](#viduvemang)
[6. Chuẩn hóa Mạng](#chuanhoamang)
[7. Đơn vị Metric](#donvimetric)


---

<a name="mucdichcuamang"></a>
#### 1. Mục đích của Mạng Máy Tính
* Mạng máy tính là tập hợp của những hê thống máy tính tự trị, ví dụ như mạng Internet.
* Nó có nhiều ứng dụng:
	+ Ứng dụng thương mại.
	+ Ứng dụng tại gia.
	+ Người dụng di động.
	
* Sử dụng nâng cao:
	+ Các vấn đề xã hội.

<a name="ungdungthuongmai"></a>
##### 1.1. Ứng dụng thương mại
* Nhiều công ty sử dụng mạng và máy tính để chia sẻ *tài nguyên* bằng mô hình **client - server**:

![client-server](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/client-server.png)

* Những mục đích phổ biến khác là để giao tiếp, ví dụ email, VoIP và thương mại điện tử.

<a name="ungdungtaigia"></a>
##### 1.2. Ứng dụng tại gia
* Hộ gia đình thường có nhiều thiết bị kết nối mạng, ví dụ như máy tính, ti vi, được kết nối đến Internet bằng cáp, DSL, kết nối không dây,...
* Người dùng sử dụng mạng để:
	+ Giao tiếp, ví dụ: mạng xã hội.
	+ Sử dụng nội dung, ví dụ: video.
	+ Thực hiện giao dịch, ví dụ: đấu giá.
* Một số ứng dụng mô hình ngang hàng (peer-to-peer), trong đó không có client và server:

![peer-to-peer](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/peer-to-peer.png)

<a name="nguoidungdidong"></a>
##### 1.3. Người dùng di động
* Máy tính bảng, máy tính xách tay và điện thoại thông minh là những thiết bị phổ biến; điểm truy cập Wifi và mạng di động 3G cung cấp kết nối không dây.
* Người dùng di động sử dụng mạng để:
	+ Giao tiếp, ví dụ: tin nhắn.
	+ Sử dụng nội dung, ví dụ: video, Web.
	+ Sử dụng cảm biến, ví dụ: GPS.
* Mạng không dây và mạng di động có mối liên quan nhưng lại khác nhau:

|Mạng không dây|Mạng di động|Ứng dụng tiêu biểu|
|---|---|---|
|No|No|Máy tính để bàn trong văn phòng|
|No|Yes|Máy tính xách tay được sử dụng trong phòng khách sạn|
|Yes|No|Mạng không dây trong các tòa nhà|
|Yes|Yes|Cửa hàng tồn kho với một một tính cầm tay|

<a name="nhungvandexahoi"></a>
##### 1.4. Những vấn đề xã hội
* Tính bình đẳng của mạng - Mạng không giói hạn.
* Quyền sở hữu nội dung, ví dụ: luật bảo vệ quyền tác giả DMCA.
* Nặc danh và kiểm duyệt.
* Bảo mật, ví dụ: theo dõi Web và nhận diện.
* Trộm cắp, ví dụ: botnet và phishing.

<a name="tinhbinhdangcuamang"></a>
##### 1.5. Tính bình đẳng của mạng
* Một số nhà vận hành mạng chặn nội dụng vì lý do riêng.
* Những người phản đối việc này cho rằng, peer-to-peer và các nội dung khác nên được đối xử ngang bằng nhau bới vì chúng chỉ là các bit trong mạng.
* Lập luận cho rằng truyền thông không được phân biệt nội dung hoặc mã nguồn hoặc người cung cấp nội dung này, được gọi là tính bình đẳng của mạng.


<a name="phancung"></a>
#### 2. Phần cứng của Mạng
* Mạng có thể được phân loại theo quy mô sau:

|Quy mô|Loại|
|---|---|
|Lân cận|PAN|
|Tòa nhà|LAN|
|Thành phố|MAN|
|Quốc gia|WAN|
|Thế giới|The Internet|

<a name="pan"></a>
##### 2.1. Personal Area Networks
* Kết nối những thiết bị trong khu vực xung quanh một người.
* Ví dụ : Bluetooth

![bluetooth](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/bluetooth.png)

<a name="lan"></a>
##### 2.2. Local Area Networks
* Kết nối những thiết bị trong khu một căn nhà hoặc văn phòng làm việc.
* Được gọi là mạng doanh nghiệp trong một công ty.
* Phần lớn sử dụng cáp đồng nhưng một vài sử dụng Cáp Quang.

![lan](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/lan.png)

<a name="man"></a>
##### 2.3. Metropolitan Area Networks
* Kết nối những thiết bị trong khu vực đô thị.
* Ví dụ: MAN dựa trên hệ thống truyền hình cáp.

![man](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/man.png)

<a name="wan"></a>
##### 2.4. Wide Area Networks
* Kết nối những thiết bị trong khu vực một quốc qua.
* Ví dụ: WAN kết nối 3 văn phòng chi nhánh.

![wan-1](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/wan-1.png)

* Hệ thống mạng của **ISP** (Internet Service Privider) cũng là một WAN. Khách hàng thuê kết nối từ ISP để sử dụng nó.

![wan-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/wan-2.png)

* Một **VPN** cũng là một WAN nhưng được xây dụng trên những đường liên kết ảo trên Internet.

![wan-3](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/wan-3.png)

<a name="phanmem"></a>
#### 3. Phần mềm của Mạng

<a name="mohinhthamchieu"></a>
#### 4. Mô hình tham chiếu

<a name="viduvemang"></a>
#### 5. Ví dụ về Mạng

<a name="chuanhoamang"></a>
#### 6. Chuẩn hóa Mạng

<a name="donvimetric"></a>
#### 7. Đơn vị Metric


---

### Tài liệu tham khảo:

[1] Lecture 1. Introduction to networks. http://scisweb.ulster.ac.uk/%7Ekevin/com320/notes.htm


---

### Hết
