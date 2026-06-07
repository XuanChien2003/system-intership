# Tìm hiểu về mô hình OSI:
## Mô hình:
 Mô hình OSI (Open Systems Interconnection), hay mô hình tham chiếu kết nối các hệ thống mở, là một khung khái niệm được phát triển bởi Tổ chức Quốc tế về Tiêu chuẩn hóa (ISO) nhằm thiết lập các tiêu chuẩn cho hệ thống mạng hiện đại. Mô hình này đóng vai trò như một ngôn ngữ chung cho mạng máy tính, cho phép các công nghệ phần cứng và phần mềm khác nhau có thể giao tiếp hiệu quả bằng các giao thức tiêu chuẩn.

## Các layer của mô hình OSI: khái niệm, đặc điểm, chức năng các tầng
Mô hình OSI (Open Systems Interconnection) là một khung khái niệm chia các chức năng truyền thông mạng thành **7 tầng (lớp)** riêng biệt.

![Tầng OSI](/ChienNX/01.CCNA/2.OSI/Img/Cactang.png)

### 1. Tầng 7 – Application Layer (Tầng Ứng dụng)
![Application Layer](/ChienNX/01.CCNA/2.OSI/Img/application_layer.png)

* **Cách hoạt động:** Nhận yêu cầu trực tiếp từ người dùng (ví dụ: gõ URL trên trình duyệt, gửi email) và cung cấp các giao thức dịch vụ để phần mềm ứng dụng có thể tương tác với hệ thống mạng.
* **Giao thức:** HTTP/HTTPS, FTP, SMTP, IMAP, POP3, DNS, LDAP.
* **Chức năng:** Là giao diện trực tiếp giữa người dùng và hệ thống mạng. Tầng này không phải là bản thân phần mềm ứng dụng, mà cung cấp các giao thức cho phần mềm sử dụng.
  * **Thiết bị đầu cuối ảo của mạng (Network Virtual Terminal):** Cho phép các ứng dụng trên các máy tính khác nhau tương tác với nhau như thể chúng đang chạy trên cùng một thiết bị.
  * **Quản lý, truy cập và chuyển file (FTAM - File transfer access and management):** Cung cấp khả năng truyền tải, truy cập và quản lý các tệp tin từ xa (như FTP, quản lý tệp từ xa, quản lý quyền truy cập).
  * **Các dịch vụ mạng thông dụng:** Hỗ trợ dịch vụ thư điện tử (SMTP, IMAP, POP3), dịch vụ thư mục (LDAP) và dịch vụ web (HTTP) để kết nối và chia sẻ thông tin.

---

### 2. Tầng 6 – Presentation Layer (Tầng Trình bày)
![Presentation Layer](/ChienNX/01.CCNA/2.OSI/Img/presentation_layer.png)

* **Cách hoạt động:** Đóng vai trò như một "tầng phiên dịch" (Translation layer), chịu trách nhiệm xử lý định dạng dữ liệu để đảm bảo máy gửi và máy nhận có thể hiểu nhau một cách thống nhất.
* **Giao thức / Định dạng:** SSL/TLS, JPEG, GIF, MPEG, ASCII, EBCDIC.
* **Chức năng:** Đóng vai trò "phiên dịch viên" của mạng, đảm bảo dữ liệu từ máy gửi được định dạng sao cho máy nhận có thể hiểu được.
  * **Phiên dịch (Translation):** Chuyển đổi dữ liệu giữa các định dạng mã hóa khác nhau của tầng ứng dụng sang định dạng mạng chung (ví dụ: từ ASCII sang EBCDIC) và ngược lại.
  * **Mã hóa và giải mã (Encryption and Decryption):** Bảo mật thông tin bằng cách mã hóa dữ liệu trước khi truyền đi qua mạng và giải mã khi đến đích nhằm chống truy cập trái phép (như SSL/TLS).
  * **Nén dữ liệu (Compression):** Giảm kích thước của dữ liệu để tối ưu hóa băng thông truyền tải và nâng cao tốc độ mạng tùy thuộc vào yêu cầu cụ thể.

---

### 3. Tầng 5 – Session Layer (Tầng Phiên)
![Session Layer](/ChienNX/01.CCNA/2.OSI/Img/session_layer.png)

