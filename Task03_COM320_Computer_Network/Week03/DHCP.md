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
---


<a name="muctieu"></a>
### 1. Mục tiêu
* Hiểu được cách hoạt động của **DHCP** (Dynamic Host Configuration Protocol). File trace ở đây:
<scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/trace-dhcp.pcap>

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
	
	![ipconfig](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/ifconfig.png)
	
	3. Một khi bạn đã bắt được một vài lưu lượng DHCP, hãy dừng lại.

<a name="step2"></a>	
### 4 Step 2: Inspect the Trace
* Ở bước này và các bước tiếp theo, chúng ta chỉ xem xét quá trình trao đổi DHCP ngắn được mô tả ở trên. Điều này là do lưu lượng mà bạn bắt được có thể thay đổi qua các thiết lập. Bạn có thể có một vài gói tin DHCP trên một mạng tĩnh (quiet) hoặc nhiều gói tin DHCP trên một mạng bận bộn (busy) (đặc biệt nếu một lớp học đang thực hiện lab này!). Các chi tiết của các gói tin DHCP có thể thay đổi tùy thuộc vào cách máy tính thực hiện DHCP. Có thể có nhiều gói tin cùng một loại trong một quá trình trao đổi do các server sao chép, và cũng có thể có các gói tin DHCP khác loại.
* Hãy tìm quá trình trao đổi DHCP ngắn (trong gói tin DHCP Request và gói tin DHCP Ack) trong file trace. Chọn gói tin DHCP Request, và quan sát chồng giao thức để xem các DHCP message được mang như thế nào. Giao thức liên kết có thể là Ethernet, và giao thức cao hơn là IP. Sau đó đến UDP, vì thế mỗi DHCP message được chứa trong gói tin UDP. Trên đầu UDP, Wireshark có thể báo là **BOOTP** (Bootstrap Protocol) thay vì DHCP. Ở đây khó hiểu một chút, nhưng DHCP được thực hiện như là một phần mở rộng của một giao thức cũ được gọi là BOOTP. Bạn có thể nghĩ phần BOOTP như là DHCP header và message. Xem ví dụ ở dưới:

![bootstrap](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/bootstrap.png)
	
---

### Tài liệu tham khảo:

[1] Lab-DHCP. http://scisweb.ulster.ac.uk/~kevin/com320/labs/wireshark/lab-DHCP.pdf

---

### Hết