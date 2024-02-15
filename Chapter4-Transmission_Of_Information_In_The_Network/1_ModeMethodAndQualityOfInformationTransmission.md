# Chế độ, phương thức và chất lượng truyền thông tin

## 1. Chế độ truyền thông tin (Transmission mode)

Chế độ truyền thông tin thể hiện chiều truyền thông tin giữa hai thiết bị trong mạng. Có ba chế độ chính:

- **Chế độ đơn công (Simplex):** Chỉ cho phép truyền thông tin theo một chiều. Một thiết bị chỉ có thể gửi hoặc nhận thông tin, không thể thực hiện cả hai cùng lúc.
  
- **Chế độ bán song công (Half-duplex):** Cho phép truyền thông tin hai chiều, nhưng không đồng thời. Một thiết bị có thể gửi và nhận dữ liệu, nhưng chỉ một trong hai chức năng có thể hoạt động tại một thời điểm.

- **Chế độ song công (Full-duplex):** Cho phép truyền thông tin hai chiều đồng thời. Thiết bị có thể gửi và nhận dữ liệu tại cùng một thời điểm.

---

## 2. Phương thức truyền thông tin (Transmission method)

Phương thức truyền thông tin mô tả số lượng thiết bị tham gia vào quá trình truyền thông tin. Các phương thức chính bao gồm:

- **Unicast:** Truyền thông tin từ một thiết bị tới một thiết bị khác. Đây là mô hình cơ bản và phổ biến nhất.

- **Broadcast:** Truyền thông tin từ một thiết bị tới tất cả thiết bị khác trong mạng. Điều này rất quan trọng cho hoạt động của nhiều giao thức mạng.

- **Multicast:** Truyền thông tin từ một thiết bị tới một nhóm thiết bị khác. Phương thức này thường được sử dụng bởi router và các giao thức định tuyến.

---

## 3. Xung đột và miền xung đột

- **Xung đột tín hiệu:** Tình trạng tín hiệu đến từ nhiều nguồn “va chạm” nhau, dẫn đến việc truyền thông tin thất bại.

- **Miền xung đột (Collision domain):** Khu vực trong mạng nơi tín hiệu có khả năng gây xung đột. Các thiết bị như repeater và hub có thể mở rộng miền xung đột, trong khi bridge và switch có tác dụng tách biệt miền xung đột.

- **Miền quảng bá (Broadcast domain):** Khu vực mạng nơi frame dữ liệu di chuyển tự do mà không bị ngăn chặn. Các thiết bị trong cùng một miền quảng bá có thể gửi frame dữ liệu cho nhau.

---

## 4. Chất lượng truyền thông tin

- **Băng thông (Bandwidth):** Tốc độ truyền thông tin tối đa qua một đường liên kết, thường đo bằng bps (bit per second).

- **Thông lượng (Throughput):** Tốc độ truyền thông tin thực tế trung bình qua một liên kết mạng.

- **Thông lượng hữu dụng (Goodput):** Tốc độ truyền thông tin thực tế của liên kết mạng, không bao gồm các thông tin hỗ trợ giao thức.

- **Độ trễ:** Khoảng thời gian cần thiết để chuyển một khối dữ liệu từ node này đến node khác, bao gồm:
  
  - **Trễ xử lý:** Thời gian đóng gói hoặc xử lý gói tin tại các node.
  
  - **Trễ truyền lan:** Thời gian truyền một bit thông tin trên đường liên kết từ nguồn đến đích.
  
  - **Trễ truyền tin:** Thời gian để truyền hết các bit của một frame lên đường truyền.

  - **Trễ hàng đợi:** Thời gian xử lý tại các hàng đợi trong các node mạng.

---

Những khái niệm này rất quan trọng trong việc thiết kế và tối ưu hóa các hệ thống mạng, giúp đảm bảo tính hiệu quả và độ tin cậy trong việc truyền thông tin.