* **Cách hoạt động:** Quản lý việc thiết lập, duy trì và đồng bộ hóa các "phiên làm việc" (kết nối tạm thời) để trao đổi dữ liệu giữa các ứng dụng trên các thiết bị đang giao tiếp.
* **Chức năng:** Thiết lập, duy trì và chấm dứt các kết nối (phiên làm việc) giữa hai ứng dụng đang giao tiếp.
  * **Thiết lập, duy trì, chấm dứt phiên (Session establishment, maintenance, and termination):** Khởi tạo, giữ ổn định và đóng cửa sổ giao tiếp giữa các quy trình một cách an toàn.
  * **Đồng bộ hóa (Synchronization):** Chèn các điểm kiểm tra (checkpoint) vào luồng dữ liệu. Nếu xảy ra sự cố đứt mạng giữa chừng, dữ liệu có thể phục hồi và truyền tiếp từ điểm kiểm tra gần nhất thay vì phải tải lại từ đầu.
  * **Kiểm soát hội thoại (Dialog Controller):** Quyết định hướng truyền dữ liệu trong phiên, bao gồm một chiều (simplex), hai chiều lần lượt (half-duplex) hoặc hai chiều đồng thời (full-duplex).

---

### 4. Tầng 4 – Transport Layer (Tầng Vận chuyển/Giao vận)
![Transport Layer](/ChienNX/01.CCNA/2.OSI/Img/transport_layer.png)

* **Cách hoạt động:** Nhận dữ liệu từ tầng phiên, quản lý luồng dữ liệu một cách toàn vẹn và chia nhỏ thành các phân đoạn (**Segment**), sử dụng các giao thức phù hợp để truyền đi không lỗi và đúng thứ tự.
* **Giao thức:** TCP (Tin cậy, hướng kết nối), UDP (Nhanh, không hướng kết nối).
* **Chức năng:** Đảm bảo truyền tải dữ liệu toàn vẹn, không lỗi và đúng thứ tự, chia dữ liệu thành các Segment.
  * **Phân mảnh/Phân đoạn và tái hợp (Segmentation and Reassembly):** Chia nhỏ dữ liệu lớn từ tầng trên thành các đoạn nhỏ để dễ truyền tải và lắp ghép lại nguyên vẹn tại đích.
  * **Kiểm soát kết nối:** Thiết lập, duy trì và kết thúc các kết nối logic giữa bên gửi và bên nhận.
  * **Kiểm soát lưu lượng (Flow Control):** Điều chỉnh tốc độ truyền dữ liệu để tránh gây hiện tượng quá tải cho thiết bị nhận.
  * **Kiểm soát lỗi (Error Control):** Phát hiện phân đoạn bị lỗi/mất và thực hiện kiểm tra, yêu cầu gửi lại dữ liệu khi cần thiết.
  * **Định địa chỉ điểm dịch vụ (Service Point Addressing):** Sử dụng các số cổng (**Port**) để định danh chính xác dịch vụ hoặc ứng dụng cụ thể đang chạy trên máy chủ.

---

### 5. Tầng 3 – Network Layer (Tầng Mạng)
![Network Layer](/ChienNX/01.CCNA/2.OSI/Img/network_layer.png)

* **Cách hoạt động:** Chịu trách nhiệm truyền các gói tin (**Packet**) xuyên suốt qua nhiều môi trường mạng khác nhau (LAN sang WAN) từ thiết bị nguồn ban đầu đến thiết bị đích cuối cùng thông qua các chặng trung gian.
* **Giao thức & Thiết bị:** IP (IPv4/IPv6), ICMP; Thiết bị: **Router** (Bộ định tuyến), Layer 3 Switch.
* **Chức năng:** Tìm đường đi (định tuyến - routing) và chuyển các gói tin (packet) qua nhiều mạng khác nhau để đến đích tối ưu.
  * **Định địa chỉ logic (Logical Addressing):** Gán địa chỉ logic (địa chỉ IP) cho mỗi thiết bị trong mạng, giúp định danh nguồn và đích trên toàn bộ mạng rộng lớn và đa dạng.
  * **Định tuyến (Routing):** Sử dụng các thuật toán và bảng định tuyến để tìm kiếm, chọn lựa lộ trình tối ưu nhất giúp dữ liệu đến đích nhanh chóng (áp dụng trong mạng nội bộ LAN hoặc qua các mạng khác WAN).

