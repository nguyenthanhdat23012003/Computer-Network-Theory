**[Vietnamese Below]**

# Network Application Models

When developing network software, an important consideration is the **role of components in the system**.

A **network application model (architecture)** defines the division of roles and tasks of components in a network application system and how they are interconnected. There are two main models:



### Client-Server Model
- The application is divided into two parts:
  - **Server**: Sends information.
  - **Client**: Receives information.
- **Characteristics of the Client-Server Model**:
  - The server program must always be active to serve clients.
  - The server must operate on a host machine with a **fixed address** that clients can identify. This address is called an **IP address**.
  - Client programs do not communicate directly with each other but through the server.



### Peer-to-Peer (P2P) Model
- All components in the system have the same role; there is no dedicated server.
- **Peer**: Each application running on a machine is called a peer.
- **Characteristics of the P2P Model**:
  - Peers can communicate directly with each other without a server.
  - High scalability.
  - Cost advantages, as it does not require expensive server infrastructure or high bandwidth.

---

# Mô hình ứng dụng mạng

Khi phát triển một phần mềm mạng, một vấn đề quan trọng là **vai trò của các thành phần trong hệ thống**.

**Mô hình (kiến trúc) ứng dụng mạng** là sự phân chia vai trò và nhiệm vụ của các thành phần trong một hệ thống phần mềm ứng dụng mạng, cũng như cách thức chúng liên kết với nhau. Có hai mô hình chính:



### Mô hình Client-Server
- Ứng dụng được chia làm hai phần:
  - **Server**: Chuyển gửi thông tin đi.
  - **Client**: Nhận thông tin về.
- **Đặc điểm của mô hình Client-Server**:
  - Chương trình server phải luôn hoạt động để chờ phục vụ các client.
  - Server phải hoạt động trên máy chủ có **địa chỉ cố định** mà client có thể xác định được. Địa chỉ này gọi là **địa chỉ IP**.
  - Các chương trình client không giao tiếp trực tiếp với nhau mà thông qua server.



### Mô hình Peer-to-Peer (P2P)
- Tất cả các thành phần trong hệ thống đều có vai trò giống nhau, không có server chuyên biệt.
- **Peer**: Mỗi ứng dụng chạy trên một máy, được gọi là một peer.
- **Đặc điểm của mô hình P2P**:
  - Các peer có thể trực tiếp truyền thông với nhau mà không cần server.
  - Khả năng mở rộng tốt.
  - Ưu thế về chi phí, không đòi hỏi hạ tầng máy chủ và băng thông lớn.
