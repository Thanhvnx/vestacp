# Bài 4. Hướng dẫn cài đặt SSL Lets Encrypt

Bạn có thể tạo chứng chỉ SSL Lets Encrypt cho domain theo 2 cách là: giao diện và command line. Trong bài này, mình sẽ hướng dẫn bạn cài chứng chỉ SSL cho domain theo 2 cách.

## 1. Cài chứng chỉ SSL Lets Encrypt cho domain bằng giao diện VestaCP.

Và dĩ nhiên, để cài được SSL Lets Encrypt cho domain thì trước tiên bạn cần đăng nhập vào VestaCP với thông tin đăng nhập của admin. 

<img src="https://github.com/Thanhvnx/picture/blob/master/2020-04-11_08-11.png">

Ở đây mình sẽ cài SSL cho domain test.vietnix.vn. Thì ban đầu domain này sẽ không có SSL và chỉ truy cập theo giao thức http.

<img src ="https://github.com/Thanhvnx/picture/blob/master/a.png">
<img src ="https://github.com/Thanhvnx/picture/blob/master/b.png">

### Các bước cài SSL  

- Bước 1: Di chuyển đến phần web để chọn domain cần chỉnh sửa. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/c1.png">

- Bước 2: Chỉnh sửa domain. Ta chọn “Edit” để vào thêm SSL vào.

<img src ="https://github.com/Thanhvnx/picture/blob/master/c.png">

- Bước 3:  Ta sẽ tích chọn  2 ô “ SSL Support” và “ Lets Encrypt Support” để cài SSL cho domain. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/d.png">

- Bước 4: Ta chọn “Save” để lưu chỉnh sửa. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/h.png">

### Kết quả 

Sau khi chỉnh sửa thì chúng ta sẽ thấy domain này đã có chứng chỉ SSL.

<img src ="https://github.com/Thanhvnx/picture/blob/master/e.png">

Và chúng ta có thể truy cập https với domain này. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/f.png">

### Lưu ý

- Thêm và trỏ domain về VestaCP trước khi cài: Let’s Encrypt chỉ có thể ký khi domain bạn đã truy cập server. Do vậy bạn muốn thêm domain nào thì hãy thêm tên miền vào VestaCP và trỏ về máy chủ trước.
- Trong bước “Edit” có mục Aliases. Mặc định thì chỗ này sẽ là www.test.vietnix.vn. Ở đây mình sẽ để trống ô này vì mình không trỏ domain www.test.vietnix.vn về máy chủ.

<img src ="https://github.com/Thanhvnx/picture/blob/master/g.png">

Aliases hay còn gọi Parked domain cho phép chúng ta chạy một website trên nhiều domain khác nhau. Aliases là một domain khác với domain chính nhưng có cùng cấu trúc thư mục với domain chính. Ví dụ: ta có domain chính là test.vietnix.vn thì chúng ta có thể tạo thêm một aliases www.test.vietnix.vn. Khi chúng ta truy cập địa chỉ test.vietnix.vn hoặc www.test.vietnix.vn thì chúng ta sẽ nhận được nội dung giống nhau ở cả 2 doamin trên. 

## 2.  Cài chứng chỉ SSL Lets Encrypt cho domain bằng command line

Chúng ta sẽ cài SSL Lets Encrypt cho domain abc.vietnix.vn 

Domain abc.vietnix.vn chưa có chứng chỉ SSL nên chỉ truy cập theo giao thức http. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/1a.png">
<img src ="https://github.com/Thanhvnx/picture/blob/master/2a.png">

Đầu tiên chúng ta phải đăng nhập vào server thông qua SSH bằng quyền root. 

### Các bước cài SSL cho domain 

- Xác định domain này có trên VPS hay không?. Bằng cách dùng lệnh

grep “abc.vientnix.vn” /etc/httpd/conf.d/vesta.conf

- Tạo chứng chỉ và bật SSL trên domain “ v-add-letsencrypt-domain USER DOMAIN “

v-add-letsencrypt-domain admin abc.vietnix.vn

- Hiển thị đường dẫn tới lệnh v-add-letsencrypt-domain

which v-add-letsencrypt-domain

- gia hạn SSL  cho domain
 crontab -u admin -e 

sau đó điền “ * * */89 * * /usr/local/vesta/bin/v-add-letsencrypt-domain abc.vietnix.vn “ vào dòng cuối của file. 

Cuối cùng thì restart lại vesta 

/etc/init.d/vesta restart 

### Kết quả 

domain này đã có chứng chỉ SSL. Có thể truy cập với https 

<img src ="https://github.com/Thanhvnx/picture/blob/master/3a.png">
<img src ="https://github.com/Thanhvnx/picture/blob/master/4a.png">



