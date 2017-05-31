## Netstat

> Tài liệu: Netstat
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **31/05/2017**

### Mục lục
[1. Netstat](#netstat)

[2. Cách sử dụng Netstat](#cachsudung)

---

<a name="netstat"></a>
### 1. Netstat
* Lệnh **netstat** có sẵn trong Command Prompt trên hầu hết các phiên bản Windows bao gồm Windows 8, Windows 7, Windows Vista, Windows XP, các hệ điều hành Windows Server và một số phiên bản Windows cũ cũng có.
* Netstat cho phép bạn hiển thị các số liệu về Ethernet interface. Nếu bất kỳ lỗi nào được hiển thị trên màn hình, bạn có thể gặp một số vấn đề với kết nối mạng, điều làm cho kết nối mạng chậm lại. Nếu các gói tin lỗi tiến đến 1% tổng số các gói tin, có thể là một vài vấn đề với NIC hoặc interface vật lý của bạn.

<a name="cachsudung"></a>
### 2. Cách sử dụng Netstat
1. Mở Command Prompt hoặc DOS Prompt.
2. Gõ vào `netstat` để liệt kê các kết nối mạng hiện tại, không chỉ các kết nối bên trong (inbound) mà cũng có các kết nối bên ngoài (outbound).
3. Bạn hãy xem một danh sách các kết nối được liệt kê. Rất hữu dụng để truy tìm các cuộc tấn công trực tiếp.
4. Gõ vào `netstat -?` để xem các tùy chọn với lệnh này. Bạn hãy để một số tùy chọn: -a, -e, và một số tùy chọn khác.
5. Bây giờ hãy nhập `netstat -a`.
6. Nhập `netstat -e`. Các số liệu này bao gồm số lượng byte và gói tin nhận được và gửi qua Ethernet interface.
7. Gõ `netstat -f`. Lệnh này sẽ hiển thị thông tin của tất cả các kết nối đang hoạt động.
8. Để xem các thống kê về các giao thức, dùng lệnh `netstat -s`.
9. Để giới hạn hiển thị chỉ thống kê IP, gõ `netstat - ps IP` và nhấn Enter.
10. Để xem bảng thống kê các mạng đang hoạt động cập nhật mỗi 5 giây một lần, gõ `netstat -e -t 5` và nhấn Enter. Nhấn **Ctrl + C** để dừng chương trình.
11. Lệnh `netstat -o`. Lệnh này hiển thị các kết nối TCP đang hoạt động, nhưng nó cũng hiển thị mã nhận dạng tương ứng [-o] cho mỗi kết nối vì bạn có thể xác định chương trình nào trên máy tính đã khởi tạo.
12. Chú ý đến cột PID. Trong một số trường hợp, các PID đều giống nhau, có nghĩa là cùng một chương trình trên máy tính đã mở các kết nối này. Tuy nhiên để xác định chương trình nào được đại diện bởi số PID 2948 trên máy tính, tất cả bạn phải làm là mở *Task Manager*, nhấn vào thẻ *Processes*, chú ý *Image Name* liệt kê bên cạnh số PID bạn đang tìm trong cột PID. Hãy mở và thử làm điều này. Ngoài ra, cũng phải lưu ý rằng việc sử dụng lệnh **netstat** với tùy chọn **-o** rất có hữu ích khi theo dõi chương trình nào đang sử dụng băng thông quá lớn. Nó cũng có thể giúp định vị vị trí của một số loại mã độc, hoặc thậm chí là một số phần mềm hợp pháp khác, có thể gửi thông tin đi mà không có sự cho phép của bạn.
Lưu ý: Mặc dù ví dụ này và ví dụ trước được chạy trên cùng một máy tính và chỉ trong một phút, bạn có thể thấy rằng danh sách các kết nối TCP đang kết nối khác biệt đáng kể. Điều này là do máy tính của bạn liên tục kết nối và ngắt kết nối với các thiết bị khác trong mạng của bạn và qua Internet.
13. Để hiển thị thông tin ICMP, gõ `netstat -ps ICMP` và nhấn Enter. Một loạt các loại ICMP message được hiển thị cùng với số lượng của mỗi loại đã được nhận và gửi đi. Hầu hết, nếu không phải là tất cả, thì sẽ là các Echo và Echo Reply message.
14. Hỏi địa chỉ IP của một bạn khác. Sau đó sử dụng ví dụ. Gõ `ping 193.61.191.71` và nhấn Enter. Lệnh này sẽ tạo các message *ICMP Destination Unreachable*.
15. Để xem số lượng các message ICMP Destination Unreachable tăng, hãy nhập `netstat -ps ICMP`  và nhấn Enter. Các message *ICMP TTL-Expired* sử dụng trong Tracert được gọi là các message *Time Exceeded* trong Netstat.
16. Nhập `tracert www.ulster.ac.uk` và nhấn Enter.
17. Để xem số lượng các message Time Exceeded tăng lên, gõ `netstat -ps ICMP` và nhấn Enter.
18. Để hiển thị bảng định tuyến của máy tính bạn, nhập `netstat -r` và nhấn Enter. Mỗi máy tính đều có một bảng định tuyến để quyết định interface nào sẽ gửi các gói tin đi. Dòng đầu tiên liệt kê các đích là **0.0.0.0**, đó là **default gateway** của bạn.
19. Cuối cùng, gõ `netstat -s -p tcp -f`. Ở đây chúng ta muốn xem bảng thống kê cụ thể của giao thức [-s] nhưng không phải tất cả chúng, chỉ xem của TCP [-p tcp]. Chúng ta cũng muốn các địa chỉ bên ngoài (foreign) được hiển thị dưới dạng FQDN [-f]. Hãy cuộn lên cửa sổ lệnh để xem bảng thống kê TCP được hiển thị trước khi danh sách các kết nối đang hoạt động được tạo.

---

### Tài liệu tham khảo:

[1] Netstat. http://scisweb.ulster.ac.uk/~kevin/com320/labs/netstat.html

---

### Hết
