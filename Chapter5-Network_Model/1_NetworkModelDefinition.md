**[Vietnamese Below]**

# Concept of Network Models

A network model describes the architecture, components, and design used to establish communication between a source system and a destination system. Network models are also known as protocol stacks, protocol suites, or network stacks.

The two most widely used network models are the Open System Interconnection model (**OSI model**) and the **TCP/IP model**.

All network models are built on a layered architecture. In this architecture:
- The number, roles, and functions of each layer are predefined within a specific network model.
- The number of layers, their names, and their functions vary between models.

Each layer contains entities, which can be either software or hardware, that perform distinct tasks within the network system. Each entity provides services to the layer immediately above it and uses the services of the layer immediately below.

Entities at the same layer share common features regarding the services they provide, though they may implement these services in different ways. An entity at one layer functions like software; the software of a higher layer calls the software of the layer immediately below through predefined APIs.



## Interaction in Layered Architecture

Protocol programs at various layers interact like functions calling one another. Higher-level functions call lower-level functions to perform specific tasks; only functions in adjacent layers can directly call each other.

These functions do not call directly but interact via **interfaces** (special program units that only contain descriptions, including input and output data, without any implementation details).

The concepts of **SDU (Service Data Unit)**, **PCI (Protocol Control Information)**, and **PDU (Protocol Data Unit)** mentioned earlier apply here.

---

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

Các hàm không gọi trực tiếp, mà gọi qua **interface** (là một đơn vị chương trình đặc biệt chỉ chứa phần mô tả, bao gồm dữ liệu đầu vào và đầu ra, mà không chứa phần thực thi).

Các thông tin về **SDU**, **PCI**, và **PDU** đã nói trong phần trước đó.
