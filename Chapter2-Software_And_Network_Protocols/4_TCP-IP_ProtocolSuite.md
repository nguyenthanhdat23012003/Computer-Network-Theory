# Bộ giao thức TCP/IP

Trên thiết bị đầu cuối có đồng thời nhiều giao thức cùng hoạt động: các giao thức gắn với phần mềm ứng dụng, những giao thức cung cấp dịch vụ truyền thông end-to-end và host-to-host, ngoài ra còn có các giao thức gắn với phần cứng. 

Các giao thức này không hoạt động độc lập mà có sự quan hệ với nhau, tương tự như cách gọi function, method trong ngôn ngữ lập trình (giao thức ứng dụng gọi tới giao thức end-to-end, giao thức end-to-end gọi đến giao thức host-to-host).

Một nhóm các giao thức trên thiết bị đầu cuối có quan hệ với nhau như vậy tạo thành một **bộ giao thức**, hiện nay thì bộ giao thức TCP/IP là bộ giao thức phổ biến nhất.

## Các tầng trong bộ giao thức TCP/IP

Bộ giao thức TCP/IP chia giao thức vào các nhóm, mỗi nhóm được gọi là **một tầng**, có tổng 4 tầng:

1. **Tầng ứng dụng (Application Layer)**: Chứa các giao thức mà thực thi của nó được tích hợp trong các phần mềm. Các giao thức tầng ứng dụng phổ biến gồm:
   - **HTTP**: Sử dụng bởi trình duyệt và web server.
   - **SMTP, POP3, IMAP**: Sử dụng bởi chương trình email client và server.
   - **FTP**: Sử dụng bởi FTP client và server (ví dụ FileZilla).

2. **Tầng giao vận (Transport Layer)**: Chứa các giao thức cung cấp dịch vụ truyền thông end-to-end, chủ yếu bao gồm:
   - **Giao thức TCP (Transmission Control Protocol)**: Cung cấp dịch vụ truyền thông tin cậy hướng liên kết.
   - **UDP (User Datagram Protocol)**: Cung cấp dịch vụ truyền thông không tin cậy phi liên kết tốc độ cao.

3. **Tầng liên mạng (Internet Layer)**: Chứa các giao thức cung cấp dịch vụ truyền thông host-to-host:
   - **Giao thức IP**.
   - **Giao thức IPv6**.

4. **Tầng liên kết (Link Layer)**: Chứa các giao thức giúp kết nối thiết bị đầu cuối với mạng cục bộ:
   - **Giao thức ARP (Address Resolution Protocol)**: Giao thức phân giải địa chỉ dùng để xác định địa chỉ vật lý MAC gắn với địa chỉ IP của thiết bị.
   - **Giao thức RARP (Reverse ARP)**: Dùng để xác định địa chỉ vật lý MAC gắn với địa chỉ logic của thiết bị.
   - **Giao thức NDP (Neighbor Discovery Protocol)**: Phiên bản ARP cho IPv6.
   - **Giao thức DHCP (Dynamic Host Configuration Protocol)** và **DHCPv6**: Tự động gán thông số cấu hình cho thiết bị.

Mặc dù có rất nhiều giao thức nhưng thực tế bộ giao thức TCP/IP yêu cầu phải thực thi các giao thức sau:
- **Internet Protocol (IP)**.
- **Address Resolution Protocol (ARP)**.
- **Internet Control Message Protocol (ICMP)**.
- **Transmission Control Protocol (TCP)**.
- **User Datagram Protocol (UDP)**.
- **Internet Group Management Protocol (IGMP)**.

Ngoài ra, giao thức IPv6 yêu cầu thêm **NDP**, **ICMPv6**, và **MLD**. Hầu hết các giao thức ở tầng giao vận và tầng mạng, các giao thức tầng ứng dụng không bắt buộc bởi chúng đi kèm với ứng dụng.

## Cách thức hoạt động của giao thức

