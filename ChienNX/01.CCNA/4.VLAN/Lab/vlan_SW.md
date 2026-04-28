# Cấu hình chia VLAN trên Switch
![](/ChienNX/01.CCNA/4.VLAN/Img/BtVLAN.png)

|VLAN|Port|
|----|----|
|VLAN10|Fa0/1, Fa0/2|
|VLAN11|Fa0/11, Fa0/12|
|VLAN12|Fa0/21, Fa0/22|

## Các bước thực hiện:
### 1. Truy cập vào switch
- Mở Cisco Packet Tracer -> Chọn Switch -> Chọn CLI

### 2. Cấu hình CLI
```plaintext
Switch> enable
Switch# configure terminal
```
 - `enable`: Truy cập vào chế độ EXEC đặc quyền từ chế độ người dùng (User EXEC mode). Ở chế độ EXEC đặc quyền, có thể kiểm tra cấu hình và thực hiện các lệnh nâng cao hơn.
- `configure terminal`: Chuyển từ EXEC đặc quyền sang Global Configuration Mode để thay đổi cấu hình thiết bị. Khi vào chế độ này, có thể tạo VLAN, cấu hình cổng, đặt tên, v.v.
    
### 3.Tạo các VLAN10, VLAN11, VLAN12
```
Switch>enable
Switch#configure terminal

Switch(config)#vlan 10
Switch(config-vlan)#name VLAN10
Switch(config-vlan)#exit

Switch(config)#vlan 11
Switch(config-vlan)#name VLAN11
Switch(config-vlan)#exit

Switch(config)#vlan 12
Switch(config-vlan)#name VLAN12
Switch(config-vlan)#exit
```
Kiểm tra các port gán đúng vlan chưa
```
Switch#show vlan
```
![](/ChienNX/01.CCNA/4.VLAN/Img/active.png)
### 4.Gán các port vào VLAN đã định trước
```
Switch>enable
Switch#configure terminal

Switch(config)#interface fastEthernet 0/1
Switch(config-if)#switchport access vlan 10
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/2
Switch(config-if)#switchport access vlan 10
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/11
Switch(config-if)#switchport access vlan 11
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/12
Switch(config-if)#switchport access vlan 11
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/21
Switch(config-if)#switchport access vlan 12
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/22
Switch(config-if)#switchport access vlan 12
Switch(config-if)#end
```

### 5.Kiểm tra các port gán đúng vlan chưa
```
Switch#show vlan
```
![](/ChienNX/01.CCNA/4.VLAN/Img/Taovlan.png)

### 6.Kiểm tra ping từ các PC trong cùng VLAN -> OK

1. Chọn từng PC → Desktop → IP Configuration
2. Nhập thông tin IP tĩnh theo VLAN tương ứng.

**Cấu hình chi tiết từng thiết bị:**

- PC-1:
  - IP Address: 10.10.10.11
  - Subnet Mask: 255.255.255.0
  - Default Gateway: (Bỏ trống nếu không có Router)
- Các PC khác làm tương tự.
- Nếu kết nối vẫn đỏ thì chọn vào Physical tắt nguồn pc bằng nút 'đỏ' sau đó tháo WMP300N thay bằng PT-HOST-NM-1CE hoặc thay bằng PT-HOST-NM-1CFE kéo bằng con trỏ chuột để kết nối sang Ethernet

**Thực hiện ping:**

1. Chọn PC muốn kiểm tra kết nối: Nhấn vào PC-1 hoặc PC khác trong sơ đồ.
2. Mở công cụ "Command Prompt": Vào tab Desktop → Chọn Command Prompt.
3. Thực hiện lệnh ping:

```plaintext
ping [địa_chỉ_IP]
```

![](/ChienNX/01.CCNA/4.VLAN/Img/pingok.png)

###  7.Ping giữa các VLAN khác nhau -> Không ping được.

- Từ PC-1 ping đến PC khác. nếu cùng vlan sẽ trả về `reply`, khác vlan trả về `Request time out`.
  
![](/ChienNX/01.CCNA/4.VLAN/Img/pingchuaok.png)