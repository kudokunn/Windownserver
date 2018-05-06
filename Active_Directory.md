## 1. Khái niệm Active Directory (AD)

Active Directory là một cơ sở dữ liệu của các tài nguyên trên mạng (object) cũng như các thông tin liên quan đến các đối tượng đó. Active Directory cung cấp một mức độ ứng dụng mới cho môi trường doanh nghiệp. Dịch vụ thư mục trong mỗi domain có thể lưu trữ hơn mười triệu đối tượng, đủ để phục vụ mười triệu người dùng trong mỗi domain

### 2. Chức năng: 

* Lưu giữ một danh sách tập trung các tên tài khoản người dùng, mật khẩu tương ứng và các tài khoản máy tính.

* Cung cấp một Server đóng vai trò chứng thực hoặc server quản lý đăng nhập. Server này gọi là domain controller.

* Duy trì một bảng hướng dẫn hoặc một bảng chỉ mục (index) giúp các máy tính trong mạng có thể dò tìm nhanh một tài nguyên nào đó trên các máy tính khác trong vùng.

*  Cho phép chúng ta tạo ra những tài khoản người dùng với những mức độ quyền khác nhau như: toàn quyền trên hệ thống mạng, chỉ có quyền
backup dữ liệu hay shutdown Server từ xa…

* Cho phép chia nhỏ miền của mình ra thành các miền con subdomain hay các đơn vị tổ chức OU (Organizational Unit). Sau đó có thể ủy quyền cho các quản trị viên bộ phận quản lý từng bộ phận nhỏ.

### 3. Các cấu trúc của AD

#### 3.1: Một số khái niệm:

#### Object classes 

Là các loại đối tượng mà bạn có thể tạo ra trong Active Directory. Có ba loại object classes thông dụng là: User, Computer, Printer. ( Tài liệu đang học là bản Window server 2008)

#### Attributes 

Là tập các giá trị (value) phù hợp với thuộc tính (attribute) và được kết hợp với một đối tượng cụ thể.

Hình anh: 1.PNG

#### Organizational Units (OU): 

* Organizational Unit hay OU là đơn vị nhỏ nhất trong hệ thống AD, nó được xem là một vật chứa các đối tượng (Object) được dùng để sắp xếp các đối tượng khác nhau phục vụ cho mục đích quản trị của bạn. 

* OU cũng được thiết lập dựa trên subnet IP và được định nghĩa là “một hoặc nhiều subnet kết nối với nhau”. Việc sử dụng OU có hai công dụng chính sau:

1. Trao quyền kiếm soát một tập hợp các tài khoản người dùng, máy tính hay các thiết bị mạng cho một nhóm người hay quản trị viên phụ nào đó (sub-administrator), từ đó giảm bớt công tác quản trị cho người quản trị toàn bộ hệ thống.

2. Kiểm soát và khóa bớt một số chức năng trên các máy trạm của người dùng trong OU thông qua việc sử dụng các đối tượng chính sách nhóm
(GPO) Group Policy Object

Hình 2.PNG

#### Domain:

* Domain là đơn vị chức năng chính của CẤU TRÚC LOGIC Active Directory. Nó là phương tiện để qui định một tập hợp những người dùng, máy tính, tài nguyên chia sẻ có những qui tắc bảo mật giống nhau từ đó giúp cho việc quản lý các truy cập vào các Server dễ dàng hơn. Domain đáp ứng ba chức năng chính sau:

 + Đóng vai trò như một khu vực quản trị (administrative boundary) các đối tượng, là một tập hợp các định nghĩa quản trị cho các đối tượng chia sẻ như: có chung một cơ sở dữ liệu thư mục, các chính sách bảo mật, các quan hệ ủy quyền với các domain khác.

 + Giúp chúng ta quản lý bảo mật các các tài nguyên chia sẻ.

 + Cung cấp các Server dự phòng làm chức năng điều khiển vùng DC (domain controller), đồng thời đảm bảo các thông tin trên các server này được đồng bộ với nhau.
 
 #### Domain Tree
 
Domain Tree là cấu trúc bao gồm nhiều domain được sắp xếp có cấp bậc theo cấu trúc hình cây. Domain tạo ra đầu tiên được gọi là domain root và nằm gốc của cây thư mục. Tất cả các domain tạo ra sau sẽ nằm bên dưới domain root và được gọi là domain con (child domain). Tên của các domain con phải khác biệt nhau. Domain Tree bao gồm ít nhất 1 Root Domain và 1 Child Doamin 

hình 3.PNH

#### Forest 

Forest là một mô hình tổ chức của AD, một forest gồm nhiều domain trees có quan hệ với nhau, các domain trees trong forest là độc lập với nhau về tổ chức> Một forest phải đảm bảo thoả các đặc tính sau:

+ Toàn bộ domain trong forest phải có một schema chia sẻ chung

+ Các domain trong forest phải có một global catalog chia sẻ chung

+ Các domain trong forest phải có mối quan hệ trust hai chiều với nhau

+ Các tree trong một forest phải có cấu trúc tên(domain name) khác
nhau

+ Các domain trong forest hoạt động độc lập với nhau, tuy nhiên hoạt
động của forest là hoạt động của toàn bộ hệ thống tổ chức doanh
nghiệp.

Hình 4 PNG

#### Site: 

Một site bao gồm một hay nhiều mạng con liên kết với nhau. Có thể cấu hình việc truy xuất và tạo bản sao cho Active Directory hiệu quả nhất và lập ra một lịch cập nhật để không ảnh hưởng đến thông lượng của mạng

Hình 5 PNG

#### Domain controllers

* Domain Controller là một máy tính hay server cài đặt Windows Server sẽ được cài đặt để lên DC và lưu trữ bản sao cơ sở dữ liệu tên miền. 

* Một domain có thể có một hay nhiều domain controller, mỗi domain controller đều có bản sao dữ liệu của Domain Directory. 

* Các máy trạm phải join vào domain goi là domain client

* User tạo ra bởi hệ thống domain trên DC gọi là Domain User

=> Hệ thống domain là hệ thống máy tính client join vào domain do DC quản lý

* Điều kiện để lên DC 1. HĐH winserver 2. Card mạng 3. Hệ thống có DNS server

* Domain Controller chịu trách nhiệm chứng thực cho users và chịu trách nhiệm đảm bảo các chính sách bảo mật được thực thi. Các chức năng chính của domain controller:

  - Mỗi domain controller lưu trữ các bản sao thông tin của Active Directory cho chính domain đó, chịu trách nhiệm quản lí thông tin và
tiến hành đồng bộ dữ liệu với các domain controller khác trong cùng một domain.

  -  Domain Controller trong một Domain có khả năng tự động đồng bộ dữ liệu với các domain controller khác trong cùng một domain. Khi bạn thực hiện một tác vụ đối với thông tin lưu trữ trên domain controller, thì thông tin này sẽ tự động được đồng bộ hóa đến các domain controller khác. Tuy nhiên để đảm bảo sự ổn định cho hệ thống mạng, chúng ta cần phải có một chính sách hợp lí cho các domain trong việc
đồng bộ hóa thông tin dữ liệu với một thời điểm phù hợp.

- ..........

