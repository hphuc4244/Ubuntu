# Ubuntu
#### 1. Cài đặt Samba
Để cài đặt Samba, chúng tôi chạy:

  `$ sudo apt update`

  `$ sudo apt install samba`

Chúng tôi có thể kiểm tra xem cài đặt có thành công hay không bằng cách chạy:


  `$ whereis samba`
  
Sau đây là đầu ra của nó:

`samba: /usr/sbin/samba /usr/lib/samba /etc/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz`

#### 2. Thiết lập Samba

Bây giờ Samba đã được cài đặt, chúng ta cần tạo một thư mục cho nó để chia sẻ:


  `$ mkdir /home/<username>/<thư mục cần share> sambashare/`
  
 Ví dụ
  
  `$ mkdir /home/<username>/sambashare/`
  
Lệnh trên tạo một thư mục mới sambashare trong thư mục chính mà chúng ta sẽ chia sẻ sau.

Tệp cấu hình cho Samba được đặt tại `/etc/samba/smb.conf` . Để thêm thư mục mới dưới dạng chia sẻ, chúng tôi chỉnh sửa tệp bằng cách chạy:



`$ sudo nano /etc/samba/smb.conf`

Ở cuối tệp, thêm các dòng sau:

` sambashare]

    comment = Samba on Ubuntu 
    
    path = /home/username/sambashare
    
    read only = no
    
    browsable = yes   
`

Sau đó nhấn Ctrl-Ođể lưu và Ctrl-Xthoát khỏi trình soạn thảo văn bản nano .

Những gì chúng tôi vừa thêm vào
bình luận: Một mô tả ngắn gọn về chia sẻ.
path: Thư mục chia sẻ của chúng tôi.

chỉ đọc: Quyền sửa đổi nội dung của thư mục chia sẻ chỉ được cấp khi giá trị của chỉ thị này là no.

có thể duyệt: Khi được đặt thành yes, các trình quản lý tệp như trình quản lý tệp mặc định của Ubuntu sẽ liệt kê phần chia sẻ này trong “Mạng” (nó cũng có thể xuất hiện dưới dạng có thể duyệt).

Bây giờ chúng ta đã định cấu hình chia sẻ mới của mình, hãy lưu nó và khởi động lại Samba để nó có hiệu lực:

sudo service smbd restart
Cập nhật các quy tắc tường lửa để cho phép lưu lượng truy cập Samba:

sudo ufw allow samba

