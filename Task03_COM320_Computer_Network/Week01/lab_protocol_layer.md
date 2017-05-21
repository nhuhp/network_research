## Thực hành Lab - Protocol Layers

> Tài liệu: Lab Protocol Layers
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **21/05/2017**

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
11. Sau khi tải về thành công, trở lại Wireshark và dùng menu hoặc các phím để dừng. Nếu bạn thành công, cửa sổ Wireshark sẽ hiển thị nhiều gói tin, và hầu hết là nó sẽ đầy đủ. Số lượng gói tin đã bắt được sẽ phụ thuộc vào kích thước của trang web, nhưng ít nhất là có 8 gói tin được bắt, thông thường là từ 20-100, và nhiều gói tin có màu xanh lá. Tôi đề nghị bạn dừng ghi bằng cách nhấn Stop màu Đỏ trên giao diện vì nó sẽ dễ dàng hơn để tìm kiếm "200 gói tin OK". Một ví dụ được hiển thị bên dưới.

![capture-port-80](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/capture-port-80.png)

### 5. Step 2: Inspect a Trace 
* Chọn một gói tin có cột Protocol là "HTTP" và cột Info ghi là "GET". Nó là gói tin mang Web request (HTTP) từ máy tính của bạn lên server. (Bạn có thể nhấn vào tiêu đề cột để sắp xếp theo giá trị đó, mặc dù nó không khó để tìm ra một gói tin HTTP bằng cách kiểm tra). Giờ hãy quan sát kỹ hơn về cách cấu trúc gói tin ánh xạ lại các giao thức đang sử dụng. Vì chúng ta đang lấy về một trang web, chúng ta biết những giao thức đang được sử dụng hiển thị ở dưới. Đó là HTTP, một giao thức web tầng ứng dụng dùng để lấy URL. Giống như nhiều ứng dụng Internet, nó chạy phía trên các giao thức tầng transport TCP/IP và tầng network. Các giao thức ở tầng link và physical phụ thuộc vào mạng của bạn, nhưng thông thường được kết hợp ở các dạng của Ethernet (có hiển thị) nếu máy tính có nối dây mạng, hoặc 802.11 (không hiển thị) nếu máy tính kết nối mạng không dây.

![protocol-stack-web](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/protocol-stack-web.png)

* Với các gói tin HTTP GET đã chọn, xem xét kỹ hơn để hiểu về sự giống nhau và khác nhau chúng và chồng giao thức được mô tả kế tiếp. Các khối giao thức được liệt kê trong bảng giữa. Bạn có thể mở rộng mỗi khối (bằng cách nhấn vào biểu tượng "+" mở rộng) để xem chi tiết.
	+ Khối Wireshark đầu tiền là "Frame". Đây không phải là một giao thức, nó là một record có thể mô tả thông tin tổng thể về gói tin, bao gồm thời gian nó bị bắt và số bit dài.
	+ Khối thứ hai là "Ethernet". Lưu ý rằng bạn có thể tạo một trace trên một máy tính dùng 802.11 nhưng vẫn thấy khối Ethernet thay vì khối 802.11. Tại sao? Điều đó xảy ra bởi vì chúng ta yêu cầu Wireshark bắt lưu lượng ở định dạng Ethernet trên tùy chọn bắt, vì thế nó chuyển header 802.11 thật thành một header Ethernet giả.
	+ Sau đó đến, IP, TCP và HTTP, giống như thứ ta muốn. Lưu ý rằng cách sắp xếp này là từ dưới cùng của chồng giao thức lên trên. Đây là do khi các gói tin được chuyển xuống chồng giao thức, thông tin header của giao thức ở tầng thấp sẽ được gắn thêm vào phần trước của thông tin từ giao thức ở tầng cao hơn. Vì thế, các giao thức tầng thấp sẽ đến trước tiên trong gói "trên đường dây". 
	
### 6. Step 3: Inspect a Trace Again
* Bây giờ hãy tìm gói tin HTTP khác, gói response từ server đến máy tính, và nhìn vào cấu trúc của gói tin này để so sánh sự khác nhau với gói HTTP GET. Gói tin này có "200 OK" trong trường Thông tin, chứng tỏ là đã lấy về thành công. Trong trace của chúng ta, có thêm hai khối trong bảng chi tiết được thể hiện hình sau:
	+ Khối đầu tiên ghi vài thứ giống như "[...reassembled TCP segments...]". Chi tiết trong phần capture sẽ thay đổi, nhưng khối này thì mô tả hơn gói tin chứa nó. Nhiều khả năng, các response của web đã được gửi qua mạng là một loạt các gói tin và được ghép lại với nhau sau khi chúng đến máy tính. Gói tin có nhãn HTTP là gói tin cuối cùng của response và khối này sẽ liệt kê các gói tin được ghép với nhau để có được một response hoàn chỉnh. Mỗi gói tin này được xem như sử dụng giao thức TCP mặc dù các gói tin mang một phần của HTTP response. Chỉ có gói tin cuối cùng được hiển thị giao thức HTTP khi toàn bộ HTTP message đã được hiểu, và nó sẽ liệt kê các gói tin được ghép với nhau để tạo thành HTTP response.
	+ Khối thứ hai ghi "Line-based text data...". Chi tiết trong phần capture sẽ thay đổi nhưng khối này mô tả nội dung của trang web đã được tải về. Trong trường hợp của chúng ta, nó thuộc loại text/html, mặc dù nó có thể dễ dàng hiểu được text/xml, image/jpeg hay nhiều loại khác. Đối với Frame record, đây không phải là một giao thức thật sự. Thay vào đó, nó là mô tả nội dung gói tin mà Wireshark tạo ra để giúp chúng ta hiểu được lưu lượng mạng.
	
	![response](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/response.png)

