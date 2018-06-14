### Lý thuyết

1. Khái niệm: 

NIC Teaming cho phép gộp 2 hoặc nhiều NIC vật lý (Network Interface Card) liên kết với nhau, tạo thành 1 NIC logic có khả năng LoadBalancing và  tăng HA (High Availability) cho hệ thống
Note: High Availability ~ Fault Tolerance

2. Cấu hình 

- Yêu cầu: Ít nhất 2 card mạng trở lên để có thể gộp

- Vào Server Manager => Local Server => NIC Teaming => Kích Disable 

- Vào trường TASK => NewTeam.

- Các thành phần

        Team name :điền tên của Team cần tạo – trường hợp này là Team1
        Member adapters : chọn NIC cần thêm vào team – trường hợp này chọn 3 NIC đầu.
        Addional properties : Lựa chọn những thuộc tính đi kèm.
        
        + Teaming mode : gồm 3 mode

          ++ Static Teaming : cắm cùng switch
          ++ Switch Independent : cắm switch nào cũng đc ( dĩ nhiên nó chỉ phục vụ lớp mạng của nó )
          ++ LACP : giao thức để tạo EthernetChanel ( có thể lên google để tìm hiểu thêm về LACP )
          
        + Load balancing mode

          ++ Address Hash : dùng cho máy thật
          ++ Hyper-V Port : dùng cho máy ảo
          
        + Standby Adapter : đây là chức năng Fault Tolerance.

          ++ Non (all adapters Active) : tất cả đều active và chạy LoadBalancing ( không có Fault Tolerance )
          ++ Tên adapter 1…  :  nếu chọn Adapter 1, thì adapter 1 sẽ về chế độ standby, nếu có NIC nào fail nó sẽ lên làm active
          ++ Tên adapter 2… : tương tự như trên.
          
  - Vào Network xem card mạng thì có một card mới tạo là Team1 có một IP duy nhất đại diện 3 card mạng đã chọn trên. 3 card mạng kia không có địa chỉ
