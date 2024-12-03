**[Vietnamese Below]**

## Self-Contribution on HTTP

### HTTP is Stateless, but not Sessionless:

- HTTP is considered **stateless** because each HTTP request from the client (browser user) to the server (host) is treated as independent. This means each HTTP request does not retain state information from the previous one. The server processes the current request without knowing about earlier requests from the same client.
- Although HTTP is stateless, web applications often need to store and manage user **session** information. A session is a mechanism that allows retaining a user's state during a specific time period while they interact with the web application. Session information usually includes variables like login information, shopping cart contents, language preferences, etc.
- The session mechanism is often implemented using storage methods such as **cookies** or **URL rewriting**. Whenever a user accesses the web application, a session ID is assigned to the user, and information related to this session is stored (usually server-side) and maintained across HTTP requests.

### HTTPS Protocol

- HTTP operates on a Client–Server model. Website access is carried out through communication between these two entities. When you visit a website via HTTP, the browser establishes a connection to the website’s server using the IP address provided by the DNS system. After receiving the request, the server sends back the corresponding commands to render the website, including content such as text, images, videos, audio, etc.
- During the connection and data exchange process, your browser inherently trusts the IP address as being from the website’s server you intended to access **without any authentication measures**. The information transmitted via HTTP (including IP address, data entered into the website, etc.) is also **not encrypted or secured**. This vulnerability is exploited by hackers to steal user information, commonly referred to as **sniffing attacks**.
- **The HTTPS Protocol** (Hypertext Transfer Protocol Secure) is the secure version of HTTP, used to protect the transmission of information over the Internet. It is an important method to ensure data security and integrity between the client (user) and server.
  In essence, this is the HTTP protocol with the integration of **SSL certificates** to encrypt communication messages for increased security. HTTPS can be understood as a safer and more secure version of HTTP.
- Both **SSL and TLS** use the **PKI** (Public Key Infrastructure) asymmetric system. This system employs two “keys” to encrypt communication: a “public key” and a “private key.” Anything encrypted by the public key can only be decrypted by the private key, and vice versa. These standards ensure content is encrypted before transmission and decrypted upon receipt. This makes it impossible for hackers to “understand” the intercepted information.
- The data transmission of HTTPS is similar to HTTP; however, when the browser uses the TCP protocol to package an HTTPS request into packets, these packets must pass through the TSL or SSL security layer.
- When investigating the data flow of an HTTPS request, the steps and network layers involved differ somewhat from HTTP because HTTPS uses encryption to protect data during transmission. Below are the specific steps for an HTTPS request:
  - **TLS Handshake**:
    - **Application Layer**: The user wants to access a secure website, using a URL starting with "https://example.com." The browser generates an HTTPS request.
    - **Transport Layer**: The browser uses the TCP protocol like HTTP to package the HTTPS request into packets. However, unlike HTTP, this packet passes through the Transport Layer Security (TLS) or Secure Sockets Layer (SSL) before being sent to TCP for transmission.
    - **TLS Handshake**: Before transmitting actual data, the client and server must establish a secure connection through a process called "TLS handshake":
      - **Client Hello**: The client sends a "Client Hello" message to the server, proposing supported TLS versions and other details such as encryption algorithms.
      - **Server Hello**: The server responds with a "Server Hello" message, agreeing on the TLS version and selecting security parameters such as SSL/TLS certificates, encryption algorithms, and more.
      - **Authentication and Pre-master Secret**: The server authenticates itself, and both the client and server agree on a "pre-master secret" for encryption.
      - **Session Keys**: Based on the pre-master secret and selected information, the client and server generate session keys for encrypting and decrypting data.
    - **Data Encryption and Transmission**: After successfully establishing the TLS secure connection, data from the HTTP request is encrypted with session keys, then packaged into TCP packets as usual.
    - **Network Layer**: The encrypted and secured TCP packets pass through the network, just like HTTP. The network layer still uses the IP protocol to route packets to the destination server.
    - **Data Link Layer and Physical Layer**: At routing points, the encrypted TCP packets from the HTTPS request are converted into data frames compatible with the network’s data link and physical layers.
    - **Server Side**: When the encrypted TCP packets reach the web server, they are decrypted using session keys established during the TLS handshake. The web server then processes the HTTPS request as a standard HTTP request.
    - **HTTPS Response**: The above process is repeated for the HTTPS response, with data from the web server encrypted by TLS and sent back to the client.