1. Tìm gói tin HTTP GET có "**200 OK (text/html)**" trong trường Thông tin (Info), thể hiện việc tải về đã thành công.

![HTTP-GET](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/HTTP-GET.png))

2. Lăn xuống ở giữa bảng, nhấn chuột phải vào **[+] Line-based text data: text/html**.

3. Lúc này xuất hiện một trình đơn, chọn **Copy --> Bytes --> Printable Text Only**. 

![printable-text-only](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/printable-text-only.png))

4. Tất cả code của trang chủ Ulster sẽ được sao chép lại.

5. Mở một trình soạn thảo văn bản như là Notepad++ và dán đoạn code HTML vào một file mới. Lưu thành "**UlsterHomePage.html**". Tiếp theo, mở Explorer, di chuyển đến nơi lưu file, nhấn vào và mở bằng trình duyệt mặc định.

6. Lưu ý rằng phần lớn trang chủ Ulster đã thực sự được gửi đến máy tính của bạn.

### 7. Step 4: Packet Structure
* Kiểm tra một gói HTTP GET để thấy vị trí và kích thước tình bằng byte các header của các giao thức TCP, IP và Ethernet. Lưu ý đến phạm vi của Ethernet header và payload Ethernet IP qua Ethernet để gửi qua mạng. Cũng lưu ý đến phạm vi của IP header và payload IP.

Để làm việc với size, quan sát khi bạn nhấn một khối protocol trong bảng giữa (chính khối đó, không phải "+" mở rộng) sau đó Wireshark sẽ highlight số byte nó tương ứng trong gói tin ở bảng dưới và hiển thị độ dài ở dưới cùng cửa sổ. Ví dụ, nhấn vào header của IPv4 của một gói tin trong trace sẽ hiển thị độ dài là 20 byte. (Trace của bạn sẽ khác nhau nếu nó là IPv6, và cũng khác nhau kể cả đối với IPv4 phụ thuộc và nhiều tùy chọn.) Bạn cũng có thể sử dụng kích thước tổng thể của gói tin ở trong cột Length hay trong khối Frame detail.

***Trả lời:***

![HTTP-GET-structure](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/HTTP-GET-structure.png))

* Có vài điểm cần chú ý:
	+ Thứ tự của các header (Ethernet, IP, TCP, HTTP) là chồng giao thức từ dưới lên trên bởi vì các tầng thấp nằm ngoài cùng trong gói tin khi nó được đi qua mạng.
	+ Sinh viên có quan tâm, chú ý một số điểm khác nhau giữa kích thước của Ethernet header trong Wireshark và trong đoạn text sẽ được khám phá trong những lab sau.
	+ Kích thước của các IP và TCP header thường là 20 byte mỗi cái, nhưng nó cũng có thể lớn trong một số trường hợp phụ thuộc vào OS, ví dụ như IPv6 thay vì IPv4 và những trường TCP header tự chọn sẽ có thể tăng gấp đôi những con số này.
	+ Kích thước của HTTP message sẽ thay đổi phụ thuộc vào tool sử dụng và URL được sử dụng để gửi Web request. Đối với wget/curl, nó có thể là từ 100-300 byte.
	+ Ethernet payload bao gồm mọi thứ bên ngoài Ethernet header. Vì thế, Ethernet không cần hiểu cấu trúc bên trong của IP/TCP/HTTP, nó tùy vào những tầng cao hơn để quyết định header và giới hạn message.
	+ Tương tự, IP payload bao gồm mọi thứ bên ngoài IP header. Lưu ý rằng kể cả IP header hay payload đều không xen phủ đến Ethernet header.
	
### 8. Step 5: Demultiplexing Keys
* Khi một một Ethernet frame đến máy tính, tầng Ethernet phải truyền gói tin mà nó chứa lên tầng cao hơn để xử lý. Hành động tìm tầng cao hơn để xử lý các gói tin nhận được gọi là ghép kênh. Chúng ta biết rằng trong trường hợp này, tầng cao hơn là IP. Nhưng làm cách nào để giao thức Ethernet biết được điều đó? Sau cùng, tầng cao hơn có thể là một giao thức khác hoàn toàn (như là ARP). Chúng ta gặp vấn đề tương tự ở tầng IP - IP phải có thể xác định được rằng nội dung của IP message là một gói tin TCP vì thế có thể truyền nó đến giao thức TCP đến xử lý. Câu trả lời là giao thức sử dụng nội dung trong header của chúng như là "khóa ghép kênh"  để xác định tầng cao hơn.
* Nhìn vào Ethernet và IP header của một gói tin đã tải về trong phần chi tiết và trả lời những câu hỏi sau:
1. Trường nào trong Ethernet header là khóa ghép kênh cho biết tầng tiếp theo là IP? Giá trị nào được sử dụng trong trường này để biểu thị "IP"?
Trả lời: Khóa ghép kênh cho Ethernet là trường Type. Nó chứa 0x800 khi tầng cao hơn là IP.
2. 	Trường nào trong IP header là khóa ghép kênh cho biết tầng tiếp theo là TCP? Giá trị nào được sử dụng trong trường này để biểu thị "TCP"?
Trả lời: Khóa ghép kênh cho IP là trường Protocol. Nó có giá trị 6 khi tầng tiếp theo là TCP.


### Tài liệu tham khảo:

[1] http://scisweb.ulster.ac.uk/~kevin/com320/labs.htm

[2] Lab Protocol Layers. http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/lab-protocol-layers.pdf

---

### Hết