# Các thiết bị mạng 

## 1.Modem
![Modem](/ChienNX/01.CCNA/VLAN/Img/Modem.png)

Khái niệm: Modem (Modulator - Demodulator) là một thiết bị mạng dùng để kết nối với nhà cung cấp dịch vụ Internet (ISP), giúp chuyển đổi tín hiệu số thành tín hiệu analog (hoặc ngược lại) để truyền dữ liệu qua các phương tiện truyền dẫn như cáp quang, ADSL, cáp đồng trục hoặc 4G/5G.
### Chức năng của Modem:
 - Kết nối internet: Modem là cầu nối thiết yếu để bạn truy cập internet. Nó cho phép bạn gửi và nhận email, duyệt web, xem video, chơi game trực tuyến và thực hiện nhiều hoạt động khác trên mạng.
 - Chuyển đổi tín hiệu: Modem thực hiện việc chuyển đổi tín hiệu kỹ thuật số từ máy tính thành tín hiệu analog tương thích với đường truyền internet và ngược lại.
 - Phân chia tín hiệu: Một số modem có khả năng chia sẻ kết nối internet cho nhiều thiết bị cùng lúc thông qua cổng Ethernet hoặc Wi-Fi.
### Ưu nhược điểm của Modem:
1. Ưu điểm:
 - Kết nối internet: Modem giúp bạn truy cập internet một cách dễ dàng và nhanh chóng, mở ra cánh cửa đến kho tàng thông tin và giải trí khổng lồ.
 - Truyền tải dữ liệu: Modem cho phép bạn gửi và nhận dữ liệu qua mạng internet, phục vụ cho công việc, học tập và giải trí.
- Chia sẻ kết nối: Một số modem có thể chia sẻ kết nối internet cho nhiều thiết bị cùng lúc, giúp tiết kiệm chi phí và tối ưu hóa hiệu quả sử dụng.
- Dễ dàng cài đặt: Hầu hết modem đều được thiết kế đơn giản, dễ dàng cài đặt và sử dụng, ngay cả với những người không rành về công nghệ.
Giá thành đa dạng: Modem có nhiều mức giá khác nhau, phù hợp với nhu cầu và khả năng tài chính của nhiều đối tượng người dùng.
2. Nhược điểm: 
- Tốc độ: Tốc độ truy cập internet của modem phụ thuộc vào loại kết nối internet (ADSL, cáp quang, 4G/5G) và gói cước mà bạn sử dụng. Một số modem đời cũ không đáp ứng được nhu cầu sử dụng internet tốc độ cao của người dùng.
- Bảo mật: Modem thường là mục tiêu tấn công của tin tặc, dẫn đến nguy cơ đánh cắp thông tin cá nhân và dữ liệu. Do đó, cần chú ý bảo mật modem bằng cách cập nhật phần mềm thường xuyên và sử dụng mật khẩu mạnh.
- Khả năng tương thích: Một số modem không tương thích với các thiết bị hoặc dịch vụ internet nhất định. Do đó bạn cần kiểm tra kỹ thông số kỹ thuật của modem trước khi mua.
- Một số sự cố: Modem sẽ dễ gặp sự cố do nhiều nguyên nhân như lỗi phần mềm, hư hỏng phần cứng hoặc do nhà cung cấp dịch vụ internet nếu không được sử dụng đúng cách nên người dùng cần lưu ý.

## 2.Router (Bộ định tuyến)
![Modem](/ChienNX/01.CCNA/VLAN/Img/router.png)

Khái niệm: Router là thiết bị mạng hoạt động ở Layer 3 (Network Layer) của mô hình OSI. Nó chịu trách nhiệm định tuyến gói tin giữa các mạng khác nhau.
### Chức năng của Modem:
 - Định tuyến: Xác định đường đi tối ưu cho các gói tin dựa trên địa chỉ IP. Định tuyến gói tin từ nguồn đến đích bằng cách sử dụng bảng định tuyến (Routing Table).
 - Kết nối nhiều mạng khác nhau (LAN → WAN, LAN → Internet).
 - Chuyển đổi địa chỉ IP (NAT) để cho phép nhiều thiết bị trong mạng nội bộ truy cập Internet.
 - Quản lý lưu lượng: Kiểm soát và quản lý lưu lượng mạng.
 - Bảo mật: Cung cấp các tính năng bảo mật như firewall, VPN.
