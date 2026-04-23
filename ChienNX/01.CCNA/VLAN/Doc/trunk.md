### 1. Khái niệm đường Trunk
**Đường Trunk** hay **Trunking** là một kỹ thuật kết nối các thiết bị mạng (như switch hoặc router) để tạo thành một mạng lớn hơn, đặc biệt phổ biến trong các mạng LAN hoặc VLAN. Đây là một kết nối chuyên dụng cho phép truyền dữ liệu của nhiều mạng con (subnet) hoặc nhiều VLAN khác nhau thông qua **một đường truyền vật lý duy nhất**.

### 2. Đặc điểm
- Cho phép truyền dữ liệu của nhiều VLAN qua một cổng vật lý duy nhất bằng cách gắn thêm tag VLAN vào gói tin.
- Thường sử dụng giao thức 802.1Q để đánh dấu (tag) các gói tin.
- Được sử dụng khi cần kết nối giữa các Switch với nhau hoặc giữa Switch với Router để truyền tải dữ liệu của nhiều VLAN.

Khi một cổng được cấu hình trunk, dữ liệu từ nhiều VLAN sẽ truyền qua cùng một đường truyền. Để phân biệt gói tin thuộc VLAN nào, người ta sử dụng các giao thức gắn thẻ (tagging). Có 2 chuẩn phổ biến là IEEE 802.1Q (DOT1Q) và ISL

### 3.Chuẩn IEEE 802.1Q (DOT1Q)
 IEEE 802.1Q (còn gọi là DOT1Q) là tiêu chuẩn mở do IEEE phát triển, được sử dụng rộng rãi trên các thiết bị mạng của nhiều hãng khác nhau (Cisco, HP, Juniper...).

 Gói tin VLAN khi đi qua cổng trunk sẽ được gắn thẻ VLAN (VLAN Tagging) theo chuẩn 802.1Q.

![trunk](/ChienNX/01.CCNA/VLAN/Img/trunk.png)
#### Cách hoạt động

- Thêm một thẻ (tag VLAN) vào gói tin Ethernet để xác định VLAN mà nó thuộc về.
- Kích thước tag VLAN: 4 byte (32 bit) được chèn vào giữa phần Header và Payload của gói tin Ethernet.
- Có khái niệm Native VLAN: Gói tin thuộc Native VLAN sẽ không gắn tag khi truyền qua Trunk.
- Khái niệm Native VLAN: Gói tin thuộc Native VLAN sẽ không gắn tag khi truyền qua Trunk.

#### Cấu trúc thẻ VLAN (802.1Q VLAN Tag - 4 byte)

| Thành phần | Kích thước | Ý nghĩa |
|-----------|-------------|---------|
| Type | 2 byte | Luôn có giá trị 0x8100, giúp thiết bị mạng nhận biết đây là gói tin VLAN |
| Priority (PRI - Class of Service - CoS) | 3 bit | Xác định mức độ ưu tiên của gói tin (giá trị từ 0 - 7). Dùng cho QoS (Quality of Service). |
| Token Ring Encapsulation (CFI - Canonical Format Indicator) | 1 bit | Dùng để xác định định dạng địa chỉ MAC. Thường là 0 (Ethernet chuẩn). Nếu là 1, có thể dùng trong Token Ring (hiếm khi dùng) |
| VLAN ID (VID - VLAN Identifier) | 12 bit | Xác định VLAN của gói tin, giá trị từ 1 - 4094 (0 và 4095 bị cấm sử dụng) |

#### Ví dụ VLAN Tagging với 802.1Q

Gói tin từ VLAN 10 khi truyền qua Trunk Port sẽ được thêm Tag VLAN 10. Switch nhận được gói tin sẽ đọc tag này để biết nó thuộc VLAN nào.


