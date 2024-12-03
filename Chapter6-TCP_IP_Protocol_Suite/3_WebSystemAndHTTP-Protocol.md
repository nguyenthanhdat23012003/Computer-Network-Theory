**[Vietnamese Below]**

# Web Systems and HTTP Protocol

## Common Characteristics of Application Layer Protocols:

- Application layer protocols are diverse and tied to the applications using them. These protocols are typically not general-purpose but serve specific applications, so discussing an application layer protocol usually involves mentioning the software that utilizes it.
- Regarding packet structure, application layer protocols are of two types: text-based protocols and byte-based protocols. Text-based protocols create packets as formatted character strings (e.g., HTTP packets). Byte-based protocols produce packets as byte strings, such as in ICMP.
- Application protocols typically follow one of two communication models: request-response or one-way communication. 
  - **Request-response model**: A half-duplex communication where data can be transmitted bidirectionally but not simultaneously. One side sends a request, and the other processes it and responds.
  - **One-way model**: A simplex communication mode.
- For data control methods:
  - **In-band control**: Control commands are sent with the data, like in HTTP.
  - **Out-of-band control**: Control commands and data are sent through separate communication channels, as in FTP.
- All application protocols use one of the two transport services: TCP or UDP. The choice depends on the application's requirements.



## Web Systems

A web system is a network application consisting of two main components: a **web server** and a **web browser**.

- **Web server**: A computer configured to run web applications and provide resources such as web pages, files, and other online services. Databases store and manage data for web applications, enabling querying and data retrieval services.
- **Web browser**: A software installed on personal computers or mobile devices to access web pages and applications on the Internet. It allows users to view online content, interact with web applications, and use online services.

### Difference Between Web Systems and Web Applications

- **Web system**: A collection of components and services interconnected to serve various purposes and functions. It is larger in scale and more complex in structure.
- **Web application**: A specific software program running on a web browser, performing one or more specific tasks. It is smaller in scale and focused on particular functionalities.

In a web system, the HTTP protocol is used to exchange data between the web server and the web browser.

HTTP operates on a client-server model, where web browsers (clients) send requests to web servers, and servers respond with HTTP responses containing the requested resources.

<p align="center">
  <img src="../image/Chapter6/Client_Server_Architecture.png" alt="Client_Server_Architecture">
</p>



### How HTTP Works

1. **Client Sends an HTTP Request to the Server**: 
   - When a user enters a URL into the browser, the browser creates an HTTP request and sends it to the server using TCP transport services.

2. **Server Receives the HTTP Request**: 
   - Upon receiving the request, the server processes it to retrieve the requested resource.

3. **Server Processes the HTTP Request**:
   - The server verifies the request, authenticates the user (if required), and locates the requested resource.

4. **Server Returns an HTTP Response**:
   - After processing the request, the server sends an HTTP response containing the requested resource, including HTTP headers, status codes, and the content.

5. **Client Receives the HTTP Response**:
   - Once the client receives the response, the browser displays the requested content to the user.



### HTTP Packet Structure

HTTP has two types of packets with distinct structures:
- **HTTP Request Packet**
- **HTTP Response Packet**

Each packet is essentially a formatted text string.

#### HTTP Request Packet

An HTTP request consists of the following parts:
- **Method**: Specifies the action the client wants to perform on the server's resource, e.g., GET (retrieve information), POST (create a resource), PUT (update a resource), DELETE (delete a resource), and more.
- **URL (Uniform Resource Locator)**: Identifies the address of the resource the client wants to access.
- **Headers**: Contain information about the client's request, such as content type, language, authentication details, etc.
- **Body**: Contains specific information the client wants to send to the server, such as form data or uploaded files.

<p align="center">
  <img src="../image/Chapter6/HTTP_Request.png" alt="HTTP_Request">
</p>

#### HTTP Response Packet

An HTTP response consists of the following parts:
- **Status Code**: Indicates the outcome of the client's request, e.g., success (200 OK), not found (404 Not Found), server error (500 Internal Server Error), etc.
- **Headers**: Contain information about the server's response, such as content type, language, authentication details, etc.
- **Body**: Contains specific information the server wants to return to the client, such as HTML content, JSON, XML, etc.

With knowledge of these packet structures and programming with the TCP protocol, one can create a simple web server or a program to send HTTP requests to a web server.



## Data Transmission via HTTP

The HTTP protocol is used to transmit various types of data between the client and server. Common types of data include HTML, CSS, JavaScript, images, JSON, and XML.

