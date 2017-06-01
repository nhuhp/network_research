## NetInfo

> Tài liệu: NetInfo
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **01/06/2017**

### Mục lục

[1. NetInfo](#netinfo)

[2. Cách sử dụng NetInfo](#cachsudungnetinfo)

---

<a name="netinfo"></a>
### 1. NetInfo
**Sử dụng Netinfo để thu thập thông tin Máy tính và Mạng.** 

* Nó chính xác là một **ping flood**. Một chương trình gửi một số lượng lớn các gói tin ping để một host. Chúng làm cho host đó phải reply, gây ngắt chu kỳ CPU và băng thông. Một biến thể là **tấn công Smurf** (Smurf attack), trong đó các gói ping sẽ được gửi đến một địa chỉ broadcast. Tất cả các request chứa địa chỉ nguồn giả mạo được smurf. Khi các máy tính respond đến các gói ping broadcast, chúng gửi reply đến một host duy nhất mà có địa chỉ là giả mạo. Host lúc này bị tràn ngập các gói ping response, gây chậm hoặc thậm chí đóng băng khi nó xử lý tất cả các gói tin. Các cuộc tấn công từ chối dịch vụ phân tán (Distributed denial-of-service - DDoS) sử dụng nhiều hệ thống để tấn công một tài nguyên mạng duy nhất. Thường thì các hệ thống tấn công không biết mình đang tham gia vì phần mềm tấn công được cài đặt như là một phần mềm độc hại và được thiết lập hoạt động vào ngày và khoảng thời gian nhất định.
* Trong project này, bạn hãy tải và cài đặt một phiên bản Netinfo dùng thử. Netinfo là một tuyển tập 15 công cụ mạng hiện tại trên một giao diện đơn giản và dễ sử dụng. File tải về là một file *Microsoft installer* (.msi), có nghĩa là phải giải nén để chạy nó.

<a name="cachsudungnetinfo"></a>
### 2. Cách sử dụng Netinfo
1. Khởi động trình duyệt Web và [tải](http://scisweb.ulster.ac.uk/~kevin/com320/labs/netinfo.msi) netinfo.msi.
2. Làm theo hướng dẫn để tải và cài đặt NetInfo.

![netinfo](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/netinfo.png)

3. Hỏi một người bạn của bạn về địa chỉ IP của họ, ví dụ, 192.168.1.105.
4. Gõ **`ping ten-maytinh`** (thay ten-maytinh bằng tên máy tính mà bạn chọn, ví dụ, 192.168.1.105) và nhấn Enter.
5. Khởi động **NetInfo**.
6. Nhấn vào thẻ **Services**, trong ô **Host**, nhập vào địa chỉ IP ở trên và nhấn **Verify**. (Nếu bạn làm project này một mình, bạn có thể nhập **127.0.0.1** trong ô Host để quét chính máy tính của bạn).
7. Bạn sẽ thấy màn hình giống với hình dưới.

![netinfo-scan-port](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/netinfo-scan-port.png)

8. Tìm những port có trạng thái Mở (**Open**). Những port mở đại diện các dịch vụ mạng mà máy tính cung cấp nhưng cũng biểu thị các lỗ hổng mà kẻ tấn công có thể khai thác. Ghi lại tên và số của các port này:

![open-port](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/open-port.png)

9. Xóa output của lệnh gần đây bằng cách nhấn chuột phải trên NetInfo, trỏ đến **Clear**, và chọn **All**.

![clear-output](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/clear-output.png)

10. Tiếp theo, bạn sẽ quét một phạm vi địa chỉ IP để xem máy tính nào đang hoạt động trong mạng. Bạn làm điều này bằng cách chọn vào thẻ **scanner**.
11. Trong ô **Address**, nhập 3 octet đầu của địa chỉ IP mà bạn đã sử dụng trước đó và số 0 cho octet cuối cùng. Ví dụ, nếu địa chỉ bạn sử dụng là 192.168.1.105, hãy nhập 192.168.1.0. Thiết lập này sẽ quét tất cả các địa chỉ từ 192.168.1.0 đến 192.168.1.255.
12. Bạn sẽ thấy màn hình giống với hình dưới.

![netinfo-scan-ip](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/netinfo-scan-ip.png)

13. Nhấn **Start**. Ghi lại tên và địa chỉ của 3 máy tính địa chỉ mà NetInfo hiển thị trạng thái "**Host is alive**". (Bạn có thể sắp xếp các kết quả bằng cách nhấn vào cột **Status**).
14. Ở cột **Name**, nhấn chuột phải vào một trong các máy tính, trỏ đến **Send to**, và nhấn **Services**. Bên thẻ **Services**, nhấn **Verify** để xem danh sách của dịch vụ mà máy tính này cung cấp.

![send-to](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/send-to.png)

15. Bạn sẽ thấy kết quả giống thế này:

![netinfo-scan-comp](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week02/img/netinfo-scan-comp.png)

16. Bây giờ hãy trở lại danh sách các host alive lúc trước và thử "send to" với những dịch vụ khác.

### Tài liệu tham khảo:

[1] NetInfo.http://scisweb.ulster.ac.uk/~kevin/com320/labs/netinfo.html

---

### Hết
