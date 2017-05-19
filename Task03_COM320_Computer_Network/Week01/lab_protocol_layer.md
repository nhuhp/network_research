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

<http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-protocol-layers.pcap>

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

![packet-sniffer-structure](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/packet-sniffer-structure.png)

* Thành phần thứ hai của một packet sniffer là phân tích gói tin (packet analyzer), thành phần hiển thị nội dung của tất cả các trường có trong gói tin. Để làm được việc đó, packet analyzer phải "hiểu" cấu trúc của các các gói tin được trao đổi bằng giao thức, Ví dụ, giả sử chúng ta muốn hiển thị các trường của gói tin được trao đổi bằng giao thức HTTP trong hình trên. Packet analyzer phải hiểu được định dạng của các frame Ethernet, vì vậy có thể định dạng được IP datagram có trong một frame Ethernet.. Và nó cũng phải hiểu được định dạng của IP datagram, vì thế nó có thể lấy ra TCP segment có trong IP datagram. Cuối cùng nó cũng phải hiểu được cấu trúc của TCP segment, vì vậy nó có thể lấy được nội dung gói tin HTTP chứa trong TCP segment. Cuối cùng, nó phải hiểu được giao thức HTTP, vì thế, ví dụ, byte đầu tiên của HTTP message  sẽ chứa chuỗi "GET", "POST", hoặc "HEAD".

<a name="step1"></a>
### 4. Step 1: Capture a Trace 
1. Chạy Wireshark.
	* Nhấn *Windows Key* và gõ "**wireshark**", sau đó chuột phải chọn **Run as Administrator**.
	
	![launch-wireshark](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/launch-wireshark.png)
	
2. Màn hình chính hiện một danh sách các interface. Chọn một interface.

	![interface-list](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/interface-list.png)

3. Chọn *Start* để bắt đầu.
4. Wireshark sẽ bắt mọi gói tin trên interface đó. Nhấn vào card mạng trên máy tính mà bạn đang làm việc. Ví dụ, **Ethernet Driver** để bắt đầu bắt gói tin (tức là Wireshark bắt đầu bắt tất cả các gói tin được gửi đến/ từ interface đó), một một màn hình sẽ hiển thị các thông tin về những gói tin được bắt. Một khi bạn bắt đầu bắt gói tin, bạn có thể dựng nó lại bằng cách chọn **Stop**.
Chúng ta muốn xem cấu trúc của các gói tin. Một trang Web đơn giản có URL từ một server, được truy cập từ máy tính của bạn, có thể cho ra các lưu lượng.
5. Mở trình một trình duyệt, ví dụ như Chrome và chọn một URL và tải nó về. Ví dụ: <http://www.ulster.ac.uk>
6. Tắt những tab không cần thiết trên trình duyệt và windows. Bằng cách thu nhỏ hoạt động của trình duyệt, bạn sẽ không cho máy tính tải những nội dung web không cần thiết và tránh được những lưu lượng ngẫu nhiên.
7. Bây giờ quay lại Wireshark và bạn sẽ thấy một màn hình tương tự thế này.

	![packet-screen](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/packet-screen.png)


#### Giao diện chính của Wireshark

![wireshark-interface](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/wireshark-interface.png)

Giao diện Wireshark có năm thành phần chính:
* Menu command là những menu chuẩn nằm trên cùng cửa sổ. Menu *File* cho phép bạn lưu dữ liệu các gói tin đã bắt hay mở một tập tin chứa dữ liệu gói tin được bắt lần trước. Menu *Capture* cho phép bạn bắt đầu bắt gói tin. 
* Phần cửa sổ liệt kê các gói tin hiển thị tóm tắt về gói tin bắt được trong một dòng, trong đó bao gồm số thứ tự gói tin (được đặt bởi Wireshark, không có số thứ tự gói tin chứa trong trong header của bất kỳ giao thức nào), thời gian mà gói tin bị bắt, địa chỉ nguồn và đích của gói tin, loại giao thức, và thông tin cụ thể về giao thức, được chứa trong gói tin. Danh sách gói tin có thể được sắp xếp theo bất kỳ loại danh mục có trong này bằng cách nhấn vào tên cột. Trường *loại giao thức* liệt kê các giao thức cao nhất gửi hoặc nhận gói tin này, tức là giao thức này  là nguồn hay được chứa trong gói tin này.
* Phần cửa sổ chi tiết header của gói tin cung cấp các thông thi chi tiết về gói tin được chọn (được đánh dấu) trong phần cửa số liệt kê các gói tin. (Để chọn một gói tin trong cửa sổ liệt kê gói tin, đặt con trỏ đến dòng tóm tắt của gói tin đó trong cửa sổ và nhấn chuột trái). Những chi tiết này bao gồm thông tin về Ethernet frame (giả sử gói tin được gửi/nhận qua một Ethernet interface) và IP datagram chứa gói tin này. Số lượng thông tin hiển thị của Ethernet và tầng IP có thể được mở rộng hoặc thu nhỏ bằng cách nhấn vào *ô cộng trừ* bên trái dòng Ethernet frame hoặc IP datagram trong cửa sổ chi tiết gói tin.
* Phần cửa sổ nội dung gói tin hiển thị toàn bộ nội dung của frame bị bắt, ở cả hai định dạng ASCII và thập lục phân. Phía trên của giao diện Wireshark, là trường lọc hiện thị gói tin, có thể gõ tên giao thức hoặc các thông tin khác để lọc thông tin hiển thị trên cửa sổ liệt kê gói tin.

#### Lọc lưu lượng
Trở lại với phần lưu lượng đã được bắt ở trước. Chúng ta sẽ xem cách mà có thể chọn lưu lượng trang Web ra khỏi những lưu lượng khác.
8. Bạn có hai tùy chọn. Đơn giản là bạn gõ "***tcp.port==80***" trong khung lọc trên màn hình chính như hình:

![filter-port-80](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/filter-port-80.png)

9. Thay vì phương pháp ở trên, bạn cũng có thể filter bằng cách gõ "***port 80***" vào khung lọc như hình ở dưới. Phần lọc này sẽ ghi lại lưu lượng chuẩn web và không có loại gói tin khác mà máy tính có thể gửi. Việc kiểm tra sẽ dịch các địa chỉ mà máy tính gửi và nhận gói tin thành tên, như vậy sẽ giúp bạn nhận ra gói tin đi đến hoặc từ máy tính của bạn. 

![capture-option](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/capture-option.png)

10. Khi quá trính bắt đã được khởi động, vào một trang sử dụng *http* (không dùng https). Lúc này, các gói tin sẽ được Wireshark ghi lại là nội dung được chuyển. Thử lại <http://www.ulster.ac.uk> trên trình duyệt của bạn.
11. Sau khi tải về thành công, trở lại Wireshark và dùng menu hoặc các phím để dừng. Nếu bạn thành công, cửa sổ Wireshark sẽ hiển thị nhiều gói tin, và hầu hết là nó sẽ đầy đủ. Số lượng gói tin đã bắt được sẽ phụ thuộc vào kích thước của trang web, nhưng ít nhất là có 8 gói tin được bắt, thông thường là từ 20-100, và nhiều gói tin có màu xanh lá. Tôi đề nghị bạn dừng ghi bằng cách nhấn 
### Tài liệu tham khảo:

---

### Hết