## 1. Khái niệm Active Directory (AD)

Active Directory là một cơ sở dữ liệu của các tài nguyên trên mạng (object) cũng như các thông tin liên quan đến các đối tượng đó. Active Directory cung cấp một mức độ ứng dụng mới cho môi trường doanh nghiệp. Dịch vụ thư mục trong mỗi domain có thể lưu trữ hơn mười triệu đối tượng, đủ để phục vụ mười triệu người dùng trong mỗi domain

### 2. Chức năng: 

* Lưu giữ một danh sách tập trung các tên tài khoản người dùng, mật khẩu tương ứng và các tài khoản máy tính.

* Cung cấp một Server đóng vai trò chứng thực hoặc server quản lý đăng nhập. Server này gọi là domain controller.

* Duy trì một bảng hướng dẫn hoặc một bảng chỉ mục (index) giúp các máy tính trong mạng có thể dò tìm nhanh một tài nguyên nào đó trên các máy tính khác trong vùng.

*  Cho phép chúng ta tạo ra những tài khoản người dùng với những mức độ quyền khác nhau như: toàn quyền trên hệ thống mạng, chỉ có quyền
backup dữ liệu hay shutdown Server từ xa…

* Cho phép chia nhỏ miền của mình ra thành các miền con subdomain hay các đơn vị tổ chức OU (Organizational Unit). Sau đó có thể ủy quyền cho các quản trị viên bộ phận quản lý từng bộ phận nhỏ.

### 3. đối tượng trong AD

#### 3.1:  
Object classes là một bản thiết kế mẫu hay một khuôn mẫu cho các
loại đối tượng mà bạn có thể tạo ra trong Active Directory. Có ba loại
object classes thông dụng là: User, Computer, Printer.
 Attributes, nó được định nghĩa là tập các giá trị phù hợp và được kết
hợp với một đối tượng cụ thể. Như vậy Object là một đối tượng duy
nhất được định
