# Tìm hiểu VLAN
## 1.Tại sao cần chia VLAN

![Vlan](/ChienNX/01.CCNA/VLAN/Img/chiavlan.png)

*   **Tăng cường tính bảo mật:** VLAN cho phép **tách biệt các nhóm người dùng** và ngăn chặn sự truy cập trái phép vào các tài nguyên nhạy cảm. Các thiết bị ở các VLAN khác nhau không thể giao tiếp trực tiếp với nhau nếu không có thiết bị định tuyến, giúp bảo vệ thông tin nội bộ của các phòng ban như kế toán hay nhân sự khỏi các phòng ban khác.
*   **Cải thiện hiệu suất mạng:** Kỹ thuật này giúp chia nhỏ mạng LAN thành các **miền quảng bá (broadcast domain) riêng biệt**. Điều này giúp giảm thiểu lưu lượng quảng bá không cần thiết, giải quyết vấn đề tắc nghẽn, từ đó tối ưu hóa băng thông và tăng tốc độ truy cập cho hệ thống.
*   **Linh hoạt trong quản lý:** Quản trị viên có thể nhóm các thiết bị dựa trên **chức năng, bộ phận hoặc ứng dụng** thay vì vị trí địa lý. Bạn có thể dễ dàng thêm, xóa hoặc di chuyển các máy tính trong mạng chỉ bằng cách thay đổi cấu hình phần mềm mà không cần tác động đến hạ tầng cáp vật lý.
*   **Tiết kiệm chi phí đầu tư:** VLAN cho phép tạo ra nhiều mạng logic trên cùng một hạ tầng vật lý có sẵn. Doanh nghiệp **không cần mua thêm các thiết bị phần cứng** hay lắp đặt thêm hệ thống cáp riêng biệt cho từng mạng LAN khác nhau, giúp tối ưu hóa chi phí thiết bị.
*   **Giảm độ phức tạp của hệ thống:** Khi một hệ thống mạng LAN có **vượt quá 200 thiết bị**, việc quản lý trở nên khó khăn. Chia VLAN giúp phân đoạn mạng để quản trị viên dễ dàng theo dõi và xử lý sự cố cho từng nhóm thiết bị riêng biệt.

## 2.Khái niệm, cách hoạt động VLAN

### Khái niệm:

- LAN là một mạng cục bộ (Viết tắt của Local Area Network), được định nghĩa là tất cả các máy tính trong cùng một miền quảng bá(broadcast domain).
- Broadcast domain là phạm vi trong nhà mạng mà một gói tin Broadcast gửi ra sẽ tới được tất cả thiết bị trong phạm vi đó.
- Các Router (bộ định tuyến chặn tin broadcast) trong khi các switch chỉ chuyển tiếp chúng.

![Vlan](/ChienNX/01.CCNA/VLAN/Img/vlan.png)
 
- VLAN (Virtual Local Area Network) là một kỹ thuật cho phép chia một mạng LAN vật lý thành các mạng logic riêng biệt, được gọi là các VLAN. Chúng hoạt động độc lập với nhau, ngay cả khi các thiết bị được kết nối vào cùng một switch (bộ chuyển mạch).

### Phân loại VLAN:
![Vlan](/ChienNX/01.CCNA/VLAN/Img/loaivlan.png)

 VLAN sẽ được chia thành 3 loại gồm:

 - VLAN dựa vào mỗi cổng riêng biệt: cứ một cổng Ethernet sẽ được gắn cho một VLAN nên mỗi máy tính gắn với một cổng của switch đã được định danh tại VLAN gốc của nó.

- VLAN dựa vào địa chỉ MAC: cứ mỗi một địa chỉ MAC xuất hiện, chúng đều sẽ được gắn cho một VLAN nhất định.

- VLAN dựa vào giao thức kết nối: tương tự như địa chỉ MAC nhưng chỉ khác ở chỗ là sử dụng địa chỉ IP để định danh.

 ### cách hoạt động VLAN:

 ![Vlan](/ChienNX/01.CCNA/VLAN/Img/hoatdong.png)

*   **Xác định bằng VLAN ID:** Mỗi mạng VLAN được định danh trên các switch bằng một chỉ số gọi là **VLAN ID**. Mỗi cổng (port) trên switch sẽ được gán cho một hoặc nhiều VLAN ID cụ thể; nếu không được chỉ định, cổng đó sẽ thuộc về một VLAN mặc định.
*   **Cơ chế gắn thẻ (Tagging):**
    *   Chỉ số VLAN ID được dịch sang một **thẻ (tag) 12 bit**, cho phép thiết lập tối đa **4.096 VLAN** trên mỗi miền chuyển mạch.
    *   Việc gắn thẻ tuân theo tiêu chuẩn **IEEE 802.1Q**, trong đó switch sẽ thêm thẻ VLAN vào khung Ethernet.
    *   Đối với **VLAN tĩnh**, switch chèn thẻ liên kết với ID của cổng nhập; đối với **VLAN động**, thẻ được chèn dựa trên ID của thiết bị hoặc loại lưu lượng mà nó tạo ra.
