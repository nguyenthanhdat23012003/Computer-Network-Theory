**[Vietnamese Below]**

### Terminal Equipment in Computer Networks

Terminal equipment are essential components in computer networks, serving as the source or destination of user data. To operate in a network environment, an terminal equipment must ensure both hardware and software connectivity.

#### 1. Physical Connection to the Network
To establish a physical connection, terminal equipment use a **NIC (Network Interface Card)**, also known as a network card. This device enables computers or terminal equipment to connect to a network. A single device can have multiple NICs to connect to multiple networks simultaneously.

#### 2. Logical Connection
Logical connections between terminal equipment and the network are maintained through various protocols. To function within a network, an terminal equipment requires an operating system (OS) with integrated TCP/IP protocol support. All modern operating systems support the TCP/IP protocol suite, allowing efficient network participation.

#### 3. IP Address
In a network with multiple terminal equipment, each device, called a **node**, is assigned a unique address known as an **IP address**. This IP address helps identify and differentiate devices within the network.

#### 4. Network Application Software
Applications installed on terminal equipment can interact with the network via protocols supported by the operating system. These applications are referred to as **network application software**. Protocols at the transport and internet layers do not directly handle user data but process byte streams.

#### 5. Data Conversion
To utilize protocols, application programs must convert user data into byte streams and vice versa. Protocols at these layers automatically generate their data by adding a small byte sequence called a **header** to the beginning of the received byte stream (payload), forming a larger byte sequence.

#### 6. Protocol Data Unit (PDU)
The larger byte sequence is called a **PDU (Protocol Data Unit)**, which includes:
- **Protocol Control Information (PCI)**.
- **Service Data Unit (SDU)**.

- The PDU of TCP is called a **segment**.
- The PDU of UDP is called a **datagram**.
- The PDU of IP is called a **packet**.

Specifically, an IP packet includes:
- **IP header** (control information for the IP protocol).
- **Segment** or **Datagram** (depending on the transport protocol used).

Thus, terminal equipment are not just simple connection points but also play a critical role in data transport and processing within a computer network.

<div style="border-top: 2px solid white; margin: 20px 0;"></div>

### Thiết bị đầu cuối trong mạng máy tính

Thiết bị đầu cuối là thành phần quan trọng trong mạng máy tính, đóng vai trò nguồn hoặc đích của dữ liệu người dùng. Để thiết bị đầu cuối có thể hoạt động trong môi trường mạng, nó cần đảm bảo kết nối cả về mặt phần cứng và phần mềm.

#### 1. Kết nối vật lý với mạng
Để kết nối vật lý với mạng, thiết bị đầu cuối sử dụng **NIC (Network Interface Card)**, còn được gọi là card mạng hoặc card giao diện mạng. Thiết bị này cho phép máy tính hoặc thiết bị đầu cuối kết nối với mạng. Có thể gắn nhiều card mạng trên một thiết bị để kết nối với nhiều mạng khác nhau.

#### 2. Kết nối logic
Kết nối logic giữa thiết bị đầu cuối và mạng được đảm bảo thông qua nhiều giao thức khác nhau. Để có thể hoạt động trên mạng, thiết bị đầu cuối cần cài đặt một hệ điều hành (OS) có tích hợp bộ giao thức TCP/IP. Tất cả các hệ điều hành hiện nay đều hỗ trợ bộ giao thức này, cho phép thiết bị tham gia vào mạng một cách hiệu quả.

#### 3. Địa chỉ IP
Trên một mạng có nhiều thiết bị đầu cuối, mỗi thiết bị được gọi là **node** và được gán một địa chỉ duy nhất, gọi là **địa chỉ IP**. Địa chỉ IP này giúp định danh và phân biệt các thiết bị trong mạng.

#### 4. Phần mềm ứng dụng mạng
Các phần mềm được cài đặt trên thiết bị đầu cuối có thể thông qua các giao thức do hệ điều hành hỗ trợ để tương tác với mạng máy tính. Những phần mềm này thường được gọi là **phần mềm ứng dụng mạng**. Tất cả các giao thức ở tầng giao vận và tầng liên mạng không trực tiếp làm việc với dữ liệu người dùng mà chỉ xử lý các chuỗi byte.

#### 5. Chuyển đổi dữ liệu
Để khai thác các giao thức, chương trình ứng dụng cần phải chuyển đổi dữ liệu người dùng thành chuỗi byte và ngược lại. Các giao thức ở hai tầng này tự động tạo ra dữ liệu của riêng mình bằng cách bổ sung thêm một chuỗi byte nhỏ gọi là **header** vào trước chuỗi byte mà nó nhận (payload), tạo thành một chuỗi byte lớn hơn.

#### 6. Đơn vị dữ liệu giao thức (PDU)
Chuỗi byte lớn được gọi là **PDU (Protocol Data Unit)**, bao gồm:
- **Thông tin điều khiển của giao thức (PCI - Protocol Control Information)**.
- **Đơn vị dữ liệu dịch vụ (SDU - Service Data Unit)**.

- PDU của TCP được gọi là **segment**.
- PDU của UDP được gọi là **datagram**.
- PDU của IP được gọi là **packet**.

Cụ thể, một packet IP bao gồm:
- **IP header** (thông tin điều khiển của giao thức IP).
- **Segment** hoặc **Datagram** (tùy thuộc vào giao thức truyền tải đang sử dụng).

Như vậy, thiết bị đầu cuối không chỉ là một điểm kết nối đơn giản mà còn là một phần quan trọng trong việc vận chuyển và xử lý dữ liệu trong mạng máy tính.