- Through the TLS handshake process and encryption throughout the data transmission process, HTTPS ensures user data is safely protected during network transmission, preventing attacks such as eavesdropping and data tampering.

### SSL Protocol

- SSL is a security protocol providing privacy, authentication, and integrity on the Internet.
- SSL uses data encryption to ensure sensitive information is not exposed while transmitted over the network.
- SSL uses data encryption to protect information. It can be likened to sending a letter to your parents but not wanting anyone else to read it except your parents. You and your parents agree on a common encryption rule before sending the letter. Before sending the letter, you encrypt it according to the agreed rule, and when it reaches your parents, they decrypt it. Even if the letter is intercepted or read by someone along the way, they cannot understand its contents because it’s encrypted, and they don’t have the key to decrypt it.
- An SSL certificate acts like an ID badge or identification proving someone’s identity (similar to a personal ID card). An SSL certificate contains the following information:
  - **Website Address Information**: The SSL certificate lists the domains it applies to.
  - **Public Key**: Part of the certificate used to encrypt data before it’s sent to the server. This public key is publicly accessible.
  - **Private Key**: Secretly stored on the web server, the private key must decrypt data encrypted by the public key.
- Types of SSL Certificates:
  - **Single Domain**: Applies to a single domain.
  - **Wildcard Domain**: Applies to a domain and its subdomains.
  - **Multi-Domain**: Applies to multiple domains.
- SSL certificates also have different levels of validation:
  - **Domain Validation**: The most common, least stringent, and cheapest level of validation. All the business needs to do is prove they control the domain, primarily through DNS record validation or HTTP validation.
  - **Organization Validation**: This involves more thorough and manual validation: The CA contacts the individual or business requesting the certificate to validate the certificate for the correct entity. These certificates are more trusted by users.
  - **Extended Validation**: Requires a full background check of the organization before an SSL certificate can be issued.
- TLS (Transport Layer Security) is a network security protocol and the evolution of SSL.
- The entire TLS connection process involves complex steps and algorithms but can be summarized in the following basic steps:
  - **Handshake**: The initial step in establishing a secure connection. The browser or application sends a connection request to the server, and the server responds with its SSL/TLS certificate information and a public key.
    - **Client Hello**: The client sends a "Client Hello" message to the server. This message includes:
      - The TLS version the client supports.
      - A list of encryption suites supported by the client.
      - A random string generated by the client.
      - Other necessary parameters.
    - **Server Hello**: The server responds with a "Server Hello" message to the client. This message includes:
      - The TLS version chosen by the server.
      - The encryption suite chosen by the server from the client’s list.
      - A random string generated by the server.
      - The server’s SSL/TLS certificate.
      - Other necessary parameters.
  - Certificate Verification:
    - Server Certificate:
      - The browser checks the server’s SSL/TLS certificate.
      - The certificate is issued and signed by a trusted Certificate Authority (CA).
      - The browser verifies that the certificate was signed by a trusted CA, has not expired, and the domain in the certificate matches the server’s domain.
  - Session Key Creation:
    - Session Key:
      - After successfully verifying the certificate, the browser creates a new session key, which is a secret key.
      - The browser encrypts this session key using the server’s public key and sends it to the server. This step creates the "Premaster Secret."
  - Encrypting and Transmitting Data:
    - Building the Session Key:
      - Both the browser and the server use the "Premaster Secret," along with the "client random" and "server random," to create a session key using a session key generation algorithm.
      - This session key is used to encrypt and decrypt transmitted data throughout the connection session to ensure performance.
    - Sending Finished Messages:
      - The browser sends a "Finished" message encrypted with the session key, confirming the handshake is complete.
      - The server sends back a "Finished" message encrypted with the session key, confirming the handshake is complete.
    - Encrypting and Transmitting Data:
      - After a successful handshake, all data transmitted between the browser and server is encrypted using the session key.
      - This ensures that no information can be read as it travels across the network.
    - Ending the Session:
      - When the connection session ends, both the browser and the server discard the session key.
      - All information about the session is deleted to ensure security and prevent session key reuse.


