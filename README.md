# [cite_start]BÁO CÁO ĐỒ ÁN MÔN HỌC MẠNG MÁY TÍNH NÂNG CAO [cite: 3, 4]
[cite_start]**ĐỀ TÀI: XÂY DỰNG HỆ THỐNG MẠNG THREE LEG FIREWALL** [cite: 5]

## 📖 Giới thiệu dự án
[cite_start]Trong bối cảnh các mối đe dọa an ninh mạng ngày càng gia tăng, việc bảo vệ các hệ thống mạng của tổ chức là yếu tố quan trọng[cite: 92]. [cite_start]Tường lửa 3 chân (3-Legged Firewall) là một giải pháp an ninh mạng mạnh mẽ giúp bảo vệ các hệ thống quan trọng[cite: 96]. 

[cite_start]Dự án này sử dụng công cụ pfSense để thiết lập mô hình 3 legged firewall với ba khu vực mạng: Internal, DMZ, và Internet[cite: 97, 102]. [cite_start]Mô hình giúp phân tách rõ ràng các khu vực mạng quan trọng, đảm bảo rằng các dịch vụ công khai được bảo vệ và cách ly khỏi mạng nội bộ[cite: 100, 108].

## 👥 Thông tin nhóm thực hiện
* [cite_start]**Trường/Khoa:** Trường Đại học Sài Gòn - Khoa Công nghệ thông tin [cite: 1, 2]
* **Giảng viên hướng dẫn:** ThS. [cite_start]Lương Minh Huấn [cite: 6]
* **Thành viên:**
  * [cite_start]Ngô Thị Minh Thi - 3122410396 - ntmthi.0234@gmail.com [cite: 8, 13]
  * [cite_start]Tô Khổng Mỹ Hằng - 3122410104 - myhang03112004@gmail.com [cite: 9, 13]
  * [cite_start]Ngô Khánh Tâm - 3122410370 - khanhtam08022004@gmail.com [cite: 11, 13]
  * [cite_start]Đặng Phúc Tấn - 3122410375 - tdangphuc902@gmail.com [cite: 10, 13]

## 🏗️ Kiến trúc hệ thống
Mô hình tường lửa ba chân bao gồm ba vùng mạng chính:
* [cite_start]**Internet (Mạng toàn cầu):** Mạng công cộng nơi tất cả kết nối đến từ bên ngoài[cite: 212].
* [cite_start]**DMZ (Demilitarized Zone):** Khu vực trung gian chứa các dịch vụ công cộng như public web server[cite: 215, 312]. [cite_start]DMZ giúp cô lập các tài nguyên công khai khỏi mạng nội bộ[cite: 216].
* [cite_start]**Internal Network (Mạng nội bộ):** Mạng riêng của tổ chức, được bảo vệ nghiêm ngặt, tách biệt hoàn toàn với Internet[cite: 218, 220].

## ⚙️ Các tính năng đã cấu hình
* [cite_start]**Phân đoạn mạng:** Cách ly mạng nội bộ và DMZ khỏi mạng ngoài internet[cite: 240].
* [cite_start]**NAT & Firewall Rules:** Cấu hình các quy tắc firewall để đảm bảo an toàn giữa các khu vực mạng trên pfSense[cite: 119].
* [cite_start]**Bảo vệ Web Server:** Cho phép truy cập an toàn vào dịch vụ công khai tại DMZ mà không làm lộ mạng nội bộ[cite: 243, 250].
