**[Vietnamese Below]**

# File Transfer Software and FTP Protocol

## FTP File Transfer System
The FTP file transfer system consists of two independent software components: **FTP client** and **FTP server**, interacting using the FTP protocol.

- **FTP server** consists of two components:
  - **Server Protocol Interpreter** (PI)
  - **Server Data Transfer Process** (DTP)

  The server must interface with the file system on the server machine.

- **FTP client** includes three components:
  - **User Protocol Interpreter** (PI)
  - **User Data Transfer Process** (DTP)
  - **User Interface**

  The client must also interface with the local file system.

### TCP Connections
- **Server PI** and **Client PI** maintain a TCP connection. This connection is established once the client successfully authenticates and is kept alive until the client logs out or the server terminates it. This TCP connection is referred to as the **control connection** or **control channel**.
- **Server DTP** and **User DTP** maintain a second TCP connection when the client requests data transfer. This connection is temporary and only established for the duration of the data transfer. Once the transfer is complete, this connection is terminated. This second TCP connection is referred to as the **data connection** or **data channel**.

- The client includes an additional **User Interface** component. This component allows the end user to interact with the client software. The server lacks a corresponding component. The User Interface merely serves as a medium for user interaction, converting the interaction into equivalent FTP commands or command groups to be sent over the control channel. When a response is received, it converts the response into a user-friendly format. UI commands and FTP commands differ from each other.

## FTP Protocol
The FTP protocol is a standard internet protocol for transferring files between computers over a TCP/IP network, primarily used in FTP file transfer systems and integrated into some IDEs (e.g., JetBrains IDEs).

FTP operates on a request/response model and uses the transport service of TCP. FTP uses two separate TCP connections: one for transmitting control commands and another for transmitting data, making it an **out-of-band** protocol.

- **Control Channel**: The channel maintained between the client and server for exchanging commands and responses.
- **Data Channel**: A temporary channel established to transfer files or directories.

### FTP Commands
FTP commands are sent from the client to the server to request specific actions:
- **Connection Control Commands**: Commands to establish, maintain, and disconnect sessions (e.g., USER, PASS, QUIT, REIN).
- **Data Transfer Commands**: Examples include TYPE, MODE, STRU, ALLO.
- **Directory Control Commands**: Examples include CWD, CDUP, PWD, MKD, RMD, DELE, RNRF, RNTO.
- **Information Commands**: Commands to request or provide information (e.g., SYST, STAT, HELP, NOOP).

FTP commands can be issued using FTP client software or through the operating system's command line interface. Commands may include optional parameters.

### FTP Responses
FTP responses are sequences of characters sent from the server to the client to indicate the status of requests made by the client:
- **1xx**: Temporary replies, asking the client to wait.
- **2xx**: Success responses.
- **3xx**: Responses requiring further client action, such as providing credentials.
- **4xx**: Client-side errors.
- **5xx**: Server-side errors.

## Establishing the Control Channel
Control channel setup process:
1. The client opens a TCP connection to the server on port 21.
2. The server sends a notification to the client and waits for a login request.
3. The client sends a username and password to the server.
4. If authentication is successful, the server sends a confirmation message to the client, granting access to the server's file system.
5. The client can issue control commands to perform actions on the server.
6. The control channel is maintained throughout the session, and the client may terminate it by sending the QUIT command, closing the TCP connection.

## Establishing the Data Channel
There are two data channel modes: **active mode** and **passive mode**.
- In active mode, the client opens a random port and sends this port information to the server via the control channel. The server then opens its port 20 to the client's port to establish the data channel.
- In passive mode, the server opens a random port and sends this port information to the client via the control channel. The client then opens a connection from its random port to the server's port to establish the data channel.

### Passive Data Channel Setup Process
1. The client sends the PASV command via the control channel to request the server to use passive mode.
2. The server opens a random port and responds with a 227 message containing the port information to the client via the control channel.
3. The client sends a data retrieval (RETR) or storage (STOR) command with the file name to be transferred over the control channel to instruct the server to start the transfer.
4. The client opens a connection from its random port to the server's random port to establish the data channel.
5. The server and client begin transferring the file over the data channel.
6. After the transfer is complete, the data channel is closed, and a 226 response is sent via the control channel to confirm the transfer is finished.

