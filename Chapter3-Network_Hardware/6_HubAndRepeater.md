# Hub và Repeater

### Repeater (Bộ lặp tín hiệu)
- **Repeater** là thiết bị mạng LAN dùng để tái tạo và khuếch đại tín hiệu. Do tín hiệu truyền đi ở khoảng cách lớn có thể bị suy hao, repeater giúp đảm bảo tín hiệu được duy trì ổn định trên đường truyền dài.

### Hub (Bộ tập trung tín hiệu)
- **Hub** là thiết bị mạng LAN với nhiều cổng cho phép kết nối nhiều thiết bị, thực hiện nhiệm vụ chuyển tiếp tín hiệu giữa tất cả các thiết bị kết nối với nó.
- Mỗi hub có nhiều cổng **RJ45** để:
  - Kết nối với thiết bị đầu cuối qua **cáp thẳng**.
  - Kết nối với hub khác qua **cáp chéo**.
- Hub giúp mở rộng mạng LAN về cả phạm vi và số lượng thiết bị.
- **Cách thức hoạt động của Hub**:
  - Hub chuyển tiếp tín hiệu nhận từ một cổng đến tất cả các cổng còn lại. 
  - Các thiết bị ở các cổng sẽ so sánh địa chỉ MAC trong tín hiệu nhận được để xác định xem thông tin có dành cho mình hay không.
- **Xung đột tín hiệu**: Nếu nhiều thiết bị cùng gửi tín hiệu lên đường truyền, sẽ có nguy cơ xung đột tín hiệu, gây hỏng quá trình truyền thông. Để kiểm soát điều này, sử dụng giao thức **CSMA/CD** (Carrier-Sense Multiple Access with Collision Detection).
- **So sánh với Repeater**: Hub tương tự như repeater nhưng có nhiều cổng hơn, cho phép kết nối nhiều thiết bị hơn.

### Phân loại Hub
- **Passive Hub**: Chỉ chuyển tiếp tín hiệu mà không khuếch đại. Khoảng cách từ máy tính đến hub phải nhỏ hơn hoặc bằng nửa khoảng cách giữa hai máy tính trên mạng.
- **Active Hub**: Có khả năng khuếch đại và tái tạo tín hiệu, giúp tăng khoảng cách truyền.
- **Intelligent Hub**: Hub chủ động có thêm chức năng hỗ trợ quản trị.

### Ưu và nhược điểm của Hub và Repeater
- **Ưu điểm**: Giá thành rẻ, dễ lắp đặt.
- **Nhược điểm**:
  - Không phân biệt được tín hiệu thực và nhiễu.
  - Không làm giảm lưu lượng mạng hoặc tránh tắc nghẽn.
  - Bị giới hạn về số lượng kết nối.
