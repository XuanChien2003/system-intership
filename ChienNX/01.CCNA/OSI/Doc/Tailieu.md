# Tìm hiểu về mô hình OSI:
## Mô hình:
 Mô hình OSI (Open Systems Interconnection), hay mô hình tham chiếu kết nối các hệ thống mở, là một khung khái niệm được phát triển bởi Tổ chức Quốc tế về Tiêu chuẩn hóa (ISO) nhằm thiết lập các tiêu chuẩn cho hệ thống mạng hiện đại. Mô hình này đóng vai trò như một ngôn ngữ chung cho mạng máy tính, cho phép các công nghệ phần cứng và phần mềm khác nhau có thể giao tiếp hiệu quả bằng các giao thức tiêu chuẩn.

## Các layer của mô hình OSI: khái niệm, đặc điểm, chức năng các tầng
Mô hình OSI (Open Systems Interconnection) là một khung khái niệm chia các chức năng truyền thông mạng thành **7 tầng (lớp)** riêng biệt.

![Tầng OSI](/ChienNX/01.CCNA/OSI/Img/Cactang.png)

### 1. Tầng 7 – Application Layer (Tầng Ứng dụng)
![Application Layer](/ChienNX/01.CCNA/OSI/Img/application_layer.png)
*   **Khái niệm:** Là tầng trên cùng, đóng vai trò là giao diện trực tiếp giữa người dùng và hệ thống mạng thông qua các ứng dụng phần mềm.
*   **Đặc điểm:** Tầng này cung cấp các giao thức hỗ trợ gửi, nhận và trình bày dữ liệu cho người dùng cuối Các giao thức phổ biến bao gồm HTTP/HTTPS (duyệt web), SMTP/POP3 (email) và FTP (truyền tệp).
*   **Chức năng:** Cung cấp dịch vụ đầu cuối ảo, quản lý việc truy cập và chuyển đổi tệp tin, cũng như các dịch vụ thư mục và thư điện tử.

### 2. Tầng 6 – Presentation Layer (Tầng Trình bày)
![Presentation Layer](/ChienNX/01.CCNA/OSI/Img/presentation_layer.png)
*   **Khái niệm:** Còn được gọi là tầng phiên dịch, chịu trách nhiệm xử lý các vấn đề liên quan đến cú pháp và ngữ nghĩa của dữ liệu.
*   **Đặc điểm:** Đảm bảo dữ liệu gửi đi từ tầng ứng dụng của một hệ thống có thể được tầng ứng dụng của hệ thống khác hiểu được.
*   **Chức năng:** 
    *   **Phiên dịch:** Chuyển đổi giữa các định dạng mã hóa khác nhau (ví dụ: ASCII sang EBCDIC).
    *   **Mã hóa và giải mã:** Đảm bảo an toàn thông tin khi truyền trên mạng.
    *   **Nén dữ liệu:** Giảm kích thước dữ liệu để tối ưu hóa băng thông truyền tải.

### 3. Tầng 5 – Session Layer (Tầng Phiên)
![Session Layer](/ChienNX/01.CCNA/OSI/Img/session_layer.png)
*   **Khái niệm:** Quản lý các "phiên" (session) – là các kết nối tạm thời để trao đổi dữ liệu giữa hai ứng dụng.
*   **Đặc điểm:** Điều phối mạng giữa hai ứng dụng từ khi bắt đầu đến lúc kết thúc và xử lý các xung đột đồng bộ hóa.
*   **Chức năng:** Thiết lập, duy trì, đồng bộ hóa và kết thúc các cuộc hội thoại giữa hai thiết bị. Nó cho phép phục hồi từ các điểm kiểm tra (checkpoints) nếu xảy ra sự cố trong quá trình truyền.

### 4. Tầng 4 – Transport Layer (Tầng Vận chuyển/Giao vận)
![Transport Layer](/ChienNX/01.CCNA/OSI/Img/transport_layer.png)
*   **Khái niệm:** Đảm bảo việc truyền dữ liệu đáng tin cậy và toàn vẹn giữa hai thiết bị đầu cuối.
*   **Đặc điểm:** Dữ liệu tại tầng này được gọi là các Phân đoạn (Segments). Sử dụng các giao thức chính như TCP (tin cậy, có kết nối) và UDP (không kết nối, tốc độ nhanh).
*   **Chức năng:** 
   Chia nhỏ dữ liệu từ tầng trên thành các phân đoạn, kiểm soát luồng (flow control) để phù hợp tốc độ nhận, và thực hiện kiểm soát lỗi để yêu cầu truyền lại khi cần thiết.

### 5. Tầng 3 – Network Layer (Tầng Mạng)
![Network Layer](/ChienNX/01.CCNA/OSI/Img/network_layer.png)
*   **Khái niệm:**  Chịu trách nhiệm truyền tải dữ liệu giữa các thiết bị nằm ở các mạng khác nhau.
*   **Đặc điểm:** Đơn vị dữ liệu tại đây là các Gói tin (Packets)
. Tầng này sử dụng địa chỉ logic (địa chỉ IP) để định danh thiết bị
*   **Chức năng:** 
  Định tuyến (Routing) để xác định con đường vật lý tối ưu nhất cho dữ liệu đi từ nguồn đến đích. Nó cũng thực hiện phân mảnh và tái hợp các gói tin khi cần thiết