### Ưu nhược điểm của Router:
1. Ưu điểm:
 - Giúp giảm lưu lượng mạng.
 - Giúp chia sẻ Wi-Fi và kết nối mạng với nhiều thiết bị.
- Phân phối các gói dữ liệu để giảm tải dữ liệu.
- Cung cấp kết nối giữa các kiến trúc mạng khác nhau.
2. Nhược điểm: 
- Tốc độ kết nối mạng bị giảm khi có nhiều thiết bị cùng kết nối.
- Cần có modem thì mới chia sẻ được Wi-Fi.

## 3.Switch (L2 & L3)
![Switch (L2 & L3)](/ChienNX/01.CCNA/VLAN/Img/Switch%20(L2%20&%20L3).png)

Khái niệm: Switch là một thiết bị mạng hoạt động chủ yếu ở Layer 2 (Data Link Layer) nhưng cũng có Switch Layer 3 có thể hoạt động ở Layer 3 (Network Layer). Switch có chức năng chính là chuyển mạch (switching) các gói tin trong cùng một mạng LAN.

**Switch Layer 2 (L2 Switch):**

- Kết nối các thiết bị trong cùng một mạng LAN.
- Dùng địa chỉ MAC để chuyển tiếp gói tin.
- Hỗ trợ VLAN để phân chia mạng thành nhiều nhóm logic.
- Các tính năng cơ bản: STP (Spanning Tree Protocol), VLAN Trunking, MAC Address Table.

**Switch Layer 3 (L3 Switch):**

- Kết hợp chức năng của Switch L2 + Router.
- Có thể định tuyến giữa các VLAN (Inter-VLAN Routing) mà không cần router.
- Hỗ trợ giao thức định tuyến: OSPF, EIGRP, RIP.
- Tốc độ nhanh hơn router vì xử lý ở phần cứng thay vì phần mềm.

Switch L2: Chuyển mạch dựa trên địa chỉ MAC, dùng trong mạng LAN.
Switch L3: Có thể định tuyến giữa các VLAN, thay thế router trong một số trường hợp.
### Ưu nhược điểm của Switch:
Dựa trên nguồn tài liệu bạn cung cấp, dưới đây là chi tiết về các ưu điểm và nhược điểm của thiết bị Switch trong hệ thống mạng:

1. Ưu điểm của Switch
Việc sử dụng Switch mang lại nhiều lợi ích vượt trội so với các thiết bị kết nối truyền thống như Hub:

*   **Hiệu suất truyền tải cao:** Khác với Hub gửi dữ liệu đến tất cả các cổng, Switch chỉ gửi dữ liệu đến đúng thiết bị đích dựa trên địa chỉ MAC, giúp **giảm thiểu xung đột và tối ưu hóa băng thông**.
*   **Hỗ trợ tăng băng thông đáng kể:** Switch cho phép truyền tải dữ liệu đồng thời qua nhiều cổng khác nhau, giúp giảm độ trễ. Các dòng Switch hiện đại còn hỗ trợ các chuẩn tốc độ cực cao như **10G, 40G hoặc lên đến 100G** cho các trung tâm dữ liệu.
*   **Quản lý và bảo mật linh hoạt:** Các loại Switch quản lý (Managed Switch) cho phép quản trị viên thiết lập **VLAN, QoS, và các chính sách bảo mật như ACL hay Port Security** để kiểm soát truy cập và bảo vệ dữ liệu.
*   **Khả năng mở rộng mạnh mẽ:** Switch hỗ trợ việc thêm cổng, tích hợp các mô-đun quang và các tính năng như **Stack hoặc Chaining** để kết hợp nhiều thiết bị thành một hệ thống thống nhất, giúp tiết kiệm chi phí nâng cấp.
*   **Hỗ trợ công nghệ PoE:** Nhiều loại Switch tích hợp khả năng **cấp nguồn qua cáp Ethernet (PoE)**, giúp triển khai các thiết bị như camera IP, điện thoại VoIP hay thiết bị IoT một cách linh hoạt mà không cần đi dây điện rườm rà.
  

 2. Nhược điểm của Switch
Mặc dù có nhiều lợi ích, Switch cũng tồn tại một số hạn chế cần lưu ý:

