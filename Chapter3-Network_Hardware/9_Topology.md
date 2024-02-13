## Cấu trúc liên mạng (Topology)

### Định nghĩa
Cấu trúc liên mạng (hay còn gọi là topology) là sự sắp xếp hình học của các liên kết và các node trong một mạng máy tính. Nó mô tả cách mà dữ liệu được truyền giữa các node trong mạng. Có hai loại cấu trúc liên kết mạng: 
1. **Cấu trúc vật lý**: nhấn mạnh đến cách bố trí vật lý của các thiết bị.
2. **Cấu trúc logic**: tập trung vào mô hình truyền dữ liệu giữa các node.

### Các mô hình cấu trúc vật lý căn bản
1. **Cấu trúc tuyến tính - Bus Topology**
<p align="center">
  <img src="../image/Chapter3/Bus_Topology.png" alt="Bus_Topology">
</p>
   - **Mô tả**: Tất cả thiết bị đầu cuối kết nối và sử dụng chung một đường cáp truyền tín hiệu. Đường cáp có thể là cáp xoắn hoặc cáp đồng trục. Hai đầu cáp được gắn thiết bị đặc biệt gọi là **Terminator** để ngăn chặn mất tín hiệu.
   - **Hoạt động**: Khi thiết bị đầu cuối muốn truyền dữ liệu, nó sẽ gửi gói tin lên đường truyền. Tất cả thiết bị nhận gói tin nhưng chỉ thiết bị có địa chỉ định danh trùng mới xử lý.
   - **Ưu điểm**:
     - Dễ lắp đặt và giá thành thấp.
     - Hoạt động hiệu quả với ít thiết bị, số lượng cáp ít.
     - Dễ dàng vô hiệu hóa kết nối của một thiết bị mà không ảnh hưởng đến các thiết bị khác.
     - Dễ dàng mở rộng bằng cách kết nối cáp của hai mạng tuyến tính.
   - **Nhược điểm**:
     - Không hoạt động tốt với nhiều thiết bị.
     - Tốc độ chậm, dễ bị nghẽn cổ chai.
     - Tỉ lệ mất gói tin cao, nếu cáp đứt thì mạng bị chia nhỏ.
     - Thêm thiết bị vào làm giảm hiệu năng hoạt động của mạng.

2. **Cấu trúc vòng - Ring Topology**
<p align="center">
  <img src="../image/Chapter3/Ring_Topology.png" alt="Ring_Topology">
</p>
   - **Mô tả**: Tất cả thiết bị đầu cuối kết nối với nhau thành một mạch tròn khép kín. Nếu có nhiều thiết bị, các repeater sẽ được lắp thêm để đảm bảo tín hiệu không bị suy yếu.
   - **Hoạt động**: Gói tin được truyền theo một hướng nhất định đến từng thiết bị, khi đến thiết bị có địa chỉ trùng thì được xử lý.
   - **Ưu điểm**:
     - Giảm xung đột khi truyền tin do gói tin được truyền theo một chiều nhất định.
     - Thêm thiết bị đầu cuối không ảnh hưởng đến hiệu năng.
     - Giá thành lắp đặt và mở rộng vừa phải, tốc độ truyền dữ liệu tốt.
   - **Nhược điểm**:
     - Thiết bị đầu cuối cần thẻ bài để truyền tin.
     - Tốc độ truyền chậm hơn mạng tuyến tính.
     - Khó khăn trong việc thêm thiết bị và xử lý sự cố.

3. **Cấu trúc hình sao - Star Topology**
<p align="center">
  <img src="../image/Chapter3/Star_Topology.png" alt="Star_Topology">
</p>
   - **Mô tả**: Tất cả thiết bị đầu cuối kết nối đến một thiết bị trung tâm (hub hoặc switch).
   - **Hoạt động**: Thiết bị trung tâm nhận gói tin và phân phối đến đúng đích.
   - **Ưu điểm**:
     - Độ tin cậy cao, một dây mạng lỗi không ảnh hưởng đến phần còn lại.
     - Hiệu năng cao, không xung đột nếu thiết bị trung tâm là switch.
     - Dễ lắp đặt và mở rộng, dễ xử lý sự cố.
   - **Nhược điểm**:
     - Sử dụng nhiều cáp hơn so với mạng tuyến tính và vòng.
     - Phụ thuộc vào thiết bị trung tâm; nếu hỏng thì toàn mạng sẽ bị tê liệt.
     - Chi phí lắp đặt cao hơn do chi phí cho thiết bị trung tâm.

4. **Cấu trúc lưới - Mesh Topology**
<p align="center">
  <img src="../image/Chapter3/Mesh_Topology.png" alt="Mesh_Topology">
</p>
   - **Mô tả**: Các thiết bị đầu cuối kết nối với nhau từng đôi một thông qua môi trường truyền dẫn. Có hai loại: 
     - **Partial Mesh**: Không phải hai thiết bị nào cũng kết nối với nhau.
     - **Full Mesh**: Tất cả các thiết bị đều kết nối với nhau.
   - **Hoạt động**: Khi một thiết bị gửi dữ liệu, nó chuyển trực tiếp gói tin cho thiết bị nhận.
   - **Ưu điểm**:
     - Một thiết bị lỗi không ảnh hưởng đến toàn mạng.
     - Không có vấn đề tranh chấp băng thông do kết nối trực tiếp.
     - Dễ xử lý sự cố và có tính bảo mật cao.
     - Thêm hoặc bớt thiết bị không ảnh hưởng đến toàn mạng.
   - **Nhược điểm**:
     - Chi phí lắp đặt cao do yêu cầu nhiều cáp và thiết bị.

### Mô hình mạng kết hợp
Kết hợp nhiều mô hình mạng trên để tạo ra một **mô hình mạng kết hợp**, nhằm tận dụng ưu điểm và khắc phục nhược điểm của từng mô hình.
