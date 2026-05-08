# TỔNG QUAN VỀ DNS

## I. DNS là gì?

**DNS (Domain Name System)** là hệ thống phân giải tên miền. DNS giúp chuyển đổi tên miền dễ nhớ thành địa chỉ IP để máy tính có thể kết nối đến đúng máy chủ.

Ví dụ:

```text
google.com  ->  142.250.72.14
cloud.test  ->  192.168.60.10
```

Con người dễ nhớ `google.com`, còn máy tính cần địa chỉ IP để giao tiếp. DNS chính là hệ thống đứng giữa để chuyển tên miền thành IP.

## II. Chức năng của DNS

### 1. Phân giải tên miền thành địa chỉ IP

Đây là chức năng quan trọng nhất của DNS.

Khi người dùng nhập một tên miền như `www.example.com`, DNS sẽ tìm địa chỉ IP tương ứng để trình duyệt có thể kết nối đến web server.

Ví dụ:

```text
www.example.com -> 93.184.216.34
```

### 2. Phân giải ngược

DNS cũng có thể phân giải ngược từ địa chỉ IP về tên miền.

Ví dụ:

```text
8.8.8.8 -> dns.google
```

Phân giải ngược thường dùng trong kiểm tra log, hệ thống email và bảo mật.

### 3. Lưu cache để tăng tốc độ truy cập

DNS có cơ chế lưu tạm kết quả truy vấn, gọi là **DNS Cache**.

Cache có thể nằm ở:

- Trình duyệt
- Hệ điều hành
- Router
- DNS Server của nhà mạng hoặc Public DNS

Nếu kết quả đã có trong cache, thiết bị không cần hỏi lại toàn bộ hệ thống DNS. Nhờ vậy việc truy cập website nhanh hơn.

### 4. Cân bằng tải

Một tên miền có thể trỏ đến nhiều địa chỉ IP khác nhau.

DNS có thể trả về IP khác nhau tùy theo:

- Vị trí địa lý của người dùng
- Tải của máy chủ
- Chính sách của hệ thống

Ví dụ: Người dùng ở Việt Nam có thể được trả về server gần Việt Nam hơn để truy cập nhanh hơn.

### 5. Cung cấp thông tin cho email và bảo mật

DNS không chỉ lưu IP. Nó còn lưu nhiều loại thông tin khác, ví dụ:

- Máy chủ nhận email của tên miền
- Bản ghi xác thực email
- Thông tin xác minh quyền sở hữu tên miền
- Chính sách bảo mật tên miền

## III. Các loại DNS thường gặp

### 1. ISP DNS

**ISP DNS** là DNS do nhà cung cấp Internet cấp cho người dùng.

Ví dụ nhà cung cấp:

- VNPT
- Viettel
- FPT
- CMC

Ưu điểm:

- Tự động có khi kết nối mạng
- Không cần cấu hình thủ công
- Thường gần người dùng trong hạ tầng nhà mạng

Nhược điểm:

- Tốc độ và độ ổn định phụ thuộc nhà mạng
- Nhà mạng có thể ghi log truy vấn DNS
- Một số website có thể bị chặn bằng DNS

### 2. Public DNS

**Public DNS** là DNS công cộng do các tổ chức lớn cung cấp cho mọi người dùng Internet.

Một số Public DNS phổ biến:

| Nhà cung cấp | DNS chính | DNS phụ |
| --- | --- | --- |
| Google DNS | `8.8.8.8` | `8.8.4.4` |
| Cloudflare DNS | `1.1.1.1` | `1.0.0.1` |
| OpenDNS | `208.67.222.222` | `208.67.220.220` |
| Quad9 | `9.9.9.9` | `149.112.112.112` |

Ưu điểm:

- Dễ dùng
- Tốc độ ổn định
- Có hệ thống cache lớn
- Một số dịch vụ hỗ trợ bảo mật như DNSSEC, DNS over HTTPS (DoH), DNS over TLS (DoT)

### 3. Private DNS

**Private DNS** là DNS dùng riêng trong một tổ chức hoặc mạng nội bộ.

Ví dụ trong công ty:

```text
server01.company.local -> 192.168.10.10
printer01.company.local -> 192.168.10.20
```

Private DNS giúp quản lý tên máy chủ, máy in, hệ thống nội bộ mà không cần public ra Internet.

### 4. So sánh ISP DNS, Public DNS và Private DNS

