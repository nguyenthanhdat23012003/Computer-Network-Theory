**[Vietnamese Below]**

# Information Transmission in Computer Networks

In a network system, there are many different addresses used by protocols at various levels. 
- When TCP or UDP encapsulates its PDU, it requires the port number of the destination process and the port number of the sending process.
- When IP encapsulates a packet, it requires the IP address of the source and destination machines.
- When Ethernet encapsulates a frame, it requires the MAC address of the network card on the source and destination machines within the LAN.

## Port Address

For scenarios requiring a port address, the port is determined as follows:
- The port number of the process must be provided by the application itself. This is one of the agreements within the application layer protocol. When initializing a socket, the application must provide the port number of the destination process.
- The source port is assigned by the operating system to the process, either temporarily or permanently, depending on the program's requirements.

## IP Address

For scenarios requiring an IP address:
- The source IP address is obtained from the IP configuration of the corresponding network interface.
- The destination IP address must be provided by the application program. When initializing a socket, the application must supply this destination IP address.

## MAC Address

For scenarios requiring a MAC address:
- The source MAC address is obtained directly from the network card.
- The destination MAC address is automatically obtained from the destination IP address using the ARP protocol.

Terminal equipments have two types of addresses simultaneously: a logical IP address and a physical MAC address. The IP address enables host-to-host communication across different networks, while the MAC address enables the transmission of data frames within a single LAN (within the same broadcast domain).

## ARP Protocol

ARP (Address Resolution Protocol) is a mandatory protocol within the TCP/IP suite. It is responsible for discovering a device's MAC address based on its IP address.

### Example

Two computers, A and B, are connected to the same switch and belong to the same IP range. When computer A wants to send data to computer B, its network card's Ethernet layer must create a frame before sending it over the medium. To create the frame, the MAC address of the destination is needed, while the data only contains the IP address.

1. Computer A checks that the destination IP address is within the same range as itself.
2. Computer A broadcasts an ARP frame across the entire LAN (broadcast domain) to determine the MAC address associated with computer B's IP address.
3. If computer B is active, it receives the ARP broadcast (since it is on the same network as A) and responds with its MAC address. Once A knows B's MAC address, it creates a frame directed to computer B.
4. If computer B is not active, there will be no response to A's ARP request. As a result, A cannot create a frame, and the transmission fails.
5. If A and B are on different networks, A sends the frame directly to the router (default gateway).

In theory, if a frame can be created (with the correct destination MAC), data can still be transmitted within the LAN without requiring an IP address. However, in practice, the MAC address is automatically determined through ARP. Therefore, both IP and MAC addresses are essential for TCP/IP networks.

Operating systems often manage network card information alongside IP address configurations, even though the network card does not use the IP address itself.

If the destination machine is on the same network as the source machine, the source machine will look in its MAC table to find the recipient's MAC address. If the corresponding MAC address is not found, the ARP protocol is executed to discover the MAC address and store it in the MAC table for future use. Once the MAC address is available, the sender encapsulates the frame and sends it.

If the destination machine is on a different network than the source machine, the source machine will check if a default gateway is configured. If configured, the frame is sent to the default gateway; otherwise, the packet is dropped, and a "destination host unreachable" message is displayed.

When the source and destination machines are on different networks, the process is more complex.

- The data frame is sent from the source machine to the router port connected to the LAN.
- Upon reaching the router, the frame is unpacked to extract the SDU (the IP packet). After obtaining the IP packet, the router knows the source and destination IP addresses of this packet.
- The router uses the network identifier of the destination IP address to check if the destination network is connected to it. If so, the router forwards the IP packet to the port connected to the destination network. At the destination port, the IP packet is repackaged into a frame similar to the one on the network card.

- If the destination network is not connected to the router, the router forwards the IP packet to the most appropriate port for reaching the destination network. The packet may pass through several intermediate routers before arriving at the final router (connected to the destination network).

- The process of comparing addresses and deciding on packet forwarding is based on the routing table (which can be manually created for simple networks or automatically generated via routing protocols).

- If the IP packet contains a broadcast address, the router blocks it from being forwarded to other networks. Similarly, if the IP packet contains a private address, the router prevents it from being forwarded to public areas.

<div style="border-top: 2px solid white; margin: 20px 0;"></div>

# Truyền thông tin trong mạng máy tính

Trong hệ thống mạng có tất nhiều địa chỉ khác nhau dùng bởi các giao thức ở các cấp độ. 
- Khi TCP hoặc UDP đóng gói PDU của mình đòi hỏi số cổng của tiến trình chạy trên máy đích và số cổng của chính tiến trình đang gửi dữ liệu. 
- Khi IP đóng gói packet cần đến địa chỉ IP của máy nguồn và máy đích. 
- Khi Ethernet đóng gói frame cần đến địa chỉ MAC của card mạng máy nguồn và máy đích trong LAN.

## Địa chỉ Port

Với trường hợp đòi hỏi port, port sẽ được lấy như sau:
- Port của tiến trình phải do chính chương trình ứng dụng cung cấp. Đây là một trong số các thỏa thuận trong giao thức tầng ứng dụng. Trong khi khởi tạo socket, ứng dụng phải cung cấp số cổng của tiến trình đích.
- Port nguồn do hệ điều hành cung cấp cho tiến trình, có thể cấp tạm thời hoặc lâu dài, tùy thuộc vào chương trình yêu cầu.

