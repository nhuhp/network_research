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
* Tiếp theo, bạn sẽ sử dụng lệnh arp để xem và xóa ARP cache, và bạn sẽ sử dụng lệnh ping để tạo ra ARP cache ban đầu. **Address Resolution Protocol (ARP) ** là một giao thức truyền thông dùng để phân giải địa chỉ tầng network thành địa chỉ tầng link, một chức năng quan trọng trong mạng đa truy cập (multiple-access). ARP được định nghĩa trong RFC 826 và cũng là tên của chương trình làm việc với những địa chỉ này trên hầu hết các hệ điều hành. Hãy chắc chắn rằng bạn chọn "Run as Administrator" khi khởi động Command Prompt.

![arp](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/arp.png)

1. Mở Command Prompt.
2. Gõ `arp -a`. Ghi nhớ rằng, lúc trước, máy tính đã phát hiện ra địa chỉ MAC của máy tính bạn bằng cách sử dụng ARP. Bây giờ bạn đã có địa chỉ MAC duy nhất cho máy tính của mình.
3. Một danh sách các cặp địa chỉ IP/địa chỉ MAC được hiển thị. Trường Type (cột thứ ba) biểu thị các entry là tĩnh hay động. Windows 7 thì tự động tạo ra các entry tĩnh, những các entry động được tạo ra từ các giao tiếp mạng. Nếu bạn không có entry nào, thông báo "No ARP Entries Found" sẽ hiện lên.
4. Để xóa ARP cache, gõ `arp -d` và nhấn Enter.
5. Để xác nhận rằng các entry đã được xóa, gõ `arp -a` và nhấn Enter một lần nữa.
6. Hỏi một ai đó trong phòng lab về địa chỉ IP. Họ có thể xem được bằng cách gõ `ipconfig`.
7. Gõ `ping 193.61.191.XX` (thay XX bằng địa chỉ IP của một máy tính khác trong mạng) ví dụ 193.61.191.71 và nhấn Enter.
8. Gõ `arp -a` để hiển thị lại ARP cache. Bạn sẽ thấy địa chỉ mà bạn ping đi cùng vói địa chỉ MAC của nó.
9. Gõ `arp -d` để xóa ARP cache.
10. Gõ `ping 193.61.191.XX` và nhấn Enter. (Nhớ thay XX bằng số bạn của bạn).
11. Gõ `arp -a` để hiển thị lại ARP cache. Có lẽ bạn sẽ thấy hai entry trong ARP cache.

<a name="ping"></a>
### 5. Ping

* Ping là một chương trình Internet cơ bản, cho phép bạn kiểm tra một địa chỉ Internet cụ thể có tồn tại và có chấp nhận các request. Động từ **png** có nghĩa là hành động sử tiện ích hay lệnh ping. Ping được dùng để đảm bảo rằng host mà bạn đang cố gắng truy cập đến thì đang hoạt động thật sự. Ví dụ, nếu, một người dùng không thể ping một host, thì người dùng đó sẽ không thể dùng File Transfer Protocol (FTP) để gửi file đến host đó. Ping cũng có thể được sử dụng trên một host đang hoạt động để xem nó mất bao lâu để response trở lại. Sử dụng ping, bạn có thể biết được địa chỉ IP ở dạng số từ một tên miền chứa kí hiệu. Theo một cách hiểu khác, ping có nghĩa là "to get attention of " (nhận được chú ý từ) hoặc "to check the presence of" (kiểm tra sự có mặt của) một bên (ứng dụng) khác. Ping hoạt động bằng cách gửi một gói tin đến một địa chỉ được chỉ định và chờ phản hồi.

![ping](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/ping.png)

1. Mở Command Prompt hoặc DOS Prompt.
2. Sử dụng tùy chọn `-?` trên lệnh ping và tìm ra những tùy chọn khác mà bạn có với những lệnh. Bạn nên chú ý một vài tùy chọn như là **-w**, **-t**, **-n**, **-i**.
3. Nhờ một người bạn cho bạn địa chỉ IP của họ. Nó sẽ tương tự như 193.61.191.72
4. Bây giờ thử một lệnh ping đơn giản đến máy tính của họ sử dụng, ví dụ `ping 193.61.191.72`. Nhớ sử dụng địa chỉ IP của họ (không phải là ví dụ này).
5. Thử sử dụng tùy chọn **`ping -n 2 IP ADDRESS`**, sau đó thử **`ping -n 7 IP ADDRESS`**. Khác nhau ở chỗ nào?
6. Lưu ý rằng có thực hiện một cuộc tấn công Từ chối Dịch vụ (Denial of Service - DoS) với lệnh **`ping -l 65000 -w0 -t`**.