---

### 6. Tầng 2 – Data Link Layer (Tầng Liên kết dữ liệu)
![Data Link Layer](/ChienNX/01.CCNA/2.OSI/Img/datalink_layer.png)

* **Cách hoạt động:** Nhận các gói tin từ tầng mạng và đóng gói thành các khung (**Frame**), cung cấp các cơ chế kiểm tra và điều chỉnh nhằm bảo đảm tính toàn vẹn và độ tin cậy của dữ liệu trên cùng một phân đoạn mạng cục bộ.
* **Thiết bị & Cơ chế:** **Switch**, Bridge, Địa chỉ MAC, thuật toán CRC, CSMA/CD, CSMA/CA.
* **Chức năng:** Đóng gói các gói tin thành các khung (frame) để truyền trên cùng một mạng cục bộ (LAN). Kiểm soát lỗi vật lý và gán địa chỉ vật lý (MAC).
  * **Đóng gói dữ liệu (Framing):** Chia nhỏ dữ liệu nhận được từ tầng mạng thành các khung chứa đầy đủ thông tin cần thiết để kiểm soát lỗi và đồng bộ hóa.
  * **Định địa chỉ vật lý (Physical Addressing):** Gán địa chỉ vật lý (địa chỉ MAC) cho mỗi thiết bị nhằm xác định chính xác nguồn và đích của mỗi khung dữ liệu trong mạng.
  * **Kiểm soát lưu lượng (Flow Control):** Điều hòa tốc độ truyền dữ liệu giữa bên gửi và bên nhận để ngăn ngừa tình trạng quá tải tại trạm đích.
  * **Kiểm soát lỗi (Error Control):** Phát hiện và sửa chữa các sai sót vật lý trong quá trình truyền tải nhờ sử dụng các thuật toán kiểm tra lỗi như **CRC** (Cyclic Redundancy Check).
  * **Kiểm soát truy cập (Access Control):** Xác định cách thức các thiết bị chia sẻ kênh truyền thông chung trong mạng (Ví dụ: mạng LAN dùng dây dùng CSMA/CD, mạng không dây Wi-Fi dùng CSMA/CA).

---

### 7. Tầng 1 – Physical Layer (Tầng Vật lý)
![Physical Layer](/ChienNX/01.CCNA/2.OSI/Img/physical_layer.png)

* **Cách hoạt động:** Là tầng thấp nhất trong mô hình OSI, trực tiếp thực hiện việc chuyển tiếp chuỗi bit dữ liệu (0 và 1) từ kênh truyền nguồn tới kênh truyền đích dưới dạng tín hiệu vật lý. Có thể hình dung như quá trình người đưa thư chuyển bức thư từ hòm thư này sang hòm thư khác (xem xét tốc độ, phương tiện, phương thức di chuyển).
* **Thiết bị & Môi trường:** **Hub, Repeater**, cáp mạng (cáp đồng, cáp quang), không khí (sóng vô tuyến).
* **Chức năng:** Tầng thấp nhất, chuyển đổi dữ liệu thành các tín hiệu vật lý (điện áp, xung ánh sáng, sóng vô tuyến) để truyền qua các phương tiện truyền dẫn (cáp, không gian).
  * **Biểu diễn bit:** Chuyển đổi dữ liệu số (bit) thành các loại tín hiệu vật lý tương ứng (tín hiệu điện, quang học, radio) để truyền trên phương tiện truyền dẫn.
  * **Kiểm soát tốc độ dữ liệu (Bit rate control):** Điều chỉnh tốc độ truyền, tức là số lượng bit được truyền đi trên một kênh dẫn trong một đơn vị thời gian để tương thích với khả năng của phương tiện truyền.
  * **Đồng bộ hóa các bit (Bit synchronization):** Đảm bảo bên nhận và bên gửi đồng bộ tuyệt đối về xung nhịp thời gian khi truyền/nhận từng bit để tránh hiểu sai dữ liệu.
  * **Cấu hình đường truyền & Topo vật lý (Physical topologies):** Thiết lập cấu hình vật lý của đường truyền, xác định cách sắp xếp kết nối các thiết bị phần cứng trong mạng (như topo dạng sao, dạng vòng, dạng cây...).
  * **Chế độ truyền dẫn (Transmission mode):** Xác định hướng dòng chảy dữ liệu với 3 chế độ chính: Simplex (chỉ truyền một hướng), Half-duplex (hai hướng nhưng không đồng thời), và Full-duplex (hai hướng đồng thời).
  
 ## Workflow với mô hình OSI (các bước khi mà A muốn gửi 1 thông tin đến B):

 Quy trình truyền thông tin từ thiết bị A sang thiết bị B, trong đó dữ liệu đi xuống qua 7 tầng tại bên gửi và đi ngược lên qua 7 tầng tại bên nhận.
 
