# Tìm hiểu về IPv4
## 1. IPv4 là gì?:
 IPv4 (Internet Protocol Version 4) là giao thức Internet thế hệ thứ tư, hệ thống địa chỉ phổ biến nhất hiện nay nhằm định danh và kết nối các thiết bị mạng. Sử dụng 32-bit, tạo ra khoảng 4,3 tỷ địa chỉ độc nhất. IPv4 đang dần bị thay thế bởi IPv6 do giới hạn về số lượng địa chỉ.
 
## 2. Tại sao lại không có IPv1,v2,v3,v5:

 IPv1,2,3 là những bản sơ khai trong giai đoạn từ 1973 đến 1978 lúc này TCP(giao thức vận chuyển) và IP(Giao thức internet) chưa tách rời và gộp chung thành một khối và IPv4 họ đã quyết định tách riêng TCP và IP ra riêng biệt. 

 IPv5 thực ra nó là giao thức hoàn toàn khác biệt tên là ST ( Internet Stream Protocol). Được phát triển vào cuối những năm 1970, IPv5 được thiết kế chuyên biệt để truyền tải video và giọng nói theo thời gian thực. Dù hoạt động khá tốt nhưng nó lại sử dụng 32-bit y hệt với IPv4 nó không giải quyết được vấn đề cạn kiệt IP nên chỉ dùng lại ở mức thử nhiệm.

## 3. Cấu trúc và thành phần của IPv4:

 IPv4 là một chuỗi 32-bit,biểu diễn dưới dạng 4 số nguyên phân cách nhau bởi dấu chấm. Mỗi phần tử được gọi là octet, có độ dài 8 bit có giá trị từ 1->255. 
 
 Mỗi địa chỉ IPv4 bao gồm 2 phần chính: 
 + Định danh mạng (Network identifier): Xác định mạng mà thiết bị đang kết nối.
 + Định danh máy chủ (Host identifier): Xác định thiết bị cụ thể trong mạng đó

 ![Cấu trúc IPv4](/ChienNX/01.CCNA/IPv4/Img/cautruc.png)

## 4. Các lớp của IPv4:
![Lớp IPv4](/ChienNX/01.CCNA/IPv4/Img/lop.png)

IPv4 được phân thành năm lớp chính: A, B, C, D, và E. Mỗi lớp chứa một dải địa chỉ IP hợp lệ.
|Lớp |Phạm vi giá trị(Thập Phân)|Octet đầu(Nhị phân)| Số bit cho mạng|Mục đích sử dụng chính|
|:---|:---|:---|:---|:---|
|A |1-126|0xxxxxxx| 8 bit mạng, 24 bit host|Dành cho các tổ chức cực lớn, các ISP toàn cầu hoặc tập đoàn đa quốc gia.|
|B |128 – 191|10xxxxxx| 16 bit mạng, 16 bit host|Dành cho doanh nghiệp lớn, trường đại học hoặc tổ chức có quy mô vừa đến lớn.|
|C |192 – 223|110xxxxx| 24 bit mạng, 8 bit host|Dành cho mạng nội bộ (LAN), văn phòng nhỏ, hộ gia đình (phổ biến nhất).|
|D |224 – 239|1110xxxx| Không chia mạng/host|Dùng cho Multicast (truyền tin nhóm như stream video, hội nghị trực tuyến).|
|E |240 – 255|1111xxxx| Không chia mạng/host|Dùng cho thực nghiệm, nghiên cứu hoặc dự phòng cho tương lai.|

## 5. Phân biệt IP Public và IP Private:

|Đặc điểm|IP Public|IP Private|
|:---|:---|:---|
|Tính duy nhất|Duy nhất trên toàn cầu|Duy nhất trong nội bộ,có thể trùng giữa các mạng khác với nhau|
|Người cấp|Nhà cung cấp dịch vụ Internet (ISP)|Bộ định tuyến (Router)|
|Khả năng truy cập|Truy cập trực tiếp từ Internet|Không thể truy cập trực tiếp từ Internet|
|Chi phí|Thường mất phí (IP tĩnh/động)|Miễn phí|

Dải địa chỉ private (được quy định trong RFC 1918):
 Lớp A: 10.x.x.x
 Lớp B: 172.16.x.x -> 172.31.x.x
 Lớp C: 192.168.x.x

## 6.Cách chia địa chỉ IPv4:
Chia địa chỉ IPv4 (32-bit) bao gồm việc phân chia thành 4 octet (mỗi octet 8 bit), biểu diễn dưới dạng thập phân. Địa chỉ gồm hai phần: phần mạng (network) và phần host, được xác định bởi Subnet Mask. Quy trình chia subnet bao gồm xác định số mạng con cần thiết, tính toán số bit mượn, cập nhật Subnet Mask, và xác định dải IP hợp lệ cho từng mạng.

## 7.Phân biệt multicast và broadcast:

|Đặc điểm so sánh|Multicast|Broadcast|
|:---|:---|:---|
|Định nghĩa|Một nguồn độc lập sẽ gửi một dữ liệu giống nhau cho hàng loạt người nhận ở cùng một thời điểm.|Một nguồn độc lập gửi dữ liệu cho tất cả đích đến.|
|Cách thức tương tác|Tương tác diễn ra giữa một người gửi và rất nhiều người nhận cùng lúc.|Tương tác diễn ra giữa một người gửi và tất cả người nhận khả dụng.|
|Cách thức hoạt động|Dữ liệu được luân chuyển khi nhận yêu cầu từ những người nhận cùng lúc. |Dữ liệu được luân chuyển cho tất cả người nhận bất kể có nhận được yêu cầu hay không.|
|Độ bảo mật|Có độ bảo mật cao vì dữ liệu được gửi đến một nhóm người nhận nhất định|Độ bảo mật thấp do dữ liệu được gửi đến tất cả thiết bị trong mạng lưới|
|Độ trễ|Có độ trễ trung bình|Có độ trễ cao|
## 8.Tìm hiểu các khái niệm: subnet, subnet mask, prefix:

 Subnet là một phương pháp chia mạng lớn thành mạng nhỏ, dễ quản lí hơn gọi là mạng con.

 Subnet mask là các mạng con thường được biểu thị dưới dạng một dãy số thập phân chia bởi dấu chấm (Ví dụ: 255.255.255.0), là một thành phần quan trọng trong địa chỉ IP. Nó được sử dụng để xác định phần nào của địa chỉ IP đại diện cho mạng và phần nào đại diện cho máy tính cá nhân hoặc thiết bị của mạng đó. Trong một subnet mark phần của địa chỉ IP được biểu diễn các bit 1 chỉ ra trong địa chỉ mạng, trong khi đó bit 0 chỉ ra phần địa chỉ máy tính hoặc thiết bị.

 Số prefix: Để mô tả một địa chỉ IP, người ta dùng một đại lượng khác được gọi là số prefix. Số prefix có thể hiểu một cách đơn giản là số bit mạng trong một địa chỉ IP, được viết ngay sau địa chỉ IP, và được ngăn cách với địa chỉ này bằng một dấu “/”.