### Active Data Channel Setup Process
1. The client provides an unused port and listens on that port.
2. The client uses the FTP PORT command to inform the server which port it is listening on.
3. The server initiates a connection to the client using its port 20.
4. The server sends and receives data through this connection until the transfer is complete or interrupted.

**->** Active mode is simpler and easier to understand, but it may be blocked by firewalls or NAT at the client side.


<div style="border-top: 2px solid white; margin: 20px 0;"></div>

# Phần mềm truyền file và giao thức FTP

## Hệ thống phần mềm truyền file FTP
Hệ thống phần mềm truyền file FTP gồm hai phần mềm độc lập: **FTP client** và **FTP server**, tương tác với nhau sử dụng giao thức FTP.

- **FTP server** gồm hai thành phần:
  - **Server Protocol Interpreter** (PI)
  - **Server Data Transfer Process** (DTP)

  Server phải làm việc được với hệ thống file trên máy chủ.

- **FTP client** bao gồm ba thành phần:
  - **User Protocol Interpreter** (PI)
  - **User Data Transfer Process** (DTP)
  - **User Interface**

  Client cũng phải làm việc với hệ thống file trên máy cục bộ.

### Kết nối TCP
- **Server PI** và **Client PI** duy trì một liên kết TCP. Liên kết TCP này được thiết lập khi client xác thực thành công và được duy trì đến khi client đăng xuất hoặc bị server hủy bỏ. Liên kết TCP này được gọi là **liên kết điều khiển** hoặc **kênh điều khiển**.
- **Server DTP** và **User DTP** duy trì liên kết TCP thứ hai khi client có yêu cầu truyền tải dữ liệu. Liên kết này chỉ được thiết lập tạm thời phục vụ truyền dữ liệu. Sau khi hoàn thành truyền dữ liệu, liên kết này sẽ bị hủy bỏ. Liên kết TCP thứ hai này được gọi là **liên kết dữ liệu** hoặc **kênh dữ liệu**.

- Client có thêm thành phần **User Interface**. Đây là thành phần giúp người dùng cuối sử dụng phần mềm client. Server không có thành phần tương ứng. User Interface chỉ đơn giản là giao diện cho người dùng tương tác, chuyển đổi tương tác đấy thành lệnh hoặc nhóm lệnh FTP tương ứng để đưa lên kênh điều khiển. Khi nhận được phản hồi, nó sẽ chuyển đổi phản hồi đó thành dạng người dùng có thể sử dụng được. Lệnh của UI và lệnh của FTP là khác nhau.

## Giao thức FTP
Giao thức FTP là một giao thức internet tiêu chuẩn dùng để truyền tệp tin giữa các máy tính qua mạng TCP/IP, chủ yếu được sử dụng trong hệ thống phần mềm truyền file FTP và được tích hợp trong một số IDE (ví dụ như các IDE của Jetbrain).

Giao thức FTP hoạt động theo mô hình request/response và sử dụng dịch vụ giao vận của TCP. FTP sử dụng hai liên kết TCP riêng biệt: một kết nối để truyền lệnh điều khiển và một kết nối để truyền dữ liệu, tạo ra giao thức có kiểu truyền **out-of-band**.

- **Kênh điều khiển**: Kênh duy trì giữa client và server để trao đổi các lệnh và phản hồi.
- **Kênh dữ liệu**: Kênh tạm thời được thiết lập để truyền tải các tệp tin hoặc thư mục.

