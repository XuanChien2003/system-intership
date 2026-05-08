# TÌM HIỂU VỀ DHCP

## I. DHCP là gì?

### 1. Khái niệm

![DHCP](../Img/DHCP.png)

**DHCP (Dynamic Host Configuration Protocol)** là giao thức dùng để **tự động cấp phát địa chỉ IP** và các thông số mạng cho thiết bị.

Thay vì phải cấu hình IP thủ công cho từng máy, DHCP Server sẽ tự động cấp:

- Địa chỉ IP
- Subnet Mask
- Default Gateway
- DNS Server
- Thời gian thuê IP (Lease Time)

Ví dụ: Khi laptop kết nối vào Wi-Fi, laptop sẽ tự động nhận IP như `192.168.1.10` từ router. Quá trình này thường do DHCP thực hiện.

### 2. DHCP dùng để làm gì?

DHCP giúp việc quản lý địa chỉ IP đơn giản hơn:

- **Tự động gán IP** cho thiết bị khi kết nối vào mạng.
- **Tránh trùng IP**, vì DHCP Server quản lý IP nào đã cấp, IP nào còn trống.
- **Quản lý tập trung**, quản trị viên chỉ cần cấu hình trên DHCP Server.
- **Dễ thay đổi cấu hình mạng**, vì khi đổi gateway, DNS hoặc dải IP thì chỉ cần sửa trên DHCP Server.
- **Thuận tiện khi di chuyển**, thiết bị sang mạng khác sẽ tự động nhận IP mới.

## II. Các thành phần của DHCP
![DHCP](../Img/phanloai.png)
### 1. DHCP Server

**DHCP Server** là máy chủ hoặc thiết bị chịu trách nhiệm cấp IP cho client.

DHCP Server sẽ lưu:

- Dải IP có thể cấp phát
- IP nào đã cấp
- IP đó cấp cho MAC address nào
- Thời gian thuê IP của từng thiết bị

Trong mạng gia đình, router Wi-Fi thường đóng vai trò DHCP Server.

### 2. DHCP Client

**DHCP Client** là thiết bị cần xin IP từ DHCP Server.

Ví dụ:

- Máy tính
- Laptop
- Điện thoại
- Máy in
- Camera IP

Khi kết nối vào mạng, client gửi yêu cầu xin IP. Sau khi được cấp IP, client mới có thể giao tiếp trong mạng.

### 3. DHCP Relay Agent

**DHCP Relay Agent** là thiết bị trung gian chuyển tiếp gói DHCP giữa client và server khi hai bên **không cùng subnet**.

Bình thường, gói DHCP Discover là broadcast nên router không chuyển qua subnet khác. Vì vậy cần DHCP Relay Agent để chuyển gói tin đó đến DHCP Server.

Hoạt động đơn giản:

1. Client gửi DHCP Discover trong subnet của nó.
2. Relay Agent nhận gói tin này.
3. Relay Agent chuyển tiếp đến DHCP Server bằng unicast.
4. DHCP Server phản hồi lại Relay Agent.
5. Relay Agent gửi cấu hình IP về cho client.

Trên router Cisco, DHCP Relay thường cấu hình bằng lệnh:

```text
ip helper-address <địa-chỉ-DHCP-Server>
```

### 4. DHCP Lease

**DHCP Lease** là thời gian mà client được phép sử dụng địa chỉ IP đã cấp.

Ví dụ: DHCP Server cấp IP `192.168.1.20` cho laptop trong 24 giờ. Sau 24 giờ, nếu laptop không gia hạn, IP đó có thể được cấp cho thiết bị khác.

Lease giúp DHCP Server thu hồi và tái sử dụng IP hiệu quả.

### 5. DHCP Binding

**DHCP Binding** là bảng ghi nhớ việc cấp phát IP.

Một binding thường gồm:

- Địa chỉ IP đã cấp
- Địa chỉ MAC của client
- Thời gian lease

Ví dụ:

| IP đã cấp | MAC Address | Trạng thái |
| --- | --- | --- |
| 192.168.1.10 | AA:BB:CC:11:22:33 | Đang sử dụng |

Binding giúp DHCP Server biết IP nào đang được thiết bị nào sử dụng.

## III. Cách DHCP hoạt động
![DHCP](../Img/hđ.png)
Quá trình cấp IP của DHCP thường được gọi là **DORA**:

- **D**iscover
- **O**ffer
- **R**equest
- **A**cknowledge

### Bước 1: DHCP Discover

Client vừa kết nối vào mạng nên chưa có IP.

Client gửi gói **DHCP Discover** để tìm DHCP Server.

Thông tin quan trọng:

- Source IP: `0.0.0.0`
- Destination IP: `255.255.255.255`
- Kiểu gửi: Broadcast

Ý nghĩa: "Có DHCP Server nào trong mạng không? Hãy cấp IP cho tôi."

### Bước 2: DHCP Offer

DHCP Server nhận được Discover và gửi lại **DHCP Offer**.

Gói Offer chứa:

- IP đề nghị cấp cho client
- Subnet Mask
- Default Gateway
- DNS Server
- Lease Time

Ý nghĩa: "Tôi có thể cấp cho bạn IP này."

### Bước 3: DHCP Request

Client nhận được Offer và gửi **DHCP Request** để đồng ý sử dụng IP được đề nghị.

Ý nghĩa: "Tôi đồng ý nhận IP này."

Nếu có nhiều DHCP Server cùng gửi Offer, client thường chọn một Offer và gửi Request để xác nhận.

