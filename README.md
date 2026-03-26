# XÂY DỰNG HỆ THỐNG MẠNG THREE-LEGGED FIREWALL VỚI PFSENSE

Dự án này là đồ án môn học Mạng máy tính nâng cao của Khoa Công nghệ thông tin, Trường Đại học Sài Gòn. Mục tiêu của dự án là thiết kế và triển khai giải pháp bảo mật sử dụng mô hình tường lửa 3 chân (Three-Legged Firewall).

## 👥 Thông Tin Dự Án
* **Giảng viên hướng dẫn:** ThS. Lương Minh Huấn
* **Nhóm thực hiện:**
  * Ngô Thị Minh Thi - 3122410396
  * Tô Khổng Mỹ Hằng - 3122410104
  * Đặng Phúc Tấn - 3122410375
  * Ngô Khánh Tâm - 3122410370

## 📖 Bối Cảnh & Lý Do Chọn Đề Tài
Trong bối cảnh các mối đe dọa an ninh mạng ngày càng gia tăng, các mô hình tường lửa 1 chân hay 2 chân không đủ khả năng bảo vệ tối ưu. Nhóm lựa chọn mô hình tường lửa 3 chân triển khai trên nền tảng pfSense giúp phân tách rõ ràng các khu vực mạng, cách ly mạng nội bộ và DMZ khỏi môi trường Internet.

## 🏗️ Kiến Trúc Hệ Thống (Network Architecture)

![Mô hình mạng Three-Legged Firewall](images/.png)

Hệ thống được thiết kế với 3 vùng mạng độc lập:
1. **Internet (WAN):** Mạng toàn cầu, nhận IP qua DHCP (`10.10.10.128/24`).
2. **DMZ (Demilitarized Zone):** Khu vực trung gian chứa Public Web Server (`192.168.5.10/24`). 
3. **Internal Network (LAN):** Mạng riêng của tổ chức, lưu trữ dữ liệu nhạy cảm (`192.168.0.0/24`).

## ⚙️ Các Chức Năng Đã Triển Khai

Hệ thống sử dụng tường lửa pfSense với các tính năng định tuyến và bảo mật mạnh mẽ:
* **Network Address Translation (NAT):** Sử dụng Hybrid Outbound NAT để dịch địa chỉ IP nội bộ, ẩn các máy chủ nội bộ.
  
  ![Cấu hình NAT](images/nat_configuration.png)

* **Firewall Rules & Aliases:** Thiết lập tập hợp định danh để chặn truy cập, bao gồm dải IP và tên miền mạng xã hội (`facebook.com`).
  * **LAN:** Cho phép người dùng truy cập DMZ, chặn các dải IP và tên miền không cho phép.
  
  ![Cấu hình Rules cho mạng LAN](images/lan_firewall_rules.png)

  * **DMZ:** Chặn hoàn toàn lưu lượng từ DMZ truy cập ngược vào mạng nội bộ để bảo vệ tài nguyên.

## 🧪 Kết Quả Demo

Mô hình đã được kiểm thử thành công:
* LAN truy cập thành công dịch vụ web SGU Test đặt tại DMZ.
* Máy trạm trong LAN bị chặn truy cập thành công trang `facebook.com` (The connection has timed out).

![Kết quả kiểm tra từ máy trạm LAN](images/demo_results.png)
