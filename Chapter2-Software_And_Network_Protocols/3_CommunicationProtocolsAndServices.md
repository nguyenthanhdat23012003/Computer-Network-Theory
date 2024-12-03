**[Vietnamese Below]**

# Protocols and Communication Services

Applications operate on end devices. End devices can be seen as the **environment** for applications to function. Applications use the **communication services** of the operating system on end devices to exchange information between components.

Communication services are tied to protocols. Communication protocols are implemented as software, which applications can invoke in the same way they call system functions.

## Two Types of Communication Services

1. **End-to-End Communication**: Refers to applications exchanging data with each other.
2. **Host-to-Host Communication**: Refers to end devices exchanging data with each other.

End-to-end communication services must rely on host-to-host communication services. In other words, host-to-host communication services are the foundation for end-to-end communication services.

**Example**: Sending a letter to an apartment in a large building involves two services: the postal service ensures the letter reaches the building (host-to-host), while the building's internal mail system distributes the letter to the specific apartment (end-to-end).

To perform host-to-host communication, both end devices and routers must share a common protocol. This protocol is implemented as system software on end devices and as part of the specialized operating system software running on routers.

## Types of Communication

- **Reliable Communication** and **Unreliable Communication**:
  - **Reliable Communication** ensures that data is transmitted completely and in the correct order.
  - **Unreliable Communication** does not guarantee such reliability, but it offers faster transmission speeds.

- **Connection-Oriented Communication** and **Connectionless Communication**:
  - **Connection-Oriented Communication** requires the two parties to establish a connection before transmitting data.
  - **Connectionless Communication** does not require a prior connection setup.

<div style="border-top: 2px solid white; margin: 20px 0;"></div>

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
