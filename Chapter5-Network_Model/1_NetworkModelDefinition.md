# Khái niệm mô hình mạng

Mô hình mạng mô tả kiến trúc, thành phần và thiết kế được sử dụng để thiết lập giao tiếp giữa hệ thống nguồn và hệ thống đích. Mô hình mạng còn được gọi với các tên khác như ngăn xếp giao thức, bộ giao thức, ngăn xếp mạng.

Có hai mô hình mạng được sử dụng phổ biến nhất là mô hình kết nối các hệ thống mở (mô hình OSI - Open System Interconnection) và mô hình TCP/IP.

Tất cả các mô hình mạng đều được xây dựng theo kiến trúc phân tầng. Theo kiến trúc này, mỗi mô hình mạng bao gồm nhiều layer xếp chồng lên nhau, trong đó:
- Số lượng, vai trò và chức năng của mỗi tầng được định nghĩa từ trước trong một mô hình mạng.
- Số tầng, tên các tầng và chức năng của chúng cũng không giống nhau.

Mỗi tầng chứa các thực thể, có thể là phần mềm hoặc phần cứng, có nhiệm vụ xác định riêng biệt trong hệ thống mạng. Mỗi thực thể cung cấp dịch vụ cho thực thể tầng liền trên và khai thác dịch vụ của thực thể tầng liền dưới.

Các thực thể ở cùng tầng có những điểm chung về dịch vụ mà nó cung cấp, mặc dù chúng có thể thực hiện theo những cách khác nhau. Thực thể ở mỗi tầng giống như một phần mềm; phần mềm tầng trên gọi phần mềm tầng liền dưới thông qua API được định nghĩa sẵn.

## Tương tác trong kiến trúc phân tầng

Các chương trình giao thức ở các tầng hoạt động giống như các hàm gọi lẫn nhau. Các hàm ở cấp độ cao hơn gọi các hàm ở cấp thấp hơn để làm nhiệm vụ cụ thể; chỉ các hàm ở các cấp liền kề nhau mới được gọi cho nhau.

Các hàm không gọi trực tiếp, mà gọi qua interface (là một đơn vị chương trình đặc biệt chỉ chứa phần mô tả, bao gồm dữ liệu đầu vào và đầu ra, mà không chứa phần thực thi).

Các thông tin về SDU, PCI và PDU đã nói trong phần trước đó.
