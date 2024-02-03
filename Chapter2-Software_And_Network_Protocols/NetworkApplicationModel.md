# Mô hình ứng dụng mạng

Khi phát triển một phần mềm mạng, một vấn đề quan trọng là **vai trò của các thành phần trong hệ thống**.

**Mô hình (kiến trúc) ứng dụng mạng** là sự phân chia vai trò và nhiệm vụ của các thành phần trong một hệ thống phần mềm ứng dụng mạng, cũng như cách thức chúng liên kết với nhau. Có hai mô hình chính:

---

### Mô hình Client-Server
- Ứng dụng được chia làm hai phần:
  - **Server**: Chuyển gửi thông tin đi.
  - **Client**: Nhận thông tin về.
- **Đặc điểm của mô hình Client-Server**:
  - Chương trình server phải luôn hoạt động để chờ phục vụ các client.
  - Server phải hoạt động trên máy chủ có **địa chỉ cố định** mà client có thể xác định được. Địa chỉ này gọi là **địa chỉ IP**.
  - Các chương trình client không giao tiếp trực tiếp với nhau mà thông qua server.

---

### Mô hình Peer-to-Peer (P2P)
- Tất cả các thành phần trong hệ thống đều có vai trò giống nhau, không có server chuyên biệt.
- **Peer**: Mỗi ứng dụng chạy trên một máy, được gọi là một peer.
- **Đặc điểm của mô hình P2P**:
  - Các peer có thể trực tiếp truyền thông với nhau mà không cần server.
  - Khả năng mở rộng tốt.
  - Ưu thế về chi phí, không đòi hỏi hạ tầng máy chủ và băng thông lớn.