### 6. Tầng 2 – Data Link Layer (Tầng Liên kết dữ liệu)
![Data Link Layer](/ChienNX/01.CCNA/OSI/Img/datalink_layer.png)
*   **Khái niệm:** Quản lý việc truyền dữ liệu tin cậy giữa hai thiết bị trong cùng một mạng nội bộ.
*   **Đặc điểm:** Dữ liệu được đóng gói thành các Khung (Frames). Tầng này gán địa chỉ vật lý (MAC) cho mỗi thiết bị.
*   **Chức năng:** 
   Kiểm soát truy cập môi trường truyền dẫn (như Ethernet), phát hiện và sửa lỗi ở mức độ khung dữ liệu, và kiểm soát luồng giữa các thiết bị nội bộ.

### 7. Tầng 1 – Physical Layer (Tầng Vật lý)
![Physical Layer](/ChienNX/01.CCNA/OSI/Img/physical_layer.png)
*   **Khái niệm:** Bao gồm các thiết bị phần cứng và phương tiện truyền dẫn vật lý để truyền dòng bit dữ liệu.
*   **Đặc điểm:** Dữ liệu được biểu diễn dưới dạng dãy các Bit (0 và 1). Tầng này bao gồm các chuẩn về cáp, đầu nối và tín hiệu điện/quang
*   **Chức năng:** 
    Chuyển đổi dữ liệu số thành tín hiệu vật lý để truyền đi, kiểm soát tốc độ bit, đồng bộ hóa thời gian truyền giữa bên gửi và bên nhận, và thiết lập cấu hình đường truyền (như dạng hình sao hay vòng).
  
 ## Workflow với mô hình OSI (các bước khi mà A muốn gửi 1 thông tin đến B):

 Quy trình truyền thông tin từ thiết bị A sang thiết bị B, trong đó dữ liệu đi xuống qua 7 tầng tại bên gửi và đi ngược lên qua 7 tầng tại bên nhận.
 
![Flow](/ChienNX/01.CCNA/OSI/Img/image.png)

Dựa trên các nguồn tài liệu, dưới đây là phân tích chi tiết và rút gọn quy trình truyền dữ liệu từ **thiết bị A** sang **thiết bị B** thông qua 7 tầng của mô hình OSI:

### 1. Tại thiết bị gửi (Thiết bị A) – Quá trình đóng gói (Encapsulation)
Dữ liệu di chuyển từ tầng cao nhất xuống tầng thấp nhất, mỗi tầng sẽ bọc thêm một tiêu đề (header) chứa thông tin điều khiển riêng.

*   **Tầng Ứng dụng (Lớp 7):** Thiết bị A khởi tạo dữ liệu thông qua giao thức cụ thể (như SMTP cho email hoặc HTTP cho web).
*   **Tầng Trình bày (Lớp 6):** Dữ liệu được **nén, mã hóa** và chuyển đổi sang định dạng chung mà bên nhận có thể hiểu được.
*   **Tầng Phiên (Lớp 5):** Thiết lập và khởi tạo **phiên giao tiếp** giữa A và B.
*   **Tầng Vận chuyển (Lớp 4):** Dữ liệu được chia nhỏ thành các **Phân đoạn (Segments)**; tầng này thêm tiêu đề để quản lý thứ tự và kiểm soát lỗi.
*   **Tầng Mạng (Lớp 3):** Các phân đoạn được đóng gói thành các **Gói tin (Packets)**, bổ sung địa chỉ logic (IP) của A và B để định tuyến.
*   **Tầng Liên kết dữ liệu (Lớp 2):** Các gói tin được chia thành các **Khung (Frames)**, thêm địa chỉ vật lý (MAC) và phần kiểm tra lỗi (FCS) ở cuối.
*   **Tầng Vật lý (Lớp 1):** Toàn bộ cấu trúc dữ liệu được chuyển hóa thành chuỗi **Bit (0 và 1)** để truyền qua môi trường vật lý (cáp, wifi).

### 2. Tại thiết bị nhận (Thiết bị B) – Quá trình giải nén (Decapsulation)
Thiết bị B nhận luồng bit và xử lý ngược từ tầng thấp nhất lên tầng cao nhất, gỡ bỏ tiêu đề của từng tầng tương ứng.

*   **Tầng Vật lý (Lớp 1):** Nhận luồng bit từ môi trường truyền dẫn và chuyển đổi ngược lại thành dữ liệu cho tầng trên.
*   **Tầng Liên kết dữ liệu (Lớp 2):** Kiểm tra lỗi và địa chỉ MAC, sau đó lắp ráp các khung thành các **gói tin**.
*   **Tầng Mạng (Lớp 3):** Kiểm tra địa chỉ IP để đảm bảo đúng đích, gỡ bỏ tiêu đề IP và tạo lại các **phân đoạn**.
*   **Tầng Vận chuyển (Lớp 4):** Tập hợp các phân đoạn lại thành một **khối dữ liệu duy nhất** dựa trên số thứ tự.
*   **Tầng Phiên (Lớp 5):** Xác nhận kết thúc phiên giao tiếp và chuyển dữ liệu lên tầng trình bày.
*   **Tầng Trình bày (Lớp 6):** Thực hiện **giải nén, giải mã** và đưa dữ liệu về dạng thô ban đầu.
*   **Tầng Ứng dụng (Lớp 7):** Cung cấp dữ liệu đã hoàn thiện cho phần mềm của thiết bị B, giúp người dùng đọc được thông tin.
