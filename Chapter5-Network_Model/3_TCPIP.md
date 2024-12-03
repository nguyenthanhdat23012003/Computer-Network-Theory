**[Vietnamese Below]**

# TCP/IP Model

The TCP/IP model is a reference model and conceptual framework for the suite of protocols collectively known as the TCP/IP protocol suite. It serves as the foundation for modern Internet functionality. Named after its two core protocols, TCP and IP, the model is structured into layers: Link Layer, Internet Layer, Transport Layer, and Application Layer.

---

## Layers of the TCP/IP Model

1. **Application Layer:**
   - Handles user data. Protocols in this layer use one of the two transport layer protocols to deliver information to the endpoint. Common protocols include Telnet, FTP, DNS, SMTP, SNMP, TFTP, NFS, and DHCP.

2. **Transport Layer:**
   - Contains two main protocols: TCP and UDP. This layer is responsible for serving the application layer and ensuring reliable end-to-end communication. Protocols in this layer are implemented as software and integrated directly into the operating system.

3. **Internet Layer:**
   - Responsible for routing packets across networks. This layer includes all routing protocols and the IP protocol for user data transport. Devices operating at this layer (typically routers) receive IP packets, determine their destinations, and forward them toward their endpoints. This layer also handles error messages and control information through specific protocols. These protocols can be implemented in both hardware and software: on computers, as system functions, and on routers, as hardware logic. The primary device operating at this layer is the router.

4. **Link Layer (or Network Interface Layer):**
   - Handles device drivers and hardware interfaces to connect computers to the transmission medium. Common protocols at this layer include ATM, Ethernet, PPP, Frame Relay, Token Ring, and FDDI. Most protocols at this layer are implemented in hardware, and devices like hubs/repeaters, bridges/switches operate at this layer.

---

## Comparison of OSI and TCP/IP Models

Both models have similarities in their layered structure, roles, and functions. 

- **OSI** was designed to describe any type of network, while **TCP/IP** was specifically developed to describe the TCP/IP protocol suite.
- Today, the TCP/IP protocol suite is the de facto industry standard for computer networking, making it the primary model used for comparisons.

<p align="center">
  <img src="../image/Chapter5/OSI_vs_TCPIP.png" alt="OSI_vs_TCPIP">
</p>

<div style="border-top: 2px solid white; margin: 20px 0;"></div>

# Mô hình TCP/IP

Là một mô hình tham chiếu, bản mô hình hóa của tập hợp các giao thức, thường gọi là bộ giao thức TCP/IP, đóng vai trò nền tảng trong hoạt động Internet ngày nay. Được đặt tên theo hai giao thức nòng cốt của nó là TCP và IP, được thiết kế dựa theo kiến trúc phân tầng bao gồm các tầng: Tầng liên kết, tầng liên mạng, tầng giao vận và tầng ứng dụng.

---

## Các Tầng trong Mô hình TCP/IP

1. **Tầng ứng dụng:**
   - Làm việc với dữ liệu người dùng, các giao thức thuộc tầng này sẽ sử dụng một trong hai giao thức của tầng giao vận để truyền thông tin đến điểm cuối. Các giao thức thường gặp là: telnet, FTP, DNS, SMTP, SNMP, TFTP, NFS, DHCP.

2. **Tầng giao vận:**
   - Chứa hai giao thức TCP và UDP, chịu trách nhiệm phục vụ tầng ứng dụng và đảm bảo truyền thông end-to-end. Các giao thức phía trên được thực thi ở dạng phần mềm và cài đặt trực tiếp trong hệ điều hành.

3. **Tầng liên mạng:**
   - Chịu trách nhiệm vận chuyển các gói tin qua mạng. Tầng này chứa tất cả các giao thức định tuyến và giao thức vận chuyển dữ liệu người dùng IP. Các thiết bị hoạt động ở tầng này (thường là router) có nhiệm vụ nhận gói tin IP, xác định điểm đến của gói tin IP, và chuyển gói tin IP về phía máy đích. Tầng này cũng chứa các giao thức gửi và nhận thông báo lỗi và các thông điệp điều khiển. Các giao thức ở tầng này có thể thực hiện ở cả phần cứng và phần mềm; trên máy tính thì được thực hiện ở dạng hàm hệ thống, còn trên router thì được thực hiện ở phần cứng. Thiết bị chủ yếu hoạt động ở tầng này là router.

4. **Tầng liên kết (hoặc tầng giao diện mạng):**
   - Chịu trách nhiệm hoạt động với trình điều khiển thiết bị và các giao diện phần cứng để kết nối máy tính với môi trường truyền. Một số giao thức của tầng liên kết: ATM, Ethernet, PPP, Frame relay, Token Ring, FDDI. Các giao thức ở tầng này hầu hết thực thi trong phần cứng; các thiết bị mạng như hub/repeater, bridge/switch hoạt động ở tầng liên kết.

---

## So sánh OSI và TCP/IP

Hai mô hình thực tế có sự tương đồng và cả vai trò nhiệm vụ cũng như tên gọi của các tầng. 

- **OSI** sinh ra với mục đích mô tả bất kỳ loại mạng nào, trong khi **TCP/IP** được sinh ra chỉ để mô tả cho bộ giao thức TCP/IP có sẵn.
- Tuy nhiên, hiện nay chỉ còn bộ giao thức TCP/IP được sử dụng làm chuẩn công nghiệp trong mạng máy tính, nên nó được dùng để so sánh hai mô hình mạng.

<p align="center">
  <img src="../image/Chapter5/OSI_vs_TCPIP.png" alt="OSI_vs_TCPIP">
</p>
