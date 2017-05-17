## COM320 Computer Network

> Tài liệu: COM320 Computer Networks and Operating Systems
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **17/05/2017**
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
- [3.1. Các lớp giao thức](#caclopgiaothuc)
- [3.2. Vấn đề thiết kế cho các lớp](#vandethietkechocaclop)
- [3.3. Kết nối có hướng và Phi kết nối](#ketnoicohuongvaphiketnoi)
- [3.4. Các dịch vụ sơ cấp](#cacdichvusocap)
- [3.5. Quan hệ giữa dịch vụ và giao thức](#quanhegiuadichvuvagiaothuc)

[4. Mô hình tham chiếu](#mohinhthamchieu)
- [4.1. Mô hình tham chiếu OSI](#mohinhthamchieuosi)
- [4.2. Mô hình tham chiếu TCP/IP](#mohinhthamchieutcpip)
- [4.3. Mô hình sử dụng trong tài liệu này](#mohinhsudungtrongtailieunay)
- [4.4. Nhận xét mô hình OSI và TCP/IP](#nhanxetmohinhosivatcpip) 

[5. Ví dụ về Mạng](#viduvemang)
- [5.1. Internet](#internet)
- [5.2. Mạng điện thoại di động 3G](#mangdienthoaididong3g)
- [5.3. Mạng LAN không dây](#manglankhongday)
- [5.4. RFID và mạng cảm biến](#rfidvamangcambien)
- [5.5. Peer to Peer](#peertopeer)

[6. Chuẩn hóa Mạng](#chuanhoamang)

[7. Bảo mật](#baomat)

[8. Đơn vị Metric](#donvimetric)


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

* Hệ thống mạng của **ISP** (Internet Service Provider) cũng là một WAN. Khách hàng thuê kết nối từ ISP để sử dụng nó.

![wan-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/wan-2.png)

* Một **VPN** cũng là một WAN nhưng được xây dụng trên những đường liên kết ảo trên Internet.

![wan-3](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/wan-3.png)

<a name="phanmem"></a>
#### 3. Phần mềm của Mạng
* Các lớp giao thức.
* Vấn đề thiết kế cho các lớp.
* Kết nối có hướng và Phi kết nối.
* Các dịch vụ sơ cấp.
* Quan hệ giữa dịch vụ và giao thức.

<a name="caclopgiaothuc"></a>
#### 3.1. Các lớp giao thức
* Phân lớp các giao thức là phương pháp cấu trúc chính được dùng để chia chức năng mạng.
	+ Mỗi giao thức được xem như nói đang nói chuyện với nhau.
	+ Mỗi lớp giao tiếp chỉ bằng cách sử dụng các lớp ở dưới.
	+ Mỗi dịch vụ lớp dưới được truy cập bằng một "**interface**".
	+ Ở dưới cùng, thông tin được vận chuyển bằng cách phương tiện truyền dẫn.
	
	![protocol-layer](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/protocol-layer.png)

* Ví dụ: Kiến trức "Nhà triết học - Thông dịch viên - Thư ký". Mỗi giao thức tại mỗi lớp khác nhau sẽ đáp ứng một mục đích khác nhau.
	
![architecture](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/architecture.png)
	
* Mỗi lớp sẽ đóng vào gói tin một **header** riêng cho lớp đó (chứa thông tin điều khiển) để vận chuyển và sẽ gỡ bỏ header đó ở bên nhận.

![header](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/header.png)

* Mỗi lớp cũng có thể chia tách và gộp gói tin, vv.

<a name="vandethietkechocaclop"></a>
##### 3.2. Vấn đề thiết kế cho các lớp
* Mỗi lớp giải quyết một vấn đề cụ thể nhưng phải có cơ chế để giải quyết các vấn đề thiết kế lặp lại.

|Vấn đề|Cơ chế ví dụ ở những lớp khác nhau|
|---|---|
|Đáng tin cậy nhưng Thất bại|Code xác định/sửa lỗi (§3.2,3,3). Định tuyến xung quanh thất bại|
|Sự tăng trưởng và tiến hóa Mạng|Giải quyết (§5.6) và Đặt tên (§7.1),Phân lớp giao thức (§1.3)|
|Phân bổ tài nguyên như Băng thông|Đa truy cập (§4.2), Kiểm soát tắc nghẽn (§5.3, 6.3)|
|An ninh chống lại các mối đẹ dọa|Bảo mật thông tin (§8.2, 8.6), Xác thực các bên giao tiếp (§8.7)|

<a name="ketnoicohuongvaphiketnoi"></a>
##### 3.3. Kết nối có hướng và Phi kết nối
* Một lớp có thể cung cấp 2 loại kết nối:
	+ Kết nối có hướng, phải được thiết lập để sử dụng liên tục (và ngừng hoạt động sau khi sử dụng), ví dụ: gọi điện thoại.
	+ Phi kết nối, thông tin được xử lý riêng biệt, ví dụ: phân phối bưu phẩm.

![2-conn](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/2-conn.png)

##### Ghép kênh
* Nhiều thiết kế mạng, dựa trên nhu cầu ngắn hạn của các host, chia sẻ băng thông một cách tự động thay vì gắn cho mỗi host một phần băng thông cố định mà nó có thể được sử dụng hoặc không.
* Thiết kế này gọi là *Ghép kênh thống kê*.

![multiplexing](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/multiplexing.png)

##### Switching
* **Store & Forward Switching**: Được sử dụng trên mạng gói, các node trung gian nhận được tin đầy đủ, sau đó mới gửi chúng đi đến node kế tiếp.
* **Cut-through Switching**: là một phương pháp dùng trong hệ thống chuyển mạch gói, trong đó Switch bắt đầu forward một frame (hoặc packet) trước khi nhận toàn bộ frame, thường là ngay khi địa chỉ đích được xử lý. So sánh với *Store and Forward*, kỹ thuật này làm giảm độ trễ qua Switch, nhưng giảm độ tin cậy, các frame hỏng có thể bị forward.
* **Adaptive Switching**: tự động chọn giữa *Cut-through* và *Store and Forward* giữa trên điều kiện mạng hiện thời.

###### Trễ và Mất gói tin xảy ra như thế nào?
* Gói tin đợi trong bộ đếm của Router:
	+ Tỷ lệ gói tin đến vượt quá khả năng đầu ra.
	+ Gói tin đợi, chờ đến lượt.

![delay](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/delay.png)

###### 4 nguồn gây trễ gói tin

![4-delay](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/4-delay.png)

* **d_proc**: xử lý node.
	+ Kiểm tra bit lỗi.
	+ Chọn đường ra.
	+ Thông thường < msec.

* **d_queue**: độ trễ hàng đợi.
	+ Thời gian chờ tại đầu ra. 
	+ Phụ thuộc vào mức độ tắc nghẽn của Router.
	
* **d_trans**: độ trễ do truyền tải.
	+ L: chiều dài gói tin (bits)
	+ R: băng thông đường truyền (bps)
	+ *d_trans = L/R*
	
* **d_prop**: độ trễ do lan truyền.
	+ d: chiều dài vật lý của đường truyền.
	+ s: tốc độ lan truyền trong môi trường (~ 2x10^8 m/sec)
	+ *d_prop = d/s*

<a name="cacdichvusocap"></a>
##### 3.4. Các dịch vụ sơ cấp
* Một dịch vụ được cung cấp cho các lớp trên như những phương thức sơ cấp.
* Ví dụ giả thuyết về những dịch vụ sơ cấp mà có thể cung cấp dịch vụ stream đáng tin cậy (kết nối có hướng):

|Phương thức sơ cấp|Ý nghĩa|
|---|---|
|LISTEN|Chặn Chờ kết nối đến|
|CONNECT|Thiết lập một kết nối với một peer đang chờ|
|ACCEPT|Chấp nhận kết nối đến từ một peer|
|RECEIVE|Chặn Chờ thông điệp đến|
|SEND|Gửi thông điệp cho peer|
|DISCONNECT|Hủy kết nối|

* Ví dụ giả thuyết về sử dụng những phương thức sơ cấp này trong tương tác client-server:

![primitives-client-server](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/primitives-client-server.png)

<a name="quanhegiuadichvuvagiaothuc"></a>
##### 3.5. Quan hệ giữa dịch vụ và giao thức
* Tóm tắt:
	+ Một lớp cung cấp một dịch vụ cho lớp phía trên. [theo chiều đứng].
	+ Một lớp giao tiếp với lớp ngang với nó bằng một giao thức [theo chiều ngang].
	
	![service-protocol](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/service-protocol.png)
* *Dịch vụ* và *Giao thức* là những khái niệm khác nhau. Một dịch vụ là một tập hợp các phương thức sơ cấp (hoạt động) mà một lớp cung cấp cho lớp phía trên nó.
* Dịch vụ xác định những hoạt động mà lớp cần chuẩn bị để thực hiện thay cho người dùng, nhưng nó không cho biết về cách những hoạt động này được thực hiện như thế nào.

<a name="mohinhthamchieu"></a>
#### 4. Mô hình tham chiếu
* Mô hình tham chiếu mô tả những lớp có trong một kiến trúc mạng.
	+ Mô hình tham chiếu OSI.
	+ Mô hình tham chiếu TCP/IP.
	+ Mô hình sử dụng trong tài liệu này.
	+ Nhận xét mô hình OSI và TCP/IP.

<a name="mohinhthamchieuosi"></a>
##### 4.1. Mô hình tham chiếu OSI
* Mô hình có nguyên tắc, theo tiêu chuẩn quốc tế, gồm 7 tầng, để kết nối với các hệ thống khác nhau.

|  | Tên tầng | Chức năng|
|---|---|---|
|7|Application|Cung cấp những chức năng cần thiết cho người sử dụng|
|6|Presentation|Chuyển đổi định dạng dữ liệu|
|5|Session|Quản lý phiên làm việc|
|4|Transport|Cung cấp giao nhận end-to-end|
|3|Network|Gửi gói tin qua nhiều liên kết|
|2|Data link|Gửi frame Thông tin|
|1|Physical|Gửi bit tín hiệu|

<a name="mohinhthamchieutcpip"></a>
##### 4.2. Mô hình tham chiếu TCP/IP
* Mô hình 4 tầng có nguồn gốc từ thực nghiệm; bỏ qua một số tầng OSI và sử dụng IP (Internet Protocol) làm tầng Network.

![tcp-ip](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/tcp-ip.png)

<a name="mohinhsudungtrongtailieunay"></a>
##### 4.3. Mô hình sử dụng trong tài liệu này.
* Dựa trên mô hình TCP/IP, nhưng có thêm tầng *Physical* và xem xét *Internet protocols* kỹ hơn.

![thismodel](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/thismodel.png)

<a name="nhanxetmohinhosivatcpip"></a>
##### 4.4. Nhận xét mô hình OSI và TCP/IP
* OSI:
	+ Ưu điểm: Mô hình có tầm ảnh hưởng với những khái niệm rõ ràng.
	+ Hạn chế: Mô hình, các giao thức đều lún sâu vào các chính sách và độ phức tạp.
* TCP/IP:
	+ Ưu điểm: Các giao thức có kết quả tốt, làm việc hiệu quả.
	+ Mô hình yếu có nguồn gốc sau thực tế từ các giao thức.

<a name="viduvemang"></a>
#### 5. Ví dụ về Mạng
* Internet
* Mạng điện thoại di động 3G
* Mạng LAN không dây
* RFID và mạng cảm biến

<a name="internet"></a>
##### 5.1. Internet
* Trước Internet là **ARPANET**, một hệ thống mạng chuyển mạch phân cấp, dựa trên ý tưởng của Baran.

![arpanet](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/arpanet.png)

* Internet trước đây sử dụng NSFNET(1985-1995) làm xương sống; các trường đại học kết nối để đi Internet.

![nsfnet](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/nsfnet.png)

* Internet hiện đại thì phức tạp hơn nhiều:
	+ Các mạng ISP được xem như xương sống của Internet.
	+ Các ISP kết nối để trao đổi lưu lượng tại các IXP.
	+ Mỗi Router có thể chuyển mạch gói tin.
	+ Giữa các mạng, việc trao đổi lưu lượng được thiết lập bởi các hiệp định thương mai.
	+ Khách hàng kết nối tại phần Rìa mạng bằng nhiều phương tiện - Cáp, DSL, Fiber-to-the-home, mạng không dây 3G/4G, Dial-up.
	+ Các trung tâm dữ liệu tập trung nhiều server ("the cloud").
	+ Hầu hết các lưu lượng là nội dụng từ các trung tâm dữ liệu (đặc biệt là video).
	+ Kiến trúc mạng tiếp tục cải tiến.
	
* Kiến trúc của Internet

![internet-architecture](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/internet-architecture.png)

* Mạng lưới của Nhà Cung cấp Dịch vụ Internet (ISP - Internet Service Provider) có thể trong phạm vi khu vực, quốc gia hoặc quốc tế.
* Nếu một gói tin được định tuyến đến một host được ISP  trực tiếp phục vụ, gói tin đó sẽ đi qua vùng xương sống và đi đến host đó.
* Còn không, nó sẽ phải được bàn giao qua những ISP khác. Các ISP kết nối với mạng lưới của họ để trao đổi lưu lượng tại các IXP (Internet eXchange Points).

![isp](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/isp.png)

<a name="mangdienthoaididong3g"></a>
##### 5.2. Mạng điện thoại di động 3G
* Mạng 3G được dựa trên các tế bào sóng trong không gian; mỗi tế bào cung cấp dịch vụ không dây cho các thiệt bị di động trong vùng thông qua một trạm gốc.


![cell](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/cell.png)

* Trạm gốc kết nối với hệ thống mạng lõi để tìm kiếm các thiết bị di động khác và gửi dữ liệu về mạng điện thoại và Internet.

![basestation](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/basestation.png)

* Khi thiết bị di động di chuyển, các trạm gốc sẽ bàn giao cho các trạm tiếp theo và mạng lưới sẽ theo dõi vị trí của họ.

![move-mobiles](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/move-mobiles.png)

<a name="manglankhongday"></a>
##### 5.3. Mạng LAN không dây
* Trong chuẩn 802.11, các client giao tiếp thông qua một AP (Access Point) được nối dây với phần còn lại của mạng.

![access-point](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/access-point.png)

* Tín hiệu trong băng tần ISM 2.4Ghz khác nhau về cường độ do nhiều tác động, chẳng hạn như sự biến dạng nhiều đường đi do phản xạ - đòi hỏi phải có những thiết kế truyền phức tạp, ví dụ như OFDM.

![multipath](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/multipath.png)

* Việc phát sóng có thể can thiệp lẫn nhau, và vùng phủ sóng có thể chồng lên nhau - CSMA (Carrier Sense Multiple Access) được sử dụng.

![radio-broadcast](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/radio-broadcast.png)

<a name="rfidvamangcambien"></a>
##### 5.4. RFID và mạng cảm biến
* Những đối tượng trong mạng UHF RFID:
	+ Tags (miếng dán không sử dụng pin) được đặt trên vật thể.
	+ Máy đọc gửi tín hiệu mà tags phản chiếu để giao tiếp.
	
	![rfid](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/rfid.png)
	
* Mạng cảm biến lan truyền các thiết bị nhỏ trên một khu vực:
	+ Các thiết bị gửi dữ liệu về bộ thu thông qua công nghệ không dây.
	
	![sensor-network](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/sensor-network.png)

<a name="peertopeer"></a>
##### 5.5. Peer to Peer
* Mạng máy tính Peer-to-peer (viết tắt là P2P) là mạng mà mỗi máy tính trong máy có thể đóng vai trò client và server, cho phép chia sẻ truy cập đến nhiều nguồn tài nguyên như là các tập tin, các thiết bị ngoại vi và các cảm biến mà không cần đến một server trung tâm.
* Mạng P2P có thể được sử dụng để chia sẻ âm thanh, video, dữ liệu hoặc bất cứ thứ gì ở định dạng số.
* Nhiều hệ thống peer-to-peer, chẳng hạn như BitTorrent, không có bất kỳ trung tâm dữ liệu nào. Thay vào đó, mỗi người dùng sẽ duy trì cơ sở dữ liệu riêng và cung cấp một danh sách những người ở gần đó là thành viên của hệ thống.
* Peer là những người tham gia có quyền bình đẳng như nhau. Mỗi máy tính trong mạng được gọi là một node.
* Chủ sở hữu của mỗi máy tính trong mạng P2P sẽ dành một phần tài nguyên máy tính - chẳng hạn như tốc độ xử lý, vùng lưu trữ hoặc băng thông - để cung cấp trực tiếp cho người tham gia khác mà không cần phải có sự phối hợp giữa các server hay các host.
* Với mô hình này, mỗi người vừa là nhà cung cấp, vừa là người tiêu thụ tài nguyên. Ngược lại ở mô hình client - server, nơi mà server chỉ cung cấp (gửi) và client chỉ tiêu thụ (nhận).

<a name="chuanhoamang"></a>
#### 6. Chuẩn hóa Mạng
* Các tiêu chuẩn xác định những gì cần thiết cho khả năng tương tác.
* Một số trong rất nhiều tiêu chuẩn:
||Lĩnh vực|Ví dụ|
|---|---|---|
|ITU|Viễn thông|G.992,ADSL,H.264,MPEG4|
|IEEE|Truyền thông|802.3,Ethernet,802.11,Wifi|
|IETF|Internet|RFC 2616, HTTP/1.1,RFC 1034/1035,DNS|
|W3C|Web|tiêu chuẩn HTML5, tiêu chuẩn CSS|

<a name="baomat"></a>
#### 7. Bảo mật
* Chúng ta bắt đầu từ đâu?
* Ví dụ: Phishing
* Giả mạo Thông tin có nguồn gốc từ một bên đáng tin cây, ví dụ, ngân hàng của bạn, cố lừa bạn để lộ những thông tin nhạy cảm như số tài khoản thẻ tín dụng.
* Những công cụ tấn công: DDoS, Passwords, Hashing, PGP, Encryption, Cryptography,...
* Lĩnh vực an ninh mạng:
	+ Kẻ xấu có thể tấn công mạng máy tính như thế nào.
	+ Làm thế nào để chúng ta có thể bảo vệ mạng không bị tấn công.
	+ Cách thiết kế kiến trúc mạng để miễn dịch với các cuộc tấn công.
* Ban đầu Internet không được thiết kế với (nhiều) bảo mật như người ta cứ nghĩ.
	+ Tầm nhìn ban đầu: "Một nhóm người dùng sự tin tưởng lẫn nhau, gắn liền với một mạng lưới minh bạch".
	+ Các nhà thiết kế giao thức Internet chơi "catch-up".
	+ Xem xét về bảo mật trong tất cả các lớp.
* Kẻ xấu: đưa phần mềm độc hại vào các host thông qua Internet.
	+ Phần mềm độc hại có thể đi vào các host bằng một *virus*, *worm* hoặc *Trojan horse*.
	+ Phần mềm gián điệp, phần mềm độc hại có thể ghi lại thao tác bàn phím, các trang web đã truy cập,...
	+ Những host bị lây nhiễm có thể bị đưa vào mạng botnet, được sử dụng để *spam* hay *tấn công DDoS*.
	+ Phần mềm độc hại thường có khả năng tự sao chép: từ một host lây nhiễm, xâm nhập vào các máy khác.
	+ Trojan horse:
		- Ẩn trong một số phần mềm có ích.
		- Ngày nay, thường có trong trang Web (Active-X, plugin).
	+ Virus:
		- Lây nhiễm bằng cách tiếp cận đối tượng (ví dụ như email đính kèm), chủ động thực thi.
		- Tự sao chép: Tự lan truyền đến các host, người dùng khác.
	+ Worm: 
		- Lây nhiễm bằng cách tiếp cận thụ động những đối tượng tự thực thi.
		- Tự sao chép: Tự lan truyền đến các host, người dùng khác.
		
		![worm](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/worm.png)
		
* Kẻ xấu: tấn công máy chủ, hạ tầng mạng.
	+ Tấn công từ chối dịch vụ (Denial of Service - DoS): kẻ tấn công làm cho những tài nguyên (máy chủ, băng thông) không còn khả dụng cho những lưu lượng hợp pháp bằng cách làm quá tải những nguồn tài nguyên này bằng những lưu lượng giả mạo.
	+ Các bước thực hiện:
		- Chọn mục tiêu.
		- Đột nhập vào các host xung quanh mạng (botnet).
		- Gửi các gói tin đến mục tiêu từ những host bị xâm nhập.
		
		![dos](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/dos.png)

* Kẻ xấu có thể *chặn bắt* (sniff) được gói tin.
	+ Chặn bắt gói tin (Packet Sniffing):
		- Truyền Broadcast (Ethernet được chia sẻ, mạng không dây).
		- Một số interface ngẫu nhiên đọc/ghi lại các gói tin (ví dụ, bao gồm mật khẩu) đi qua.
		
		![packet-sniffing](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/packet-sniffing.png)
		
	+ Wireshark được dùng ở những labs cuối chương là một chương trình *chặn bắt gói tin* (packet-sniffer) miễn phí.
* Kẻ xấu có thể giả mạo địa chỉ nguồn.
	+ IP spoofing: gửi gói tin với địa chỉ nguồn giả mạo.

	![ip-spoofing](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/ip-spoofing.png)
	
* Kẻ xấu có thể ghi lại và tấn công (*record and playback*).
	+ Record and playback : sniff các thông tin nhạy cảm (ví dụ như mật khẩu), và sử dụng về sau.
	
	![record-and-playback](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/record-and-playback.png)
	
<a name="donvimetric"></a>
#### 8. Đơn vị Metric
* Những prefix chính thường sử dụng:
	
![prefix](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/prefix.png)

* Sử dụng lũy thừa 10 cho tốc độ, lũy thừa 2 để lưu trữ.
	- Ví dụ: 1Mps = 1,000,000 bps; 1KB = 1024 bytes
* "B" dùng cho bytes, "b" dùng cho bits.

* Internet dưới biển.

![undersea](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/undersea.png)

---

### Tài liệu tham khảo:

[1] Lecture 1. Introduction to networks. http://scisweb.ulster.ac.uk/%7Ekevin/com320/notes.htm


---

### Hết
