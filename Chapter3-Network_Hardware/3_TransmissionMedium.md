# Môi trường truyền dẫn

Là thành phần của mạng máy tính giúp lan truyền tín hiệu giữa các thành phần phần cứng của mạng, qua đó tạo ra các liên kết vật lý giữa các thành phần phần cứng của mạng. Có nhiều loại tín hiệu vật lý có khả năng lan truyền như: sóng âm, các loại sóng cơ học, sóng điện từ, xung điện, xung quang học. Tuy nhiên, chỉ 3 loại tín hiệu được khai thác để tạo ra môi trường truyền dẫn trong mạng máy tính là sóng điện từ, xung điện và xung quang học, tương ứng với các môi trường truyền dẫn là: không khí, cáp đồng, cáp quang.

Môi trường truyền dẫn là một bộ phận của công nghệ mạng, ví dụ các công nghệ mạng LAN phổ biến hiện nay như Fast Ethernet hoặc Gigabit Ethernet sử dụng cáp xoắn - một loại cáp lõi đồng, còn công nghệ wifi sử dụng sóng điện từ truyền trong không gian.

Môi trường truyền dẫn được chia làm hai loại:

- **Môi trường truyền có định hướng**: dẫn tín hiệu theo hướng xác định (cáp xoắn, cáp đồng trục và cáp quang).
- **Môi trường truyền không định hướng**: Để tín hiệu lan truyền bao phủ cả không gian (sóng điện từ lan truyền).

## Cáp xoắn

Là loại cáp được sử dụng phổ biến nhất trong các mạng cục bộ hiện nay. Chứa 4 cặp dây đồng, trong đó hai dây mỗi cặp xoắn vào nhau nhằm mục đích giảm nhiễu giữa các cặp dây dẫn, mỗi dây đều có vỏ bọc nhựa, cả 4 dây cũng được đặt trong vỏ bọc nhựa.

Được chia thành một số loại khác nhau, liên quan đến cách thức bảo vệ chống nhiễu:

- **Cáp UTP** không có các màng kim loại bảo vệ các cặp dây cũng như cả sợi cáp -> phổ biến và giá rẻ nhất.
- **Cáp F/UTP** có một lớp màng kim loại bảo vệ chung cả 4 cặp dây.
- **Cáp S/FTP** có một lớp màng bảo vệ bốn cặp dây và thêm một lớp màng nữa bảo vệ cho mỗi cặp dây. Hai loại trên được sử dụng trong môi trường có nhiễu nặng.

Cáp xoắn cũng được chia theo chất lượng, Cat 3 -> 8, phổ biến nhất là Cat 5e (100Mbps/100m) và Cat 6 (10Gbps/55m). Phổ biến nhất trong mạng LAN hiện nay do giá ok, tốc độ cao, dễ thi công, tuy nhiên nhược điểm là khi khoảng cách truyền thông lớn có thể bị nhiễu nếu vị trí đi dây hoặc loại dây không phù hợp.

## Cáp đồng trục

Là loại cáp truyền dẫn tín hiệu điện với một dây đồng ở lõi và có các lớp bảo vệ bên ngoài, các thành phần lấy sợi dây đồng dẫn tín hiệu làm trục chung. Cấu tạo gồm 4 phần chính:

1. **Lõi kim loại**: thường làm bằng đồng hoặc kim loại mạ đồng hoặc bạc, có tác dụng truyền dẫn tín hiệu.
2. **Lớp điện môi**: làm từ nhựa, rắn, có tác dụng cố định lõi và cách ly lõi với lớp lưới chống nhiễu.
3. **Lớp lưới chống nhiễu**: là một số lớp lưới kim loại có tác dụng giảm tín hiệu nhiễu bên ngoài ảnh hưởng đến đường truyền tín hiệu bên trong.
4. **Lớp vỏ nhựa PVC**: có độ dẻo cao giúp bảo vệ lớp dây dẫn khỏi tác động từ bên ngoài.

Dây cáp đồng trục có thể truyền dẫn tín hiệu với tần số cao và ngăn chặn nhiễu điện từ và nhiễu tần số vô tuyến từ môi trường bên ngoài -> ít dùng cho mạng LAN, thường sử dụng cho tín hiệu truyền hình, camera, ….

Ba loại cáp phổ biến hiện nay là RG6 (đường kính 6.9mm, truyền xa 545m, tên khác: cáp gầy, cáp mỏng), RG11 (đường kính 10,3mm, truyền xa 1km, tên khác: cáp béo, cáp dầy), RG59 (đường kính 6,15mm, lõi đồng làm từ nhiều sợi đồng -> dẻo -> sử dụng khi cáp cần uốn cong, truyền xa <229m). 

-> Giá rẻ, dễ thi công, khoảng cách truyền lớn, ít nhiễu tuy nhiên tốc độ thấp -> ít sử dụng cho mạng LAN.

## Cáp quang

Là loại cáp truyền dẫn tín hiệu ánh sáng, tín hiệu truyền xa nhất, nhanh nhất, không nhiễu nhưng giá cao và thi công phức tạp. Cáp quang bao gồm một hoặc nhiều sợi quang, bao gồm các phần sau:

1. **Sợi lõi (Core)**: là một sợi thủy tinh hoặc nhựa tinh chế rất nhỏ nằm ở lõi có tác dụng truyền dẫn ánh sáng.
2. **Lớp phản xạ (Cladding)**: là vật chất trong suốt có chiết suất thấp bao bọc lõi, có tác dụng tạo ra hiện tượng phản xạ toàn phần khi ánh sáng truyền trong lõi.
3. **Lớp phủ (Coating)**: lớp phủ dẻo bằng nhựa bảo vệ sợi khỏi bụi bẩn và hơi nước, giảm gãy gập và uốn cong.
4. **Lớp gia cường (Strength member)**: thường làm từ vật liệu Kevlar, có tác dụng chịu nhiệt và chịu kéo căng.
5. **Lớp vỏ ngoài (Jacket)**: Lớp vỏ bảo vệ chống tác động vật lý và hóa học.

Theo cơ chế truyền ánh sáng trong lõi, cáp quang được chia làm 2 loại chính:

- **Cáp quang singlemode**: có lõi nhỏ (9 micromet) chỉ truyền một bước sóng ánh sáng -> giá thành cao nhưng tín hiệu truyền đi rất xa với tốc độ cao.
- **Cáp quang multimode**: có lõi lớn (gấp 6-8 lần singlemode), có thể truyền nhiều bước sóng -> nhược điểm là khoảng cách truyền thấp, tốc độ chậm nhưng được cái giá thành thấp.

-> cáp tốt nhất hiện nay, tốc độ cao, truyền xa, an toàn, không nhiễu nhưng giá cao.

## Các tính chất của quá trình truyền tín hiệu

Suy hao (attenuation) là sự thất thoát năng lượng (hoặc giảm cường độ tín hiệu) trong quá trình truyền tín hiệu, để bù suy hao thì dùng bộ khuếch đại tín hiệu (Amplifier).

Méo dạng (Distortion) là hiện tượng tín hiệu bị thay đổi hình dạng thường trong các tín hiệu hỗn hợp trong đó các tín hiệu được tạo nên từ nhiều tần số khác nhau (ngày xưa học thì có mấy dạng distortion cơ bản như amplitude, phase, …).

Nhiễu (noise) là những tín hiệu không mong muốn từ môi trường làm ảnh hưởng đến tín hiệu gốc truyền đi.