---

## Self-contribute cho phần HTTP

### HTTP là stateless, nhưng không sessionless:

- HTTP được coi là **stateless** vì mỗi yêu cầu HTTP từ phía client (người dùng trình duyệt) đến server (máy chủ) được xem như độc lập với nhau. Điều này có nghĩa là mỗi yêu cầu HTTP không giữ lại thông tin trạng thái (state) từ yêu cầu trước đó. Server chỉ xử lý yêu cầu hiện tại mà không có thông tin về các yêu cầu trước đó từ cùng một client.
- Mặc dù HTTP là stateless, nhưng các ứng dụng web thường cần lưu trữ và quản lý thông tin phiên làm việc (**session**) của người dùng. Phiên làm việc là một cơ chế cho phép lưu trữ trạng thái của một người dùng trong một khoảng thời gian nhất định khi họ tương tác với ứng dụng web. Thông tin trong phiên thường bao gồm các biến như thông tin đăng nhập, giỏ hàng, các tùy chọn ngôn ngữ, ...
- Cơ chế session thường được triển khai bằng cách sử dụng các cơ chế lưu trữ như **cookies** hoặc **URL rewriting**. Mỗi khi người dùng truy cập vào ứng dụng web, một ID phiên làm việc (session ID) sẽ được gán cho người dùng, và thông tin liên quan đến phiên làm việc này sẽ được lưu trữ (thường là trên server) và duy trì qua các yêu cầu HTTP.

### Giao thức HTTPS

