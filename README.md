# XÂY DỰNG HỆ THỐNG MẠNG THREE-LEGGED FIREWALL VỚI PFSENSE

[cite_start]Dự án này là đồ án môn học Mạng máy tính nâng cao của Khoa Công nghệ thông tin, Trường Đại học Sài Gòn[cite: 1, 2, 4]. [cite_start]Mục tiêu của dự án là thiết kế và triển khai giải pháp bảo mật sử dụng mô hình tường lửa 3 chân (Three-Legged Firewall)[cite: 5, 93].

## 📖 Bối Cảnh & Lý Do Chọn Đề Tài
[cite_start]Trong bối cảnh các mối đe dọa an ninh mạng ngày càng gia tăng, việc bảo vệ cơ sở hạ tầng mạng của tổ chức là yếu tố then chốt[cite: 92]. [cite_start]Các mô hình tường lửa 1 chân hay 2 chân không đủ khả năng bảo vệ tối ưu trong môi trường mạng phức tạp[cite: 98]. 

[cite_start]Do đó, nhóm lựa chọn mô hình tường lửa 3 chân triển khai trên nền tảng mã nguồn mở pfSense[cite: 97, 105]. [cite_start]Mô hình này giúp phân tách rõ ràng các khu vực mạng, cách ly mạng nội bộ và DMZ khỏi môi trường Internet, đảm bảo an toàn cho các dịch vụ công khai và dữ liệu nhạy cảm[cite: 94, 100].

## 🏗️ Kiến Trúc Hệ Thống (Network Architecture)
[cite_start]Hệ thống được thiết kế với 3 vùng mạng độc lập[cite: 102]:

1. [cite_start]**Internet (WAN):** Mạng toàn cầu, nơi chứa các mối đe dọa không đáng tin cậy[cite: 212, 214]. [cite_start]IP được cấp phát qua DHCP (Ví dụ: `10.10.10.128/24`)[cite: 312].
2. [cite_start]**DMZ (Demilitarized Zone):** Khu vực trung gian chứa các dịch vụ công cộng như Public Web Server[cite: 215, 312]. [cite_start]IP của máy chủ DMZ: `192.168.5.10/24`[cite: 312]. [cite_start]Các kết nối từ bên ngoài chỉ có thể tiếp cận DMZ mà không thể xâm nhập mạng nội bộ[cite: 216].
3. [cite_start]**Internal Network (LAN):** Mạng riêng của tổ chức, lưu trữ dữ liệu nhạy cảm[cite: 218]. [cite_start]IP máy trạm: `192.168.0.10/24` và máy client: `192.168.0.25/24`[cite: 312]. 

## ⚙️ Các Chức Năng Đã Triển Khai
[cite_start]Hệ thống sử dụng tường lửa pfSense với các tính năng định tuyến và bảo mật mạnh mẽ[cite: 271]:

* [cite_start]**Kiểm soát giao thông dữ liệu:** Thiết lập chính sách bảo mật để quản lý luồng dữ liệu giữa WAN, LAN và DMZ[cite: 178, 204].
* [cite_start]**Network Address Translation (NAT):** Sử dụng Hybrid Outbound NAT để dịch địa chỉ IP nội bộ, ẩn các máy chủ nội bộ khỏi mạng bên ngoài[cite: 268, 307, 324].
* [cite_start]**Firewall Aliases:** Tạo tập hợp định danh để chặn truy cập, bao gồm dải IP (`Blocked_IPs`: 192.168.0.20 - 192.168.0.50) và tên miền mạng xã hội (`facebook.com`)[cite: 330, 331, 332].
* **Firewall Rules:**
  * [cite_start]**WAN:** Chặn mạng Bogon và chỉ cho phép truy cập HTTP vào Web Server tại DMZ[cite: 326, 327].
  * [cite_start]**LAN:** Cho phép người dùng truy cập DMZ, cho phép ra Internet ngoại trừ các dải IP và tên miền bị cấm[cite: 328].
  * [cite_start]**DMZ:** Chặn hoàn toàn lưu lượng từ DMZ truy cập ngược vào mạng nội bộ để bảo vệ tài nguyên bên trong, chỉ cho phép DMZ ra Internet[cite: 232, 329].

## 🧪 Kết Quả Demo
[cite_start]Mô hình đã được kiểm thử thành công bằng các công cụ dòng lệnh (ping) và trình duyệt web[cite: 114, 334]:
* [cite_start]LAN truy cập thành công dịch vụ web (SGU Test) đặt tại DMZ[cite: 335].
* [cite_start]Máy trạm trong LAN bị chặn truy cập thành công trang `facebook.com` theo rule đã thiết lập[cite: 335].
* [cite_start]DMZ cách ly an toàn và không thể ping vào mạng LAN[cite: 337].
