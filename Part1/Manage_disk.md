# Quản lý ổ đĩa trên Winserver.

# Khi có nhiều ổ đĩa trên server Window thì trước hết cần "kích hoạt online các ổ đĩa lên" và "khởi động Initialize Disk" lên

![](/image/1.1.png)

![](/image/2.2.png)

### CẤU HÌNH Ổ ĐĨA TRÊN WINDOW có hai loại: Basic Disk và Dynamic Disk. 

### Tính chất Basic Disk: 

+ Hỗ trợ mỗi loại: Simple Volume

![](/image/3.3.png)

+ Có hai kiểu phân vùng cho kiểu Basic Disk: MRB và GPT.

 ++ MRB: 

              Có thể phân chia thành 4 phân vùng: 3 primary và 1 phân vùng mở rộng (extend partition). Trong phân vùng mở rộng có thể phân               chia nhiều phân vùng logic. 
              
              Hỗ trợ ổ cứng chỉ tới 2TB

 ++ GPT: 

              Hỗ trợ lên tới 128 phân vùng => KHông cần tạo các phần vùng mở rộng
              Hỗ trợ ổ cứng hơn 2TB
              
![](/image/6.6.png)             

### Tính chất Dynamic Disk: 

            Cho phép ghép nhiều ổ đĩa vật lý tạo thành ổ Logic (Volume: ổ cứng logic khi đã tạo từ phân vùng ổ đĩa vật lý # Partition:                  phân vùng chia trên ổ đĩa vật lý)

            Cho phép truyền tải dữ liệu được thực hiện cùng một lúc trên hai ổ cứng => Striped Volume

            Cho phép sao lưu dữ liệu liên tục trong suốt quá trình làm việc => Mirror Volume
            
           
![](/image/4.4.png)
           
### Các loại volume Dynamic Disk: 
  
1. Simple Volume: dữ liệu trên simple volume chỉ được lưu trữ trên 1 ổ cứng vật lý

          => Không có an toàn dữ liệu (Fault Tolerancing), và tăng tốc độ xử lý (Load Balancing) không được đảm bảo, khi ổ cứng vật lý             hỏng, thì dữ liệu có nguy cơ bị mất.

2. Span Volume: dữ liệu trên span volume được chép phân bổ trên 2 ổ cứng vật lý trở lên, các ổ cứng không nhất thiết phải giống nhau về dung lượng và chúng được ghép lại thành một Volume duy nhất. 

          => Vẫn không có khả năng đáp ứng vấn đề an toàn dữ liệu (Fault Tolerangcing), và tốc độ xử lý dữ liệu (Load Balancing) do cơ             chế ghi dữ liệu (dữ liệu được chép đầy trên span volume ở disk 1 mới chép sang các disk 2 còn lại).

3. Striped Volume (RAID-0): dữ liệu trên striped volume có thể được trao đổi cùng lúc trên 2 ổ cứng vật lý trở lên, dung lượng trên các ổ cứng vật lý của striped volume phải bằng nhau. Striped Volume có sự thay đổi trong cơ chế hoạt động, dữ liệu khi được chép trên striped được chia ra và chép đều trên các disk

          => vì thế striped đáp ứng được vấn đề tốc độ xử lý dữ liệu (Load Balancing), tuy nhiên striped không đáp ứng được vấn đề an             toàn dữ liệu (Fault Tolerangcing).

4. Mirror Volume (RAID-1): mirror volume chỉ yêu cầu 2 ổ cứng vật lý, dữ liệu khi chép trên mirror sẽ được backup sang đĩa cứng vật lý thứ 2 (vì thế dung lượng trên mirror volume chỉ bằng 1/2 dung lượng khi ta cấu hình). 

          => Do đó Mirror Volume đáp ứng nhu cầu an toàn dữ liệu (Fault Tolerangcing), nhưng không làm tăng tốc độ truy xuất dữ liệu.

5. RAID-5 volume: Raid-5 Volume là giải pháp kết hợp các loại volume (Striped Volume RAID-0, Mirror Volume RAID-1)mà ta đã đề cập ở trên. Raid-5 đáp ứng cho chúng ta cả 2 vấn đề an toàn dữ liệu (Fault Tolerangcing), và tăng tốc độ xử lý dữ liệu (Load Balancing). Để đáp ứng 2 vấn đề trên, Raid-5 đòi hỏi phải sử dụng 3 ổ đĩa cứng vật lý, và sử dụng thuật toán Parity (khi 1 trong 3 đĩa bị hỏng, thuật toán Parity sẽ tự chép những bit bị mất). Vì phải chứa thêm bit Parity nên dung lượng của Raid-5 Volume sẽ chỉ bằng 2/3 dung lượng ta cấu hình (1/3 còn lại là để chứa bit Parity).

![](/image/5.5.png)