| Tiêu chí | ISP DNS | Public DNS | Private DNS |
| --- | --- | --- | --- |
| Đơn vị quản lý | Nhà mạng | Google, Cloudflare, OpenDNS, Quad9 | Doanh nghiệp hoặc cá nhân |
| Phạm vi dùng | Khách hàng của ISP | Mọi người dùng Internet | Mạng nội bộ |
| Cấu hình | Thường tự động | Cần cấu hình thủ công | Cần tự triển khai |
| Mục đích | Phân giải Internet cho thuê bao | Phân giải nhanh, ổn định, công cộng | Quản lý tên miền nội bộ |
| Kiểm soát | Phụ thuộc ISP | Phụ thuộc nhà cung cấp Public DNS | Tổ chức tự kiểm soát |
| Ví dụ | DNS của Viettel, VNPT, FPT | `8.8.8.8`, `1.1.1.1` | `dns.local`, `cloud.test` |

## IV. Các bản ghi DNS thường gặp

### 1. A Record

**A Record** dùng để trỏ tên miền về địa chỉ IPv4.

Ví dụ:

```text
example.com  IN  A  93.184.216.34
```

Khi truy cập `example.com`, DNS trả về IP `93.184.216.34`.

### 2. AAAA Record

**AAAA Record** giống A Record nhưng dùng cho địa chỉ IPv6.

Ví dụ:

```text
example.com  IN  AAAA  2606:2800:220:1:248:1893:25c8:1946
```

### 3. CNAME Record

**CNAME Record** dùng để tạo bí danh cho một tên miền khác.

Ví dụ:

```text
www.example.com  IN  CNAME  example.com
```

Nghĩa là `www.example.com` sẽ trỏ theo bản ghi của `example.com`.

### 4. MX Record

**MX Record** dùng để xác định mail server nhận email cho tên miền.

Ví dụ:

```text
example.com  IN  MX  10 mail1.example.com
example.com  IN  MX  20 mail2.example.com
```

Số `10` và `20` là độ ưu tiên. Số càng nhỏ thì ưu tiên càng cao.

### 5. TXT Record

**TXT Record** dùng để lưu dữ liệu dạng văn bản.

TXT thường dùng cho:

- Xác thực quyền sở hữu tên miền
- Cấu hình SPF, DKIM, DMARC cho email
- Lưu thông tin bảo mật hoặc thông tin tùy chỉnh

Ví dụ:

```text
example.com  IN  TXT  "v=spf1 include:_spf.google.com ~all"
```

### 6. NS Record

**NS Record** chỉ định DNS Server nào có quyền quản lý tên miền.

Ví dụ:

```text
example.com  IN  NS  ns1.cloudflare.com
example.com  IN  NS  ns2.cloudflare.com
```

### 7. SRV Record

**SRV Record** dùng để chỉ định máy chủ và cổng cho một dịch vụ cụ thể.

Ví dụ:

```text
_sip._tcp.example.com  IN  SRV  10 60 5060 sipserver.example.com
```

Ý nghĩa:

- `_sip`: tên dịch vụ
- `_tcp`: giao thức sử dụng
- `10`: độ ưu tiên
- `60`: trọng số
- `5060`: cổng dịch vụ
- `sipserver.example.com`: máy chủ cung cấp dịch vụ

### 8. CAA Record

**CAA Record** quy định tổ chức nào được phép cấp chứng chỉ SSL/TLS cho tên miền.

Ví dụ:

```text
example.com  IN  CAA  0 issue "letsencrypt.org"
```

Nghĩa là Let's Encrypt được phép cấp chứng chỉ cho `example.com`.

## V. Hệ thống phân cấp DNS

DNS hoạt động theo mô hình phân cấp. Khi cần tìm IP của một tên miền, truy vấn có thể đi qua nhiều cấp DNS khác nhau.

### 1. Recursive DNS Server

**Recursive DNS Server** là máy chủ DNS nhận yêu cầu từ client và đi hỏi các DNS Server khác để tìm câu trả lời.

Ví dụ:

- `8.8.8.8` của Google
- `1.1.1.1` của Cloudflare
- DNS của VNPT, Viettel, FPT

Recursive DNS Server thường lưu cache để trả lời nhanh hơn cho các lần truy vấn sau.

### 2. Root DNS Server

**Root DNS Server** là cấp cao nhất trong hệ thống DNS.

Root Server không lưu IP của từng website cụ thể. Nó chỉ biết DNS Server nào quản lý các đuôi miền cấp cao như `.com`, `.vn`, `.org`.

Ví dụ: Nếu cần tìm `www.example.com`, Root Server sẽ chỉ về TLD Server của `.com`.

### 3. TLD DNS Server

**TLD DNS Server** quản lý các đuôi miền cấp cao.

Ví dụ:

- `.com`
- `.vn`
- `.edu`
- `.org`

TLD Server không trả IP cuối cùng của website. Nó cho biết Authoritative DNS Server nào đang quản lý domain đó.

### 4. Authoritative DNS Server

**Authoritative DNS Server** là DNS Server có thẩm quyền, chứa bản ghi chính thức của tên miền.

