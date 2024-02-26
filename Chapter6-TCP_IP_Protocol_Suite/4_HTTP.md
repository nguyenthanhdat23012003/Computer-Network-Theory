# Self-contribute cho phần HTTP

## HTTP là stateless, nhưng không sessionless:

- HTTP được coi là **stateless** vì mỗi yêu cầu HTTP từ phía client (người dùng trình duyệt) đến server (máy chủ) được xem như độc lập với nhau. Điều này có nghĩa là mỗi yêu cầu HTTP không giữ lại thông tin trạng thái (state) từ yêu cầu trước đó. Server chỉ xử lý yêu cầu hiện tại mà không có thông tin về các yêu cầu trước đó từ cùng một client.
- Mặc dù HTTP là stateless, nhưng các ứng dụng web thường cần lưu trữ và quản lý thông tin phiên làm việc (**session**) của người dùng. Phiên làm việc là một cơ chế cho phép lưu trữ trạng thái của một người dùng trong một khoảng thời gian nhất định khi họ tương tác với ứng dụng web. Thông tin trong phiên thường bao gồm các biến như thông tin đăng nhập, giỏ hàng, các tùy chọn ngôn ngữ, ...
- Cơ chế session thường được triển khai bằng cách sử dụng các cơ chế lưu trữ như **cookies** hoặc **URL rewriting**. Mỗi khi người dùng truy cập vào ứng dụng web, một ID phiên làm việc (session ID) sẽ được gán cho người dùng, và thông tin liên quan đến phiên làm việc này sẽ được lưu trữ (thường là trên server) và duy trì qua các yêu cầu HTTP.

## Giao thức HTTPS

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

## Giao thức SSL

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













