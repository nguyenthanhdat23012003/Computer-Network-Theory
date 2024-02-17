# Địa chỉ trong mạng máy tính và số cổng tiến trình

Trong mạng máy tính, có nhiều giao thức hoạt động đồng thời. Mỗi giao thức yêu cầu một cách xác định đối tác trên máy nguồn và máy đích. Để đạt được mục đích này, các giao thức sử dụng cơ chế đánh địa chỉ.

## 1. Các loại địa chỉ trong mạng

Tùy thuộc vào giao thức, có các cơ chế đánh địa chỉ khác nhau:

- **Địa chỉ IP:** Sử dụng bởi giao thức IP để xác định thiết bị trong mạng.
  
- **Địa chỉ MAC:** Sử dụng bởi giao thức Ethernet, được gán cứng trong card mạng.

- **Số cổng (Port):** Sử dụng bởi giao thức TCP/UDP để xác định tiến trình đang khai thác dịch vụ truyền thông.

Mỗi loại địa chỉ có cách thức cấu hình riêng:

- **Địa chỉ MAC:** Gán cứng trong card mạng.
- **Địa chỉ IP:** Phải được cấu hình trên hệ điều hành.
- **Số cổng:** Cần được cấu hình thông qua phần mềm ứng dụng.

---

## 2. Số cổng và tiến trình

Trên mỗi thiết bị đầu cuối, nhiều tiến trình có thể đồng thời khai thác các dịch vụ truyền thông do TCP hoặc UDP cung cấp. Khi dữ liệu đến đích, TCP và UDP cần một cơ chế để phân biệt dữ liệu đó dành cho tiến trình nào.

Để xác định tiến trình nào đang khai thác dịch vụ, mỗi tiến trình được đánh một số không trùng lặp, gọi là **port**. Một port là loại địa chỉ dành cho các ứng dụng khai thác dịch vụ truyền thông end-to-end do TCP hoặc UDP cung cấp.

### Một số điểm lưu ý về port:

- Một port của một dịch vụ không thể được cấp cho hai tiến trình.
  
- Port cho dịch vụ TCP và UDP là độc lập; ví dụ, hai tiến trình khác nhau có thể chiếm hai cổng 80 của hai giao thức khác nhau.

- Các tiến trình tham gia vào quá trình truyền thông phải thỏa thuận về giá trị port. Các giá trị cổng nguồn và cổng đích đều được gửi kèm với gói tin để các máy có thể xác định được cần chuyển gói tin đến tiến trình nào.

---

Những khái niệm này rất quan trọng trong việc đảm bảo khả năng giao tiếp giữa các tiến trình và dịch vụ trong mạng, giúp các thiết bị và ứng dụng có thể hoạt động hiệu quả.