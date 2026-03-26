# XÂY DỰNG HỆ THỐNG MẠNG THREE-LEGGED FIREWALL VỚI PFSENSE

## 📖 Giới thiệu
Dự án triển khai mô hình tường lửa 3 chân (Three-Legged Firewall) sử dụng nền tảng mã nguồn mở pfSense. Mục tiêu cốt lõi là thiết lập các khu vực mạng cách ly an toàn bao gồm mạng nội bộ (Internal), vùng DMZ và Internet, từ đó phân tách rõ ràng luồng truy cập và bảo vệ cơ sở hạ tầng mạng khỏi các rủi ro xâm nhập.

## 🏗️ Kiến Trúc Hệ Thống (Network Architecture)

![Mô hình mạng Three-Legged Firewall](images/.png)

Hệ thống được thiết kế với 3 vùng mạng độc lập, tuân thủ nguyên tắc quyền tối thiểu (principle of least privilege):
1. **Internet (WAN):** Mạng toàn cầu không đáng tin cậy. Nhận IP thông qua DHCP (Ví dụ: `10.10.10.128/24`).
2. **DMZ (Demilitarized Zone):** Khu vực trung gian chứa Public Web Server (`192.168.5.10/24`). Các kết nối từ bên ngoài chỉ có thể tiếp cận vùng này.
3. **Internal Network (LAN):** Mạng riêng nội bộ lưu trữ dữ liệu. Gồm máy trạm (`192.168.0.10/24`) và máy client (`192.168.0.25/24`). 

## ⚙️ Các Chức Năng Đã Triển Khai

Hệ thống sử dụng tường lửa pfSense với các tính năng định tuyến và kiểm soát truy cập chi tiết:

* **Network Address Translation (NAT):** Cấu hình Hybrid Outbound NAT để dịch địa chỉ IP nội bộ, ẩn hoàn toàn mạng LAN và máy chủ DMZ khỏi mạng bên ngoài.
  
  ![Cấu hình NAT](images/nat_configuration.png)

* **Firewall Aliases:** Tạo tập hợp định danh để quản lý rule gọn gàng, bao gồm dải IP bị chặn (`Blocked_IPs`:
