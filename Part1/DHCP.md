##  Cài đặt service DHCP và tạo scope dải DHCP
##  Tạo DHCP Relay 
##  Backup và Restore DHCP

### 1. Cài đặt service DHCP và tạo scope dải DHCP và gán reservation một IP cho máy client

B1: Vào Server Manager => Thêm service bình thường. 
B2: Vào Tool => DHCP => Scope => Làm theo các tab bình thường
B3: Trên Client => Nhận IP động (Obtain an IP address automatically)
B4: Đặt trước IP cho một client: Mở DHCP => Reservation => New Reservation => Nhập các thông số chú ý phải đúng MAC của client.

### 2. Cài đặt và cấu hình DHCP Relay Agent 

![](/image/7.PNG)

![](/image/6.PNG)

- Tình huống: Server BKAP_SRV12-01 có hai dải mạng 192 và 131. Dải 192 đã có Server BKAP-DC12-01 cấp dải này, còn dải 131 nằm ở dải khác và để nó nhận dải 131 từ Server DC12-01 thì Server BKAP-SRV12-01 cài đặt DHCP Relay để "chuyển tiếp đến Server DC12-01" để DC12 cấp IP dải 131

- Để Server BKAP-SRV có thể đến BKAP-SRV12 cần cài Role "Remote Access". Tại Tool sẽ được Service Routing and Remote Access. 
  
  Tham khảo: ....
  
