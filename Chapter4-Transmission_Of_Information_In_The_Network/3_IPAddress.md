**[Vietnamese Below]**

## Logical Address of Terminal Equipments - IP Address

In a computer network, there are usually multiple terminal equipments operating simultaneously. Each terminal equipment is a node of the network and is referred to as a **host**. To differentiate between devices, each host is assigned a unique address, known as the **IP address**.

### 1. IP Address (IPv4)

An IPv4 address is a 4-byte (32-bit) integer. The value of an IP address ranges from 0 to 2^32 - 1. The IP address is represented as an array of 4 bytes, each called an **octet**, and displayed in decimal form, ranging from 0 to 255. The octets are separated by dots.

#### Example:
- A common address in home LANs: **192.168.1.1**

#### IP Address Division
An IPv4 address is divided into two parts:
- **Network ID** (identifies the network)
- **Host ID** (identifies the host)

To specify how many bits are allocated for the network and how many for the host, a **/x** suffix is added to the IP address. For example, **192.168.1.1/24** means the first 24 bits are for the network, and the remaining 8 bits are for the host.

All IP addresses with the same Network ID are considered **addresses in the same range**. In a LAN, hosts must have IP addresses in the same range to communicate with each other.

#### Rules for Assigning IP Addresses
- The bits in the network portion cannot all be zero. For example: **0.0.0.1/24** is invalid.
- Addresses where the host identifier bits are all zeros or all ones cannot be assigned to hosts; these addresses, while valid, are reserved for specific purposes.

### 2. Subnet Mask

The **subnet mask** is a 32-bit binary number associated with the IP address to identify the bits used for the Network ID, similar to the **/x** notation mentioned above.

- **IP AND Subnet = Network IP**
- **IP OR Subnet = Broadcast IP**

#### Network IP
An IP address where the host identifier bits are all zeros (e.g., **192.168.10.0/24**) represents the entire network.

#### Broadcast IP
A broadcast address is used to send data simultaneously to all hosts within the network.

### 3. Loopback Address

The **127.x.x.x** address is the **loopback** or **localhost** address, used for communication testing without sending data onto the network (e.g., when the client and server are on the same terminal equipment).

### 4. Automatic Private IP Address

IP addresses in the range **169.254.0.0** to **169.254.255.255** are called **Automatic Private IP Addresses**. These addresses are randomly assigned by the operating system when automatic IP assignment (DHCP) fails.

### 5. IP Address Classes

IP address classes distinguish and manage IP address ranges in IPv4 by allocating specific bits for the network and host portions. The main IPv4 address classes are:

#### Class A:
- Used for large networks with many devices.
- IP range: **1.0.0.0** to **127.255.255.255**.
- The first 8 bits are the network portion, and the remaining 24 bits are for hosts.
- Example: **10.0.0.0/8** is a Class A network with subnet mask **255.0.0.0**.

#### Class B:
- Used for medium to large networks.
- IP range: **128.0.0.0** to **191.255.255.255**.
- The first 16 bits are the network portion, and the remaining 16 bits are for hosts.
- Example: **172.16.0.0/12** is a Class B network with subnet mask **255.240.0.0**.

#### Class C:
- Used for small networks.
- IP range: **192.0.0.0** to **223.255.255.255**.
- The first 24 bits are the network portion, and the remaining 8 bits are for hosts.
- Example: **192.168.0.0/16** is a Class C network with subnet mask **255.255.0.0**.

#### Class D:
- Used for **multicast**.
- IP range: **224.0.0.0** to **239.255.255.255**.
- Does not use a subnet mask because Class D addresses are used for multicast transmissions in networks.

#### Class E:
- Reserved for research and experimental purposes.
- IP range: **240.0.0.0** to **255.255.255.255**.
- Does not use a subnet mask.

#### Purpose of IP Address Classes:
- **IP Management and Distribution:** Each class accommodates networks of different sizes, enabling efficient allocation for various network scales.
- **Network Identification:** The IP address can easily indicate the class of the network, helping to apply appropriate network configurations.

### 6. IPv4 Address Types

IPv4 addresses are divided into two types:
- **Private IP:** Used within local area networks (LAN) only. These addresses are not routed on the internet and can be reused in different LANs.
- **Public IP:** Used for packets transmitted over the internet. A public IP address must be unique for each host connected to the internet.

### 7. Default Gateway

The **default gateway** is the IP address of the router connected to the local computer network. It acts as the LAN's exit point, enabling devices in the network to communicate with external networks.


---

## Địa chỉ logic của thiết bị đầu cuối - Địa chỉ IP

Trên một mạng máy tính, thường có nhiều thiết bị đầu cuối hoạt động đồng thời. Mỗi thiết bị đầu cuối là một node của mạng và được gọi là **host**. Để phân biệt giữa các thiết bị, mỗi host đều được gán một địa chỉ duy nhất, được gọi là **địa chỉ IP**.

### 1. Địa chỉ IP (IPv4)

Địa chỉ IP (IPv4) là một số nguyên 4 byte (32 bit). Giá trị của địa chỉ IP nằm trong dải từ 0 đến  2^32 - 1 . Địa chỉ IP được biểu diễn dưới dạng mảng 4 byte, mỗi byte được gọi là **octet** và được biểu diễn bằng giá trị thập phân nằm trong khoảng từ 0 đến 255. Các octet được viết tách nhau bằng dấu chấm.

#### Ví dụ:
- Địa chỉ thường gặp trong mạng LAN gia đình: **192.168.1.1**

#### Phân chia địa chỉ IP
Địa chỉ IPv4 được chia thành 2 phần: 
- **Phần định danh mạng** (Network ID)
- **Phần định danh host** (Host ID)

