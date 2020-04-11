# Bài 5.  Hướng dẫn backup user trên VestaCP

## 1. Backup user bằng giao diện VestaCP

Đầu tiên để backup user thì chúng ta cần login vào user mà chúng ta muốn backup

<img src ="https://github.com/Thanhvnx/picture/blob/master/2020-04-11_08-11.png">

- Bước 1: Tại thanh menu chức năng chọn “BACKUP”. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/11a.png">

- Bước 2: Chọn dấu “ + “  màu xanh để tạo backup 

<img src ="https://github.com/Thanhvnx/picture/blob/master/12a.png">

- Bước 3: Một thông báo sẽ xuất hiện. Ta chọn “ ok” 

<img src ="https://github.com/Thanhvnx/picture/blob/master/13a.png">

### Kết quả 

Đây là kết quả bakup. Mỗi ngày sẽ tự động backup 1 bản. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/14a.png">

## 2. Backup bằng command line

Vì mình có 2 user là “thanh_vietnix” và “admin”.

Để backup bằng command line thì bạn chỉ cần dùng câu lệnh 

“ v-backup-user thanh_vietnix “

ở đây mình làm ví dụ trên user thanh_vietnix. Và đây là kết quả mình backup. 
Backup này sẽ thực hiện  tự động 1 ngày 1 bản. 

<img src ="https://github.com/Thanhvnx/picture/blob/master/2020-04-11_15-42.png">
