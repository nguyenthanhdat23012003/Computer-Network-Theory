**[Vietnamese Below]**

# OSI (Open System Interconnection) Model

The OSI model is an ISO standard that encompasses all aspects of network communication, enabling any two systems to communicate without concern for the underlying architecture. Proprietary protocols from specific manufacturers often prevent communication between systems of different types. The OSI model was developed to ensure interoperability between any two systems.

The OSI model is not a protocol but a framework for recognizing and designing a flexible, robust, and interoperable network architecture. The OSI model consists of seven distinct yet interrelated layers:

1. **Physical Layer**
   - **Role:** Manages the physical aspects of data transmission, including voltages, cables, connectors, and physical signals. This layer defines how data is transmitted as bits over the transmission medium (copper cables, fiber optics, or wireless).
   - **Data Unit:** Bit (0 and 1).

2. **Data Link Layer**
   - **Role:** Facilitates data transfer between devices on the same network. It handles error detection and correction, access control, and data framing. This layer also manages physical addresses (MAC addresses).
   - **Data Unit:** Frame.

3. **Network Layer**
   - **Role:** Determines the path for data to travel from source to destination across multiple networks (routing). It manages logical addresses (IP addresses) and ensures data reaches its destination via routers.
   - **Data Unit:** Packet.

4. **Transport Layer**
   - **Role:** Ensures reliable data transfer between devices on a network, manages segmentation and reassembly of data, flow control, and error handling. Common protocols include TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).
   - **Data Unit:** Segment (TCP) or Datagram (UDP).

5. **Session Layer**
   - **Role:** Manages communication sessions between applications. This layer establishes, maintains, and terminates sessions. It also handles data synchronization and recovery in case of errors.
   - **Data Unit:** Data (application-level data).

6. **Presentation Layer**
   - **Role:** Handles the syntax and semantics of the information exchanged between systems. Tasks include encryption, decryption, compression, and decompression of data. This ensures that data from one system's application layer can be read by another system's application layer.
   - **Data Unit:** Data (application-level data).

7. **Application Layer**
   - **Role:** Provides direct network services to user applications. This layer includes protocols and services that users interact with directly, such as HTTP, FTP, SMTP, and DNS.
   - **Data Unit:** Data (application-level data).



## Data Flow Through OSI Layers

### When Data is Sent From a Device:

**From Top to Bottom:**
1. **Layer 7 (Application):** Data is generated and prepared for transmission.
2. **Layer 6 (Presentation):** Data is encoded and compressed if necessary.
3. **Layer 5 (Session):** A communication session is established.
4. **Layer 4 (Transport):** Data is segmented and control information is added.
5. **Layer 3 (Network):** Source and destination IP addresses are added.
6. **Layer 2 (Data Link):** Data is framed and MAC addresses are added.
7. **Layer 1 (Physical):** Data is converted into electrical signals or radio waves and transmitted over the physical medium.

**From Bottom to Top:**
1. **Layer 1 (Physical):** Physical signals are received and converted into bits.
2. **Layer 2 (Data Link):** Frames are validated, and MAC addresses are checked.
3. **Layer 3 (Network):** IP addresses are checked, and data is routed to the destination.
4. **Layer 4 (Transport):** Data is reassembled from segments, and integrity is verified.
5. **Layer 5 (Session):** The communication session is managed and synchronized.
6. **Layer 6 (Presentation):** Data is decoded and decompressed if necessary.
7. **Layer 7 (Application):** Data is delivered to the user application.

---

# Mô hình kết nối các hệ thống mở OSI

Là một trong các chuẩn ISO bao hàm mọi mặt về truyền thông mạng, cho phép bất cứ hai hệ thống nào có thể truyền thông với nhau mà không cần quan tâm đến kiến trúc bên dưới của chúng. Các giao thức riêng của một hãng sản xuất thường ngăn ngừa việc truyền thông giữa hai hệ thống không cùng một kiểu -> mô hình OSI ra đời để hai hệ thống bất kỳ có thể giao tiếp với nhau.

Mô hình OSI không phải một giao thức, nó là một mô hình để nhận biết và thiết kế một kiến trúc mạng linh động, vững chắc và có khả năng liên tác. Mô hình OSI gồm 7 tầng riêng biệt nhưng có liên quan đến nhau:

1. **Tầng vật lý (Physical Layer)**
   - **Vai trò:** Chịu trách nhiệm về các khía cạnh vật lý của việc truyền dữ liệu, bao gồm điện áp, cáp, đầu nối, và tín hiệu vật lý. Tầng này xác định các đặc điểm về cách dữ liệu được truyền đi dưới dạng các bit trên phương tiện truyền dẫn (cáp đồng, cáp quang, hoặc không dây).
   - **Dữ liệu:** Bit (0 và 1).