Để chỉ rõ bao nhiêu bit dành cho phần mạng và bao nhiêu bit dành cho phần host, người ta thường thêm ký hiệu **/x** vào sau địa chỉ IP. Ví dụ, **192.168.1.1/24** nghĩa là 24 bit đầu là định danh mạng, 8 bit sau là định danh host.

Tất cả các địa chỉ IP có chung phần định danh mạng được gọi là **các địa chỉ cùng dải**. Trong một mạng LAN, các host phải có địa chỉ IP cùng dải thì mới có thể truyền dữ liệu cho nhau.

#### Nguyên tắc đặt địa chỉ IP
- Các bit phần mạng không được đồng thời bằng 0. Ví dụ: **0.0.0.1/24** là không hợp lệ.
- Địa chỉ có các bit phần định danh đồng thời bằng 0 hoặc đồng thời bằng 1 không được gán cho host; hai địa chỉ này mặc dù hợp lệ nhưng được sử dụng cho các trường hợp riêng.

### 2. Subnet Mask

**Subnet mask** là một dãy nhị phân 32 bit đi kèm với địa chỉ IP để xác định các bit dùng cho phần Network ID, tương tự như phần **/x** đã nói ở trên. 

- **IP AND Subnet = Network IP**
- **IP OR Subnet = Broadcast IP**

#### Network IP
Địa chỉ IP có các bit thuộc phần định danh host bằng 0 (ví dụ: **192.168.10.0/24**), là địa chỉ đại diện cho toàn bộ mạng.

#### Broadcast IP
Địa chỉ quảng bá, sử dụng để gửi dữ liệu đồng thời tới tất cả các host trong mạng.

### 3. Địa chỉ Loopback

Địa chỉ **127.x.x.x** là địa chỉ **loopback** hoặc **localhost**, sử dụng khi cần khai thác dịch vụ truyền thông nhưng không muốn đưa dữ liệu lên mạng (ví dụ: client và server cùng nằm trên một thiết bị đầu cuối).

### 4. Địa chỉ IP riêng tự động

Các địa chỉ IP trong dải từ **169.254.0.0** đến **169.254.255.255** được gọi là **địa chỉ IP riêng tự động**. Đây là địa chỉ IP được hệ điều hành tự động chọn ngẫu nhiên nếu như cơ chế nhận IP tự động (DHCP) không thành công.

### 5. Phân lớp địa chỉ IP

Phân lớp địa chỉ IP là cách phân biệt và quản lý các dải địa chỉ IP trong mạng IPv4 dựa trên các thông số bit mạng và bit host được phân bố theo từng lớp (Class). Các lớp địa chỉ IP chính trong IPv4:

#### Lớp A:
- Sử dụng cho các mạng lớn có nhiều thiết bị.
- Địa chỉ IP bắt đầu từ **1.0.0.0** đến **127.255.255.255**.
- Phần đầu (8 bit đầu tiên) là bit mạng, phần còn lại (24 bit sau) là bit host.
- Ví dụ: **10.0.0.0/8** là một mạng lớp A với subnet mask **255.0.0.0**.

#### Lớp B:
- Sử dụng cho các mạng vừa và lớn.
- Địa chỉ IP bắt đầu từ **128.0.0.0** đến **191.255.255.255**.
- Phần đầu (16 bit đầu tiên) là bit mạng, phần còn lại (16 bit sau) là bit host.
- Ví dụ: **172.16.0.0/12** là một mạng lớp B với subnet mask **255.240.0.0**.

#### Lớp C:
- Sử dụng cho các mạng nhỏ.
- Địa chỉ IP bắt đầu từ **192.0.0.0** đến **223.255.255.255**.
- Phần đầu (24 bit đầu tiên) là bit mạng, phần còn lại (8 bit sau) là bit host.
- Ví dụ: **192.168.0.0/16** là một mạng lớp C với subnet mask **255.255.0.0**.

#### Lớp D:
- Sử dụng cho **multicast** (đa điểm).
- Địa chỉ IP bắt đầu từ **224.0.0.0** đến **239.255.255.255**.
- Không sử dụng subnet mask vì các địa chỉ lớp D được sử dụng cho gửi multicast trong mạng.

#### Lớp E:
- Dành cho nghiên cứu và thử nghiệm.
- Địa chỉ IP bắt đầu từ **240.0.0.0** đến **255.255.255.255**.
- Không sử dụng subnet mask.

#### Mục đích của việc phân lớp địa chỉ IP:
- **Quản lý và phân phối địa chỉ IP:** Mỗi lớp có quy mô mạng khác nhau, cho phép phân bố hiệu quả cho các mạng với quy mô khác nhau.
- **Nhận diện loại mạng:** Dựa trên địa chỉ IP, ta có thể dễ dàng nhận biết mạng thuộc lớp nào và áp dụng các cấu hình mạng phù hợp.

### 6. Địa chỉ IPv4

Địa chỉ IPv4 được chia thành hai loại: 
- **IP private:** Chỉ được sử dụng trong mạng nội bộ (LAN), không được định tuyến trên môi trường internet, có thể được sử dụng lặp lại trong các mạng LAN khác nhau.
- **IP public:** Là địa chỉ được sử dụng cho các gói tin đi trên môi trường Internet. Địa chỉ public IP phải là duy nhất cho mỗi host tham gia vào Internet.

### 7. Default Gateway

**Default gateway** là địa chỉ IP của router kết nối với mạng cục bộ của máy tính, được coi là cổng ra của mạng LAN, cho phép các thiết bị trong mạng này có thể giao tiếp với các mạng bên ngoài.
