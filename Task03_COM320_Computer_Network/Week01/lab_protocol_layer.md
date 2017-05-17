## Thực hành Lab - Protocol Layers

> Tài liệu: Lab Protocol Layers
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **17/05/2017**

### Mục lục

[1. Mục tiêu](#muctieu)

[2. Yêu cầu](#yeucau)

[3. Wireshark & cơ bản về Packet Sniffing ](#wiresharkvacobanvepacketsniffing)

[8. Step 5: Demultiplexing Keys]()

---
<a name="muctieu"></a>
### 1. Mục tiêu
* Biết được cách các giao thức và các phân lớp được thể hiện trong gói tin. Đó là những khái niệm chính về cấu trúc mạng được trình bày trong tài liệu.
* Bài lab ở đây:

http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-protocol-layers.pcap

<a name="yeucau"></a>
### 2. Yêu cầu
* **Wireshark**: Bài lab này sử dụng phầm mềm Wireshark để chặn bắt và phân tích một gói tin. Một **packet trace** là một bản ghi lưu lại lưu lượng tại một vị trí trong mạng, như là một *snapshot* chụp được tất cả các bit đi qua một sợi dây riêng biệt. Packet trace ghi lại một *timestamp* cho mỗi gói tin, cùng với những bit tạo nên gói tin, từ header của những tầng thấp đến nội dung của những tầng cao.
* Wireshark chạy trên hầu hết các hệ điều hành, bao gồm Windows, Mac và Linux. Nó cung cấp một giao diện đồ họa để có thể thấy được các chuỗi gói tin và ý nghĩa của các bit khi được diễn tả trong các header của giao thức và dữ liệu. Nó đặt màu cho từng loại giao thức và có nhiều cách để lọc và phân tích gói tin để bạn điều tra được hoạt động của các giao thức mạng. 
* Wireshark được sử dụng rộng rãi để xử lý sự cố mạng. Bạn có thể tải wireshark cho máy tính tại <www.wireshark.org>. Nó là chương trình phân tích gói tin lý tưởng cho các bài lab - vì nó ổn định, có lượng người dùng lớn và hỗ trợ tư liệu tốt trong đó hướng dẫn sử dụng <http://www.wireshark.org/docs/wsug_html_chunked>, và một diễn đàn FAQ chi tiết, tính năng phong phú bao gồm khả năng phân tích hàng trăm loại giao thức và một giao diện được thiết kế tốt.
* Wireshark chạy trên những máy tính sử dụng Ethernet, serial (PPP and SLIP), mạng LAN không dây theo chuẩn 802.11, và nhiều công nghệ link-layer khác (nếu hệ điều hành mà nó chạy cho phép Wireshark hoạt động). 
* Wireshark là một cung cụ cốt lõi cho những cuộc tấn công "man in the middle" hay những cuộc tấn công snooping tương tự. Đơn giản là nó không thể thiếu cho những ai muốn kiểm tra các gói tin được truyền qua mạng - dù tốt hay xấu ...

<a name="wiresharkvacobanvepacketsniffing"></a>
### 3. Wireshark & cơ bản về Packet Sniffing 
* Công cụ cơ bản để quan sát các thông điệp trao đổi giữa các thực thể thực hiện các giao thức gọi là *packet sniffer*. Giống như tên gọi, một packet sniffer chặn bắt ("sniff") thông điệp được gửi/nhận từ/bởi máy tính của bạn; nó cũng sẽ lưu trữ và/hoặc hiển thị nội dung của nhiều trường giao thức trong những gói tin bị bắt. Một packet sniffer thường thụ động. Nó quan sát được những thông tin được gửi và nhận bởi những ứng dụng và giao thức chạy trên máy tính, nhưng không bao giờ gửi gói tin đi. Tương tự, các gói tin nhận được trên packet sniffer không bao giờ được đánh địa chỉ rõ ràng. Thay vào đó, packet sniffer sẽ nhận được một bản sao của gói tin được gửi/nhận từ/bởi ứng dụng và các giao thức chạy trên máy tính.
* Hình ở dưới thể hiện cấu trúc của một packet sniffer. Bên phải hình là những giao thức (ở đây là Internet Protocol) và các ứng dụng (như là web browser hay ftp client) thường chạy trên máy tính. Packet sniffer, được hiển thị bên trong hình chữ nhật trong hình là phần mở rộng của một phần mềm bình thường trên máy tính và bao gồm hai phần. Thư viện bắt gói tin nhận được một bản sao của mỗi frame link-layer được gửi từ hoặc nhận bỏi máy tính của bạn. Thông tin trao đổi giao các giao thức ở tầng cao hơn như là HTTP, FTP, TCP, UDP, hoặc IP, tất cả cuối cùng được đóng gói trong các frame link-layer, được vận chuyển qua các vật liệu vật lý như là cáp Ethernet.

![packet-sniffer-structure](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/img/packet-sniffer-structure.png)



### Tài liệu tham khảo:

---

### Hết