Ví dụ: Nếu `example.com` dùng Cloudflare, thì DNS của Cloudflare có thể là Authoritative DNS Server cho domain đó.

Authoritative DNS Server trả về câu trả lời cuối cùng, ví dụ:

```text
www.example.com -> 217.64.213.12
```

### 5. Caching DNS Server

**Caching DNS Server** lưu tạm kết quả truy vấn DNS để dùng lại.

Mỗi bản ghi DNS có thời gian sống gọi là **TTL (Time To Live)**. Khi TTL hết hạn, cache phải hỏi lại DNS Server có thẩm quyền để lấy dữ liệu mới.

## VI. Cách DNS hoạt động

Ví dụ người dùng truy cập:

```text
www.example.com
```

Quá trình phân giải DNS diễn ra như sau:

### Bước 1: Client kiểm tra dữ liệu cục bộ

Máy người dùng kiểm tra theo thứ tự:

1. File hosts
2. DNS cache trên máy
3. DNS Server đã cấu hình

Nếu chưa có kết quả, máy sẽ gửi truy vấn đến Recursive DNS Server.

### Bước 2: Recursive DNS Server kiểm tra cache

Recursive DNS Server kiểm tra xem nó đã có kết quả trong cache chưa.

Nếu có, nó trả lời ngay cho client.

Nếu chưa có, nó tiếp tục hỏi hệ thống DNS phân cấp.

### Bước 3: Hỏi Root DNS Server

Recursive DNS Server hỏi Root Server:

```text
IP của www.example.com là gì?
```

Root Server không trả IP cuối cùng, mà trả lời:

```text
Hãy hỏi TLD Server của .com
```

### Bước 4: Hỏi TLD DNS Server

Recursive DNS Server hỏi TLD Server `.com`.

TLD Server trả lời:

```text
Domain example.com được quản lý bởi Authoritative DNS Server này.
```

### Bước 5: Hỏi Authoritative DNS Server

Recursive DNS Server hỏi Authoritative DNS Server của `example.com`.

Authoritative DNS Server trả lời:

```text
www.example.com có IP là 217.64.213.12
```

### Bước 6: Trả kết quả về client

Recursive DNS Server:

- Lưu kết quả vào cache
- Trả IP về cho máy người dùng

Sau đó trình duyệt dùng IP này để kết nối đến web server qua HTTP hoặc HTTPS.

## VII. Cách đổi DNS Server trên Windows

Có thể đổi DNS mặc định của nhà mạng sang Public DNS như Google DNS hoặc Cloudflare DNS.

Ví dụ DNS phổ biến:

```text
Google DNS:      8.8.8.8, 8.8.4.4
Cloudflare DNS:  1.1.1.1, 1.0.0.1
```

Các bước trên Windows:

1. Nhấn `Win + R`.
2. Gõ `ncpa.cpl`, rồi nhấn `Enter`.
3. Chuột phải vào card mạng đang dùng, chọn `Properties`.
4. Chọn `Internet Protocol Version 4 (TCP/IPv4)`.
5. Nhấn `Properties`.
6. Chọn `Use the following DNS server addresses`.
7. Nhập DNS muốn dùng, ví dụ:

```text
Preferred DNS server: 8.8.8.8
Alternate DNS server: 8.8.4.4
```

8. Nhấn `OK` để lưu.

## VIII. Cách đổi DNS Server trên macOS

Các bước trên macOS:

1. Mở `System Settings` hoặc `System Preferences`.
2. Chọn `Network`.
3. Chọn kết nối đang dùng, ví dụ Wi-Fi hoặc Ethernet.
4. Chọn `Details` hoặc `Advanced`.
5. Mở tab `DNS`.
6. Nhấn dấu `+` để thêm DNS mới.
7. Nhập DNS, ví dụ:

```text
1.1.1.1
1.0.0.1
```

8. Nhấn `OK`, sau đó nhấn `Apply`.

## IX. Tóm tắt dễ nhớ

DNS là hệ thống chuyển tên miền thành địa chỉ IP.

Cần nhớ các ý chính:

- `A`: trỏ tên miền về IPv4.
- `AAAA`: trỏ tên miền về IPv6.
- `CNAME`: tạo bí danh cho tên miền khác.
- `MX`: chỉ định mail server.
- `TXT`: lưu thông tin xác thực hoặc văn bản.
- `NS`: chỉ định name server quản lý domain.
- `SRV`: chỉ định dịch vụ, port và server.
- `CAA`: quy định CA nào được cấp chứng chỉ SSL/TLS.

Quy trình DNS cơ bản:

```text
Client -> Recursive DNS -> Root DNS -> TLD DNS -> Authoritative DNS -> IP trả về Client
```
