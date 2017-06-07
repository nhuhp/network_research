## The Data Link Layer

> Tài liệu: The Data Link Layer
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **07/06/2017**

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
- [3.1. Phạm vi Lỗi - Khoảng cách Hamming](#khoangcachhamming)			
- [3.2. Sửa lỗi - Mã Hamming](#sualoimahamming)			
- [3.3. Phát hiện lỗi - Chẵn Lẻ](#phathienloichanle)
- [3.4. Phát hiện lỗi - Checksums](#phathienloichecksums)
- [3.5. Phát hiện lỗi - CRCs](#phathienloicrc)

[4. Các giao thức Data Link sơ cấp](#cacgiaothucdatalinksocap)
- [4.1. Môi trường lớp truyền dẫn](#moitruongloptruyendan)
- [4.2. Giao thức dơn giản không tưởng](#giaothucdongiankhongtuong)
- [4.3. Stop-and-wait - Kênh không có lỗi](#stopandwaitkenhkhongcoloi)
- [4.4. Stop-and-wait - Kênh có nhiễu](#stopandwaitkenhnhieu)

[5. Giao thức Cửa sổ trượt](#giaothuccuasotruot)
- [5.1. Khái niệm Cửa sổ trượt](#khainiemcuasotruot)
- [5.2. Cửa sổ trượt một bit](#cuasotruotmotbit)
- [5.3. Go-Back-N](#gobackn)
- [5.4. Selective Repeat](#selectiverepeat)

[6. Các giao thức Data Link minh họa](#cacgiaothucdatalinkminhhoa)
- [6.1. Packet over SONET](#packetoversonet)
- [6.2. PPP](#ppp)
- [6.3. ADSL](#adsl)

---

<a name="lopdatalink"></a>
### 1. Lớp Data Link

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

<a name="phathienloivasualoi"></a>			
### 3. Phát hiện lỗi và sửa lỗi
* Các đoạn mã lỗi thêm phần dự phòng có cấu trúc vào vào dữ liệu nên các lỗi có thể được phát hiện, hoặc sửa chữa.
* Mã sửa lỗi:
	- Mã Hamming (Hamming Codes).
	- Mã chập nhị phân (Binary convolutional codes).
	- Mã Reed-Solomon và mã kiểm tra chẵn lẻ mật độ thấp (Reed-Solomon and Low-Density Parity Check codes).
		+ Phức tạp về mặt toán học, được sử dụng rộng rãi trong các hệ thống thực.
* Mã phát hiện:
	- Chẵn lẻ (Parity).
	- Checksums.
	- Mã dự phòng Cyclic (Cyclic redundancy codes).

<a name="khoangcachhamming"></a>			
#### 3.1. Phạm vi Lỗi - Khoảng cách Hamming
* Mã chuyển dữ liệu của n bit thành từ mã của n + k bit.
* Khoảng cách Hamming là số lần lật bit tổi thiểu để chuyển một từ mã hợp lệ thành một từ mã hợp lệ khác.
	- Ví dụ: 4 từ mã của 10 bit (n=2, k=8):
		+ 0000000000, 0000011111, 1111100000, và 1111111111
		+ Khoảng cách Hamming là 5.
* Giới hạn của một mã với khoảng cách:
	- 2d+1 - có thể sửa d lỗi (ví dụ như 2 lỗi ở trên).
	- d+1 - có thể phát hiện d lỗi (ví dụ như 4 lỗi ở trên).

<a name="sualoimahamming"></a>			
#### 3.2. Sửa lỗi - Mã Hamming
* Mã Hamming cung cấp một cách đơn giản để thêm các bit kiểm tra và sửa một lỗi bit:
	- Các bit kiểm tra tương đương với các tập hợp con của từ mã.
	- Việc tính toán lại các tổng chẵn lẻ (syndrome) có thể đưa ra vị trí của lỗi để lật, hoặc bằng 0 nếu không có lỗi.
	
	![hamming-code](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/hamming-code.png)
	
<a name="phathienloichanle"></a>			
#### 3.3. Phát hiện lỗi - Chẵn Lẻ
* Bit chẵn lẻ được thêm vào là modulo 2 tổng của các bit dữ liệu.
	- Tương đương với XOR; đây là phép chẵn.
	- Ví dụ: 1110000 -> 11100001
	- Phát hiện lỗi sẽ kiểm tra nếu tổng bị sai (một lỗi).
* Cách đơn giản để xác định một số lượng lẻ của lỗi.
	- Ví dụ: 1 lỗi, 11100~1~0**1**; đã phát hiện, tổng bị sai.
	- Ví dụ: 3 lỗi, 110~011~00**1**; đã phát hiện, tổng bị sai.
	- Ví dụ: 2 lỗi, 1110~11~0**1**; không phát hiện, tổng đúng.
* Lỗi cũng có thể nằm trong chính bit chẵn lẻ.
* Các lỗi ngẫu nhiên được phát hiện với xác suất 1/2.
* Hoán vị của N bit chẵn lẻ xác dịnh các lỗi bất định đến N.
	+ Mỗi tổng chẵn lẻ được thực hiện qua các bit không gần kề.
	+ Mỗi lần rối bit chẵn để N sẽ không gây ra thất bại.
	
	![burst-error](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/burst-error.png)
	
<a name="phathienloichecksums"></a>			
#### 3.4. Phát hiện lỗi - Checksums
* Checksums xử lý dữ liệu các từ N bit và thêm vào N bit kiểm tra là modulo 2^N tổng của các từ.
* Tính chất:
	+ Cải tiến phát hiện lỗi trên các bit chẵn lẻ.
	+ Phát hiện các lỗi rối đến N.
	+ Phát hiện các lỗi ngẫu nhiên với xác suất 1-2N.
	+ Dễ bị tấn công đến các lỗi hệ thống.

<a name="phathienloicrc"></a>			
#### 3.5. Phát hiện lỗi - CRCs
* Thêm các bit để dịch các frame được xem như là các đa thức có thể chia đều cho các bộ tạo đa thức.

![crc](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/crc.png)

<a name="cacgiaothucdatalinksocap"></a>			
### 4. Các giao thức Data Link sơ cấp
* Một vấn đề thiết kế quan trọng nảy sinh trong lớp Data Link là phải làm gì với các máy gửi muốn hệ thống truyền các frame hơn bên nhận nhận chúng.
* Trong kiểm soát lưu lượng dưa trên tốc độ, giao thức có một cơ chế được tích hợp sẵn để giới hạn tốc độ mà bên gửi truyền dữ liệu đi mà không cần sử dụng phản hồi từ bên nhận.
* Việc sử dụng các mã sửa lỗi thường được gọi là **FEC** (Forward Error Correction).

<a name="moitruongloptruyendan"></a>			
#### 4.1. Môi trường lớp truyền dẫn
* Thường được thực hiện như các NIC và OS driver; lớp Network (IP) thường là phần mềm hệ điều hành.

![link-layer-environment](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/link-layer-environment.png)

* Việc thực hiện các giao thức lớp truyền dẫn sử dụng các hàm thư viện.
	+ Xem code (protocol.h) để thêm chi tiết.
	
	![functions](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/functions.png)

<a name="giaothucdongiankhongtuong"></a>
#### 4.2. Giao thức dơn giản không tưởng
* Chọn một giao thức lý tưởng (p1) để bắt đầu.
	+ Giả sử không có lỗi, và bên thu nhanh bằng bên phát.
	+ Xét truyền tải dữ liệu một chiều.
	
	![one-way-transfer](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/one-way-transfer.png)
	
* Không có lỗi hay kiểm soát luồng.	

<a name="stopandwaitkenhkhongcoloi"></a>
#### 4.3. Stop-and-wait - Kênh không có lỗi
* Giao thức (p2) đảm bảo bên gửi không thể vượt qua bên nhận:
	- Bên nhận trả về một frame giả (ack) khi sẵn sàng.
	- Chỉ có một frame ra trong một thời điểm - được gọi là dừng và chờ (stop-and-wait).
	- Có thêm kiểm soát luồng.
	
![protocol-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/protocol-2.png)

<a name="stopandwaitkenhnhieu"></a>
#### 4.4. Stop-and-wait - Kênh có nhiễu
* **ARQ** (Automatic Repeat reQuest) có cơ chế kiểm soát lỗi.
	- Bên nhận ack các frame mà được vận chuyển chính xác.
	- Bên gửi thiết lập bộ đếm thời gian và gửi lại các frame nếu không có ack.
* Để chuẩn xác, các frame và các gói ack phải được đánh số.
	- Bên nhận không thể yêu cầu truyền lại (do mất mát gói ack hoặc bộ đếm thời gian sớm) từ frame mới.
	- Đối với Stop-and-wait, 2 số (1 bit) là đủ.
* Vòng lặp ở bên gửi (p3):

![sender-loop](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/sender-loop.png)
	
* Vòng lặp ở bên nhận (p3):

![receiver-loop](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/receiver-loop.png)

<a name="giaothuccuasotruot"></a>
### 5. Giao thức Cửa sổ trượt 

<a name="khainiemcuasotruot"></a>
#### 5.1. Khái niệm Cửa sổ trượt
* Bên gửi duy trì cửa sổ các frame mà nó có thể gửi.
	- Cần có bộ nhớ đệm lưu chúng để có thể truyền lại.
	- Cửa sổ tiến tới với các thông báo nhận kế tiếp.
* Bên nhận duy trì cửa sổ các frame mà nó có thể nhận được.
	- Cần giữ không gian bộ nhớ đệm cho các gói đến.
	- Của sổ tiến tới với các gói đến theo thứ tự.
* Một cửa sổ dịch chuyển tới ở bên gửi và bên nhận.
	- Ví dụ: kích thước cửa sổ là 1, với một số có liên tiếp 3 bit.
	
	![a-sliding-window](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/a-sliding-window.png)
	
* Các cửa sổ lớn hơn cho phép kỹ thuật ông dẫn (**Pipelining**) để sử dụng đường kết nối hiệu quả hơn.
	- Stop-and-wait (w=1) không hiệu quả cho những kết nối dài.
	- Cửa sổ tốt nhất sẽ phụ thuộc vào độ trễ băng thông bandwidth-delay (BD).
	- Yêu cầu **w >= 2BD + 1** để có thể đảm bảo sử dụng kết nối cao.
* Kỹ thuật ống dẫn Pipelining dẫn tới nhiều lựa chọn khác nhau để xử lý lỗi/bộ đệm.
	- Chúng ta sẽ xem xét **Go-Back-N** và **Selective Repeat**.
* Kỹ thuật tạm thời hoãn các gói ack đi ra ngoài để chúng có thể nối vào frame dữ liệu đi ra ngoài kế tiếp được gọi là **Piggybacking**.

<a name="cuasotruotmotbit"></a>
#### 5.2. Cửa sổ trượt một bit
* Truyền dữ liệu theo cả hai hướng với Stop-and-wait.
	- Các gói Ack được piggyback trên các frame truyền ngược lại để tăng hiệu quả.
	- Xử lý lỗi truyền tải, kiểm soát luồng, bộ đếm thời gian sớm.
* Mỗi node là bên gửi và bên nhận (p4):
	
	![protocol-4](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/protocol-4.png)
	
	![protocol-4-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/protocol-4-2.png)
	
* Hai trường hợp cho thấy sự tương tác khéo léo xuất hiện trong p4:	
	- Bắt đầu đồng thời (bên phải) tạo ra hoạt động chính xác nhưng chậm so với bình thường (bên trái) do lặp lại truyền dẫn.
	
![2-case](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/2-case.png)

<a name="gobackn"></a>
#### 5.3. Go-Back-N
* Bên nhận chỉ chấp nhận/ack các frame đến theo thứ tự:
	- Loại bỏ các frame theo sau một frame thiếu/lỗi.
	- Bên gửi tạm ngưng và gửi lại tất cả các frame còn tồn tại.

	![go-back-n](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/go-back-n.png)
	
* Các cân nhắc khi dùng Go-Back-N:
	- Phương pháp đơn giản cho bên nhận; chỉ cần 1 frame.
	- Tốn băng thông kết nối vì lỗi với các cửa sổ lớn; toàn bộ cửa sổ sẽ được truyền lại.
	
<a name="selectiverepeat"></a>
#### 5.4. Selective Repeat
* Bên nhận chấp nhận các frame bất kỳ chỗ nào trong cửa sổ nhận.
	- Ack bị dồn cho biết frame có thứ tự cao nhất.
	- **NAK** (negative Ack) làm cho bên gửi truyền lại một frame bị thiếu trước khi bị ngưng để gửi lại cửa sổ.
	
	![selective-repeat](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/selective-repeat.png)
	
* Những cân nhắc khi dùng Selective Repeat:
	- Phức tạp nhiều hơn Go-Back-N do bộ đệm ở bên nhận và nhiều bộ đếm thời gian ở bên gửi.
	- Việc sử dụng băng thông kết nối hiệu quả hơn vì chỉ có những frame mất mát mới được gửi lại (với tỷ lệ lỗi thấp).
	* Để chuẩn xác, yêu cầu:
		- Các số liên tiếp (s) ít nhất bằng hai lần cửa sổ (w):
		
	![s-2w](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/s-2w.png)

<a name="cacgiaothucdatalinkminhhoa"></a>
### 6. Các giao thức Data Link minh họa

<a name="packetoversonet"></a>
#### 6.1. Packet over SONET
* Packet over SONET là phương pháp được sử dụng để mang các gói tin IP qua SONET các kết nối cáp quang.
	- Sử dụng PPP (Point-to-Point Protocol) để đóng frame.
	- Giao thức được sử dụng phổ biến nhất trên các kết nối cáp quang diện rộng tạo nên hệ thống mạng liên lạc xương sống (back-bone).
	
	![packet-over-sonet](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/packet-over-sonet.png)

<a name="ppp"></a>	
#### 6.2. PPP
* PPP (Point-to-Point Protocol) là một phương pháp chung để vận chuyển các gói tin qua các đường truyền dẫn.
	- Đóng frame sử dụng một cờ (0x7E) và kỹ thuật byte stuffing.
	- "Unnumbered mode" (dịch vụ vô hướng không có thông báo nhận) được sử dụng để mang các gói tin IP.
	- Phát hiện lỗi với checksums.
	
	![ppp](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/ppp.png)
	
* Một giao thức điều khiển kết nối làm cho kết nối PPP up/down.
	
![link-control](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/link-control.png)

<a name="adsl"></a>
#### 6.3. ADSL (Asymmetric Digital Subscriber Line)
* Được sử dụng rộng rãi cho Internet băng thông rộng qua các đường dây thuê bao (Local loop).
	- ADSL chạy từ modem (khách hàng) đến DSLAM (ISP).
	- Các gói tin IP được gửi qua PPP và AAL5/ATM.
	
	![adsl](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/adsl.png)

* Dữ liệu PPP được gửi trong AAL5 frame trên các ô ATM:
	- ATM là một lớp liên kết sử dụng các ô (cell) có kích thước ngắn, cố định (53 byte); mỗi ô có một bộ định dạng mạch ảo.
	- AAL5 là một định dạng để gửi các gói tin qua ATM.
	- PPP frame được chuyển đổi sang một AAL5 frame (PPPoA).
	
	![aal5](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/aal5.png)
	
---

### Tài liệu tham khảo:

[1] The Data Link Layer. http://scisweb.ulster.ac.uk/~kevin/com320/slides/Chapter3-DataLinkLayer.pptx

---

### Hết