![Flow](/ChienNX/01.CCNA/2.OSI/Img/image.png)

### 1. Tại thiết bị gửi (Thiết bị A) – Quá trình đóng gói (Encapsulation)
Dữ liệu di chuyển từ tầng cao nhất (Tầng 7) xuống tầng thấp nhất (Tầng 1). Tại mỗi tầng (từ tầng 4 xuống tầng 2), dữ liệu sẽ được bọc thêm một tiêu đề (**Header**), riêng tầng 2 sẽ có thêm cái đuôi (**Trailer**) chứa thông tin điều khiển chuyên biệt. Đơn vị dữ liệu tại mỗi tầng được gọi là **PDU (Protocol Data Unit)**.

* **Tầng Ứng dụng (Layer 7) - PDU: Data**
    * **Cách hoạt động:** Thiết bị A khởi tạo dữ liệu thô thông qua các ứng dụng mạng và giao thức tương ứng (ví dụ: gửi mail qua SMTP, duyệt web qua HTTP/HTTPS, truyền file qua FTP).
* **Tầng Trình bày (Layer 6) - PDU: Data**
    * **Cách hoạt động:** Dữ liệu được chuyển đổi định dạng (mã hóa ký tự), thực hiện **nén** để tối ưu băng thông và **mã hóa** bảo mật (như SSL/TLS) để chuẩn bị truyền đi.
* **Tầng Phiên (Layer 5) - PDU: Data**
    * **Cách hoạt động:** Khởi tạo, quản lý và thiết lập **phiên giao tiếp (Session)** logic giữa thiết bị A và thiết bị B, đánh dấu các điểm kiểm soát (checkpoint) trên luồng dữ liệu.
* **Tầng Vận chuyển (Layer 4) - PDU: Segment (TCP) / Datagram (UDP)**
    * **Cách hoạt động:** Dữ liệu lớn từ tầng trên được cắt nhỏ thành các phân đoạn. Tầng này gắn thêm **Transport Header (L4H)** chứa thông tin quan trọng như **Cổng nguồn (Source Port)**, **Cổng đích (Destination Port)** để định vị ứng dụng, cùng với số thứ tự (Sequence Number - nếu dùng TCP) để kiểm soát lỗi và luồng.
* **Tầng Mạng (Layer 3) - PDU: Packet (Gói tin)**
    * **Cách hoạt động:** Nhận các Segment từ tầng 4 và đóng gói thành các Packet. Tầng này bổ sung **Network Header (L3H)** chứa **Địa chỉ IP nguồn (Source IP)** của thiết bị A và **Địa chỉ IP đích (Destination IP)** của thiết bị B phục vụ cho quá trình định tuyến qua các mạng khác nhau.
* **Tầng Liên kết dữ liệu (Layer 2) - PDU: Frame (Khung dữ liệu)**
    * **Cách hoạt động:** Nhận các Packet từ tầng 3 và đóng gói thành các Frame. Tầng này gắn thêm **Data Link Header (L2H)** chứa **Địa chỉ MAC nguồn (Source MAC)**, **Địa chỉ MAC đích (Destination MAC)** của thiết bị chặng kế tiếp, đồng thời chèn thêm **Data Link Trailer (L2T)** ở cuối chứa mã kiểm tra lỗi **FCS (Frame Check Sequence)** sử dụng thuật toán CRC.
* **Tầng Vật lý (Layer 1) - PDU: Bits**
    * **Cách hoạt động:** Tiếp nhận cấu trúc Frame hoàn chỉnh từ tầng 2, biến đổi toàn bộ cấu trúc này thành chuỗi các **bít 0 và 1 (Bits)**, sau đó mã hóa chúng thành các tín hiệu vật lý (xung điện, ánh sáng hoặc sóng vô tuyến) để truyền đi qua môi trường truyền dẫn (cáp đồng, cáp quang, Wi-Fi).