<a name="netsessions"></a>
### 6. Net Sessions
Net Sessions là một công cụ dùng để quản lý kết nối máy tính server. Được sử dụng mà không cần tham số, net session sẽ hiển thị thông tin về tất cả các session với máy local.
1. Mở Command Prompt.
2. Gõ `net sessions` nếu bất kỳ session nào đang hoạt động được kết nối với máy tính của bạn.
3. Nhiều khả năng sẽ hiện trạng thái "There are no sessions in the list."
4. Bạn có thể thử truy cập máy tính của bạn từ xa và thực hiện lại lệnh này. 

<a name="openfiles"></a>
### 7. Openfiles
* Openfiles truy vấn hoặc hiển thị những file mở. Nó cũng truy vấn, hiển thị hoặc ngắt kết nối với những file được mở bởi các người dùng trong mạng.
1. Mở Command Prompt.
2. Gõ vào `openfiles` nếu có file được share nào đang được mở. Có hữu ích để tìm các cuộc tấn công trực tiếp.
3. Nhiều khả năng là trạng thái "INFO: No share open files found".
4. Bạn nên thử truy cập từ xa đến máy của bạn và sau đó thực hiện lại lệnh này sau khi mở file.

<a name="fc"></a>
### 8. Fc
* Fc là một lệnh mà bạn có thể sử dụng với một bản sao chép của một máy. Nó so sánh hai file và cho biết sự khác nhau. Nếu bạn nghĩ một file cấu hình đã bị thay thế, bạn có thể so sánh với một một bản lưu trữ.
1. Mở Command Prompt, di chuyển đến thư mục chứa file bạn muốn so sánh, ví dụ C:\Windows.
2. Tìm một file log và sao chép nó (bạn có thể thực hiện phần bên ngoài command lines trong Windows), thay đổi file, và sau đó so sánh nó với phiên bản chưa thay đổi. Bạn có thể tải những file này [setupact.log](http://scisweb.ulster.ac.uk/~kevin/com320/labs/setupact.log) và [setupact1.log](http://scisweb.ulster.ac.uk/~kevin/com320/labs/setupact.log) bằng cách chuột phải và "save as".
3. Gõ `fc setupact.log setupact1.log`.
4. Bạn sẽ thấy những thay đổi.

<a name="pathping"></a>
### 9. Pathping - To try outside the lab
* Lệnh Pathping là một công cụ theo dấu đường đi kết hợp những tính năng của lệnh *ping* và *tracert* với những thông tin mở rộng mà cả hai công cụ này cung cấp. Lệnh pathping gửi các gói tin đến mỗi router trên đường đi đến điểm cuối trong một khoảng thời gian, và sau đó tính toán kết quả dựa trên những gói tin trả về từ mỗi hop. Vì lệnh cho biết mức độ mất gói tin tại bất kỳ router hay kết nối nào, nên đễ dàng xác định router nào hoặc kết nối nào gây ra vấn đề mạng. Số lượng hop mặc định là 30, và thời gian chờ mặc định trước một time-out là 3 giây. Khoảng thời gian mặc định là 250 mili giây, và số lượng truy vấn mặc định đến mỗi router trên đường là 100.
1. Mở Command Prompt.
2. Gõ `pathping www.ulster.ac.uk`.
3. Bạn sẽ thấy như sau:

![pathping-1](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/pathping-1.png)

4. Khi pathping hoạt động, ban đầu sẽ thấy kết quả đường đi vì nó được kiểm tra để tìm lỗi. Đây là đường đi giống với đường đi từ lệnh tracert. Sau đó lệnh pathping hiển thị một thông báo bận trong một vài phút (thời gian sẽ thay đổi theo hop count). Trong suốt khoảng thời gian này, pathping sẽ thu thập thông tin từ tất cả router được liệt kê trước đó và các kết nối giữa chúng. Tại thời điểm cuối cùng, kết quả sẽ được hiển thị.

![pathping-2](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week01/img/pathping-2.png)

Chú ý đến hai cột bên phải ngoài cùng - Node/Link Lost/Sent = Pct và Address - chứa những thông tin hữu ích nhất. Tìm những kết nối có độ giảm phần trăm các gói tin. Tỷ lệ hao hụt thể hiện kết nối (được đánh dấu là `|` ở cột bên phải ngoài cùng) biểu thị hao hụt gói tin được forward trên đường đi. Hao hụt này cho thấy sự tắc nghẽn kết nối. Tỷ lệ hao hụt hiển thị cho router (biểu thị bởi địa chỉ IP của chúng trong cột bên phải ngoài cùng) cho thấy CPU của những router này có thể bị quá tải. Những router bị tắc nghẽn cũng có thể là một tác nhân trong những vấn đề đầu cuối, đặc biệt là những gói tin được forward bằng những router phần mềm.

### Tài liệu tham khảo:

[1] Command Line Tools. http://scisweb.ulster.ac.uk/~kevin/com320/labs/ping&more.html

---

### Hết
