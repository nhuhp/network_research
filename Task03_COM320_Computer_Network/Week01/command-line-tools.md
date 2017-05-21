## Command Line Tools

> Tài liệu: Command Line Tools
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **21/05/2017**

### Mục lục

[1. IPConfig](#ipconfig)

[2. Tracert](#tracert)

[3. NSLookup](#nslookup)

[4. ARP](#arp)

[5. Ping](#ping)

[6. Net Sessions](#netsessions)

[7. Openfiles](#openfiles)

[8. Fc](#fc)

[9. Pathping](#pathping)

---

<a name="ipconfig"></a>
### 1. IPConfig
* IPConfig cho phép một Network Manager xem các thiết lập hệ thống TCP/IP và tái cấu hình nếu cần thiết. Đây là một công cụ tiêu chuẩn có mặt ở mọi phiên bản Windows. Nó có thể được sử dụng để xử lý xử cố mạng.
1. Mở một command prompt. Một cách để làm việc này làm nhấn **Windows key** và **R** và sau đó gõ **cmd**.
(Lưu ý, windows key nằm giữa CTRL và ALT ở bên trái bàn phím). Do giới hạn của bài lab, trước khi nhấn vào Command Prompt, chuột phải vào icon Command Prompt và chọn "Run as Administrator" từ phía dưới màn hình. Đây là cách bạn có thể làm bài hướng dẫn ARP đầy đủ.
2. Tại Command Prompt, gõ `ipconfig`.

![ipconfig-1](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/ipconfig-1.png)

3. Chú ý đến địa chỉ IP, default gateway và subnet mask của máy tính.

![ipconfig-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/ipconfig-2.png)

4. Sử dụng `-?` sau ipconfig để tìm thêm những tùy chọn khác mà bạn có với những lệnh này. Bạn nên chú ý đến một số tùy chọn, bao gồm ***/all***, ***/renew*** và một số khác.

![ipconfig-3](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/ipconfig-3.png)

5. Bây giờ hãy thử `ipconfig /all`. Bạn thấy những gì mà bạn đã thấy trước đó?

![ipconfig-4](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/ipconfig-4.png)

<a name="tracert"></a>
### 2. Tracert
* Tracert xác định đường đi đến một đích bằng cách gửi đến đích các gói tin echo Internet Control Message Protocol (ICMP) với các giá trị IP Time-to-Live (TTL) thay đổi. Mỗi Router trên đường đi được yêu cầu giảm giá trị TTL trên một gói tin ít nhất là 1 trước khi forward nó đi. Khi TTL trên một gói tin đạt 0, router sẽ gửi một "ICMP Time Exceeded" message trở về máy tính nguồn. Tracert xác định đường đi bằng cách gửi gói echo đầu tiên với TTL là 1 và tăng TTL lên 1 với mỗi truyền tiếp theo cho đến khi mục tiêu phản hồi lại hoặc đạt đến giá trị TTL cực đại. Đường đi đường xác định bằng cách kiểm tra các "ICMP Time Exceeded" message gửi lại từ những router trung gian. Một số router âm thầm đánh drop các gói tin có TTL hết hạn và trở nên vô hình với Tracert. Lệnh Tracert sẽ in ra một danh sách được sắp xếp, các interface nằm gần của các router trên đường đi mà "ICMP Time Exceeded" message trả về. Nếu sử dụng tùy chọn ` -d`, Tracert không thực hiện tra cứu DNS trên mỗi địa chỉ IP.
1. Mở Command Prompt.
2. Đáng lý ra là bạn sẽ gõ **`tracert www.ulster.ac.uk`** tuy nhiên nó đã bị khóa trong trường, nên hãy vào trang <tools.pingdom.com>
3. Gõ `www.ulster.ac.uk` vào ô ping và chọn tracert ở bên phải trong phần lựa chọn.
4. Nó sẽ thực hiện vài phần kiểm tra tracert dưới dạng biểu đồ. Bạn sẽ thấy một màn hình tương tự thế này:

![tracert](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/tracert.png)

5. Chú ý đến những hops mà máy tính đi qua để tới www.ulster.ac.uk.
6. Sau đó hãy thử thực hiện tương tự với những trang khác.
7. Bạn có để ý rằng một vài hops đầu tiên giống nhau không? Hãy viết lại các hops đi qua đến đích, và những hops giống nhau. Tại sao bạn nghĩ một số bước trung gian lại giống nhau với các đích khác nhau?

<a name="nslookup"></a>
### 3. NSLookup
* NSLookup là một công cụ quản trị mạng cho nhiều hệ điều hành máy tính để truy vấn Domain Name System (DNS) để lấy tên miền hoặc map địa chỉ IP hoặc cho bất kỳ DNS record cụ thể nào khác.
1. Mở Command Prompt.
2. Gõ `nslookup www.ulster.ac.uk`.
3. Bạn sẽ thấy: 

![nslookup](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/nslookup.png)

4. Lưu ý rằng lệnh này sẽ cung cấp cho bạn tên thật của server, theo quy ước đặt tên của mỗi công ty hosting; địa chỉ IP; và bất kỳ alias nào hoạt động dưới server đó.

<a name="arp"></a>
### 4. ARP


<a name="ping"></a>
### 5. Ping

<a name="netsessions"></a>
### 6. Net Sessions
Net Sessions là một công cụ dùng để quản lý kết nối máy tính server. Được sử dụng mà không cần tham số, net session sẽ hiển thị thông tin về tất cả các session với máy local.
1. Mở Command Prompt.
2. Gõ `net sessions` nếu bất kỳ session nào đang hoạt động được kết nối với máy tính của bạn.
3. Nhiều khả năng sẽ hiện trạng thái "There are no sessions in the list."
4. Bạn có thể thử truy cập máy tính của bạn từ xa và thực hiện lại lệnh này.
<a name="openfiles"></a>
### 7. Openfiles

<a name="fc"></a>
### 8. Fc

<a name="pathping"></a>
### 9. Pathping




### Tài liệu tham khảo:



---

### Hết