2. **Tầng liên kết dữ liệu (Data Link Layer)**
   - **Vai trò:** Cung cấp phương tiện để chuyển dữ liệu giữa các thiết bị trên cùng một mạng. Nó xử lý việc phát hiện và sửa lỗi, điều khiển truy cập đường truyền, và tạo ra các khung dữ liệu (frames). Tầng này cũng quản lý các địa chỉ vật lý (địa chỉ MAC).
   - **Dữ liệu:** Frame.

3. **Tầng mạng (Network Layer)**
   - **Vai trò:** Xác định đường đi cho dữ liệu từ nguồn đến đích qua nhiều mạng khác nhau (định tuyến). Nó quản lý các địa chỉ logic (địa chỉ IP) và đảm bảo dữ liệu đến đúng đích thông qua các router.
   - **Dữ liệu:** Packet.

4. **Tầng giao vận (Transport Layer)**
   - **Vai trò:** Đảm bảo truyền dữ liệu một cách đáng tin cậy giữa các thiết bị trên mạng, quản lý việc phân đoạn và tập hợp lại các gói dữ liệu, và kiểm soát luồng và xử lý lỗi. Các giao thức phổ biến ở tầng này là TCP (Transmission Control Protocol) và UDP (User Datagram Protocol).
   - **Dữ liệu:** Segment (TCP) hoặc Datagram (UDP).

5. **Tầng phiên (Session Layer)**
   - **Vai trò:** Quản lý các phiên giao tiếp giữa các ứng dụng. Tầng này thiết lập, duy trì, và kết thúc các phiên kết nối. Nó cũng quản lý việc đồng bộ hóa dữ liệu và khôi phục lại các phiên khi có sự cố.
   - **Dữ liệu:** Data (dữ liệu ứng dụng).

6. **Tầng trình diễn (Presentation Layer)**
   - **Vai trò:** Chịu trách nhiệm về cú pháp và ngữ nghĩa của thông tin trao đổi giữa các hệ thống. Nó thực hiện các nhiệm vụ như mã hóa, giải mã, nén, và giải nén dữ liệu. Tầng này đảm bảo rằng dữ liệu từ tầng ứng dụng của một hệ thống có thể được đọc bởi tầng ứng dụng của hệ thống khác.
   - **Dữ liệu:** Data (dữ liệu ứng dụng).

7. **Tầng ứng dụng (Application Layer)**
   - **Vai trò:** Cung cấp các dịch vụ mạng trực tiếp cho các ứng dụng người dùng. Tầng này bao gồm các giao thức và dịch vụ mà người dùng cuối tương tác trực tiếp như HTTP, FTP, SMTP, và DNS.
   - **Dữ liệu:** Data (dữ liệu ứng dụng).



## Luồng đi của dữ liệu qua các tầng trong mô hình OSI

### Khi dữ liệu được gửi từ một thiết bị:

**Từ trên xuống dưới:**
1. **Tầng 7 (Application):** Dữ liệu được tạo ra và chuẩn bị gửi đi.
2. **Tầng 6 (Presentation):** Dữ liệu được mã hóa và nén nếu cần.
3. **Tầng 5 (Session):** Phiên giao tiếp được thiết lập.
4. **Tầng 4 (Transport):** Dữ liệu được phân đoạn và thêm các thông tin điều khiển.
5. **Tầng 3 (Network):** Địa chỉ IP nguồn và đích được thêm vào.
6. **Tầng 2 (Data Link):** Dữ liệu được đóng gói thành các khung và thêm địa chỉ MAC.
7. **Tầng 1 (Physical):** Dữ liệu được chuyển đổi thành tín hiệu điện hoặc sóng radio và truyền đi qua phương tiện vật lý.

**Từ dưới lên trên:**
1. **Tầng 1 (Physical):** Tín hiệu vật lý được nhận và chuyển thành bit.
2. **Tầng 2 (Data Link):** Các khung dữ liệu được xác nhận và địa chỉ MAC được kiểm tra.
3. **Tầng 3 (Network):** Địa chỉ IP được kiểm tra và định tuyến dữ liệu tới đích.
4. **Tầng 4 (Transport):** Dữ liệu được tập hợp lại từ các phân đoạn và kiểm tra tính toàn vẹn.
5. **Tầng 5 (Session):** Phiên giao tiếp được quản lý và đồng bộ hóa.
6. **Tầng 6 (Presentation):** Dữ liệu được giải mã và giải nén nếu cần.
7. **Tầng 7 (Application):** Dữ liệu được chuyển tới ứng dụng người dùng.