### **Transmitting Traditional Web Data (HTML, CSS, JS):**
- A typical web page is created from an HTML file referencing multiple CSS and JS files. Once the HTML is downloaded to the client, the browser uses the references in the HTML to fetch the related files.

### **Transmitting Special Data Types:**
- For **Single Page Applications (SPAs)**, desktop, or mobile applications, HTTP is not used to transmit files directly.
- Instead, HTTP transmits text-based data formats:
  - **JSON**: A data format written in JavaScript object syntax. It is essentially a string generated by the server upon the client's request.
  - **XML**: Another text-based data format embedded in the response body by the server.

These formats are commonly used for data exchange between Web APIs and consuming applications, such as mobile or SPA web applications.

### **Transmitting Binary Data:**
- Binary data includes non-textual data such as images, audio, videos, and software.
- To transmit binary data, it must first be converted to text using a binary encoding algorithm like Base64. This algorithm encodes binary data into a text format, replacing unreadable characters with safe ones.
- After encoding, the binary data is included in the HTTP body and transmitted like any other text data.



## Data Transmission Mechanisms in HTTP

Using TCP transport services, HTTP supports two data transmission mechanisms: **persistent (keep-alive)** and **non-persistent**.

### Non-Persistent HTTP
- Each HTTP request is sent over a new connection between the client and the server, which is terminated after the HTTP response is sent back. 
- This mechanism optimizes network resource usage and minimizes the amount of data transmitted over the network but increases response time due to repeated connection setups.

### Persistent HTTP (Keep-Alive)
- The connection between the client and server is maintained across multiple request-response cycles.
- This reduces connection costs and latency in data transmission between the client and server.

Modern web browsers automatically use keep-alive connections for HTTP requests. However, some older servers and web applications may not support keep-alive or disable it to reduce server load.

- In **non-persistent HTTP**, web applications minimize the number of files by bundling multiple JavaScript/CSS files into one large file.
- In **persistent HTTP**, such bundling is unnecessary due to the reduced overhead from maintaining a single connection.

---

# Hệ thống web và giao thức HTTP 

## Đặc điểm chung của các giao thức tầng ứng dụng: 

- Các giao thức tầng ứng dụng rất đa dạng và luôn đi kèm với ứng dụng sử dụng chúng, các giao thức thường không phải các giao thức chung đa năng phục vụ nhiều loại ứng dụng khác nhau nên khi nói về các giao thức tầng ứng dụng thì phải đi kèm với phần mềm sử dụng nó
- Về cấu trúc gói tin, các giao thức tầng ứng dụng có 2 kiểu: giao thức dựa trên văn bản và giao thức dựa trên chuỗi byte. Giao thức dựa trên văn bản tạo ra gói tin là chuỗi ký tự có định dạng. Ví dụ gói tin HTTP là một chuỗi ký tự lớn. Giao thức dựa trên chuỗi byte tạo ra gói tin là một chuỗi byte, như trong giao thức ICMP
- Các giao thức ứng dụng thường sử dụng một trong hai mô hình truyền thông tin: mô hình truy vấn phản hồi, hoặc mô hình một chiều. Mô hình truy vấn phản hồi chính là chế độ truyền thông bán song công, với dữ liệu có thể truyền 2 chiều nhưng không đồng thời, có một bên chủ động gửi truy vấn và một bên xử lý truy vấn rồi trả lời. Mô hình một chiều chính là chế độ truyền đơn công
- Về phương thức kiểm soát dữ liệu, các giao thức ứng dụng có thể là In-band, tức là lệnh điều khiển gửi kèm với dữ liệu, như trong giao thức HTTP, hoặc là theo kiểu out-of-band, tức là lệnh điều khiển và dữ liệu đi theo những kênh truyền thông riêng, giống như trong giao thức FTP
- Tất cả các giao thức ứng dụng phải sử dụng một trong hai dịch vụ truyền thông của tầng giao vận là TCP hoặc UDP. Tùy vào yêu cầu của ứng dụng mà lựa chọn dịch vụ giao vận phù hợp

## Hệ thống web

Là một loại ứng dụng mạng bao gồm hai thành phần chính là web server và web browser. Trong đó

- Web server là một máy tính được thiết lập để chạy các ứng dụng web và cung cấp các tài nguyên như các trang web, tập tin và các ứng dụng trực tuyến khác. Cơ sở dữ liệu là nơi lưu trữ dữ liệu cho các ứng dụng web và cung cấp các dịch vụ truy vấn và lưu trữ dữ liệu
- Web browser là phần mềm cài đặt trên máy tính cá nhân hoặc các thiết bị di động để truy cập các trang web và ứng dụng trên Internet. Nó giúp người dùng truy cập các nội dung trực tuyến, tương tác với các ứng dụng web và sử dụng các dịch vụ trực tuyến khác

