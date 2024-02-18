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