- HTTP hoạt động theo mô hình Client (máy khách) – Server (máy chủ). Việc truy cập website được tiến hành dựa trên các giao tiếp giữa 2 đối tượng trên. Khi bạn truy cập một trang web qua giao thức HTTP, trình duyệt sẽ thực hiện các phiên kết nối đến server của trang web đó thông qua địa chỉ IP do hệ thống phân giải tên miền DNS cung cấp. Máy chủ sau khi nhận lệnh, sẽ trả về lệnh tương ứng giúp hiển thị website, bao gồm các nội dung như: văn bản, ảnh, video, âm thanh,…
- Trong quá trình kết nối và trao đổi thông tin, trình duyệt của bạn sẽ mặc nhiên thừa nhận địa chỉ IP đó đến từ server của chính website mà bạn muốn truy cập mà **không hề có biện pháp xác thực nào**. Các thông tin được gửi đi qua giao thức HTTP (bao gồm địa chỉ IP, các thông tin mà bạn nhập vào website…) cũng **không hề được mã hóa và bảo mật**. Đây chính là kẽ hở mà nhiều hacker đã lợi dụng để đánh cắp thông tin người dùng, thường được gọi là **tấn công sniffing**.
- **Giao thức HTTPS** (Hypertext Transfer Protocol Secure) là phiên bản an toàn hóa của giao thức HTTP, được sử dụng để bảo vệ việc truyền tải thông tin qua mạng Internet. Đây là một phương pháp quan trọng để đảm bảo tính bảo mật và sự toàn vẹn của dữ liệu giữa máy khách (client) và máy chủ (server).
Thực chất, đây chính là giao thức HTTP nhưng tích hợp thêm **Chứng chỉ bảo mật SSL** nhằm mã hóa các thông điệp giao tiếp để tăng tính bảo mật. Có thể hiểu, HTTPS là phiên bản HTTP an toàn, bảo mật hơn.
- Cả **SSL và TLS** đều sử dụng hệ thống **PKI** (Public Key Infrastructure -hạ tầng khóa công khai) không đối xứng. Hệ thống này sử dụng hai “khóa” để mã hóa thông tin liên lạc, “khóa công khai” (public key) và “khóa riêng” (private key). Bất cứ thứ gì được mã hóa bằng khóa công khai chỉ có thể được giải mã bởi khóa riêng và ngược lại. Các tiêu chuẩn này đảm bảo các nội dung sẽ được mã hóa trước khi truyền đi, và giải mã khi nhận. Điều này khiến hacker dù có chen ngang lấy được thông tin cũng không thể “hiểu” được thông tin đó.
- Cách truyền tải dữ liệu của HTTPS tương tự với HTTP, tuy nhiên khi trình duyệt sử dụng giao thức TCP để đóng gói https request thành các gói tin, gói tin này sẽ phải đi qua tầng bảo mật TSL hoặc SSL
- Khi điều tra luồng dữ liệu của một HTTPS request, các bước và tầng mạng liên quan sẽ có sự khác biệt nhất định so với HTTP vì HTTPS sử dụng mã hóa để bảo vệ dữ liệu khi truyền qua mạng. Dưới đây là mô tả các bước cụ thể cho một HTTPS request:
    - **TLS Handshake (Bắt tay TLS)**:
        - **Application Layer (Tầng ứng dụng)**: Người dùng muốn truy cập một trang web an toàn, sử dụng URL bắt đầu bằng "https://example.com". Trình duyệt web sẽ tạo ra một HTTPS request.
        - **Transport Layer (Tầng giao vận)**: Trình duyệt sẽ sử dụng giao thức TCP như trong HTTP để đóng gói HTTPS request thành các gói tin. Tuy nhiên, khác với HTTP, gói tin này sẽ đi qua tầng bảo mật Transport Layer Security (TLS) hoặc Secure Sockets Layer (SSL) trước khi gửi xuống cho TCP để chuyển đi.
    - **TLS Handshake**: Trước khi gửi dữ liệu thực sự, máy khách và máy chủ phải thiết lập một kết nối bảo mật qua một quá trình gọi là "TLS handshake":
        - **Client Hello**: Máy khách gửi một tin nhắn "Client Hello" đến máy chủ, đề xuất các phiên bản TLS hỗ trợ và các thông tin khác như các thuật toán mã hóa.
        - **Server Hello**: Máy chủ phản hồi bằng một tin nhắn "Server Hello", đồng ý với phiên bản TLS và chọn các tham số bảo mật như chứng chỉ SSL/TLS, thuật toán mã hóa và thông tin khác.
        - **Authentication and Pre-master Secret**: Máy chủ xác minh danh tính (authentication) của mình và sau đó máy khách và máy chủ sẽ thỏa thuận một "pre-master secret" để sử dụng cho việc mã hóa.
        - **Session Keys**: Dựa trên pre-master secret và thông tin đã chọn, máy khách và máy chủ tạo ra các khóa phiên (session keys) để sử dụng trong quá trình mã hóa và giải mã dữ liệu.
    - **Data Encryption and Transmission**: Sau khi thiết lập kết nối bảo mật TLS thành công, các dữ liệu từ HTTP request được mã hóa bằng các session keys và sau đó được đóng gói vào gói tin TCP như bình thường.
    - **Network Layer (Tầng mạng)**: Các gói tin TCP đã mã hóa và bảo mật qua TLS sẽ được chuyển tiếp qua mạng, giống như trong trường hợp của HTTP. Tầng mạng vẫn sử dụng giao thức IP để định tuyến các gói tin đến máy chủ đích.
    - **Data Link Layer và Physical Layer (Tầng liên kết dữ liệu và Tầng vật lý)**: Tại các điểm định tuyến, các gói tin TCP đã được giải mã từ HTTPS request sẽ được chuyển đổi thành khung dữ liệu phù hợp với tầng liên kết dữ liệu và vật lý của mạng.
    - **Server Side (Máy chủ đích)**: Khi gói tin TCP mã hóa đến máy chủ web, nó được giải mã bằng các session keys đã được thiết lập trong TLS handshake. Máy chủ web sau đó xử lý yêu cầu HTTPS như là một HTTP request thông thường.
    - **HTTPS Response**: Quá trình trên được lặp lại cho HTTPS response, với dữ liệu từ máy chủ web được mã hóa bằng TLS và sau đó được gửi trở lại cho máy khách.
