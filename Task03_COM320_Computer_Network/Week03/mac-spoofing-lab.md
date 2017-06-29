## Mac Spoofing Lab

> Tài liệu: Mac Spoofing Lab
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **29/06/2017**

### Mục lục

[1. Tổng quan](#tongquan)

[2. Các bước thực hiện](#cacbuocthuchien)

---

<a name="tongquan"></a>
### 1. Tổng quan
* MAC Spoofing cho phép kẻ tấn công chiếm được quyền truy cập vào một hệ thống mạng mà có sử dụng **MAC filtering**. Khi một AP đã kích hoạt MAC filtering, chỉ có những user có địa chỉ MAC trong Access Control List (ACL) được phép kết nối vào AP. Kẻ tấn công có thể thay đổi địa chỉ MAC của mình thành một trong các địa chỉ trong ACL của AP và kết nối đến AP. Bài thực hành lab này trình bày cách thức hoạt động MAC Spoofing bằng cách sử dụng **Win7 MAC Address Change v1.9**.
* **Win7 MAC Address Changer** là một chương trình windows đơn giản miễn phí, có thể thay đổi địa chỉ MAC (Media Access Control) của adapter mạng không dây và có dây (Không phải Router). Win7 MAC Address Changer được phát triển thành một tiện ích rất đơn giản.
* Trên thực tế, có nhiều cách sử dụng việc đổi địa chỉ MAC (địa chỉ vật lý) chẳng hạn như xử lý sự cố mạng, phần mềm và các thành phần phần cứng, để ẩn danh tính của bạn trong mạng hoặc chỉ để giải trí. Một cách dùng khác trong thực tế là trong khách sạn hoặc sân bây mà có lọc địa chỉ MAC. Cái này cho phép các dịch vụ công cộng 'vô hiệu hóa' Internet 'miễn phí' sau một khoảng thời gian là 30 phút hoặc 60 phút. Sau đó họ thường hy vọng bạn sẽ mua thêm phút. Nếu bạn không còn tiền và không thể trả tiền nhưng cần phải online, hãy làm theo hướng dẫn ở đây sẽ cho phép bạn giả mạo địa chỉ MAC sau mỗi lần hết hân và vẫn giữ kết nối miễn phí...

<a name="cacbuocthuchien"></a>
### 2. Các bước thực hiện
* Bạn phải đảm bảo công việc của bạn đã được lưu lại trước khi bắt đầu bài thực hành này vì bạn có thể mất quyền truy cập đến ổ đĩa mạng trong một khoảng thời gian ngắn vì chúng ta phải kích hoạt/vô hiệu hóa địa chỉ MAC để khởi động nó lại.
1. Tải **Win7 MAC Address Changer** từ:
	http://scisweb.ulster.ac.uk/~kevin/com320/labs/Win7MacAddressChanger.exe
2. Cài đặt chương trình và làm theo hướng dẫn.
3. Khởi động chương trình.
4. Mở cmd.
5. Trong cmd, gõ `ipconfig /all`. Chú ý đến địa chỉ MAC vật lý của card mạng. Xem hình.

![ipconfig-all](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/ipconfig-all.png)

6. Quay lại chương trình MAC Address Changer và chọn interface cần thay đổi. Bạn nên chọn interface mạng chính trên máy của bạn. Ở đây là **a**. Interface chính của bạn có thể mặc định đã được chọn rồi.

![choose-interface](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/choose-interface.png)

7. Tiếp theo là chọn hệ điều hành.

![choose-os](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/choose-os.png)

8. Tiếp theo, chọn phím **Randomize**. Điều này sẽ tạo một địa chỉ MAC mới dựa theo các hạn chế trên địa chỉ MAC.

![choose-randomize](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/choose-randomize.png)

9. Cuối cùng, chọn **Change**. Và bây giờ địa chỉ MAC của bạn đã được thay đổi trên máy tính.

![choose-change](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/choose-change.png)

10. Một cửa sổ pop up sẽ hiện ra và yêu cầu bạn vô hiệu hóa/kích hoạt lại (disable/re-enable) interface mạng.

![pop-up](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/pop-up.png)

11. Điều này có thể được thực hiện bằng cách vào *Network and Internet*/*Network and Sharing Center* trong *Control Panel*. Sau đó chọn kết nối Có dây (Wired) hoặc Không dây (Wireless).

![network-control-panel](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/network-control-panel.png)

12. Tại đây, một popup về thuộc tính card mạng sẽ hiện lên. Chọn phím **Disable**.

![card-properties-popup](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/card-properties-popup.png)

13. Interface đã bị vô hiệu hóa. Bây giờ bạn cần quay lại *Network Connections* và chuột phải trên interface đã bị vô hiệu hóa và kích hoạt nó lại.

![re-enable](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/re-enable.png)

14. Quay trở lại cmd.
15. Gõ `ipconfig /all` và kiểm tra địa chỉ MAC được chỉ định trên interface mà bạn chọn lúc trước. Địa chỉ MAC này bây giờ sẽ giống với địa chỉ MAC được chọn ngẫu nhiên bởi chương trình.

![check](https://github.com/nhuhp/network_research/blob/master/Task03_COM320_Computer_Network/Week03/img/check.png)

16. Cuối cùng, để xóa, thay đổi địa chỉ MAC trở về giá trị trước, chọn phím **Reset to Default** trên Win7 MAC Address Changer.

Hãy chú ý, bạn có thể mất kết nối mạng với ổ đĩa mạng trong một khoảng thời gian ngắn. Đó là tại sao bạn nên làm theo các bước ở trên và khôi phục địa chỉ MAC của bạn về giá trị mặc định của nó.


---

### Tài liệu tham khảo:

[1] Mac Spoofing Lab.http://scisweb.ulster.ac.uk/~kevin/com320/labs/Mac%20Spoofing%20Lab.pdf

---

### Hết
