**Mô hình TCP/IP** (Transmission Control Protocol/Internet Protocol) là bộ giao thức mạng được thiết kế để kết nối các máy tính và là **"bộ xương sống" của Internet** hiện nay,. Nó cung cấp khả năng truyền tải dữ liệu độc lập với kiến trúc phần cứng, cho phép các loại máy tính khác nhau có thể tương tác trên quy mô toàn cầu,.

### 1. Các tầng (layers) của mô hình TCP/IP
Mô hình TCP/IP tiêu chuẩn bao gồm **4 tầng** như sau:

![Tcp](/ChienNX/01.CCNA/TCP/IP/Img/tcp-ip_model.png)

*   **Tầng Ứng dụng (Application Layer):**
    *   **Khái niệm:** Là tầng giao tiếp cao nhất, cung cấp các dịch vụ mạng trực tiếp cho người dùng,.
    *   **Đặc điểm:** Kết hợp chức năng của các tầng Phiên, Trình bày và Ứng dụng trong OSI,.
    *   **Chức năng:** Trao đổi dữ liệu qua các giao thức như **HTTP/HTTPS** (duyệt web), **SMTP** (email), **FTP** (truyền tệp),.
*   **Tầng Giao vận (Transport Layer):**
    *   **Khái niệm:** Đảm bảo truyền dữ liệu tin cậy giữa các ứng dụng trên các thiết bị khác nhau.
    *   **Đặc điểm:** Sử dụng hai giao thức cốt lõi là **TCP** (tin cậy, kiểm soát lỗi chặt chẽ) và **UDP** (nhanh chóng nhưng không đảm bảo chất lượng),.
    *   **Chức năng:** Phân đoạn dữ liệu (segmentation), kiểm soát lưu lượng và sửa lỗi để đảm bảo dữ liệu đến đúng thứ tự và không bị hỏng,.
*   **Tầng Mạng/Internet (Network/Internet Layer):**
    *   **Khái niệm:** Chịu trách nhiệm định tuyến các gói tin qua mạng.
    *   **Đặc điểm:** Sử dụng giao thức **IP** để xác định địa chỉ duy nhất cho mỗi thiết bị.
    *   **Chức năng:** Định tuyến (routing), phân mảnh và tái tổ hợp các gói tin (packets) để chúng đến đúng đích.
*   **Tầng Truy cập mạng (Network Access Layer):**
    *   **Khái niệm:** Xử lý việc gửi và nhận dữ liệu trên phương tiện vật lý.
    *   **Đặc điểm:** Là sự kết hợp giữa tầng Vật lý và Liên kết dữ liệu của mô hình OSI,.
    *   **Chức năng:** Đóng gói dữ liệu thành khung (frame), quản lý địa chỉ vật lý (MAC) và truyền luồng bit qua cáp hoặc sóng vô tuyến,.

### 2. So sánh mô hình TCP/IP và mô hình OSI

#### 1. Điểm giống nhau giữa hai mô hình
Cả hai mô hình đều là những khung tham chiếu quan trọng trong lĩnh vực mạng máy tính với các đặc điểm chung:
*   **Kiến trúc phân lớp:** Cả hai đều chia quy trình truyền thông mạng thành các tầng (lớp) riêng biệt để giảm thiểu độ phức tạp và dễ quản lý.
*   **Các tầng tương đồng:** Cả hai đều có tầng **Mạng (Network)** và tầng **Giao vận (Transport)** với chức năng tương tự nhau.
*   **Kỹ thuật chuyển mạch:** Cả hai cùng sử dụng kỹ thuật chuyển gói (Packet Switching) để truyền dữ liệu qua mạng.
*   **Cơ chế hoạt động:** Đều sử dụng cơ chế đóng gói (encapsulation) khi gửi dữ liệu và giải nén (decapsulation) khi nhận dữ liệu qua từng tầng.

#### 2. Sự khác biệt cơ bản

![Compare](/ChienNX/01.CCNA/TCP/IP/Img/compare.png)

| Đặc điểm | Mô hình OSI | Mô hình TCP/IP |
| :--- | :--- | :--- |
| **Số tầng** | **7 tầng** (Vật lý, Liên kết dữ liệu, Mạng, Vận chuyển, Phiên, Trình bày, Ứng dụng). | **4 tầng** (Truy cập mạng, Mạng/Internet, Giao vận, Ứng dụng). |
| **Tính chất** | Là mô hình **tham chiếu lý thuyết**, dùng để giáo dục và chuẩn hóa quốc tế. | Là mô hình **thực tế**, được áp dụng rộng rãi và là "bộ xương sống" của Internet hiện nay. |
| **Thứ tự thiết kế** | Phát triển mô hình trước, sau đó mới phát triển các giao thức. | Các giao thức được thiết kế trước, sau đó mới phát triển mô hình để phù hợp. |
| **Phương pháp tiếp cận** | Tiếp cận theo chiều dọc; mỗi tầng thực hiện một nhiệm vụ riêng biệt, không kết hợp. | Tiếp cận theo chiều ngang; các tầng cấp cao (Phiên, Trình bày) được kết hợp vào tầng Ứng dụng. |
| **Độ tin cậy** | Thường được coi là mô hình cũ, chủ yếu dùng để tham khảo. | Được chuẩn hóa toàn cầu, nhiều người tin cậy và sử dụng phổ biến. |