- Thông qua quá trình TLS handshake và việc sử dụng mã hóa trong toàn bộ quá trình truyền tải, HTTPS đảm bảo rằng dữ liệu của người dùng được bảo vệ an toàn trên đường truyền mạng, ngăn chặn các cuộc tấn công như nghe trộm và can thiệp dữ liệu.

### Giao thức SSL

- Là một giao thức bảo mật cung cấp sa quyền riêng tư, xác thực và tính toàn vẹn trên Internet
- Sử dụng mã hóa dữ liệu để đảm bảo các thông tin nhạy cảm không bị lộ khi lan truyền qua mạng
- SSL sử dụng mã hoá dữ liệu để bảo vệ thông tin. Có thể coi SSL giống như khi bạn muốn gửi thư cho bố mẹ mình nhưng không muốn ai đọc được nội dung trừ bố mẹ, bạn và bố mẹ cần quy định một quy tắc mã hoá chung của 2 bên, trước khi gửi thư bạn thực hiện mã hoá bức thư theo quy ước, khi thư đã đến tay bố mẹ bạn thì bố mẹ bạn sẽ thực hiện giải mã bức thư đó. Cho dù bức thư đó có bị đánh cắp dọc đường đi, hoặc bị ai đó xem lén thì họ vẫn không thể đọc được nội dung của bức thư đó do thư đã được mã hoá, họ không có chìa khoá để giải bức thư của bạn.

- Chứng chỉ SSL giống như một thẻ ID hoặc một huy hiệu chứng minh ai đó là chính họ (kiểu như căn cước công dân). Một chứng chỉ SSL chứa các thông tin sau đây: 
    - **Thông tin về địa chỉ trang web**: chứng chỉ SSL liệt kê các tên miền mà nó được áp dụng
    - **Khóa công khai (public key)**: Đây là một phần chứng chỉ, và nó được sử dụng để mã hóa dữ liệu trước khi nó gửi đến được máy chủ. Khóa công khai này có thể được truy cập công khai
    - **Khóa riêng tư (private key)**: được giữ bí mật trên máy chủ web, khóa riêng tư phải giải mã được dữ liệu được mã hóa bởi khóa công khai
- Các loại chứng chỉ SSL
    - **Một tên miền duy nhất (Single Domain)**: chỉ áp dụng cho một tên miền
    - **Tên miền con (Wildcard Domain)**: áp dụng cho một tên miền và các tên miền con của tên miền đó
    - **Nhiều tên miền (Multi Domain)**: áp dụng cho nhiều tên miền
- Chứng chỉ SSL cũng có các cấp độ xác thực khác nhau
    - **Xác thực tên miền (Domain validation)**: là cấp độ xác thực phổ biến, ít nghiêm ngặt và rẻ nhất. Tất cả những gì doanh nghiệp phải làm là chứng minh họ kiểm soát tên miền, các xác thực chủ yếu bao gồm xác thực bản ghi DNS hoặc xác thực HTTP
    - **Xác thực tổ chức (Organization Validation)**: xác thực này kiểm tra kỹ lưỡng và thủ công hơn: CA liên hệ trực tiếp với cá nhân hoặc doanh nghiệp yêu cầu chứng chỉ để xác thực chứng chỉ cho đúng đối tượng. Những chứng chỉ này đáng tin cậy hơn đối với người dùng.
    - **Xác thực mở rộng (Extended Validation)**: yêu cầu kiểm tra lý lịch đầy đủ của một tổ chức trước khi chứng chỉ SSL có thể được cấp.
