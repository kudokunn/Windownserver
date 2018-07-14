### Mô hình

![](/image/VPN.PNG)


Note: có thể tạo VPN từ các thiết bị mạng Router nhưng khi đã vào được mạng công ty muốn phân quyền User này chỉ được vào các thư mục của phòng ban họ thì phải cấu hình như thế này.

### Mô hình có 4 server: 

1. Server BKAP-DC12-01: - Chạy AD tạo OU, Group, tài khoản người dùng và cho phép truy cập từ xa
                        - 1 Folder chia sẻ tên Data
                       
2. Server BKAP-SRV12-01: Join vào Domain của BKAP-DC12-01

- Cài đặt dịch vụ RADIUS Server và chỉ thiết lập Radius Client => Để chỏ đến con VPN, cho phép con VPN kia xác thực, từ đó con VPN có kết nối từ xa đến thì nó đến con Radius để xác thực

- Cài NPS (Network Policy Server) cho phép xác thực và cấp quyền các connect bằng các tài khoản User trên Server BKAP-DC12-01 chạy AD. NPS cần đọc các cơ sở dữ liệu người dùng của  BKAP-DC12-01

3. Server BKAP-SRV12-02: 

- Cài service Remote Access => Cho phép tạo kết nối VPN và cấp dải mạng khi nó vào mạng Local

4. Máy BKAP-WRK08-01: Máy test VPN từ xa

### Nguyên lý hoạt động: 

1. Server BKAP-DC12-01 tạo một User và cho phép được đăng nhập từ xa (Allow Access) trong phần Properties

2. Server BKAP-SRV12-01 join vào domain và cho phép NPS (Network Policy Server) đọc cơ sở dữ liệu người dùng của AD và xác nhận User nào được đăng nhập vào

3. Server BKAP-SRV12-02: Tạo kết nối VPN và cấp dải mạng khi nó vào mạng Local và chỏ xác thực về con RADIUS BKAP-SRV12-01

4. Máy BKAP-WRK08-01: Test VPN từ xa bằng tài khoản cấp trên AD

### Thực hiện: https://www.youtube.com/watch?v=J08bXm77nNA&list=UURcMHAr_csIFXKsEW_5cuKw&index=58






