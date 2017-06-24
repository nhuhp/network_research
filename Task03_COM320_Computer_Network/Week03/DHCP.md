## DHCP

> Tài liệu: Lab Exercise - DHCP
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **12/06/2017**

### Mục lục

[1. Mục tiêu](#muctieu)

[2. Thiết lập mạng](#thietlapmang)

[3. Step 1: Capture a Trace](#step1)

[4. Step 2: Inspect the Trace](#step2)

[5. Step 3: Details of DHCP Messages](#step3)

[6. Step 4: DHCP Message Addressing](#step4)

---

<a name="muctieu"></a>
### 1. Mục tiêu
* Hiểu được cách hoạt động của **DHCP** (Dynamic Host Configuration Protocol). File trace ở đây:
www.scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-dhcp.pcap

<a name="thietlapmang"></a>
### 2. Thiết lập mạng
* Nhắc lại, DHCP thường được sử dụng để gán địa chỉ IP của một máy tính, cũng như các tham số chẳng hạn như địa chỉ của local Router. Máy tính của bạn, client, sử dụng giao thức DHCP để giao tiếp với một DHCP server trong mạng nội bộ. Các máy tính khác trong mạng nội bộ cũng tương tác với DHCP server này. Trong triển khai, có vài thay đổi. Ví dụ, các local agent có thể là một DHCP relay để có thể chuyển tiếp các message giữa các máy tính nội bộ với một DHCP server từ xa. Hoặc DHCP server có thể được sao chép để tăng độ tin cậy, vì thế có hai hoặc nhiều DHCP server. Đối với mục tiêu của chúng ta, thì chỉ cần một DHCP server duy nhất.
* Một quá trình trao đổi DHCP hoàn thiện bao gồm 4 gói tin: **Discover**, để máy tính bạn định vị được DHCP server; **Offer** để server đề nghị cấp một địa chỉ IP; **Request** để máy tính của bạn yều cầu một địa chỉ đã được gợi ý; và **Ack** để server cấp địa chỉ. Tuy nhiên, khi một máy tính tái thiết lập lại địa chỉ IP trên mạng mà nó đã sử dụng trước đó, một cuộc trao đổi ngắn sẽ được thực hiện giữa 2 gói tin DHCP: **Request**, để yêu cầu địa chỉ IP tương tự từ server đã được sử dụng trước đó; **Ack** để server cấp địa chỉ về.

![dhcp-exchange](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/dhcp-exchange.png)

<a name="step1"></a>
### 3. Step 1: Capture a Trace
* Tiến hành như sau để thay địa chỉ IP mới và thu thập một file trace lưu lượng DHCP. Tuy nhiên, lưu ý rằng, quy trình bên dưới có thể không hoạt động trong hầu hết các trường hợp mà địa chỉ IP của máy tính bạn được gán tĩnh. Thay vào đó, bạn có thể sử dụng file trace đã được cung cấp. Ghi nhớ là không được thực hiện lab này từ xa, vì khi bạn tắt máy tính và khởi động lại interface mạng, bạn sẽ mất kết nối!
1. Khởi động Wireshark và bắt đầu bắt các gói tin với bộ lọc **(udp port 67) hoặc (udp port 68)**. DHCP không được thể hiện trực tiếp, nên chúng ta phải lọc các lưu lượng sử dụng các port UDP dành cho DHCP. (Chú ý, trong phần lọc hiển thị trên màn hình chính, bạn cũng có thể gõ `udp.port==67||udp.port==68`).

![capture-option](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/capture-option.png)

2. Khi đã bắt đầu bắt gói tin, hãy giải phóng và thay một địa chỉ IP mới bằng các lệnh được ghi bên dưới. Quá trình này có thể khiến cho máy tính của bạn bị mất kết nối mạng tạm thời, và tùy thuộc vào hệ điều hành nó có thể gây gián đoạn kết nối mạng. Để giảm thiểu sự gián đoạn này, hãy đóng bất kỳ chương trình nào đang sử dụng server từ xa và nhập lệnh sau vào cửa sổ lệnh.
	- **Windows:** Gõ lệnh `ipconfig /release` và sau đó là `ipconfig /renew`.
	- Nếu trên **Linux:** Hãy tìm tên của interface mạng chính bằng cách gõ `ifconfig` và quan sát kết quả. Interface này có thể gọi là **eth0** hoặc là một thứ gì khác. Bây giờ sử dụng lệnh `dhclient` để giải phóng địa chỉ IP đã được cấp và sau đó thay một địa chỉ mới. Ví dụ, hãy gõ, `sudo dhclient -r eth0` để giải phóng địa chỉ và sau đó là `sudo dhclient eth0` để thay một địa chỉ khác.
	
	![ipconfig](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/ipconfig.png)
	
3. Một khi bạn đã bắt được một vài lưu lượng DHCP, hãy dừng lại.

<a name="step2"></a>	
### 4. Step 2: Inspect the Trace
* Ở bước này và các bước tiếp theo, chúng ta chỉ xem xét quá trình trao đổi DHCP ngắn được mô tả ở trên. Điều này là do lưu lượng mà bạn bắt được có thể thay đổi qua các thiết lập. Bạn có thể có một vài gói tin DHCP trên một mạng tĩnh (quiet) hoặc nhiều gói tin DHCP trên một mạng bận bộn (busy) (đặc biệt nếu một lớp học đang thực hiện lab này!). Các chi tiết của các gói tin DHCP có thể thay đổi tùy thuộc vào cách máy tính thực hiện DHCP. Có thể có nhiều gói tin cùng một loại trong một quá trình trao đổi do các server sao chép, và cũng có thể có các gói tin DHCP khác loại.
* Hãy tìm quá trình trao đổi DHCP ngắn (trong gói tin DHCP Request và gói tin DHCP Ack) trong file trace. Chọn gói tin DHCP Request, và quan sát chồng giao thức để xem các DHCP message được mang như thế nào. Giao thức liên kết có thể là Ethernet, và giao thức cao hơn là IP. Sau đó đến UDP, vì thế mỗi DHCP message được chứa trong gói tin UDP. Trên đầu UDP, Wireshark có thể báo là **BOOTP** (Bootstrap Protocol) thay vì DHCP. Ở đây khó hiểu một chút, nhưng DHCP được thực hiện như là một phần mở rộng của một giao thức cũ được gọi là BOOTP. Bạn có thể nghĩ phần BOOTP như là DHCP header và message. Xem ví dụ ở dưới:

![bootstrap](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/bootstrap.png)

* Mở rộng phần BOOTP (DHCP) (sử dụng biểu tượng dấu "+" mở rộng) để xem chi tiết của một DHCP Request message. Có nhiều trường, nhưng chúng ta chỉ làm rõ một vài trường hơn là xem chúng hết. Những trường này đều được chứa trong tất cả DHCP message, mặc dù chúng có những giá trị khác nhau trong những message khác nhau.
	- Một Message bắt đầu bằng một **Message Type**. Nó là một **Boot Request**, được đùng để cho tất cả DHCP message gửi từ máy tính bạn đến một DHCP server.
	- Sau một vài trước là một trường **Transaction ID**. Tất cả gói tin DHCP trong một cuộc trao đổi cụ thể giữa một client và server mang cùng một Transaction ID; đó là cách để cả hai thiết bị đầu cuối biết rằng các gói tin thuộc về cuộc trao đổi chứ không phải là một hoạt động DHCP khác xảy ra đồng thời.
	- Có một số trường địa chỉ IP. Các trường này được sử dụng để chứa các địa chỉ chẳng hạn như địa chỉ mà máy tính đang được gán.
	- Có một trường **Magic Cookie**. Nó chứa một giá trị cho thấy phần còn lại của message chứa một loạt các tùy chọn DHCP. Tức là, đây là thực sự là một DHCP message, không phải là một BOOTP message.
	- Mỗi tùy chọn DHCP thì độc lập, với một loại mã thể hiện những gì nó đại diện, cùng với một độ dài và giá trị. Tùy chọn đầu tiên là **DHCP message Type**, cho biết loại DHCP message đang được mang. Những tùy chọn khác sẽ thay đổi với mỗi loại DHCP message. Ví dụ, một DHCP Request sẽ có một tùy chọn **Requested IP Address** để yêu cầu một địa chỉ cụ thể, với một **DHCP Ack** sẽ có một tùy chọn **IP Address Lease Time** cho biết địa chỉ IP này đã được gán bao lâu.

* Bây giờ hãy chọn một gói tin DHCP Ack và so sánh các trường BOOTP. Chúng tôi sẽ hỏi những câu hỏi về những trường này trong phần tiếp theo, nhưng bây giờ chúng tôi muốn bạn quan sát rằng gói DHCP Ack có cùng định dạng chung, nhưng có các giá trị khác nhau trong mỗi trường và mạng các tùy chọn DHCP khác nhau. 
* Bạn có thể duyệt các tùy chọn trong DHCP Request và Ack để tìm hiểu về DHCP. Bạn có thể thấy, ví dụ, địa chỉ IP được server gán bao lâu, tính bằng giây, phút, giờ hoặc bằng giờ. Bạn cũng có thể xem các tham số cấu hình khác được gán bởi DHCP server, chẳng hạn địa chỉ IP của domain name server và Router, subnet mask, tên miền của máy chủ và nhiều hơn nữa.
* Bạn cũng có thể tạo toàn bộ chuỗi DHCP message mà được trao đổi để thiết lập mạng của bạn. Nếu có thể sẽ đơn giản như đoạn trao đổi ngắn với Request và Ack, hoặc nó có thể là một đoạn trao đổi đầy đủ với Discover, Offer, Request và Ack. Nó có thể có những message bổ sung chẳng hạn như Release, và nó cũng có thể có nhiều các message (vì dụ như hai hay nhiều Offer hay Ack) do có nhiều các DHCP server. Làm phúc tạp cuộc trao đổi bằng máy tính của bạn bằng cách có thể bắt các lưu lượng DHCP xảy ra đồng thời thời những máy tính khác. Bạn có thể sử dụng Transaction ID để phân biệt các cuộc trao đổi khác nhau, và hãy nhìn vào địa chỉ Ethernet nguồn để xem những DHCP message nào được gửi bởi máy tính của bạn. Có thể các lưu lượng DHCP khác được trộn vào với cuộc trao đổi của bạn.

<a name="step3"></a>	
### 5. Step 3: Details of DHCP Messages
* Hãy dành thời gian tìm hiểu DHCP. Chú ý vị trí của Ethernet, IP, UDP và khối giao thức BOOTP.
* Trả lời những câu hỏi sau dựa trên việc xem xét các trường BOOTP/DHCP trong cả hai gói DHCP Request và DHCP Ack. Câu trả lời có ở trang tiếp theo.
	1. Hai giá trị nào trong trường **BOOTP Message Type**?
	2. Trường Transaction ID dài bao nhiêu? Hãy cho biết liệu có khả năng các hoạt động DHCP xảy ra đồng thời được thực hiện bởi các máy tính khác nhau sẽ xảy ra để chọn cùng một Transaction ID.
	3. Tên của trường mang địa chỉ IP đang được gán cho client? Bạn sẽ tìm thấy trường này được điền vào DHCP Ack, vì message đó đang hoàn thành nhiệm vụ.
	4. Giá trị Magic Cookie nào là viết tắt cho DHCP?
	5. Tùy chọn DHCP đầu tiên là DHCP Message Type. Giá trị nào viết tắt cho loài này?
	6. DHCP Request thường sẽ có một tùy chọn **Client Identifier**. Hãy xem giá trị của tùy chọn này. Nó định danh Client như thế nào? Hãy đoán xem.
	7. DHCP Ack thường sẽ có một tùy chọn **Server Identifier**. Hãy xem giá trị của tùy chọn này. Nó định danh Server như thế nào? Hãy đoán xem.
	8. Giá trị nào đại diện cho tùy chọn **Requested IP Address**? **IP Address Lease Time**?
	9. Làm sao để bên nhận DHCP message biết được rằng nó đã đạt đến tùy chọn cuối cùng?
	
* Trả lời:
	
	![structure-dhcp-message](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/structure-dhcp-message.png)
	
	1. Hai giá trị là **Boot Request** (1) và **Boot Reply** (2).
	2. Transaction ID dài 4 byte. Do đó rất khó có khả năng xảy ra va chạm trong một số tương đối nhỏ các quá trình DHCP diễn ra đồng thời (cho đến khi con đó tiến đến 216!).
	3. Trường "**Your (client) IP address**" mang địa chỉ IP đang được gán cho client.
	4. Giá trị Magic Cookie DHCP là **0x63825363**.
	5. Giá trị 53 viết tắt cho DHCP Message Type.
	6. Thông thường, Client Identifier mang địa chỉ Ethernet của Client, những có thể sử dụng một số loại định danh khác (ví dụ như hostname, serial number).
	7. Thông thường, Server Identifier mang địa chỉ IP của DHCP Server, những có thể sử dụng một số loại định danh khác.
	8. Giá trị 50 viết tắt cho Request IP Address và 51 là cho IP Address Lease Time.
	9. Phần tùy chọn cuối cùng của DHCP được định danh bằng một tùy chọn DHCP gọi là **End** có giá trị là 255.
	
<a name="step4"></a>	
### 6. Step 4: DHCP Message Addressing
* Bây giờ chúng ta sẽ xem cách DHCP message được đánh địa chỉ đến các máy tính tại các lớp UDP, IP và Ethernet. Điều này rất thú vị bởi vì DHCP được dùng để gán địa chỉ IP - một máy tính yêu cầu một địa chỉ DHCP mà có thể không có địa chỉ IP của riêng nó cũng không biết địa chỉ IP của DHCP server.
* Hãy bắt đầu bằng việc chọn một gói tin DHCP Request và xem chi tiết UDP của nó trong bảng giữa của Wireshark. Chúng ta sẽ chỉ xem DHCP Request message để giữ mọi thứ đơn giản, vì các chi tiết đánh địa chỉ sẽ khác nhau đối với các DHCP message khác. Câu trả lời nằm ở trang tiếp theo.
	1. Port nào mà DHCP client sử dụng, và port nào mà DHCP server sử dụng?
	Port rất quan trọng bởi vì các UDP message được đánh địa chỉ dùng port. Cả hai port này đều nằm trong Request trong trường port nguồn và đích (và bạn cũng sẽ thấy chúng trong Ack).
	
* Bây hãy xem các địa chỉ IP trong IP protocol header của gói tin để đến câu hỏi tiếp theo. Đừng nhìn vào trong các trường BOOTP để xem các tham số DHCP, vì chúng ta quan tâm đến cách mà các DHCP message được đánh địa chỉ tại các lớp giao thức thấp. Khi yêu cầu được gửi đi, máy tính của bạn không có địa chỉ IP và có thể không biết cả địa chỉ IP của DHCP server, vì thế việc đánh địa chỉ IP sẽ khác với một gói tin IP thông thường.
	2. Địa chỉ IP nguồn nào được đặt trong Request message? Nó là một giá trị đặc biệt có nghĩa là "host này nằm trong mạng này" (this host on this network) được dùng để khởi tạo.
	3. Địa chỉ IP đích nào được đặt trong Request message? Nó cũng là một giá trị được dành riêng, được thiết kế để truy cập đến DHCP server ở bất cứ đâu trong mạng nội bộ.
	
* Cuối cùng, xem địa chỉ Ethernet để trả lời câu hỏi tiếp theo.
	4. Địa chỉ Ethernet nguồn nào được đặt trong Request message và địa chỉ Ethernet đích nào được đặt trong Request message? Một trong những địa chỉ này là một địa chỉ dự trữ.

Xem việc đánh địa chỉ sẽ giúp bạn hiểu được tại sao máy tính của bạn có thể ghi lại lưu lượng DHCP của nhiều máy tính nội bộ trong bản trace. Do việc đánh địa chỉ chưa được thiết lập nên nhiều DHCP message được gửi đến tất cả các máy tính trong máy nội bộ. Điều này để chắc chắn mỗi máy tính để nhận được các DHCP message dành cho chúng, nhưng nó cũng đặt ra một khó khăn: một máy tính có thể nhận được các DHCP message mà dành cho các máy tính khác.
	5. Làm cách nào để một máy tính hoạt động với một DHCP message mà nó nhận được dành cho nó cũng như một phản hồi đến DHCP Request message của nó mà không phải là phản hồi dành cho một máy tính không? Gợi ý: Nếu bạn không chắc chắn thì hãy quay lại các trường mà bạn đã xem xét ở Bước 2.
	
* Trả lời:
	1. DHCP client (máy tính của bạn) sử dụng UDP port 68 và DHCP server sử dụng UDP port 67.
	2. Địa chỉ IP nguồn là 0.0.0.0. Nó là một địa chỉ đặc biệt được dùng trong suốt quá trình khởi tạo địa chỉ.
	3. Địa chỉ IP đích là 255.255.255.255. Nó là địa chỉ broadcast, có nghĩa là message được gửi đi cho tất cả các máy tính nằm trong mạng. (Không thể sử dụng một địa chỉ broadcast subnet bị giới hạn, ví dụ như, 192.168.255.255, vì client chưa biết subnet mask).
	4. Địa chỉ Ethernet nguồn đơn giản chính là địa chỉ Ethernet của chính máy tính của bạn, vì nó đã được gán cho NIC của bạn. Địa chỉ Ethernet đích là ff:ff:ff:ff:ff:ff, địa chỉ broadcast Ethernet được đặt riêng, vì thế gói tin đi đến tất cả các máy tính có trong máy nội bộ.
	5. Các DHCP message trong một cuộc trao đổi thì mang cùng một Transaction ID. Như thế, một máy tính tìm kiếm một gói phản hồi DHCP chẳng hạn như một gói Ack với một Transaction ID mà khớp với giá trị nằm trong DHCP message trước chẳng hạn như gói Request (Đây là phần bổ sung cho bất cứ bộ lọc địa chỉ Ethernet: nếu phản hồi là unicast thì nó sẽ lấy địa chỉ Ethernet của máy tính làm địa chỉ đích của nó).
		
---

### Tài liệu tham khảo:

[1] Lab-DHCP. http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/lab-DHCP.pdf

---

### Hết