#### 3. Mối liên hệ và cách ánh xạ giữa các tầng
Mô hình TCP/IP được coi là phiên bản rút gọn của mô hình OSI nhằm tập trung vào ứng dụng thực tế. Cụ thể:
*   **Tầng Ứng dụng của TCP/IP** tương ứng với sự kết hợp của 3 tầng: **Ứng dụng, Trình bày và Phiên** của mô hình OSI.
*   **Tầng Giao vận** được giữ nguyên tên và chức năng ở cả hai mô hình.
*   **Tầng Internet của TCP/IP** tương ứng với **tầng Mạng** của OSI (đổi tên từ Network thành Internet).
*   **Tầng Truy cập mạng của TCP/IP** là sự kết hợp của 2 tầng thấp nhất trong OSI là **Vật lý và Liên kết dữ liệu**.
   
 ### 3.Tìm hiểu về giao thức TCP/UDP và so sánh giữa chúng

#### 1. Giao thức TCP (Transmission Control Protocol)
*   **Khái niệm:** Là giao thức **hướng kết nối** (connection-oriented), nghĩa là thiết bị gửi và nhận phải thiết lập một kết nối ổn định trước khi dữ liệu bắt đầu được truyền đi.

Cơ chế **bắt tay 3 bước (3-way handshake)** của giao thức TCP không chỉ đơn thuần là gửi các gói tin qua lại, mà là một quá trình **đồng bộ hóa các số thứ tự (Sequence Number)** và thiết lập các thông số cần thiết để đảm bảo việc truyền dữ liệu sau đó diễn ra tin cậy và chính xác.

![3 bước](/ChienNX/01.CCNA/TCP/IP/Img/image.png)

#### **Bước 1: Thiết lập yêu cầu (SYN)**
Host A muốn kết nối với Host B sẽ gửi một phân đoạn (segment) đặc biệt:
*   **Cờ điều khiển:** Bật cờ **SYN** (Synchronize) để yêu cầu đồng bộ hóa.
*   **Số thứ tự (Sequence Number - SEQ):** Host A tự chọn một số thứ tự khởi đầu ngẫu nhiên, ví dụ **SEQ = 100**.
*   **Đặc điểm:** Phân đoạn này không chứa dữ liệu thực tế (no data), nhưng trong TCP, hoạt động gửi cờ SYN vẫn được tính tương đương với **1 byte** dữ liệu để quản lý thứ tự.

#### **Bước 2: Xác nhận và phản hồi (SYN/ACK)**
Host B nhận được gói tin SYN và phản hồi lại để chấp nhận kết nối:
*   **Cờ điều khiển:** Bật cả hai cờ **SYN** và **ACK** (Acknowledgment).
*   **Số xác nhận (Acknowledgment Number):** Vì Host B đã nhận được SEQ=100 của A và cờ SYN được tính là 1 byte, nên Host B sẽ mong muốn nhận byte tiếp theo từ A là **101**. Do đó, **ACK = 101**.
*   **Số thứ tự (SEQ) của Host B:** Host B cũng tự chọn một số thứ tự khởi đầu cho mình, ví dụ **SEQ = 300**.
*   **Đặc điểm:** Tương tự, gói tin này cũng được tính là 1 byte cho phần quản lý dù không có dữ liệu.

#### **Bước 3: Hoàn tất thiết lập (ACK)**
Host A nhận được phản hồi từ Host B và gửi gói tin cuối cùng để xác nhận:
*   **Cờ điều khiển:** Chỉ bật cờ **ACK**.
*   **Số thứ tự (SEQ):** Host A gửi byte mà Host B đang mong đợi, nên **SEQ = 101**.
*   **Số xác nhận (ACK):** Host A xác nhận đã nhận được phân đoạn SEQ=300 của Host B bằng cách yêu cầu byte tiếp theo là **301**. Do đó, **ACK = 301**.

**Tóm tắt ý nghĩa các cờ và thông số:**

 SYN (Synchronize): Yêu cầu thiết lập và đồng bộ hóa các số thứ tự khởi đầu.

 ACK (Acknowledgment): Xác nhận đã nhận được dữ liệu và thông báo số thứ tự của byte tiếp theo mà bên nhận đang chờ đợi.

 Sequence Number: Dùng để đánh số thứ tự từng byte dữ liệu được truyền đi, đảm bảo tính toàn vẹn và thứ tự của thông điệp.

*   **Đặc điểm nổi bật của giao thức TCP:**
    *   **Độ tin cậy cao:** Đảm bảo dữ liệu đến đích đầy đủ, đúng thứ tự và không bị lỗi,.
    *   **Cơ chế báo nhận (ACK):** Khi nhận được dữ liệu, bên nhận sẽ gửi xác nhận. Nếu bên gửi không nhận được xác nhận, nó sẽ gửi lại cho đến khi thành công,.
    *   **Kiểm soát luồng và tắc nghẽn:** TCP điều chỉnh tốc độ truyền để tránh gây quá tải cho thiết bị nhận hoặc mạng.