## Địa chỉ IP

Với trường hợp đòi hỏi địa chỉ IP:
- Địa chỉ IP của máy nguồn được lấy từ cấu hình IP của giao diện mạng tương ứng.
- Địa chỉ IP của máy đích phải do chương trình ứng dụng cung cấp, trong khi khởi tạo socket, ứng dụng phải cung cấp địa chỉ IP đích này.

## Địa chỉ MAC

Với trường hợp địa chỉ MAC:
- Địa chỉ MAC nguồn được lấy từ chính card mạng.
- Địa chỉ MAC đích được lấy tự động từ địa chỉ IP đích thông qua giao thức ARP.

Các thiết bị đầu cuối đồng thời có hai loại địa chỉ: địa chỉ logic IP và địa chỉ vật lý MAC. Địa chỉ IP cho phép truyền thông host-to-host nằm trong các mạng khác nhau, còn địa chỉ MAC cho phép truyền thông frame dữ liệu trong nội bộ một mạng LAN (trong cùng một miền quảng bá).

## Giao thức ARP

ARP (Address Resolution Protocol) là một giao thức bắt buộc của bộ giao thức TCP/IP. Giao thức này có nhiệm vụ tìm hiểu địa chỉ MAC của thiết bị thông qua địa chỉ IP của nó.

### Ví dụ

Có hai máy tính A và B đều kết nối với cùng một switch, nằm cùng dải địa chỉ IP. Khi này máy A muốn chuyển dữ liệu cho máy B sẽ cần Ethernet ở card mạng tạo frame trước khi đưa lên đường truyền, và để tạo frame cần địa chỉ MAC của máy đích, trong khi data chỉ chứa địa chỉ IP.

1. Máy A kiểm tra thấy địa chỉ IP của máy đích nằm cùng dải với nó.
2. Máy A gửi một frame ARP quảng bá ra toàn mạng LAN (miền quảng bá) để xác định địa chỉ MAC được liên kết với địa chỉ IP của máy B.
3. Nếu máy B đang hoạt động, nó nhận được gói ARP quảng bá vì nằm trong cùng mạng với máy A và phản hồi lại địa chỉ MAC của nó cho máy A. Khi biết được địa chỉ MAC của B, A sẽ tạo frame định hướng đến máy B.
4. Nếu máy B không hoạt động -> không có phản hồi cho máy A -> A không biết địa chỉ MAC của máy đích -> không tạo được frame và gửi thất bại.
5. Nếu A và B không cùng một mạng thì A sẽ chuyển thẳng frame đến router (default gateway).

Về lý thuyết, nếu có thể chế tạo ra frame (với đủ MAC đích) thì vẫn có thể truyền nó đi trong LAN mà không cần đến IP. Tuy nhiên, trên thực tế, MAC được xác định tự động thông qua ARP. Do đó, địa chỉ IP và MAC là bắt buộc đối với mạng TCP/IP.

Trên các hệ điều hành thường quản lý chung thông tin card mạng với cấu hình địa chỉ IP, mặc dù card mạng không sử dụng địa chỉ IP. 

Nếu máy đích cùng mạng với máy nguồn thì máy nguồn sẽ tìm trong bảng MAC table của mình để có được địa chỉ MAC của máy nhận. Trong trường hợp nó không tìm được địa chỉ MAC tương ứng, giao thức ARP sẽ được thực hiện để tìm địa chỉ MAC và lưu vào bảng MAC để sử dụng ở các lần sau. Sau khi có địa chỉ MAC thì máy gửi sẽ đóng gói frame và gửi đi.

Nếu máy đích khác địa chỉ mạng với máy nguồn thì máy nguồn sẽ kiểm tra xem máy có được khai báo default gateway hay không. Nếu có thì gửi frame đến default gateway, nếu không sẽ loại bỏ gói tin và thông báo “destination host unreachable".

Trong trường hợp máy nguồn và máy đích nằm ở các mạng khác nhau, quá trình diễn ra khá phức tạp. 

- Frame dữ liệu được chuyển từ máy nguồn đến cổng router kết nối với LAN. 
- Khi tới router, frame được mở ra để lấy SDU (là IP packet), sau khi lấy được IP packet, router biết được IP nguồn và đích của packet này. 
- Router sử dụng phần định danh mạng của địa chỉ IP đích để xem mạng đích có kết nối với nó hay không. Nếu có, router chuyển tiếp gói tin IP sang cổng kết nối với mạng đích, ở cổng đích, gói tin IP lại phải được đóng gói thành frame giống trên card mạng.

- Nếu mạng đích không kết nối với router, nó sẽ chuyển tiếp gói tin IP sang cổng phù hợp nhất để nó có thể tới được mạng đích. Gói tin sẽ phải qua nhiều router trung gian trước khi tới được router cuối cùng (router kết nối với mạng đích). 

- Quá trình so sánh địa chỉ và quyết định chuyển tiếp gói tin này được thực hiện dựa trên bảng định tuyến (bảng này có thể tạo chạy với các mạng đơn giản hoặc tạo tự động thông qua giao thức định tuyến). 

- Nếu gói tin IP chứa địa chỉ quảng bá, router sẽ chặn gói tin này không cho nó chuyển sang các mạng khác, hoặc nếu gói tin IP chứa địa chỉ private, router cũng chặn nó lại không cho chuyển sang các vùng public.