### Bước 4: DHCP ACK

DHCP Server gửi **DHCP ACK** để xác nhận việc cấp IP thành công.

Sau khi nhận ACK, client cấu hình IP trên card mạng và có thể giao tiếp trong mạng.

Ý nghĩa: "IP này đã được cấp cho bạn, bạn có thể sử dụng."

## IV. Các thông điệp DHCP thường gặp

### 1. DHCP Discover

Client gửi để tìm DHCP Server khi chưa có IP.

- Nguồn: `0.0.0.0`
- Đích: `255.255.255.255`
- Kiểu gửi: Broadcast

### 2. DHCP Offer

DHCP Server gửi để đề nghị một địa chỉ IP cho client.

Nó gồm IP và các thông số như gateway, DNS, subnet mask, lease time.

### 3. DHCP Request

Client gửi để chấp nhận IP được cấp hoặc để gia hạn IP đang dùng.

Có 2 trường hợp phổ biến:

- Sau khi nhận Offer, client gửi Request để chấp nhận IP.
- Khi sắp hết lease, client gửi Request để gia hạn IP.

### 4. DHCP ACK

DHCP Server gửi để xác nhận cấp IP thành công.

Sau gói này, client bắt đầu sử dụng IP.

### 5. DHCP NAK

DHCP Server gửi khi không chấp nhận yêu cầu của client.

Ví dụ:

- Client xin lại IP cũ nhưng IP đó không còn hợp lệ.
- Client đang ở sai subnet.
- IP đã được cấp cho thiết bị khác.

Khi nhận NAK, client phải quay lại xin IP từ đầu.

### 6. DHCP Release

Client gửi để trả lại IP cho DHCP Server khi không dùng nữa.

Ví dụ: Máy tính tắt máy hoặc ngắt kết nối mạng.

### 7. DHCP Inform

Client đã có IP tĩnh, nhưng vẫn muốn xin thêm thông tin như DNS hoặc gateway từ DHCP Server.

DHCP Inform không dùng để xin IP mới.

## V. Gia hạn địa chỉ IP

Địa chỉ IP do DHCP cấp không phải lúc nào cũng dùng vĩnh viễn. Nó có thời gian thuê gọi là **Lease Time**.

Quá trình gia hạn:

- Khi đạt **50% thời gian lease (T1)**, client gửi DHCP Request bằng unicast đến DHCP Server đã cấp IP.
- Nếu không thành công, đến **87.5% thời gian lease (T2)**, client gửi Request bằng broadcast để tìm server có thể gia hạn.
- Nếu hết lease mà vẫn không gia hạn được, client mất IP và phải Discover lại từ đầu.

Ví dụ: Lease Time là 8 giờ.

- Sau 4 giờ, client bắt đầu xin gia hạn.
- Nếu thất bại, đến khoảng 7 giờ, client thử lại bằng broadcast.
- Nếu hết 8 giờ vẫn thất bại, client không được dùng IP đó nữa.

## VI. Ưu điểm và nhược điểm của DHCP

### 1. Ưu điểm

- **Dễ quản lý:** Không cần cấu hình IP thủ công trên từng máy.
- **Giảm lỗi cấu hình:** Hạn chế nhập sai IP, subnet mask, gateway hoặc DNS.
- **Tránh trùng IP:** DHCP Server quản lý danh sách IP đã cấp.
- **Linh hoạt:** Thiết bị di chuyển sang mạng khác sẽ tự động nhận IP mới.
- **Phù hợp mạng lớn:** Quản trị viên có thể quản lý IP tập trung.

### 2. Nhược điểm

- **Phụ thuộc vào DHCP Server:** Nếu DHCP Server lỗi, client có thể không nhận được IP.
- **Không phù hợp cho một số thiết bị cần IP cố định:** Máy chủ, máy in, camera nên dùng IP tĩnh hoặc DHCP Reservation.
- **Có rủi ro bảo mật:** DHCP không xác thực client mặc định, nên có thể xuất hiện DHCP Server giả mạo.
- **Cần DHCP Relay nếu khác subnet:** Client và server khác mạng thì phải cấu hình relay.

## VII. Lỗi DHCP thường gặp

### 1. Client nhận IP 169.254.x.x

Đây là địa chỉ APIPA. Lỗi này thường xảy ra khi client không liên lạc được DHCP Server.

Nguyên nhân có thể là:

- DHCP Server bị tắt
- Dây mạng hoặc Wi-Fi lỗi
- VLAN sai
- Chưa cấu hình DHCP Relay
- Hết IP trong pool

### 2. Trùng địa chỉ IP

Xảy ra khi có thiết bị cấu hình IP tĩnh trùng với IP trong DHCP Pool.

Cách khắc phục:

- Không đặt IP tĩnh trong dải DHCP cấp phát
- Loại trừ các IP quan trọng khỏi DHCP Pool
- Dùng DHCP Reservation nếu cần IP cố định

### 3. Lease Time quá dài

Nếu Lease Time quá dài, IP bị giữ lâu và không được giải phóng nhanh.

Điều này dễ gây thiếu IP trong các mạng có nhiều thiết bị ra vào liên tục, ví dụ Wi-Fi công ty, quán cafe, trường học.

### 4. Sai Gateway hoặc DNS

Client có IP nhưng không vào Internet hoặc không truy cập được tên miền.

Nguyên nhân có thể là:

- Sai Default Gateway
- Sai DNS Server
- DHCP Server cấp sai option