*   **Ứng dụng:** Phù hợp cho các dịch vụ yêu cầu độ chính xác tuyệt đối như duyệt web (HTTP/HTTPS), gửi email (SMTP), truyền tệp (FTP) hoặc đăng nhập từ xa (SSH),,.

#### 2. Giao thức UDP (User Datagram Protocol)
*   **Khái niệm:** Là giao thức **không kết nối** (connectionless), thực hiện truyền dữ liệu ngay lập tức mà không cần thiết lập kết nối trước (kiểu truyền "best effort"),.
*   **Đặc điểm nổi bật của giao thức UDP:**
    *   **Tốc độ nhanh:** UDP bỏ qua quá trình kiểm tra lỗi và xác nhận nên tốc độ truyền tải cao hơn nhiều so với TCP,,.
    *   **Không đảm bảo tin cậy:** Gói tin có thể bị mất, trùng lặp hoặc đến không đúng thứ tự mà bên gửi không hề hay biết,.
    *   **Header nhẹ:** Chỉ có kích thước **8 byte**, giúp giảm tải cho hệ thống,,.
*   **Ứng dụng:** Ưu tiên cho các dịch vụ cần tốc độ thời gian thực và có thể chấp nhận mất mát dữ liệu nhỏ như truyền phát video trực tuyến (Streaming), trò chơi trực tuyến (Gaming), đàm thoại qua mạng (VoIP) hoặc các truy vấn nhỏ như DNS,,,.

#### 3. So sánh chi tiết TCP và UDP
- Giống nhau: đều là các giao thức mạng TCP/IP, có chức năng kết nối các máy lại với nhau và có thể gửi dữ liệu cho nhau….
![TCP/UDP](/ChienNX/01.CCNA/TCP/IP/Img/UDP-TCP.png)
- Khác nhau:

| Tiêu chí | Giao thức TCP | Giao thức UDP |
| :--- | :--- | :--- |
| **Tính chất kết nối** | Hướng kết nối (có bắt tay 3 bước), | Không kết nối (truyền ngay lập tức), |
| **Độ tin cậy** | Rất cao, đảm bảo dữ liệu nguyên vẹn, | Thấp, không đảm bảo dữ liệu đến đích, |
| **Thứ tự dữ liệu** | Đảm bảo đúng thứ tự gửi đi, | Không sắp xếp thứ tự gói tin, |
| **Tốc độ** | Chậm hơn do có nhiều thủ tục kiểm soát, | Rất nhanh do lược bỏ các thủ tục phức tạp, |
| **Kích thước Header** | Lớn (20 - 60 byte), | Nhỏ (8 byte), |
| **Kiểm soát luồng** | Có cơ chế kiểm soát luồng và tắc nghẽn | Không có cơ chế kiểm soát luồng |
| **Hình thức truyền** | Stream (luồng byte nối Byte), | Datagram (từng khối dữ liệu rời rạc) |

### 4. Workflow truyền thông tin từ A đến B (TCP/IP)
![Flow](/ChienNX/01.CCNA/TCP/IP/Img/flow.png)

Khi thiết bị A gửi thông tin đến thiết bị B, quy trình diễn ra qua các bước đóng gói và giải nén dữ liệu,:

*   **Tại thiết bị gửi (A):**
    1.  **Tầng Ứng dụng:** Người dùng thực hiện hành động (như gửi email). Dữ liệu được tạo ra và định dạng theo giao thức ứng dụng.
    2.  **Tầng Giao vận:** Dữ liệu được chia thành các **phân đoạn (segments)**. TCP thêm tiêu đề để quản lý thứ tự và kiểm soát lỗi,.
    3.  **Tầng Internet:** Các phân đoạn được đóng gói thành **gói tin (packets)**. IP thêm địa chỉ IP nguồn (A) và đích (B),.
    4.  **Tầng Truy cập mạng:** Các gói tin được đóng vào **khung (frames)** chứa địa chỉ MAC và chuyển đổi thành **luồng bit** để truyền qua dây cáp hoặc wifi,.

*   **Quá trình truyền dẫn:** Các bit di chuyển qua các thiết bị trung gian (như router) dựa trên thông tin định tuyến IP,.

*   **Tại thiết bị nhận (B):**
  
    5.  **Tầng Truy cập mạng:** Nhận luồng bit, kiểm tra khung dữ liệu và gỡ bỏ tiêu đề lớp vật lý/liên kết,.
    6.  **Tầng Internet:** Kiểm tra địa chỉ IP đích. Nếu đúng là thiết bị B, gói tin sẽ được mở để lấy phân đoạn dữ liệu bên trong,.
    7.  **Tầng Giao vận:** Kiểm tra lỗi, sắp xếp lại các phân đoạn theo đúng thứ tự và gỡ bỏ tiêu đề TCP,.
    8.  **Tầng Ứng dụng:** Nhận dữ liệu hoàn chỉnh ban đầu và hiển thị cho người dùng thông qua ứng dụng tương ứng,.
