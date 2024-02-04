# Khái niệm giao thức mạng

**Giao thức mạng** là tập hợp các quy tắc điều khiển quá trình truyền thông mà các thành phần của hệ thống mạng phải tuân theo khi tham gia vào quá trình truyền thông.

Mỗi giao thức là một bộ quy tắc quy định ba yếu tố chính:
1. **Cấu trúc của thông tin**: Xác định cách thức thông tin được tổ chức và định dạng.
2. **Trình tự trao đổi thông tin**: Quy định thứ tự các thông điệp được gửi và nhận.
3. **Các hành động cần thực hiện khi gửi/nhận thông tin**: Các quy tắc xác định thời điểm và cách thức một thành phần gửi thông điệp và phản hồi thông điệp.

### Các yếu tố của giao thức mạng
- **Các loại thông điệp cần trao đổi**: Xác định các thông điệp khác nhau mà các thành phần trong hệ thống cần sử dụng.
- **Cú pháp của thông điệp**: Định nghĩa cách thức thông điệp được xây dựng.
- **Ý nghĩa của các trường**: Chỉ định ý nghĩa và vai trò của từng trường trong thông điệp.

### Vai trò của giao thức mạng
Giao thức mạng đóng vai trò như một **ngôn ngữ chung** gắn kết và phối hợp hoạt động của các thiết bị.

### Đặc tả giao thức
**Đặc tả giao thức** là một bản thiết kế của giao thức được viết thành văn bản. Khi phát triển ứng dụng theo đặc tả và cài đặt lên các thiết bị thành một chương trình gọi là **thực thi giao thức**.

### Giao thức mở và giao thức độc quyền
- **Giao thức mở**: Là giao thức mà ai cũng có thể truy cập và sử dụng. Các giao thức mở được mô tả tại [RFC Editor](https://www.rfc-editor.org/).
- **Giao thức độc quyền**: Là giao thức kín chỉ nhà phát triển mới biết. Ví dụ: Skype sử dụng giao thức độc quyền riêng, có thể do mô hình P2P mà Skype sử dụng nên phải sử dụng giao thức độc quyền để tăng tính bảo mật.
