# Bài tập
# Cho biết địa chỉ nào sau đây có thể dùng cho host:

|Địa chỉ|Trả lời|Giải thích|
|:---|:---|:---|
|150.100.255.255|Không|Vì nó là broadcast toàn bộ phần host là 1|
| 175.100.255.18|Có|Vì nó thuộc lớp B 128->191|
| 195.234.253.0|Không|Vì địa chỉ IP không được là mạng có phần host là 0|
| 100.0.0.23|Có|Vì nó thuộc lớp A 1->126|
| 188.258.221.176|Không|Giá trị octet không được >255|
| 127.34.25.189|Không|Vì nó thuộc dải loopback 127.0.0.0 - 127.255.255.255|
| 224.156.217.73|Không|Vì nó thuộc địa chỉ multicast (224.0.0.0 - 239.255.255.255)|

# 4.6.1. Cho mạng và số bit mượn. Giả sử có hỗ trợ subnet zero. Hãy xác định :
- Số subnet có thể có.
- Số host/subnet.
- Với mỗi subnet, hãy xác định: địa chỉ mạng, địa chỉ host đầu, địa chỉ host cuối,
địa chỉ broadcast (nếu số lượng mạng quá nhiều chỉ cần ghi ra một vài mạng đầu
và mạng cuối cùng), subnet mask và số prefix.
## 1. 192.168.2.0/24 mượn 5 bit.
 Số subnet có thể có: 2^5 = 32 subnet.

 Số host trên mỗi subnet 2^3 -2 = 6 (host/subnet).

 Số bước nhảy 2^3 = 8

|Stt subnet|Địa chỉ mạng|Địa chỉ host đầu|Địa chỉ broadcast|Địa chỉ host cuối|
|:---|:---|:---|:---|:---|
|Subnet 1|192.168.2.0|192.168.2.1|192.168.2.7|192.168.2.6|
|Subnet 2|192.168.2.8|192.168.2.9|192.168.2.15|192.168.2.14|    
|Subnet 3|192.168.2.16|192.168.2.17|192.162.2.23|192.168.2.22|   
|---|---|---|---|---|    
|Subnet 32|192.168.2.248|192.168.2.249|192.168.2.255|192.168.2.254|  

 Subnet mask 255.255.255.248 

 Số prefix 24 + 5 = 29 
## 2. 192.168.12.0/24 mượn 3 bit.
 Số subnet có thể có: 2^3 = 8 subnet.

 Số host trên mỗi subnet 2^5 -2 = 30(host/subnet).

 Số bước nhảy 2^5 = 32

|Stt subnet|Địa chỉ mạng|Địa chỉ host đầu|Địa chỉ broadcast|Địa chỉ host cuối|
|:---|:---|:---|:---|:---|
|Subnet 1|192.168.12.0|192.168.12.1|192.168.12.31|192.168.2.30|
|Subnet 2|192.168.12.32|192.168.12.33|192.168.12.63|192.168.12.62|    
|Subnet 3|192.168.12.64|192.168.12.65|192.168.12.127|192.168.12.126|   
|---|---|---|---|---|    
|Subnet 7|192.168.12.224|192.168.12.225|192.168.12.255|192.168.12.254|  

 Subnet mask 255.255.255.224 

 Số prefix 24 + 3 = 27 
## 3. 172.16.2.0/24 mượn 2 bit.
 Số subnet có thể có: 2^2 = 4 subnet.

 Số host trên mỗi subnet 2^6 -2 = 62(host/subnet).

 Số bước nhảy 2^6 = 64

|Stt subnet|Địa chỉ mạng|Địa chỉ host đầu|Địa chỉ broadcast|Địa chỉ host cuối|
|:---|:---|:---|:---|:---|
|Subnet 1|172.16.2.0|172.16.2.1|172.16.2.63|172.16.2.62|
|Subnet 2|172.16.2.64|172.16.2.65|172.16.2.127|172.16.2.126|    
|Subnet 3|172.16.2.128|172.16.2.129|172.16.2.191|172.16.2.190|   
|Subnet 4|172.16.2.192|172.16.2.193|172.16.2.255|172.16.2.254|  

 Subnet mask 255.255.255.192

 Số prefix 24 + 2 = 26 
