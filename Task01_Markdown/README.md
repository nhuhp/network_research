## Tìm hiểu Markdown

> Tài liệu: Tìm hiểu về Markdown	
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **08/05/2017**

### Mục lục

[1. Tổng quan về Markdown](#tongquanvemarkdown)

[2. Sử dụng Markdown](#sudungmarkdown)

- [a. Header](#header)
- [b. Italic](#italic)
- [c. Bold](#bold)
- [d. Strike through](#strikethrough)
- [e. List](#list)
- [f. Link](#link)
- [g. Image](#image)
- [h. Code and Syntax Highlighting](#syntaxhighlighting)
- [i. Blockquotes](#blockquotes)
- [j. Tables](#table)
- [k. Horizontal Line](#horizontalline)

---
<a name="tongquanvemarkdown"></a>
### 1. Tổng quan về Markdown:

**Markdown** là một ngôn ngữ đánh dấu bằng cú pháp định dạng văn bản thuần. Nó được thiết kế để chuyển đổi qua *HTML* và nhiều định dạng khác sử dụng một công cụ cùng tên. Markdown thường được sử dụng để định dạng file *readme*, viết thông báo cho các diễn dàn trực tuyến và được tạo các siêu văn bản  sử dụng editor văn bản thuần (không biết dịch thế nào đây: plain text editor). ***John Gruber*** đã tạo ra Markdown vào năm 2004 cùng với ***Aaron Swartz***. Với mục tiêu là cho phép mọi người sử dụng một định dạng ở dạng *plain text* dễ đọc, dễ viết và tùy chọn chuyển đổi nó thành XHTML (hoặc HTML) hợp lệ.

Một số ứng dụng sử dụng ngôn ngữ Markdown: *Github*, Gitbook, Reddit, Diaspora, Stack Overflow, OpenStreetMap,...

Phần mở rộng của markdown: `.md`

<a name="sudungmarkdown"></a>
### 2. Sử dụng Markdown:

<a name="header"></a>
#### a. Header:

Markdown hỗ trợ 2 kiểu viết tiêu đề: Setext và ATX.

* Với *Setext* : sử dụng kí tự `=` và `-` gạch chân dưới tiêu đề, sử dụng cho 2 thẻ `<h1>` và `<h2>`.
VD:
```
Header1
=

Header2
-
```
Kết quả:
Header1
=
Header2
-

* Với *ATX* : sử dụng ký tự `#` đặt trước các tiêu đề. Số ký tự đặt trước tiêu đề biểu diễn lần lượt từ `<h1>` đến `<h6>`
```
# Header1
## Header2
### Header3
#### Header4
##### Header5
###### Header6
```
# Header1
## Header2
### Header3
#### Header4
##### Header5
###### Header6

<a name="italic"></a>
#### b. Italic:
Sử dụng ký tự `*` hoặc `_` đặt trước và sau phần muốn in nghiêng.

VD:
`*in nghiêng*` hoặc `_in nghiêng_`
Kết quả:
*in nghiêng* hoặc _in nghiêng_

<a name="bold"></a>
#### c. Bold:
Sử dụng ký tự `**` hoặc `__` đặt trước và sau phần muốn in đậm.
VD:
`**in đậm**` hoặc `__in đậm__`
Kết quả:
**in đậm** hoặc __in đậm__

<a name="strikethrough"></a>
#### d. Strike through:
Sử dụng ký tự `~~` đặt trước và sau phần muốn gạch giữa.

VD:
```
~~Gạch giữa~~
```
Kết quả:
~~Gạch giữa~~

<a name="list"></a>
#### e. List:
* List sử dụng số thứ tự: 
```
1. Dòng 1:
2. Dòng 2:
3. Dòng 3:
```
1. Dòng 1:
2. Dòng 2:
3. Dòng 3:

* List sử dụng ký hiệu:
```
* Dấu sao
+ Dấu cộng
- Dấu trừ
```
* Dấu sao
+ Dấu cộng
- Dấu trừ


<a name="link"></a>
#### f. Link:
Có **2** cách để tạo links : ***inline-style*** và ***reference-style***
* *inline-style*
Cú pháp:
```
[Tên liên kết](link)
Mở rộng: [Tên liên kết](link "Tiêu đề tự chọn cho liên kết")
```
Đoạn văn bản trong dấu `[]` tương đương với giá trị của thuộc tính *title* trong thẻ `<a>` và link đặt trong dấu `()` sẽ tương đương với giá trị thuộc tính *href* trong thẻ `<a>`
VD:
```
[Đây là đường dẫn đến Google](https://www.google.com)
[Đây là đường dẫn đến Google](https://www.google.com "Tìm kiếm bằng Google")
```
Kết quả:
[Đây là đường dẫn đến Google](https://www.google.com)
[Đây là đường dẫn đến Google](https://www.google.com "Tìm kiếm bằng Google")

* *reference-style*
Cú pháp:
```
[Tên liên kết][Label]
[Label]:link

Mở rộng: 
[Label]:link "Tiêu đề tự chọn cho liên kết"
```
VD:
```
Bấm vào [đây][lb] để truy cập Google.

[lb]:https://www.google.com "Truy cập Google"
```
Kết quả:
Bấm vào [đây][lb] để truy cập Google.

[lb]:https://www.google.com "Truy cập Google"

Để ngắn gọn, có thể gộp phần [Tên liên kết] với [Label] thành một.

```
Bấm vào [đây] để truy cập Google.

[đây]:https://www.google.com "Truy cập Google"
```
Bấm vào [đây] để truy cập Google.

[đây]:https://www.google.com "Truy cập Google"

* Ngoài ra, nếu để URL trong cặp dấu `<` `>`, thì URL sẽ tự động tạo đường dẫn đến nó.
Cú pháp:
```
<URL>
```
VD:
```
<https://www.google.com>
```
Kết quả:
<https://www.google.com>

<a name="image"></a>
#### g. Image:
Tương tự links, hình ảnh cũng có 2 cách để tạo:
* *inline-style*
Cú pháp:
```
![Tên hình ảnh](link của hình ảnh "Mô tả tùy chọn")
```
VD:
```
![anh-dep](https://github.com/nhuhp/network_research/blob/master/Task01_Markdown/img/GitHub-Mark.png)
```
Kết quả:
![anh-dep](https://github.com/nhuhp/network_research/blob/master/Task01_Markdown/img/GitHub-Mark.png)

Đoạn văn bản trong dấu `[]` tương đương với giá trị của thuộc tính *alt* trong thẻ `<img>` và link đặt trong dấu `()` sẽ tương đương với giá trị thuộc tính *src* trong thẻ `<img>`

* *reference-style*
Cú pháp:
```
![Tên hình ảnh][Label]
[Label]:link của hình ảnh "Mô tả tùy chọn"
```
VD:
```
![anh-dep][lb]
[lb]: https://github.com/nhuhp/network_research/blob/master/Task01_Markdown/img/GitHub-Mark.png
```

<a name="syntaxhighlighting"></a>
#### h. Code and Syntax Highlighting:
Sử dụng dấu ` đặt đầu và cuối cú pháp cần highlight.
VD:
```
`syntax`
```
Kết quả:
`syntax`

Sử dụng dấu ` ``` ` để highlight một đoạn có nhiều dòng.
Sử dụng dấu ` ``` ` kèm theo `tên ngôn ngữ` để hightlight code của ngôn ngữ đó.

<a name="blockquotes"></a>
#### i. Blockquotes:
VD:
```
> Tài liệu: Tìm hiểu về Markdown	
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **08/05/2017**
```
Kết quả:
> Tài liệu: Tìm hiểu về Markdown	
> 
> Thực hiện: **Phạm Hoàng Nhu**
> 
> Cập nhật lần cuối: **08/05/2017**

<a name="table"></a>
#### j. Tables:
Cấu trúc bảng:
```
|col 1|col 2|col 3|
|:----|:---:|----:|
|a|b|c|
```
Hàng đầu tiên, định danh của các cột
Hàng thứ hai, canh lề cho từng cột
`:-----` hoặc `-----` dùng để canh trái.
`:----:` dùng để canh giữa.
`-----:` dùng để canh phải.
Những hàng tiếp theo, chứa nội dung tương ứng với các cột.
VD:
|col 1|col 2|col 3|
|:----|:---:|----:|
|a|b|c|
*Lưu ý:* Các dấu `|` ở ngoài cùng có thể lược bỏ.
```
col 1|col 2|col 3
:----|:---:|----:
a|b|c
```
<a name="horizontalline"></a>
#### k. Horizontal Line: 
`---`
---
`***`
***
`___`
___
 
### Tài liệu tham khảo:
[1] namnguyen. Học sử dụng Markdown. https://namnguyen.gitbooks.io/hoc-su-dung-markdown/content/index.html
[2] Linh Nguyễn. Markdown Là Gì. http://www.codehub.vn/Markdown-La-Gi
[3] Adam Pritchard. Markdown Cheatsheet. https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[4] https://github.com/hocchudong/git-github-for-sysadmin
[5] https://help.ghost.org/hc/en-us/articles/224410728-Markdown-Guide

### Hết


