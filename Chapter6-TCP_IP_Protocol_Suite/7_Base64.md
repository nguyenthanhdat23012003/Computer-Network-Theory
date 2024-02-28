# Base64

**Base64** là một phương thức mã hóa dữ liệu để truyền tải qua các hệ thống mà chỉ hỗ trợ các ký tự văn bản ASCII. Thuật toán Base64 mã hóa dữ liệu nhị phân thành chuỗi văn bản an toàn và dễ dàng truyền tải qua các giao thức như email và HTTP.

## Cách thức hoạt động

Base64 hoạt động bằng cách chuyển đổi mỗi nhóm 3 byte (24 bit) dữ liệu nhị phân thành 4 ký tự mã hóa từ bảng mã Base64. Bảng mã Base64 bao gồm các ký tự sau:

- 26 ký tự chữ cái viết hoa (A-Z)
- 26 ký tự chữ cái viết thường (a-z)
- 10 chữ số (0-9)
- 2 ký tự đặc biệt (+ và /)

Tổng cộng, bảng mã Base64 có 64 ký tự (do đó có tên là Base64).

### Quá trình mã hóa

Quá trình mã hóa Base64 diễn ra như sau:

1. **Chia nhóm 3 byte:** 
    Dữ liệu đầu vào được chia thành các nhóm 3 byte (24 bit). Nếu dữ liệu không đủ 3 byte, nó sẽ được bổ sung thêm các byte 0 (zero-padding).

2. **Chuyển đổi sang 4 khối 6-bit:** 
    Mỗi nhóm 3 byte sẽ được chuyển thành 4 khối 6-bit. Mỗi khối 6-bit này sẽ được ánh xạ tới một ký tự trong bảng mã Base64. 
   
    Cụ thể: Một nhóm 3 byte (24 bit) sẽ được chia thành 4 phần 6-bit: `01000001 01000010 01000011   (A B C)`
    Sẽ trở thành 4 khối 6-bit: `010000 010100 001001 000011 (16 20 9 3)`

3. **Ánh xạ đến ký tự Base64:**
Các giá trị 6-bit được ánh xạ đến bảng mã Base64. Ví dụ:
`010000 010100 001001 000011 (16 20 9 3) (Q U J D)`


4. **Bổ sung padding nếu cần thiết:** 
Nếu số byte đầu vào không chia hết cho 3, thì kết quả sẽ được bổ sung thêm ký tự "=" để đảm bảo độ dài của chuỗi kết quả là bội số của 4.

### Ví dụ mã hóa

Mã hóa chuỗi "Man" thành Base64:

- **Dữ liệu đầu vào (ASCII):** M = 77, a = 97, n = 110
- **Dạng nhị phân:** M = 01001101, a = 01100001, n = 01101110
- **Kết hợp lại:** 01001101 01100001 01101110
- **Chia thành 4 khối 6-bit:** 010011 010110 000101 101110
- **Ánh xạ đến Base64:** TWFu
- Không cần bổ sung ký tự "=" vì dữ liệu đầy đủ.

### Quá trình giải mã

Quá trình giải mã Base64 ngược lại với quá trình mã hóa:

1. Loại bỏ các ký tự "=" nếu có.
2. Ánh xạ ngược các ký tự Base64 thành các khối 6-bit.
3. Kết hợp các khối 6-bit thành nhóm 3 byte (24-bit).
4. Loại bỏ các byte 0 đã thêm vào (nếu có).

Quá trình mã hóa và giải mã rất đơn giản. Xem thêm [tại đây](https://en.wikipedia.org/wiki/Base64).

## Ứng dụng của Base64

Base64 được sử dụng rộng rãi trong nhiều ứng dụng, chẳng hạn:

- **Email:** Mã hóa nội dung nhị phân trong các email MIME.
- **HTTP:** Truyền tải dữ liệu nhị phân qua URL và JSON.
- **Lưu trữ và truyền tải dữ liệu:** Đảm bảo dữ liệu nhị phân an toàn trong các hệ thống chỉ hỗ trợ văn bản.

## Kết luận

Base64 là một thuật toán mã hóa dữ liệu đơn giản nhưng rất hiệu quả để truyền tải dữ liệu nhị phân dưới dạng văn bản ASCII. Hiểu cách thức hoạt động của Base64 giúp bạn dễ dàng áp dụng nó trong các ứng dụng truyền tải và lưu trữ dữ liệu.