Các ứng dụng có các giao thức khác nhau, và các giao thức này luôn đi kèm và được tích hợp thành một module của chương trình. Ví dụ, **HTTP** luôn đi kèm với hệ thống phần mềm web.

Trên hệ điều hành, các giao thức của tầng giao vận và tầng liên mạng được cung cấp ở dạng các chương trình con của hệ thống. Các chương trình ứng dụng có thể khai thác các dịch vụ truyền thông do các giao thức này cung cấp thông qua **socket API**, nghĩa là thông qua socket API để gọi tới các chương trình TCP, UDP hoặc IP để yêu cầu gửi data đi.

Tất cả các giao thức ở tầng giao vận và tầng liên mạng đều làm việc với dữ liệu ở dạng **chuỗi byte**. Nhiệm vụ chuyển dữ liệu thành chuỗi byte và ngược lại là nhiệm vụ của chương trình ứng dụng. Các giao thức của hai tầng này sẽ tự động tạo ra chuỗi byte của riêng mình từ dữ liệu mà ứng dụng gửi bằng cách bổ sung thêm header và gắn vào trước payload (payload là dữ liệu ứng dụng gửi đi). Kết quả sinh ra một chuỗi byte lớn được gọi là **một đơn vị dữ liệu của giao thức**. Đơn vị của TCP là **segment**, của UDP được gọi là **datagram**, của IP được gọi là **packet**.

Các giao thức tầng liên kết có thể hoạt động cả ở trên phần cứng, điều mà các giao thức ở ba tầng còn lại không làm được. 

## Vai trò của Port

Trên mỗi thiết bị đầu cuối, có rất nhiều tiến trình đồng thời khai thác các dịch vụ truyền thông do các giao thức TCP và UDP cung cấp. Do đó, khi dữ liệu đến đích thì cần một cơ chế để phân biệt dữ liệu dành cho tiến trình nào.

Để TCP hoặc UDP xác định được tiến trình nào đang khai thác dịch vụ của mình, thì mỗi tiến trình được đánh một **số cổng (port)** gọi là port. Port có giá trị từ 0 -> 2^16-1, các tiến trình có thể chọn ngẫu nhiên bất kỳ giá trị port nào, miễn là port đó free (chưa có tiến trình nào chọn). Hệ điều hành cũng có thể chọn ngẫu nhiên số port để gắn cho tiến trình.

Các tiến trình tham gia vào quá trình truyền thông phải thỏa thuận với nhau về giá trị port. Các giá trị port nguồn và port đích đều phải được gửi đi kèm theo gói tin TCP/UDP để các máy có thể xác định được cần chuyển gói tin đến cho tiến trình nào.

### Một số điểm đáng chú ý về port:

- Là một điểm kết nối logic trong mạng máy tính, nơi mà dữ liệu được gửi và nhận thông qua các giao thức mạng. Mỗi port được xác định bằng một số nguyên từ 0 -> 65535.
- Vai trò của port là phân biệt các dịch vụ và quản lý kết nối.

### Các loại Port:

1. **Well-known Ports (Cổng nổi tiếng)**: Có giá trị từ 0-1023, được dành riêng cho các dịch vụ hệ thống và giao thức chuẩn.
2. **Registered Ports (Cổng đăng ký)**: Có giá trị từ 1024-49151, được đăng ký cho các ứng dụng cụ thể của các tổ chức và nhà phát triển.
3. **Dynamic/Private Ports (Cổng động/riêng tư)**: Có giá trị từ 49152-65535, được gán động cho các ứng dụng cần thiết, thường là các kết nối tạm thời.

### Cách hoạt động của port:

Khi một thiết bị muốn giao tiếp với một dịch vụ cụ thể trên mạng thì nó sẽ gửi dữ liệu đến một địa chỉ IP và một port cụ thể. Khi đó, trên nơi nhận được request sẽ lắng nghe và tiếp nhận các request trên port này.