- TLS (Transport Layer Security) là một giao thức bảo mật mạng, là bản tiến hóa của SSL
- Toàn bộ quá trình kết nối TLS bao gồm các bước kết nối và thuật toán phức tạp, tuy nhiên có thể mô tả trong các bước cơ bản sau đây:
    - **Bắt tay (handshake)**: là bước đầu tiên trong việc thiết lập kết nối bảo mật, trình duyệt hoặc ứng dụng gửi yêu cầu kết nối đến máy chủ, máy chủ phản hồi với thông tin về chứng chỉ SSL/TLS của nó và một khóa công khai
        - **Client Hello**: Client gửi một thông điệp “Client Hello" đến server, thông điệp này bao gồm: 
            - Phiên bản TLS mà client hỗ trợ
            - Danh sách các bộ mã hóa mà client hỗ trợ
            - Một chuỗi số ngẫu nhiên được tạo bởi client
            - Các thông số cần thiết khác 
        - **Server Hello**: Server phản hồi với một thông điệp “Server Hello” đến client, thông điệp này bao gồm:
            - Phiên bản TLS mà server chọn sử dụng
            - Bộ mã hóa mà server chọn từ danh sách của client
            - Một chuỗi số ngẫu nhiên được tạo bởi server
            - Chứng chỉ SSL/TLS của server
            - Các thông số cần thiết khác
    - Xác minh chứng chỉ
        - Chứng chỉ Server:
            - Trình duyệt kiểm tra chứng chỉ SSL/TLS của server
            - Chứng chỉ này được phát hành và ký bởi một Cơ quan cấp chứng chỉ đáng tin cậy
            - Trình duyệt xác minh chứng chỉ được lý bởi một CA mà trình duyệt tin tưởng, chưa hết hạn và tên miền trong chứng chỉ khớp với tên miền máy chủ
    - Tạo khóa phiên 
        - Khóa phiên
            - Sau khi xác minh chứng chỉ thành công, trình duyệt tạo một khóa phiên (session key) mới, cũng là khóa bí mật
            - Trình duyệt mã hóa khóa phiên này bằng khóa công khai của máy chủ và gửi nó đến máy chủ. Đây là bước tạo ra “Premaster Secret"
    - Mã hóa và truyền dữ liệu
        - Xây dựng khóa phiên
            - Cả trình duyệt và máy chủ sử dụng “Premaster Secret", cùng với “client random" và “server random" để tạo một khóa phiên (session key) thông qua một thuật toán tạo khóa phiên
            - Khóa phiên này sẽ được sử dụng để mã hóa và giải mã dữ liệu truyền tải trong suốt phiên kết nối để đảm bảo hiệu suất
        - Gửi thông điệp Finished
            - Trình duyệt gửi thông điệp “Finished" được mã hóa bằng mã phiên, xác nhận rằng phần bắt tay đã hoàn tất
            - Máy chủ gửi lại thông điệp “Finished” được mã hóa bằng khóa phiên, xác nhận rằng phần bắt tay đã hoàn tất.
        - Mã hóa và truyền dữ liệu
            - Sau khi bắt tay thành công, tất cả dữ liệu truyền giữa trình duyệt và máy chủ được mã hóa bằng khóa phiên.
            - Điều này đảm bảo rằng bất kỳ thông tin nào cũng không thể đọc được khi nó truyền qua mạng.
        - Kết thúc phiên
            - Khi phiên kết nối kết thúc, cả trình duyệt và máy chủ sẽ hủy bỏ khóa phiên.
            - Mọi thông tin về phiên này sẽ bị xóa để đảm bảo an toàn và không thể tái sử dụng khóa phiên.