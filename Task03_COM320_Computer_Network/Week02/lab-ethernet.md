## Lab Ethernet	

> Tài liệu: Lab Ethernet
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **30/05/2017**

### Mục lục
[1. Mục tiêu](#muctieu)

[2. Yêu cầu](#yeucau)

[3. Step 1: Capture a Trace](#step1)

[4. Step 2: Inspect the Trace](#step2)

[5. Step 3: Ethernet Frame Structure](#step3)

[6. Step 4: Scope of Ethernet Address](#step4)

[7. Step 5: Broadcast Frames](#step5)

[8. Step 6: IEEE 802.3](#step6)

---

<a name="muctieu"></a>
#### 1. Mục tiêu
* Để tìm ra chi tiết của Ethernet frame. Ethernet là một giao thức tầng link phổ biến. Các máy tính hiện đại kết nối với các switch Ethernet hơn là sử dụng Ethernet cổ điển.
* File trace ở đây: : <http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-ethernet.pcap>

<a name="yeucau"></a>
#### 2. Yêu cầu
* **Wireshark**: Lab này này sử dụng phần mềm Wireshark để bắt và kiểm tra trace gói tin. Một trace gói tin là một record của lưu lượng tại một vị trí trên mạng, như thể một snapshot giữ lại tất cả bit truyền qua một đường dây cụ thể. Bản trace record một timestamp cho mỗi gói tin, cùng với các bit tạo thành gói, từ các header của tầng dưới đến nội dung của tầng trên. 
1. **Launching Wireshark** với quyền **Administrator**.

![launching-wireshark](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/launching-wireshark.png)

2. Chọn **Interface**

![interface-list](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/interface-list.png)

* Nhìn màn hình bên phải của Wireshark, sẽ có một danh sách các Interface. Đây là danh sách các interface mạng trên máy tính bạn. Một khi bạn chọn một interface, Wireshark sẽ bắt tất cả gói tin trên interface đó. Click vào card mạng trên máy tính mà bạn đang sử dụng. Như ví dụ trên, đó là **Ethernet Driver** để bắt đầu bắt gói tin (tức là để Wireshark bắt đầu bắt tất cả các gói tin gửi đến/đi từ interface đó), một màn hình như ở phần sau sẽ được hiển thị, cho biết thông tin về các gói tin bị bắt. Một khi bạn bắt đầu bắt gói tin, bạn có thể dừng nó lại bằng cách chọn phím biểu tượng **Stop**.

<a name="step1"></a>
#### 3. Step 1: Capture a Trace
* Tiến hành như sau để bắt gói tin ping. Chuột phải và chọn "Save Link As" tải file sau: <http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-ethernet.pcap>
1. Mở file trace từ nơi bạn lưu trữ, ví dụ D:\Downloads
2. Bạn  sẽ thấy hình tương tự như sau:

![ethernet-trace-open](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/ethernet-trace-open.png)

3. Gõ "**icmp**" vào ô lọc (filter) và nhấn Enter (hoặc Apply nếu có).

![icmp-filter](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/icmp-filter.png)

<a name="step2"></a>
#### 4. Step 2: Inspect the Trace
* Chọn bất kỳ gói tin nào trong file trace (trong bảng phía trên) để xem chi tiết cấu trúc của nó (trong bảng ở giữa) và các byte tạo thành gói tin đó (trong bảng phía dưới). Bây giờ chúng ta hãy kiểm tra chi tiết của các gói tin. Như trong hình, chúng ta chọn gói tin đầu tiên trong file trace. Chú ý rằng chúng ta đang sử dụng thuật ngữ "gói tin" một cách tùy tiện. Mỗi record bị bắt bởi Wireshark tương ứng chính xác hơn với một frame trong định dạng Ethernet mà mang một gói tin như là payload của nó; Wireshark có thể phân tích cấu trúc này càng nhiều càng tốt.
* Trong bảng ở giữa, mở các trường Ethernet header (sử dụng dấu mở rộng hoặc biểu tượng "+") để thấy thông tin chi tiết của chúng. Mối quan tâm của chúng ta là Ethernet header, bạn có thể bỏ qua các giao thức ở các tầng cao hơn (trong trường hợp này là IP và ICMP). Chú ý những điều sau:
	- Các frame trong trace này là DIX Ethernet, gọi là "**Ethernet II**" trong Wireshark.
	- Không có trường Preamble trong các trường được hiển thị trong Wireshark. Preamble là một cơ chế ở tầng Vật lý để giúp NIC định danh được điểm khởi đầu của một frame. Nó không mang dữ liệu hữu ích nào và không nhận được như những trường khác.
	- Có một địa chỉ đích và một địa chỉ nguồn. Wireshark giải mã một số bit trong phần OUI (Organizationally Unique Identifier) của địa chỉ và cho biết nhà cung cấp của NIC, ví dụ: Dell cho địa chỉ nguồn.
	- Có một trường **Type**. Đối với các ping message, loại Ethernet là IP, có nghĩa là Ethernet payload mang một gói tin IP. (Không có trường Độ dài (Length) như trong định dạng IEEE 802.3. Thay vào đó, độ dài của một Ethernet frame được xác định bởi phần cứng của máy nhận, trong đó tìm những frame hợp lệ mà bắt đầu là một preamble và kết thúc là một checksum chính xác, sau đó đẩy lên các tầng cao hơn cùng với gói tin).
	- Không có trường **Data** per se - phần dữ liệu bắt đầu với IP header ngay sau Ethernet header.
	- Không có **Pad**. Một Pad sẽ có mặt ở cuối nếu frame không nhỏ hơn 64 byte, kích thước nhỏ nhất của Ethernet frame.
	- Không có **Checksum** trong hầu hết các trace, mặc dù nó thật sự tồn tại. Thông thường, phần cứng Ethernet gửi hoặc nhận các frame tính toán hoặc kiểm tra trường này và thêm nó vào hoặc là tháo nó ra. Dó đó, đơn giản là nó chỉ không xuất hiện trên OS hay Wireshark tronng hầu hết các thiết lập.
	- Cũng không có trường **VLAN**. Nếu VLAN được sử dụng, các tag VLAN thường được thêm vào và gỡ bỏ bởi các switch port nên chúng sẽ không xuất hiện trong máy host sử dụng mạng.
	
* Q1. Địa chỉ MAC của nguồn `#1` từ địa chỉ 128.208.2.151?
* Q2. Nhấn vào `#12` và mở rộng phần [+] Address Resolution Protocol trong bảng ở giữa. Địa chỉ đích MAC 00:00:00:00:00:00 có ý nghĩa gì?
* Q3. Nhấn lại vào `#12` và mở rộng phần [+] Address Resolution Protocol trong bảng ở giữa. Tại sao trường protocol lại được liệt kê là IP trong khi nó không phải là một gói tin IP?

<a name="step3"></a>
#### 5. Step 3: Ethernet Frame Structure
* Hãy cố gắng hiểu định dạng của Ethernet frame. Chú ý phạm vi của Ethernet header và Ethernet payload. Xem cấu trúc frame ở hình bên dưới.
	- Để làm việc với các kích thước, quan sát thấy rằng khi bạn nhấn vào khối giao thức trong bảng ở giữa (chính khối đó, không phải là dấu mở rộng [+]) thì Wireshark sẽ highlight phần byte mà nó tương ứng với gói tin ở trong bảng ở dưới và hiển thị độ dài tại cuối cửa sổ. Bạn cũng có thể sử dụng kích thước tổng thể của gói tin được hiển thị trong cột Length hoặc trong khối chi tiết Frame.
	
	![structure-ethernet-frame](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/structure-ethernet-frame.png)
	
* Có vài điểm cần lưu ý:
	- Phần địa chỉ đích (Destination Address) đứng trước phần địa chỉ nguồn (Source Address).
	- Phần pad không xuất hiện vì các gói tin mà chúng ta xem xét thì đủ lớn để không cần phần pad nữa.
	- Không giống như nhiều giao thức, Ethernet có một phần cuối (trailer) (chứa checksum, và pad nếu có) cũng như một header. Phần checksum được xử lý bởi phần cứng và không xuất hiện trên Wireshark.
	- Ethernet header dài 14 byte.
	
* Q1. Nhấn vào `#12` và mở rộng phần [+] Address Resolution Protocol trong bảng ở giữa. Opcode (1) có ý nghĩa gì? Opcode (2) có ý nghĩa gì?
(Chú ý, trên một số phiên bản Wireshark, opcode (1)) được biểu diễn là (0x0001) và opcode (2) được biểu diễn là (0x0002)).
* Q2. Nhấn vào `#12` và mở rộng phần [+] và lấy giá trị thập lục phân cho trường loại Ethernet Frame 2 byte?

<a name="step4"></a>
#### 6. Step 4: Scope of Ethernet Address
* Mỗi Ethernet frame mang một địa chỉ nguồn và đích. Một trong những địa chỉ là địa chỉ máy tính bạn. Nó là nguồn frame được gửi, và đích frame được nhận. Nhưng địa chỉ khác thì sao? Giả sử bạn ping một server Internet từ xa, nó không thể là địa chỉ Ethernet của server bởi vì một Ethernet frame được đánh địa chỉ để đi trong một mạng LAN. Thay vào đó, nó sẽ là địa chỉ Ethernet của router hoặc default gateway, giống như AP của bạn trong trường này 802.11. Đây là thiết bị kết nối mạng LAN của bạn đến phần còn lại của Internet. Ngược lại, địa chỉ IP trong khối IP của mỗi gói tin cho biết các điểm nguồn và đích. Chúng là của máy bạn và của server.

![ethernet-ip](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/ethernet-ip.png)

1. Mở Wireshark và bắt đầu bắt gói tin. Bạn có thể muốn xóa bộ lọc đang tồn tại hoặc đơn giản đóng và mở Wireshark lại để bắt đầu bắt gói tin mới.
2. Trong ô lọc, gõ: **ip.src==địa-chỉ-IP-của-bạn**, ví dụ, *ip.sr==193.61.191.71*
(Bạn có xem địa chỉ IP của bạn bằng cách chạy cmd và gõ **ipconfig /all**)
3. Hỏi đồng nghiệp của bạn về địa chỉ IP của họ, ví dụ, 193.61.191.71
4. Mở cmd bằng cách nhấn tổ hợp **<WINDOWS KEY> + R**
5. Gõ **ping địa-chỉ-IP-của-bạn**, ví dụ, *ping 193.61.191.71*
6. Trở lại Wireshark và dừng bắt gói tin.

* Một vài điều cần lưu ý:
	- Các địa chỉ Ethernet và IP sẽ thay đổi theo file trace của bạn bởi vì máy tính khác nhau, nhưng chúng sẽ có chung định dạng ví dụ, 6 byte ở hệ thập phân hoặc 4 byte có dấu chấm.
	- Các địa chỉ Ethernet và IP sẽ tương ứng với máy tính của bạn và máy tính đồng nghiệp bạn.
	- Một số địa chỉ Ethernet và IP không xuất hiện từ file trace. Chúng được hiển thị là "??"

<a name="step5"></a>	
#### 7. Step 5: Broadcast Frames
* File trace mầ bạn đã thu thập ở trên đã bắt lưu lượng unicast Ethernet được gửi giữa một nguồn và đích cụ thể, ví dụ, máy tính của bạn đến router. Nó cũng có thể gửi các lưu lượng multicast hoặc broadcast Ethernet, tương ứng với một nhóm máy tính hoặc tất cả các máy tính trên mạng Ethernet. Chúng ta có thể biết địa chỉ đó là unicast, multicast hay broadcast. Lưu lượng Broadcast được gửi đến địa chỉ Ethernet đã đặt riêng thì có các bit được bật lên "1". Lưu lượng Multicast được gửi đến những địa chỉ có một "1" trong bit đầu tiên được gửi trên dây; Broadcast là một trường hợp đặc biệt của Multicast. Lưu lượng Broadcast và Multicast được sử dụng rộng rãi để phát hiện các giao thức, ví dụ, một gói tin gửi đến mọi người để tìm kiếm máy in.
1. Để bắt được các Broadcast và Multicast frame, sử dụng bộ lọc trước khi bắt đầu và gõ "**ether multicast**". Chọn **Capture** trong màn hình chính và chọn **Options**. Không được nhầm lẫn với bộ lọc trong lúc đang bắt thì sẽ không chấp nhận biểu thúc lọc ở trên.
2. Chờ đến 30 giây để ghi lại các lưu lượng nền, sau đó dừng lại. Nếu bạn không bắt được bất kỳ gói tin nào với bộ lọc này, hãy sử dụng file trace mà chúng tôi cung cấp.
Trên hầu hết các Ethernet, có một cuộc trao đổi về các lưu lượng nền khi các máy tính trao đổi các message để duy trì trạng thái mạng, đó là lý do tại sao chúng ta cố bắt các lưu lượng mà không cần chạy bất kỳ chương trình nào khác. Bộ lọc "ether multicast" sẽ bắt cả hai multicast và broadcast Ethernet frame, nhưng không phải là các unicast frame thông thường. Bạn có thể phải chờ một lúc để bắt các gói tin này, nhưng trên hầu hết các mạng LAN có nhiều máy tính, bạn sẽ thấy ít nhất một gói tin mỗi vài giây.

![wireshark-capture-options](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/wireshark-capture-options.png)

3. Kiểm tra các gói tin multicast và broadcast mà bạn đã bắt, nhìn vào chi tiết của các địa chỉ nguồn và địa chỉ đích. Hầu hết đều có địa broadcast Ethernet, vì các broadcast frame có xu hướng phổ biến hơn multicast frame. Nhìn vào một broadcast frame để xem địa chỉ nào được sử dụng để broadcast Ethernet. Mở rộng trường địa chỉ Ethernet của cả broadcast và multicast frame để xem bit nào được đặt để phân biệt broadcast/multicast hoặc nhóm lưu lượng với một lưu lượng unicast. Bạn có thể thấy các thông tin như sau:

![filter](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/filter.png)

Lưu ý: Trước khi tiếp tục, bạn nên xóa "ether multicast" trong ô lọc bằng cách chọn Stop, chọn Capture options và xóa "ether multicast" trong ô lọc.

4. Trả lời các câu hỏi:
* Địa chỉ broadcast Ethernet là gì, được viết dưới dạng chuẩn nào mà Wireshark hiển thị?
b. Bit nào của địa chỉ Ethernet được sử dụng để xác định nó là unicast hay multicast/broadcast?

<a name="step6"></a>
#### 8. Step 6: IEEE 802.3
* Chúng ta trở lại với file trace mà bạn đã tải về lúc trước.
<http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-ethernet.pcap>

* Bạn có thể mở lại file trace từ nơi bạn được tải nó về, ví dụ D:\Downloads hoặc chọn *File menu* và mở *Recent*. File trace sẽ được liệt kê ở đây.
* Có một số IEEE 802.3 frame trong file trace đã cung cấp. Để tìm các gói IEEE 802.3, nhập vào ô lọc (phía bảng trên của cửa sổ Wireshark) "llc" (đó là đường chữ thường của "LLC") bởi vì định dạng IEEE 802.3 có giao thức LLC ở phía trên. LLC cũng có mặt trong mạng không dây IEEE 802.11, nhưng không có mặt trong DIX Ethernet. Bạn bên xem 3 gói tin như hình.

![llc-header](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/llc-header.png)

* Hãy xem chi tiết các IEEE 802.3 frame, bao gồm cả LLC header, chẳng hạn như gói tin số 20 trong file trace đã cung cấp.
* Hình này cho thấy các chi tiết của bản trace. Quan sát trường Type bây giờ là trường Length. Theo ví dụ trên, frame này đủ ngắn để thêm vào các số "0" để định danh cho **Trailer** hoặc **Padding**.
* Trả lời các câu hỏi sau: 
1. So sánh độ dài của các header IEEE 802.3 kết hợp LLC so với DIX Ethernet header?
	- Bạn có thể sử dụng Wireshark để làm việc này. Lưu ý rằng phần Trailer/Padding và Checksum được hiển thị như một phần của header, nhưng chúng sẽ xuất hiện ở cuối frame.
2. Làm cách nào để máy tính nhận biết được frame đó là DIX Ethernet hay IEEE 802.3?
3. Nếu IEEE 802.3 không có trường Type, vậy làm cách nào để lớp cao hơn xác định được? Sử dụng Wireshark để tìm khóa giải mã kênh.

#### Trả lời câu hỏi:
* Step 2:
	- 1. Địa chỉ MAC is 00:25:64:d5:10:8b.
	- 2. ARP sử dụng địa chỉ MAC broadcast đã được dành riêng 00:00:00:00:00:00 trong ARP Request để tìm địa chỉ IP 128.208.2.42. Nó chứa thông tin đó trong một bộ nhớ ARP Cache cho phép giao tiếp không giới hạn với 128.208.2.42 (trong một khoảng thời gian) mà không cần broadcast nữa. Cũng lưu ý rằng nó đã biết địa chỉ IP nhưng nó cần một địa chỉ MAC để biết nó là một máy thực tế.
	- 3. Type của giao thức ARP được thiết lập là "IP" bởi vì chúng ta đang yêu cầu ARP phân giải một địa chỉ IP. ARP cũng có thể được sử dụng để phân giải các địa chỉ cho các giao thức mạng khác.
* Step 3:
	- 1. Opcode (1) hay (0x0001) có nghĩa là ARP request và Opcode (2) hay (0x0002) có nghĩa là ARP reply.
	- Giá trị thập lục phân của trường Type Ethernet Frame là 0x0806, dành cho ARP.
* Step 5:
	- Địa chỉ Broadcast là ff:ff:ff:ff:ff:ff. Đây là 48 bit được bật lên 1 trong dạng tiêu chuẩn.
	- Bit cho broadcast/multicast hay "group" được hiển thị bởi Wireshark là ".... ...1 .... .... ...." hay một bit trong các bit thấp của byte địa chỉ đầu tiên. Chúng ta cũng có thể viết 01:00:00:00:00:00. Thật ra bit này được truyền qua dây đầu tiên bởi vì Ethernet đã xác định thứ tự truyền là bit ít quan trọng nhất của mỗi byte trước.
	
	
---

### Tài liệu tham khảo:

[1] Lab Ethernet. http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/lab-ethernet.pdf

---

### Hết
