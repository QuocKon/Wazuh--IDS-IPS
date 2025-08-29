# Wazuh--IDS-IPS
## Lý thuyết về Wazuh
1️⃣ Giới thiệu Wazuh

Wazuh là nền tảng SIEM (Security Information and Event Management) và IDS/IPS (Intrusion Detection/Prevention System) mã nguồn mở.

Chức năng chính:

Phân tích nhật ký (log analysis).

Giám sát tính toàn vẹn tệp (File Integrity Monitoring - FIM).

Phát hiện phần mềm độc hại và hành vi bất thường.

Quản lý tuân thủ (PCI DSS, GDPR, HIPAA, NIST…).

Hỗ trợ phản ứng chủ động (Active Response) để ngăn chặn tấn công.

2️⃣ Các thành phần chính của Wazuh

Wazuh Agent: Cài đặt trên endpoint (Windows, Linux, macOS, cloud instance). Thu thập log, giám sát hệ thống, gửi dữ liệu về server.

Wazuh Server:

Phân tích dữ liệu từ agent thông qua decoders & rules.

Quản lý agent, cấu hình, cập nhật từ xa.

Kích hoạt cảnh báo và phản ứng chủ động.

Wazuh Indexer: Lưu trữ & lập chỉ mục dữ liệu log/cảnh báo, hỗ trợ tìm kiếm & phân tích real-time.

Wazuh Dashboard: Giao diện web để trực quan hóa, phân tích dữ liệu, quản lý agent và cấu hình hệ thống.

Cơ chế giao tiếp:

Agent ↔ Server: Kết nối bảo mật (AES/TLS).

Server ↔ Indexer: Thông qua Filebeat, dữ liệu được lập chỉ mục và lưu trữ.

Dashboard ↔ Server: Sử dụng RESTful API để quản lý và hiển thị dữ liệu.

3️⃣ Cài đặt và cấu hình Wazuh

Cài đặt 3 thành phần chính: Indexer, Server, Dashboard.

Quá trình cài đặt gồm:

Chuẩn bị môi trường (Linux server, IP cố định).

Chạy script cài đặt (wazuh-install.sh) với file cấu hình config.yml.

Khởi chạy dịch vụ và kiểm tra trạng thái (systemctl status ...).

Cài đặt agent trên máy mục tiêu (Linux/Windows).

Sau khi cài đặt thành công, agent kết nối về server và hiển thị trong dashboard.

4️⃣ Hệ thống luật (Rules) trong Wazuh

Rules là trung tâm phát hiện sự kiện bảo mật. Được viết bằng XML, áp dụng trên log đã được giải mã.

Có 2 loại:

Default rules: Có sẵn trong thư mục /var/ossec/ruleset/rules/.

Custom rules: Người dùng tự định nghĩa tại /var/ossec/etc/rules/local_rules.xml.

Các rule có ID duy nhất, mức độ cảnh báo (Level 0–15).

Rule có thể được tạo mới hoặc ghi đè lên rule mặc định bằng thẻ overwrite="yes".

Ví dụ:

Rule phát hiện nhiều lần đăng nhập SSH thất bại → cảnh báo brute force.

Rule giám sát thay đổi tệp hệ thống → cảnh báo FIM.

5️⃣ Active Response

Cho phép phản ứng tự động khi phát hiện tấn công.

Ví dụ:

Phát hiện brute force SSH → tự động chặn IP tấn công bằng firewall.

Phát hiện tiến trình độc hại → dừng tiến trình.

Giúp giảm thiểu thiệt hại trước khi quản trị viên kịp xử lý.

👉 Tóm lại, Wazuh là một hệ thống mạnh mẽ, kết hợp giám sát an ninh tập trung + phát hiện xâm nhập + phản ứng tự động. Hai chương đầu cung cấp nền tảng lý thuyết quan trọng: từ kiến trúc, cơ chế hoạt động, đến cách cài đặt, cấu hình và xây dựng luật bảo mật trong Wazuh.
