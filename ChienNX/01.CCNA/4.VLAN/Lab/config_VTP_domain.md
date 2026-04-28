## Cấu hình VTP domain
### Sơ đồ lab:
![](/ChienNX/01.CCNA/VLAN/Img/lab2.png)

**Quy hoạch VLAN:**
- VLAN10 : 192.168.10.0/24
- VLAN20 : 192.168.20.0/24

![](/ChienNX/01.CCNA/4.VLAN/Img/lab2.1.png)

**Quy hoạch IP và kết nối:**

![](/ChienNX/01.CCNA/4.VLAN/Img/lab2.2.png)

# Cấu hình VTP
## 1. Đặt IP cho các PC theo phân hoạch

- PC-1:
  - IP Address: 192.168.10.11
  - Subnet Mask: 255.255.255.0
  - Default Gateway: (Bỏ trống nếu không có Router)
- Các PC khác làm tương tự.
  
## 2. Thiết lập các VLAN trên 2 SW
### Trên SW 1
Đặt tên:
```
Switch>enable 
Switch#configure terminal 
Switch(config)#hostname SW1
SW1(config)#
```

Tạo 2 VLAN10 và VLAN20:
```
SW1(config)#vlan 10
SW1(config-vlan)#name VLAN10
SW1(config-vlan)#exit

SW1(config)#vlan 20
SW1(config-vlan)#name VLAN20
SW1(config-vlan)#exit

SW1(config)#
```

Gán các port vào đúng các VLAN định sẵn:
```
SW1(config)#interface fastEthernet 0/10
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface fastEthernet 0/11
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface fastEthernet 0/20
SW1(config-if)#switchport access vlan 20
SW1(config-if)#exit

SW1(config)#exit
```

Kiểm tra lại:

![](/ChienNX/01.CCNA/4.VLAN/Img/lab2.3.png)

### Trên SW2
Đặt tên:
```
Switch>enable 
Switch#configure terminal 
Switch(config)#hostname SW2
SW2(config)#
```

Tạo 2 VLAN10 và VLAN20:
```
SW2(config)#vlan 10
SW2(config-vlan)#name VLAN10
SW2(config-vlan)#exit

SW2(config)#vlan 20
SW2(config-vlan)#name VLAN20
SW2(config-vlan)#exit

SW2(config)#
```

Gán các port vào đúng các VLAN định sẵn:
```
SW2(config)#interface fastEthernet 0/10
SW2(config-if)#switchport access vlan 10
SW2(config-if)#exit

SW2(config)#interface fastEthernet 0/20
SW2(config-if)#switchport access vlan 20
SW2(config-if)#exit

SW2(config)#exit
```
- `interface fastEthernet 0/10`: Chọn cổng vật lý FastEthernet 0/10 để cấu hình.
- `switchport mode access`: Chuyển cổng sang chế độ Access (cổng này chỉ thuộc một VLAN duy nhất).
- `switchport access vlan 10`: Gán VLAN 10 cho cổng.
- `exit`: Thoát khỏi chế độ cấu hình cổng.

Kiểm tra lại:

![](/ChienNX/01.CCNA/4.VLAN/Img/lab2.3.png)

## 3. Cấu hình VTP
### Đặt IP cho các interface VLAN trên 2 SW
Đặt địa chỉ IP cho interface VLAN10 của SW1 là `192.168.10.1` và VLAN20 là `192.168.20.1`
```
SW1#configure terminal 
SW1(config)#interface vlan 10
SW1(config-if)#
SW1(config-if)#ip address 192.168.10.1 255.255.255.0
SW1(config-if)#no shutdown
SW1(config-if)#exit
SW1(config)#

SW1(config)#interface vlan 20
SW1(config-if)#ip address 192.168.20.1 255.255.255.0
SW1(config-if)#no shutdown 
SW1(config-if)#exit 

SW1(config)#exit
SW1#
```

Đặt địa chỉ IP cho interface VLAN10 của SW2 là `192.168.10.2` và VLAN20 là `192.168.20.2`
```
SW2#configure terminal 
SW2(config)#interface vlan 10
SW2(config-if)#
SW2(config-if)#ip address 192.168.10.2 255.255.255.0
SW2(config-if)#no shutdown
SW2(config-if)#exit
SW2(config)#

SW2(config)#interface vlan 20
SW2(config-if)#ip address 192.168.20.2 255.255.255.0
SW2(config-if)#no shutdown 
SW2(config-if)#exit 

SW2(config)#exit
SW2#
```

### Thiết lập VTP Server và VTP Client
Mặc định thì Catalyst switch sẽ được cấu hình làm VTP Server. Giờ ta sẽ thiết lập:

- Switch 1: VTP Server
- Switch 2: VTP CLient.

Ngoài ra, ta đặt 
- VTP domain : NH
- VTP password : nhanhoa2020.

#### Trên SW1
```
SW1>enable 
SW1#vlan database 
SW1(vlan)#vtp server
SW1(vlan)#vtp domain NH
SW1(vlan)#vtp password nhanhoa2020
SW1(vlan)#exit
```
- `vtp mode server`: Đặt switch ở chế độ VTP Server, có thể tạo, sửa, xóa VLAN và đồng bộ với các switch client.
- `vtp doamin NH`: Đặt tên miền VTP là NH. Các switch muốn đồng bộ phải cùng domain.
- `vtp password nhanhoa2020`: Thiết lập mật khẩu nhanhoa2020 để bảo vệ và đảm bảo chỉ các switch có cùng mật khẩu mới đồng bộ dữ liệu.
  
#### Trên SW2
```
SW2>enable 
SW2#vlan database 
SW2(vlan)#vtp client
SW2(vlan)#vtp domain NH
SW2(vlan)#vtp password nhanhoa2020
SW2(vlan)#exit
```

### Tạo đường trunk từ SW1 đến SW2
Ta sẽ bật trunking trên các port nối giữa 2 switch là `Fa0/1` trên **SW1** và `Fa0/1` trên **SW2**.

SW1
```
SW1#configure terminal 
SW1(config)#interface fastEthernet 0/1
SW1(config-if)#switchport mode trunk 
SW1(config-if)#end
SW1#
```

SW2
```
SW2#configure terminal 
SW2(config)#interface fastEthernet 0/1
SW2(config-if)#switchport mode trunk 
SW2(config-if)#end
SW2#
```

## 4. Các lệnh kiểm tra sau khi cấu hình xong

![](/ChienNX/01.CCNA/4.VLAN/Img/lab2.4.png)

```
SW# show vtp status

SW# show vtp password

SW# show vlan

SW# show interfaces trunk
```
