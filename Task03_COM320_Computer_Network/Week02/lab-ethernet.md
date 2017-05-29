## Lab Ethernet	

> Tài liệu: Lab Ethernet
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **29/05/2017**

### Mục lục
[1. Mục tiêu](#muctieu)
[2. Yêu cầu](#yeucau)
[3. Step 1: Capture a Trace](#step1)
[4. Step 4: Inspect the Trace](#step2)

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

#### 4. Step 2: Inspect the Trace
* Chọn bất kỳ gói tin nào trong file trace (trong bảng phía trên) để xem chi tiết cấu trúc của nó (trong bảng ở giữa) và các byte tạo thành gói tin đó (trong bảng phía dưới). Bây giờ chúng ta hãy kiểm tra chi tiết của các gói tin. Như trong hình, chúng ta chọn gói tin đầu tiên trong file trace. Chú ý rằng chúng ta đang sử dụng thuật ngữ "gói tin" một cách tùy tiện. Mỗi record bị bắt bởi Wireshark tương ứng chính xác hơn với một frame trong định dạng Ethernet mà mang một gói tin như là payload của nó; Wireshark có thể phân tích cấu trúc này càng nhiều càng tốt.
* Trong bảng ở giữa, mở các trường Ethernet header (sử dụng dấu mở rộng hoặc biểu tượng "+") để thấy thông tin chi tiết của chúng. Mối quan tâm của chúng ta là Ethernet header, bạn có thể bỏ qua các giao thức ở các tầng cao hơn (trong trường hợp này là IP và ICMP). Chú ý những điều sau:
	- Các frame trong trace này là DIX Ethernet, gọi là "**Ethernet II**" trong Wireshark.
	- Không có trường Preamble trong các trường được hiển thị trong Wireshark. Preamble là một cơ chế ở tầng Vật lý để giúp NIC định danh được điểm khởi đầu của một frame. Nó không mang dữ liệu hữu ích nào và không nhận được như những trường khác.
	- Có một địa chỉ đích và một địa chỉ nguồn. Wireshark giải mã một số bit trong phần OUI (Organizationally Unique Identifier) của địa chỉ và cho biết nhà cung cấp của NIC, ví dụ: Dell cho địa chỉ nguồn.
	- Có một trường **Type**. Đối với các ping message, loại Ethernet là IP, có nghĩa là Ethernet payload mang một gói tin IP. (Không có trường Độ dài (Length) như trong định dạng IEEE 802.3. Thay vào đó, độ dài của một Ethernet frame được xác định bởi phần cứng của máy nhận, trong đó tìm những frame hợp lệ mà bắt đầu là một preamble và kết thúc là một checksum chính xác, sau đó đẩy lên các tầng cao hơn cùng với gói tin).

---

### Tài liệu tham khảo:

[1] Lab Ethernet. http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/lab-ethernet.pdf

---

### Hết