### Lệnh FTP
Các lệnh của giao thức FTP được gửi từ client đến server để yêu cầu một số hành động nhất định:
- **Lệnh điều khiển kết nối**: các lệnh thiết lập, duy trì và ngắt kết nối (USER, PASS, QUIT, REIN).
- **Lệnh truyền tải dữ liệu**: ví dụ TYPE, MODE, STRU, ALLO.
- **Lệnh điều khiển thư mục**: ví dụ CWD, CDUP, PWD, MKD, RMD, DELE, RNRF, RNTO.
- **Lệnh thông tin**: yêu cầu hoặc cung cấp thông tin, ví dụ SYST, STAT, HELP, NOOP.

Các lệnh của giao thức FTP có thể được gửi bằng cách sử dụng phần mềm khách FTP hoặc bằng cách sử dụng cửa sổ dòng lệnh của hệ điều hành. Các lệnh có thể có hoặc không có các tham số đi kèm.

### Phản hồi FTP
Phản hồi FTP là chuỗi các ký tự được gửi từ server đến client để thông báo trạng thái của các yêu cầu được gửi từ máy khách:
- **1xx**: phản hồi tạm thời, yêu cầu client đợi.
- **2xx**: phản hồi thành công.
- **3xx**: phản hồi liên quan đến client, yêu cầu client cung cấp thông tin xác thực.
- **4xx**: lỗi máy khách.
- **5xx**: lỗi máy chủ.

## Thiết lập kênh điều khiển
Quy trình thiết lập kênh điều khiển:
1. Client mở một kết nối TCP đến server trên cổng 21.
2. Server gửi thông báo đến client và chờ yêu cầu đăng nhập từ client.
3. Client gửi tên người dùng và mật khẩu đến server.
4. Nếu xác thực thành công, server gửi thông báo xác nhận đến client và cho phép client truy cập hệ thống tệp của server.
5. Client có thể gửi các lệnh điều khiển đến server để thực hiện các thao tác.
6. Kênh điều khiển được duy trì trong suốt phiên làm việc, để kết thúc thì client có thể gửi lệnh QUIT để đóng kết nối TCP.

## Thiết lập kênh dữ liệu
Có hai chế độ kênh dữ liệu: **chế độ chủ động (active mode)** và **chế độ thụ động (passive mode)**.
- Trong active mode, client mở một cổng ngẫu nhiên và gửi thông tin cổng này cho server qua kênh điều khiển. Server sau đó mở cổng 20 của nó đến cổng của client để thiết lập kênh dữ liệu.
- Trong passive mode, server mở một cổng ngẫu nhiên và gửi thông tin cổng này cho client qua kênh điều khiển. Client sau đó mở kết nối từ cổng ngẫu nhiên của nó đến cổng của server để thiết lập kênh dữ liệu.

### Quy trình thiết lập kênh dữ liệu thụ động
1. Client gửi lệnh PASV qua kênh điều khiển để yêu cầu server sử dụng chế độ thụ động.
2. Server mở một cổng ngẫu nhiên và gửi phản hồi 227 với thông tin cổng này cho client qua kênh điều khiển.
3. Client gửi lệnh lấy dữ liệu (RETR hoặc STOR) với tên tệp tin muốn truyền qua kênh điều khiển để yêu cầu server bắt đầu truyền tải.
4. Client mở kết nối từ cổng ngẫu nhiên của nó đến cổng của server để thiết lập kênh dữ liệu.
5. Server và client bắt đầu truyền tải tệp tin qua kênh dữ liệu.
6. Sau khi truyền xong, đóng kết nối kênh dữ liệu và gửi phản hồi 226 qua kênh điều khiển để xác nhận hoàn thành quá trình truyền tải.

### Quy trình thiết lập kênh dữ liệu chủ động
1. Client cung cấp một cổng chưa dùng và lắng nghe trên cổng đó.
2. Client dùng lệnh FTP PORT để báo cho server là nó đang lắng nghe trên cổng nào.
3. Server dùng cổng 20 để khởi tạo một kết nối về client.
4. Server sẽ gửi và nhận dữ liệu qua kết nối này cho đến khi hoàn thành hoặc bị ngắt.

**->** Thiết lập kiểu chủ động đơn giản và dễ hiểu hơn, tuy nhiên có thể bị chặn bởi tường lửa hoặc NAT ở phía client.
