WINDOW DEPLOY SERVICE: Dịch vụ triển khai hệ điều hành window. Được dùng để triển khai cài đặt hàng loạt hệ điều hành Window cho client qua giao thức PXE. 

Mô hình: 

![](image\WDS.PNG)

Thực hiện: https://www.youtube.com/watch?v=JtzKEGJPZ4I&list=UURcMHAr_csIFXKsEW_5cuKw&index=44

Trên server DC-12: 
+ Cài DHCP

Trên server SRV-12: 
+ Join Domain
+ Cài Winser Deploy Service => add được 2 file image: image.vim và file boot: boot.vim
+ Window Imange Manager => Tạo file Answer để tự động cài đặt hoàn toàn

Trên Client 8.1:

+ Phải cài đặt được một cách tự động
+ Tự join vào Domain
+ Tự vào được tên miền

