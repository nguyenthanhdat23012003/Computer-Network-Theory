**[Vietnamese Below]**

## Base64

**Base64** is a method for encoding data to be transmitted through systems that support only ASCII text characters. The Base64 algorithm encodes binary data into a text string that is safe and easy to transmit over protocols like email and HTTP.

### How It Works

Base64 works by converting each group of 3 bytes (24 bits) of binary data into 4 encoded characters from the Base64 character set. The Base64 character set includes:

- 26 uppercase letters (A-Z)
- 26 lowercase letters (a-z)
- 10 digits (0-9)
- 2 special characters (+ and /)

In total, the Base64 character set has 64 characters (hence the name Base64).

#### Encoding Process

The Base64 encoding process involves the following steps:

1. **Divide into 3-byte groups:**
   Input data is divided into groups of 3 bytes (24 bits). If the data is not a multiple of 3 bytes, zero-padding is added.

2. **Convert to 4 blocks of 6 bits:**
   Each group of 3 bytes is converted into 4 blocks of 6 bits. Each 6-bit block is mapped to a character in the Base64 character set.
   
   Specifically: A group of 3 bytes (24 bits) like `01000001 01000010 01000011 (A B C)` 
   becomes 4 blocks of 6 bits: `010000 010100 001001 000011 (16 20 9 3)`

3. **Map to Base64 characters:**
   The 6-bit values are mapped to the Base64 character set. For example:
   `010000 010100 001001 000011` maps to `Q U J D`.

4. **Add padding if necessary:**
   If the input bytes are not a multiple of 3, the output is padded with `=` characters to ensure the output length is a multiple of 4.

#### Encoding Example

Encoding the string "Man" into Base64:

- **Input data (ASCII):** M = 77, a = 97, n = 110
- **Binary representation:** M = 01001101, a = 01100001, n = 01101110
- **Combine into 24 bits:** 01001101 01100001 01101110
- **Divide into 4 blocks of 6 bits:** 010011 010110 000101 101110
- **Map to Base64:** TWFu
- No `=` padding is needed since the input data is complete.

#### Decoding Process

The Base64 decoding process reverses the encoding steps:

1. Remove any `=` padding characters.
2. Map the Base64 characters back to 6-bit blocks.
3. Combine the 6-bit blocks into groups of 3 bytes (24 bits).
4. Remove any padding bytes added during encoding.

The encoding and decoding processes are straightforward. For more information, see [here](https://en.wikipedia.org/wiki/Base64).

### Applications of Base64

Base64 is widely used in various applications, such as:

- **Email:** Encoding binary content in MIME emails.
- **HTTP:** Transmitting binary data in URLs and JSON payloads.
- **Data Storage and Transmission:** Ensuring binary data can be safely handled in text-only systems.

### Conclusion

Base64 is a simple yet effective algorithm for encoding binary data as ASCII text. Understanding how Base64 works allows you to apply it easily in data transmission and storage scenarios.


---

## Base64

**Base64** là một phương thức mã hóa dữ liệu để truyền tải qua các hệ thống mà chỉ hỗ trợ các ký tự văn bản ASCII. Thuật toán Base64 mã hóa dữ liệu nhị phân thành chuỗi văn bản an toàn và dễ dàng truyền tải qua các giao thức như email và HTTP.

### Cách thức hoạt động

Base64 hoạt động bằng cách chuyển đổi mỗi nhóm 3 byte (24 bit) dữ liệu nhị phân thành 4 ký tự mã hóa từ bảng mã Base64. Bảng mã Base64 bao gồm các ký tự sau:

- 26 ký tự chữ cái viết hoa (A-Z)
- 26 ký tự chữ cái viết thường (a-z)
- 10 chữ số (0-9)
- 2 ký tự đặc biệt (+ và /)

Tổng cộng, bảng mã Base64 có 64 ký tự (do đó có tên là Base64).

#### Quá trình mã hóa

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

#### Ví dụ mã hóa

Mã hóa chuỗi "Man" thành Base64:

- **Dữ liệu đầu vào (ASCII):** M = 77, a = 97, n = 110
- **Dạng nhị phân:** M = 01001101, a = 01100001, n = 01101110
- **Kết hợp lại:** 01001101 01100001 01101110
- **Chia thành 4 khối 6-bit:** 010011 010110 000101 101110
- **Ánh xạ đến Base64:** TWFu
- Không cần bổ sung ký tự "=" vì dữ liệu đầy đủ.

#### Quá trình giải mã

Quá trình giải mã Base64 ngược lại với quá trình mã hóa:

1. Loại bỏ các ký tự "=" nếu có.
2. Ánh xạ ngược các ký tự Base64 thành các khối 6-bit.
3. Kết hợp các khối 6-bit thành nhóm 3 byte (24-bit).
4. Loại bỏ các byte 0 đã thêm vào (nếu có).

Quá trình mã hóa và giải mã rất đơn giản. Xem thêm [tại đây](https://en.wikipedia.org/wiki/Base64).

### Ứng dụng của Base64

Base64 được sử dụng rộng rãi trong nhiều ứng dụng, chẳng hạn:

- **Email:** Mã hóa nội dung nhị phân trong các email MIME.
- **HTTP:** Truyền tải dữ liệu nhị phân qua URL và JSON.
- **Lưu trữ và truyền tải dữ liệu:** Đảm bảo dữ liệu nhị phân an toàn trong các hệ thống chỉ hỗ trợ văn bản.

### Kết luận

Base64 là một thuật toán mã hóa dữ liệu đơn giản nhưng rất hiệu quả để truyền tải dữ liệu nhị phân dưới dạng văn bản ASCII. Hiểu cách thức hoạt động của Base64 giúp bạn dễ dàng áp dụng nó trong các ứng dụng truyền tải và lưu trữ dữ liệu.