### Phân biệt hệ thống web và ứng dụng web

- Hệ thống web là một tập hợp các thành phần và dịch vụ liên kết với nhau, phục vụ nhiều mục đích và chức năng khác nhau. Nó có quy mô lớn và cấu trúc phức tạp.
- Ứng dụng web là một chương trình phần mềm cụ thể chạy trên web browser, thực hiện một hoặc nhiều chức năng cụ thể. Nó có quy mô nhỏ hơn và tập trung vào một số tác vụ nhất định.

Trong một hệ thống web, giao thức HTTP được sử dụng để trao đổi dữ liệu giữa web server và web browser

HTTP hoạt động dựa trên mô hình client-server, trong đó các web browser (client) gửi các yêu cầu đến web server (server), và server trả về các phản hồi HTTP chứa các tài liệu được yêu cầu

<p align="center">
  <img src="../image/Chapter6/Client_Server_Architecture.png" alt="Client_Server_Architecture">
</p>

### Quá trình hoạt động của HTTP

- **Client gửi yêu cầu HTTP đến server**: Khi người dùng nhập địa chỉ URL vào trình duyệt, trình duyệt sẽ tạo yêu cầu HTTP và gửi nó đến server sử dụng các dịch vụ truyền thông của TCP
- **Server nhận yêu cầu HTTP**: Khi server nhận yêu cầu HTTP từ client, nó sẽ xử lý yêu cầu này để trả về tài liệu được yêu cầu
- **Server xử lý yêu cầu HTTP**: Server sẽ kiểm tra yêu cầu HTTP để đảm bảo tính hợp lệ của yêu cầu, xác thực người dùng (nếu cần thiết) và tìm kiếm tài liệu được yêu cầu
- **Server trả về phản hồi HTTP**: Sau khi server xử lý yêu cầu, nó sẽ trả về phản hồi HTTP chứa tài liệu yêu cầu. Phản hồi này bao gồm các tiêu đề HTTP, mã trạng thái và nội dung tài liệu
- **Client nhận phản hồi HTTP**: Sau khi client nhận được phản hồi HTTP, trình duyệt sẽ hiển thị tài liệu được yêu cầu cho người dùng

### Cấu trúc gói tin của HTTP

Giao thức HTTP có hai loại gói tin với cấu trúc khác nhau: 
- gói tin truy vấn (HTTP request)
- gói tin phản hồi (HTTP response)
Mỗi loại gói tin thực chất chỉ là các chuỗi văn bản có định dạng xác định.

**Gói tin truy vấn của HTTP** bao gồm các phần sau:
- Method (phương thức): xác định hành động mà client muốn thực hiện trên tài nguyên của server, ví dụ như GET (lấy thông tin), POST (tạo mới tài nguyên), PUT (cập nhập tài nguyên), DELETE (xóa tài nguyên), cùng nhiều phương thức khác
- URL (Uniform Resource Locator): xác định địa chỉ của tài nguyên mà client muốn truy cập trên server
- Headers (tiêu đề): chứa các thông tin về yêu cầu của client, ví dụ như kiểu dữ liệu yêu cầu, ngôn ngữ yêu cầu, thông tin xác thực và các thông tin khác
- Body (nội dung): chứa các thông tin cụ thể  mà client muốn gửi đến server, ví dụ như dữ liệu form, file tải lên, …

<p align="center">
  <img src="../image/Chapter6/HTTP_Request.png" alt="HTTP_Request">
</p>

**Gói tin phản hồi của HTTP** bao gồm các phần sau:
- Status code (mã trạng thái): xác định kết quả yêu cầu của client, ví dụ như thành công (200 OK), tài nguyên không tìm thấy (404 Not Found), lỗi server (500 Internal Server Error), …
- Headers (tiêu đề): chứa các thông tin về phản hồi của server, ví dụ như kiểu dữ liệu trả về, ngôn ngữ phản hồi, thông tin xác thực và các thông tin khác
- Body (nội dung): chứa các thông tin cụ thể mà server muốn trả về cho client, ví dụ như nội dung HTML, JSON, XML, …

Như vậy, nếu biết cấu trúc của gói tin này và lập trình với giao thức TCP thì có thể tự xây dựng một chương trình web server đơn giản, hoặc một chương trình để phát truy vấn HTTP tới web server

