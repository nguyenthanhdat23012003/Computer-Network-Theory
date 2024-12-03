**[Vietnamese Below]**

## Modes, Methods, and Quality of Information Transmission

### 1. Transmission Modes

Transmission modes describe the direction of information flow between two devices in a network. There are three primary modes:

- **Simplex Mode:** Allows information to flow in only one direction. A device can either send or receive information but not both.

- **Half-Duplex Mode:** Allows bidirectional communication, but not simultaneously. A device can send and receive data, but only one function operates at a time.

- **Full-Duplex Mode:** Enables simultaneous bidirectional communication. Devices can send and receive data at the same time.



### 2. Transmission Methods

Transmission methods describe the number of devices involved in the communication process. Key methods include:

- **Unicast:** Information is transmitted from one device to another specific device. This is the most basic and common model.

- **Broadcast:** Information is transmitted from one device to all other devices in the network. This method is crucial for many network protocols.

- **Multicast:** Information is transmitted from one device to a group of devices. This method is often used by routers and routing protocols.



### 3. Collision and Collision Domain

- **Signal Collision:** Occurs when signals from multiple sources interfere, causing communication failure.

- **Collision Domain:** A network area where signals can collide. Devices like repeaters and hubs expand the collision domain, while bridges and switches isolate collision domains.

- **Broadcast Domain:** A network area where data frames can move freely without restriction. Devices within the same broadcast domain can exchange data frames.



### 4. Quality of Information Transmission

- **Bandwidth:** The maximum rate of data transmission over a link, typically measured in bps (bits per second).

- **Throughput:** The actual average rate of data transmission over a network link.

- **Goodput:** The effective data transmission rate of a network link, excluding protocol overhead.

- **Latency:** The time required to transfer a block of data from one node to another, including:
  
  - **Processing Delay:** Time taken to process or encapsulate packets at nodes.
  
  - **Propagation Delay:** Time taken for a single bit of information to travel across the link from source to destination.
  
  - **Transmission Delay:** Time required to push all the bits of a frame onto the transmission medium.
  
  - **Queueing Delay:** Time spent in queues at network nodes.



These concepts are crucial for designing and optimizing network systems, ensuring efficiency and reliability in information transmission.

---

## Chế độ, phương thức và chất lượng truyền thông tin

### 1. Chế độ truyền thông tin (Transmission mode)

Chế độ truyền thông tin thể hiện chiều truyền thông tin giữa hai thiết bị trong mạng. Có ba chế độ chính:

- **Chế độ đơn công (Simplex):** Chỉ cho phép truyền thông tin theo một chiều. Một thiết bị chỉ có thể gửi hoặc nhận thông tin, không thể thực hiện cả hai cùng lúc.
  
- **Chế độ bán song công (Half-duplex):** Cho phép truyền thông tin hai chiều, nhưng không đồng thời. Một thiết bị có thể gửi và nhận dữ liệu, nhưng chỉ một trong hai chức năng có thể hoạt động tại một thời điểm.

- **Chế độ song công (Full-duplex):** Cho phép truyền thông tin hai chiều đồng thời. Thiết bị có thể gửi và nhận dữ liệu tại cùng một thời điểm.



### 2. Phương thức truyền thông tin (Transmission method)

Phương thức truyền thông tin mô tả số lượng thiết bị tham gia vào quá trình truyền thông tin. Các phương thức chính bao gồm:

- **Unicast:** Truyền thông tin từ một thiết bị tới một thiết bị khác. Đây là mô hình cơ bản và phổ biến nhất.

- **Broadcast:** Truyền thông tin từ một thiết bị tới tất cả thiết bị khác trong mạng. Điều này rất quan trọng cho hoạt động của nhiều giao thức mạng.

- **Multicast:** Truyền thông tin từ một thiết bị tới một nhóm thiết bị khác. Phương thức này thường được sử dụng bởi router và các giao thức định tuyến.



### 3. Xung đột và miền xung đột

- **Xung đột tín hiệu:** Tình trạng tín hiệu đến từ nhiều nguồn “va chạm” nhau, dẫn đến việc truyền thông tin thất bại.

- **Miền xung đột (Collision domain):** Khu vực trong mạng nơi tín hiệu có khả năng gây xung đột. Các thiết bị như repeater và hub có thể mở rộng miền xung đột, trong khi bridge và switch có tác dụng tách biệt miền xung đột.

- **Miền quảng bá (Broadcast domain):** Khu vực mạng nơi frame dữ liệu di chuyển tự do mà không bị ngăn chặn. Các thiết bị trong cùng một miền quảng bá có thể gửi frame dữ liệu cho nhau.



### 4. Chất lượng truyền thông tin

- **Băng thông (Bandwidth):** Tốc độ truyền thông tin tối đa qua một đường liên kết, thường đo bằng bps (bit per second).

- **Thông lượng (Throughput):** Tốc độ truyền thông tin thực tế trung bình qua một liên kết mạng.

- **Thông lượng hữu dụng (Goodput):** Tốc độ truyền thông tin thực tế của liên kết mạng, không bao gồm các thông tin hỗ trợ giao thức.

- **Độ trễ:** Khoảng thời gian cần thiết để chuyển một khối dữ liệu từ node này đến node khác, bao gồm:
  
  - **Trễ xử lý:** Thời gian đóng gói hoặc xử lý gói tin tại các node.
  
  - **Trễ truyền lan:** Thời gian truyền một bit thông tin trên đường liên kết từ nguồn đến đích.
  
  - **Trễ truyền tin:** Thời gian để truyền hết các bit của một frame lên đường truyền.

  - **Trễ hàng đợi:** Thời gian xử lý tại các hàng đợi trong các node mạng.



Những khái niệm này rất quan trọng trong việc thiết kế và tối ưu hóa các hệ thống mạng, giúp đảm bảo tính hiệu quả và độ tin cậy trong việc truyền thông tin.
