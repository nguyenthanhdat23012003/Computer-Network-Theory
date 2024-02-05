# Giao thức và dịch vụ truyền thông

Ứng dụng hoạt động trên các thiết bị đầu cuối. Các thiết bị đầu cuối có thể được xem là **môi trường** cho các ứng dụng hoạt động. Các ứng dụng sử dụng **dịch vụ truyền thông** của hệ điều hành trên thiết bị đầu cuối để truyền thông tin giữa các thành phần.

Các dịch vụ truyền thông gắn với các giao thức. Các giao thức truyền thông được thực thi ở dạng phần mềm, mà ứng dụng có thể gọi đến như kiểu gọi một hàm của hệ thống.

## Hai loại dịch vụ truyền thông

1. **Truyền thông end-to-end**: Là việc các ứng dụng truyền dữ liệu cho nhau.
2. **Truyền thông host-to-host**: Là việc các thiết bị đầu cuối truyền dữ liệu cho nhau.

Dịch vụ truyền thông end-to-end phải sử dụng tới dịch vụ truyền host-to-host. Nói cách khác, dịch vụ truyền host-to-host là nền tảng hoạt động cho dịch vụ truyền end-to-end. 

**Ví dụ**: Khi gửi thư đến một căn hộ trong một tòa chung cư lớn, dịch vụ bưu chính chỉ chịu trách nhiệm đưa thư đến tòa chung cư (host-to-host); bản thân chung cư sẽ có dịch vụ phân phối thư đến từng căn hộ (end-to-end).

Để thực hiện nhiệm vụ truyền host-to-host, trên cả thiết bị đầu cuối và router cần phải cài chung một giao thức. Giao thức này được thực thi dưới dạng phần mềm hệ thống trên thiết bị đầu cuối và là một phần mềm chạy hệ điều hành chuyên dụng của router.

## Các loại truyền thông

- **Truyền thông không tin cậy** và **truyền thông tin cậy**: 
  - **Truyền thông tin cậy** là dịch vụ truyền thông trong đó giao thức đảm bảo rằng dữ liệu được truyền đi đầy đủ và đúng thứ tự.
  - **Truyền thông không tin cậy** thì không đảm bảo được như vậy, tuy nhiên tốc độ truyền của truyền thông không tin cậy sẽ cao hơn.

- **Truyền thông hướng liên kết** và **truyền thông phi liên kết**: 
  - **Truyền thông hướng liên kết** là hai bên thiết lập liên kết trước khi truyền tải dữ liệu.
  - **Truyền thông phi liên kết** thì không cần thiết lập liên kết.
