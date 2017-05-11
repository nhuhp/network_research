## Git và Github

> Tài liệu: Git and Github
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **10/05/2017**

### Mục lục

[1. Git và Github](#gitvagithub)
- [1.1 Git](#git)

- [1.2 Cơ chế hoạt động của Git](#cochehoatdongcuagit)
 
- [1.3 Github](#github)

[2. Một số lệnh cơ bản của Git](#motsolenhcobancuagit)

- [2.1. Add](#add)

- [2.2. Remove](#remove)

- [2.3. Commit](#commit)

- [2.4. Push](#push)

- [2.5. Fetch](#fetch)

- [2.6. Clone](#clone)

- [2.7. Fork](#fork)

- [2.8. Star](#star)

- [2.9. Watch](#watch)

- [3.10. Pull](#pull)

[3. Cài đặt Git, Generate, add SSH Key](#caidatgitgenerateaddsshkey)

- [3.1. Cài đặt Git](#caidatgit)

- [3.2. Các thiết lập ban đầu](#cacthietlapbandau)

- [3.3. Liên kết tài khoản github bằng SSH](#lienkettaikhoan)

	+ [3.3.1. Generating a new SSH key](#generateing)
	
	+ [3.3.2. Add SSH key](#addkey)
	
	+ [3.3.3. Caching Github password in Git](#caching)

---

<a name="gitvagithub"></a>
### 1. Git và Github:

<a name="git"></a>
#### 1.1. Git:
* Git là một **hệ thống quản lý phiên bản phân tán** (Distributed Version Control System - DVCS) để theo dõi các thay đổi trong các tập tin trên máy tính và phối hợp làm việc với những tập tin đó. Nó chủ yếu được sử dụng trong phát triển phần mềm, nhưng nó cũng được sử dụng để theo dõi sự thay đổi trong bất kỳ tập tin. 
* Git được tạo ra bởi *Linus Torvalds* năm 2005.
* Git là một phần mềm miễn phí được phân phối dưới các điều khoản của GNU General Public License version 2.
* Có thể hiểu cách hoạt động của Git như sau:
	Git giúp lưu lại các thay đổi phiên bản bằng cách tạo ra một **snapshot** trên mỗi tập tin và thư mục sau khi commit, từ đó có thể dễ dàng khôi phục phiên bản đó bằng cách tái sử dụng lại snapshot đó. Một người khác có thể xem các thay đổi của bạn ở từng phiên bản, họ có thể đối chiếu các thay đổi của bạn rồi gộp phiên bản của bạn và phiên bản của họ vào với nhau. Cuối cùng, tất cả có thể đưa các thay đổi vào mã nguồn của mình lên một kho chứa mã nguồn.
* Tại sao nên sử dụng Git?
	+ Dễ sử dụng, an toàn và nhanh chóng.
	+ Giúp quy trình làm việc theo nhóm đơn giản hơn rất nhiều bằng việc kết hợp các phân nhánh.
	+ Dễ dàng trong việc triển khai sản phẩm.
	
<a name="cochehoatdongcuagit"></a>
#### 1.2. Cơ chế hoạt động của Git:

<a name="github"></a>
#### 1.3. Github:
* Github là dịch vụ cung cấp kho lưu trữ mã nguồn Git dựa trên nền web cho các dự án phát triển phần mềm. Nó cung cấp tất cả các chức năng kiểm soát phiên bản phân phối và quản lý mã nguồn (SCM)  của Git cũng như thêm các tính năng của nó. Nó cung cấp kiểm soát truy cập và một số tính năng cộng tác như theo dõi lỗi, quản lý tác vụ,...
* GitHub cung cấp cả phiên bản trả tiền lẫn miễn phí cho các tài khoản. Các dự án mã nguồn mở sẽ được cung cấp kho lưu trữ miễn phí. 
* Người sử dụng phải tạo ra một tài khoản để có thể đóng góp nội dung cho Github, nhưng bất kỳ ai cũng có thể tải về và sử dụng các kho mã nguồn công khai.

<a name="motsolenhcobancuagit"></a>
### 2. Một số lệnh cơ bản của Git:

<a name="add"></a>
#### 2.1. Add:

<a name="remove"></a>
#### 2.2. Remove:

<a name="commit"></a>
#### 2.3. Commit:

<a name="push"></a>
#### 2.4. Push:

<a name="fetch"></a>
#### 2.5. Fetch:

<a name="clone"></a>
#### 2.6. Clone:

<a name="fork"></a>
#### 2.7. Fork:

<a name="star"></a>
#### 2.8. Star:

<a name="watch"></a>
#### 2.9. Watch:

<a name="pull"></a>
#### 2.10. Pull:

<a name="caidatgitgenerateaddsshkey"></a>
### 3. Cài đặt Git, Generate, add SSH Key:

<a name="caidatgit"></a>
#### 3.1. Cài đặt Git:
* Git có khả năng chạy trên nhiều hệ điều hành khác nhau như Linux, Windows, Mac OSX, ...
* Trên Windows:
	+ Yêu cầu máy tính phải cài đặt **.NET 4.5** trở lên.
	+ Vào đường dẫn này để tải Git cho máy tính: <https://git-scm.com/download/win>
	+ Sau khi tải Git, cài đặt và sử dụng bình thường.
* Trên Linux:
	+ Sử dụng các lệnh sau để cài đặt Git:
	+ Đối với Debian/Ubuntu:
	```
	$ apt-get install git
	```
	+ Đối với Centos/Fedora (tính đến Fedora 21):
	```
	$ yum install git
	```
	+ Đối với Fedora 22 trở đi:
	```
	$ dnf install git
	```
	+ Đối với ArchLinux:
	```
	$ pacman -S git
	```
* Trên Mac OSX:
	+ Tải gói cài đặt tại đường dẫn sau để cài đặt: <https://git-scm.com/download/mac>
	
<a name="cacthietlapbandau"></a>
#### 3.2. Các thiết lập ban đầu:
* Sau khi cài Git xong, việc đầu tiên là thiết lập tên và địa chỉ email sử dụng cho git.
```
git config --global user.name "tên/username"
git config --global user.email "email sử dụng cho git"
```

* Lựa chọn trình soạn thảo mặc định, có thể là vi, vim, nano,...
```
git config --global core.editor vi
```

* Liệt kê các thiết lập đã làm:
```
git config --list
```

<a name="lienkettaikhoan"></a>
#### 3.3. Liên kết tài khoản github bằng SSH:

<a name="generateing"></a>
##### 3.3.1. Generating a new SSH key:
* Tạo SSH key mới: 
```
$ ssh-keygen -t rsa
```
* Thiết lập file lưu key. Nhấn *Enter* để sử dụng thiết lập mặc định. 

![file-save](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/file-save.png)

* Thiết lập mật khẩu cho key. Nhập vào và **ghi nhớ** mật khẩu này. Sau quá trình này, có 2 file được tạo ra. 1 file lưu *private key*, 1 file lưu *public key*.

![passphrase](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/passphrase.png)

* Thêm SSH key vào *ssh-agent*. Đầu tiên khởi động ssh-agent.
```
ssh-agent -s
```

![ssh-agent](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/ssh-agent.png)

* Sau đó, thêm private key được lưu trong file `id_rsa` vào ssh-agent. Khi được yêu cầu nhập mật khẩu, hãy nhập mật khẩu vừa tạo ở trên.
```
ssh-add ~/.ssh/id_rsa
```

* Cuối cùng, mở file `id_rsa.pub` chứa public key và copy toàn bộ đoạn key này.

![public-key](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/public-key.png)

<a name="addkey"></a>
##### 3.3.2. Add SSH key:
* Đăng nhập vào <https://github.com/>, vào *Settings*, ở mục *SSH and GPG keys*. Chọn **New SSH key**.

![new-ssh-key](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/new-ssh-key.png)

* Đặt tên cho key ở ô *Title* và dán nội dung key vừa copy ở phần trên vào ô *Key*. Sau đó, chọn *Add SSH key*.

![add-ssh-key](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/add-ssh-key.png)

* Cuối cùng, ta được:

![fingerprint](https://github.com/nhuhp/network_research/blob/master/Task02_Git_And_Github/img/fingerprint.png)

<a name="caching"></a>
##### 3.3.3. Caching Github password in Git:

### Tài liệu tham khảo:

[1] Wikipedia. Git. https://en.wikipedia.org/wiki/Git

[2]	Thạch Phạm. Series Git Cơ Bản. https://thachpham.com/tools/git-gioi-thieu-serie-git-co-ban.html

[3] GitHub Help. https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

[4] https://github.com/hocchudong/git-github-for-sysadmin

---

### Hết