*   **Chi phí đầu tư và vận hành lớn:** Các dòng Switch quản lý cao cấp thường có **giá thành đắt hơn nhiều** so với Switch không quản lý (Unmanaged). Ngoài ra, doanh nghiệp còn tốn chi phí cho việc đào tạo nhân sự và bảo trì phần mềm.
*   **Yêu cầu kỹ năng cấu hình chính xác:** Để Switch hoạt động hiệu quả, người quản trị cần có kiến thức vững chắc. Việc **cấu hình sai có thể dẫn đến nghẽn mạng**, giảm hiệu suất hoặc tạo ra các lỗ hổng bảo mật.
*   **Nguy cơ lộ thông tin khi bị tấn công:** Do có các giao diện quản lý từ xa, Switch có thể trở thành mục tiêu của các cuộc tấn công mạng như **xâm nhập đánh cắp dữ liệu hoặc cài malware** nếu không được bảo mật bằng mã hóa và tường lửa phù hợp.

## 4.Firewall (Tường lửa)
![Modem](/ChienNX/01.CCNA/VLAN/Img/tuonglua.png)

Khái niệm: Firewall là một thiết bị hoặc phần mềm bảo mật mạng hoạt động chủ yếu ở Layer 3 & 4 (Network & Transport Layer) nhưng cũng có thể kiểm soát Layer 7 (Application Layer), có chức năng kiểm soát lưu lượng mạng dựa trên các quy tắc được định nghĩa.
### Chức năng của Firewall:
 - Kiểm soát truy cập: Cho phép hoặc chặn lưu lượng dựa trên địa chỉ IP, cổng, giao thức.
 - Ngăn chặn tấn công: Phát hiện và ngăn chặn các tấn công từ bên ngoài.
 - Bảo vệ dữ liệu: Bảo vệ dữ liệu khỏi các truy cập trái phép.
### Ưu nhược điểm của Firewall:
1. Ưu điểm:
 - Kiểm soát lưu lượng truy cập: Giám sát và lọc tất cả dữ liệu ra vào mạng dựa trên các quy tắc bảo mật đã thiết lập, ngăn chặn các truy cập trái phép.
 - Ngăn chặn các cuộc tấn công mạng: Giúp bảo vệ hệ thống khỏi các mối đe dọa như hacker, virus, và các phần mềm độc hại từ môi trường Internet không tin cậy.
- Bảo vệ quyền riêng tư: Bằng cách che giấu các địa chỉ IP nội bộ và cấu trúc mạng bên trong, tường lửa giúp ngăn chặn việc thu thập thông tin nhạy cảm của tổ chức.
- Ghi nhật ký và giám sát (Logging): Cho phép quản trị viên theo dõi các nỗ lực truy cập bất thường để kịp thời xử lý sự cố.
2. Nhược điểm: 
- Ảnh hưởng đến hiệu suất mạng: Việc kiểm tra và sàng lọc từng gói tin có thể gây ra độ trễ (latency), làm giảm tốc độ truyền tải dữ liệu, đặc biệt là với các dòng tường lửa cũ hoặc cấu hình quá phức tạp.
- Chi phí đầu tư và vận hành: Các thiết bị tường lửa chuyên dụng (Next-Generation Firewall) thường có giá thành cao và yêu cầu chi phí bản quyền phần mềm định kỳ.
- Độ phức tạp trong cấu hình: Việc thiết lập quy tắc (rules) sai có thể dẫn đến việc chặn nhầm các dịch vụ cần thiết hoặc vô tình tạo ra các lỗ hổng bảo mật.
- Không thể bảo vệ tuyệt đối: Tường lửa không thể ngăn chặn các cuộc tấn công từ bên trong mạng nội bộ, các cuộc tấn công qua kỹ thuật xã hội (social engineering), hoặc các mối đe dọa ẩn trong các luồng dữ liệu đã được mã hóa nếu không có tính năng giải mã.
### 5.Hub (Bộ tập trung)

![hub](/ChienNX/01.CCNA/VLAN/Img/hub.png)

Khái niệm: Hub là một thiết bị mạng đơn giản, hoạt động ở Layer 1 (Physical Layer), có chức năng chia sẻ kết nối mạng.

### Chức năng của Hub:

- Chia sẻ kết nối: Mở rộng mạng bằng cách chia sẻ một cổng mạng thành nhiều cổng.
- Broadcast: Gửi dữ liệu đến tất cả các cổng.

### Nhược điểm:

- Khi nhận được dữ liệu, Hub phát (broadcast) ra tất cả các cổng, gây xung đột dữ liệu và giảm hiệu suất mạng.
- Bảo mật kém: Dữ liệu có thể bị nghe lén.
- Không thể học địa chỉ MAC như Switch.