## Truyền dữ liệu qua HTTP

Giao thức HTTP sử dụng để truyền tải nhiều loại dữ liệu khác nhau giữa client và server. Các loại dữ liệu thông dụng nhất bao gồm HTML, CSS, Javascript, file ảnh, dữ liệu JSON, dữ liệu XML

**Truyền các loại dữ liệu web truyền thống như HTML, CSS, JS:** 
- Thông thường, một trang web được tạo ra từ một file HTML, file này sẽ tham chiếu đến nhiều file CSS và file JS khác, mỗi khi HTML được tải về client, trình duyệt sẽ căn cứ vào các tham chiếu chứa trong HTML để tải các file có liên quan về.

**Truyền các loại dữ liệu đặc biệt:** 
- Với các ứng dụng đơn trang (SPA), ứng dụng desktop, hoặc ứng dụng mobile, giao thức HTTP không được sử dụng để truyền tải các file. 
- Do HTTP sử dụng văn bản cho cấu trúc gói tin, bất kỳ văn bản nào cũng có thể gửi qua giao thức này. 
- Có hai định dạng văn bản đặc biệt được sử dụng phổ biến:
    - JSON 
    - XML. 

- Chương trình server gửi các chuỗi kí tự JSON hoặc XML trong:
    - JSON là một loại định dạng dữ liệu được viết theo cú pháp tạo object của ngôn ngữ JavaScript. Thực chất JSON cũng chỉ là một chuỗi ký tự được chương trình server sinh ra theo yêu cầu của client
    - XML là một loại ngôn ngữ định dạng dữ liệu khác cũng ở dạng văn bản. Chuỗi XML được chương trình server nhúng và phần body của gói tin response.
    - Hai loại văn bản đặc biệt này được sử dụng để định dạng dữ liệu trao đổi giữa ứng dụng Web API và ứng dụng khai thác nó, như ứng dụng mobile, desktop, ứng dụng web đơn trang (SPA)

**Truyền dữ liệu nhị phân:**
- Dữ liệu nhị phân là những loại dữ liệu khác mà không thể hiện trực tiếp văn bản, thường dùng để lưu trữ các tập tin ảnh, âm thanh, video, phần mềm, …
- Đối với dữ liệu nhị phân, cần phải có cơ chế chuyển đổi nó thành văn bản trước khi có thể nhúng vào body của HTTP, thường sử dụng thuật toán mã hóa nhị phân Base64 (là một thuật toán mã hóa dữ liệu nhị phân thành dạng văn bản, trong quá trình chuyển đổi, các ký tự không hợp lệ hoặc không thể đọc được sẽ được thay thế bằng các ký tự an toàn)
- Để chuyển đổi file nhị phân sang Base64, có thể sử dụng các thư viện mã hóa Base64 có sẵn trong các ngôn ngữ lập trình. sau đó truyền dữ liệu đã được mã hóa qua giao thức HTTP như bình thường

## Cơ chế truyền dữ liệu trong HTTP

- Do sử dụng dịch vụ truyền TCP, giao thức HTTP có hai cơ chế truyền dữ liệu: persistent (keep-alive) và non-persistent

- Trong cơ chế non-persistent, mỗi yêu cầu HTTP được gửi qua một  kết nối mới giữa máy khách và máy chủ, kết nối sẽ bị ngắt sau khi phản hồi HTTP được trả về cho máy khách. Cơ chế này giúp tối ưu hóa sử dụng tài nguyên mạng và giảm thiểu khối lượng thông tin được gửi qua mạng. Tuy nhiên, nó cũng tăng thời gian phản hồi do mỗi yêu cầu phải thiết lập một kết nối mới

- Trong cơ chế persistent (còn gọi là keep-alive), kết nối giữa client và server được duy trì cho nhiều vòng phát truy vấn và nhận phản hồi. Cơ chế này giảm thiểu chi phí kết nối và giảm độ trễ (latency) trong việc truyền tải dữ liệu giữa client và server

- Các trình duyệt web hiện đại thường tự động sử dụng kết nối keep-alive khi gửi yêu cầu HTTP đến máy chủ. Tuy nhiên, một số máy chủ và ứng dụng web cũ hơn có thể không hỗ trợ kết nối keep-alive hoặc tắt đi để giảm tải cho máy chủ

- Nếu sử dụng cơ chế non-persistent, ứng dụng web sẽ cố gắng tạo ít file nhất có thể, bằng cách gộp nhiều file js/css thành một file lớn để gửi đi trong một response, còn sử dụng cơ chế keep-alive thì không cần gộp file




