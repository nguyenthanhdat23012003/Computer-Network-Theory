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