---

### 2. Tại thiết bị nhận (Thiết bị B) – Quá trình mở gói / Giải nén (Decapsulation)
Thiết bị B nhận được tín hiệu vật lý và thực hiện quá trình xử lý ngược lại hoàn toàn, di chuyển từ tầng thấp nhất (Tầng 1) lên tầng cao nhất (Tầng 7). Tại mỗi tầng, thiết bị sẽ đọc thông tin điều khiển, kiểm tra tính hợp lệ, gỡ bỏ Header/Trailer của tầng đó rồi chuyển dữ liệu lên tầng trên.

* **Tầng Vật lý (Layer 1) - PDU: Bits**
    * **Cách hoạt động:** Nhận các tín hiệu vật lý từ môi trường truyền dẫn, giải mã các tín hiệu này ngược trở lại thành chuỗi các **bít (Bits)** và chuyển lên tầng 2 dưới dạng một Frame thô.
* **Tầng Liên kết dữ liệu (Layer 2) - PDU: Frame**
    * **Cách hoạt động:** Thiết bị B đọc thông tin trong L2H và L2T. Nó sử dụng mã **FCS** để kiểm tra xem Frame có bị lỗi hay nhiễu trong quá trình truyền hay không. Đồng thời kiểm tra **Địa chỉ MAC đích**: nếu trùng với MAC của nó (hoặc là địa chỉ Broadcast/Multicast), nó sẽ **gỡ bỏ L2H và L2T**, hoàn trả lại **Packet** để chuyển lên tầng 3. (Nếu lỗi hoặc sai MAC, Frame sẽ bị hủy).
* **Tầng Mạng (Layer 3) - PDU: Packet**
    * **Cách hoạt động:** Thiết bị B kiểm tra **Địa chỉ IP đích** trong L3H. Nếu địa chỉ IP trùng với IP của thiết bị B (hoặc thiết bị B đóng vai trò là Router đích), nó sẽ xác nhận gói tin đã đến đúng đích. Thiết bị B thực hiện **gỡ bỏ L3H (IP Header)**, giải phóng **Segment** và chuyển lên tầng 4.
* **Tầng Vận chuyển (Layer 4) - PDU: Segment / Datagram**
    * **Cách hoạt động:** Đọc thông tin trong L4H. Thiết bị B dựa vào số thứ tự (Sequence Number) để sắp xếp lại các phân đoạn bị xáo trộn thành luồng dữ liệu hoàn chỉnh, kiểm tra sửa lỗi (nếu có). Sau đó, nó đọc **Destination Port (Cổng đích)** để xác định chính xác ứng dụng/dịch vụ nào ở tầng trên sẽ tiếp nhận dữ liệu này. Cuối cùng, **gỡ bỏ L4H**, chuyển **Data** lên tầng 5.
* **Tầng Phiên (Layer 5) - PDU: Data**
    * **Cách hoạt động:** Xác định luồng dữ liệu thuộc về phiên làm việc nào đang mở, điều phối tiến trình hội thoại, kiểm tra tính toàn vẹn tại các điểm dừng (checkpoint) và thực hiện thủ tục đóng/duy trì phiên giao tiếp tương ứng.
* **Tầng Trình bày (Layer 6) - PDU: Data**
    * **Cách hoạt động:** Tiếp nhận dữ liệu, thực hiện quá trình ngược lại là **giải mã** (Decryption nếu có) và **giải nén** (Decompression nếu có). Sau đó, phiên dịch cấu trúc dữ liệu từ định dạng mạng chung về định dạng ngôn ngữ/mã ký tự mà ứng dụng cụ thể có thể hiểu được.
* **Tầng Ứng dụng (Layer 7) - PDU: Data**
    * **Cách hoạt động:** Nhận dữ liệu sạch, thô và hoàn chỉnh cuối cùng từ tầng 6. Giao thức của tầng ứng dụng tương tác và chuyển tiếp dữ liệu này hiển thị lên giao diện phần mềm (như Trình duyệt web Chrome, Outlook, ứng dụng chat...), giúp người dùng cuối đọc và tương tác được với thông tin.
