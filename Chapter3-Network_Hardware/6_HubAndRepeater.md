**[Vietnamese Below]**

# Hub and Repeater

### Repeater (Signal Amplifier)
- A **Repeater** is a LAN device used to regenerate and amplify signals. Since signals degrade over long distances, a repeater ensures stable signal transmission over extended paths.

### Hub (Signal Concentrator)
- A **Hub** is a LAN device with multiple ports that allows connections to multiple devices, forwarding signals between all connected devices.
- Each hub features multiple **RJ45 ports** for:
  - Connecting to end devices via **straight-through cables**.
  - Connecting to other hubs via **crossover cables**.
- Hubs expand LANs in both range and the number of connected devices.
- **How a Hub Works**:
  - A hub forwards signals received from one port to all other ports.
  - Devices connected to these ports compare the MAC address in the received signal to determine if the information is intended for them.
- **Signal Collision**: If multiple devices transmit signals simultaneously, collisions may occur, disrupting communication. This is managed using the **CSMA/CD** (Carrier-Sense Multiple Access with Collision Detection) protocol.
- **Comparison with Repeater**: A hub functions similarly to a repeater but includes multiple ports, enabling connections to several devices.

### Types of Hubs
- **Passive Hub**: Simply forwards signals without amplifying them. The distance from a computer to the hub must not exceed half the maximum distance between two computers in the network.
- **Active Hub**: Amplifies and regenerates signals, extending the transmission range.
- **Intelligent Hub**: An active hub with additional administrative support features.

### Advantages and Disadvantages of Hubs and Repeaters
- **Advantages**:
  - Cost-effective.
  - Easy to install.
- **Disadvantages**:
  - Cannot distinguish between real signals and noise.
  - Does not reduce network traffic or prevent congestion.
  - Limited in the number of connections.

<div style="border-top: 2px solid white; margin: 20px 0;"></div>

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