*   **Chuyển tiếp và cách ly dữ liệu:** 
    *   Các khung Ethernet đã gắn thẻ sẽ được switch chuyển tiếp dựa trên địa chỉ MAC đích, nhưng **chỉ chuyển đến các cổng có cùng liên kết VLAN**.
    *   Toàn bộ lưu lượng quảng bá (broadcast), unicast và multicast đều bị giới hạn trong phạm vi các cổng thuộc cùng một VLAN đó.
    *   Điều này giúp mỗi VLAN cung cấp quyền truy cập dữ liệu riêng biệt cho các thiết bị kết nối với cổng tương ứng, giúp sử dụng tài nguyên hiệu quả và bảo mật hơn.
*   **Hoạt động trên đường trung kế (Trunk):**
    *   Các **đường Trunk** kết nối giữa các switch có khả năng nhận biết những VLAN nào đang trải dài trên hệ thống.
    *   Khi khung dữ liệu đi đến switch đích, **thẻ VLAN sẽ bị xóa bỏ** trước khi khung được truyền tới máy tính nhận cuối cùng.
*   **Ngăn chặn vòng lặp:** Mỗi VLAN sẽ chạy một giao thức **STP (Spanning Tree Protocol)** riêng biệt để ngăn chặn hiện tượng lặp vòng (loop) dữ liệu trong mạng lớp 2. Nếu cấu trúc của nhiều VLAN giống nhau, có thể sử dụng STP đa trường hợp để giảm chi phí vận hành hệ thống.
  
  ### 3.Nhược điểm của VLAN

- Packet dễ dàng bị rò rỉ giữa các VLAN.
- Packet gặp phải tình trạng inject, tạo điều kiện cho các cuộc tấn công mạng xuất hiện.
- Virus từ hệ thống đơn lẻ dễ dàng lan rộng khắp toàn bộ mạng khi sử dụng.
- Cần có sự hiện diện của một router bổ sung để quản lý công việc trong các mạng lớn.
- Khả năng tương tác có thể gặp khó khăn.
- Không thể chuyển tiếp lưu lượng mạng từ mạng VLAN này sang các VLAN khác.

### 4.VLAN và LAN khác nhau như thế nào ?
![So sánh VLAN và LAN](/ChienNX/01.CCNA/VLAN/Img/vlanvslan.png)

|Tiêu chí so sánh|LAN(Local Area Network)|VLAN(Virtual Local Area Network)|
  |------|---------|----------|
  |Phạm vi| Là mạng cục bộ được giới hạn trong khu vực địa lý nhất định. Ví dụ như toà nhà, khu dân cư, văn phòng| Là một mạng ảo được tạo ra để chia phạm vi mạng LAN thành nhiều đoạn ảo, không phụ thuộc vào vị trí địa lý.|
  |Cách tổ chức| Được tổ chức theo dạng cấu trúc vật lý, các máy tính được kết nối thông qua một cấu trúc chuyển mạch hay Hub.| Tổ chức logic, cho phép thiết bị thuộc cùng 1 nhóm thông qua cấu hình phần mềm mà không cần thiết phải kết nối vật lý với nhau.|
  |Quản lý và bảo mật| Quản lý thông qua cấu hình vật lý của mạng, quá trình bảo mật được vào các biện pháp khác như cấu hình và mật khẩu.| Quá trình cấu hình dựa trên cấu hình logic, đảm bảo dữ liệu được bảo mật nhờ tính năng ngăn chặn giữa các VLAN khác nhau, đồng thời tăng tính an toàn cho toàn bộ dữ liệu.
  |Hiệu suất và linh hoạt |Dễ gặp vấn đề liên quan đến hiệu suất sử dụng, đặc biệt là khi có nhiều máy tính cùng kết nối với một bộ chuyển mạch hoặc một đoạn mạng.| Dễ dàng cải thiện hiệu suất, khả năng linh hoạt thông qua việc chia mạng thành các nhóm ảo, điều này giúp giảm tải lưu lượng trong quá trình hoạt động, đồng thời cải thiện khả năng quản lý dữ liệu của mạng VLAN.
  |Chi phí và quản lý| Đòi hỏi phải có cấu hình vật lý, nếu mở rộng chi phí có thể tăng cao hoặc làm thay đổi cấu trúc| Sử dụng VLAN sẽ giúp doanh nghiệp giảm chi phí và thời gian quản lý nếu cần thay đổi cấu hình mạng, không cần phải thay đổi cấu trúc Vật lý