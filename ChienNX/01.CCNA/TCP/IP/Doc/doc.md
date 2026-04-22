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
![Compare](/ChienNX/01.CCNA/TCP/IP/Img/compare.png)
Dựa trên các nguồn tài liệu, việc so sánh mô hình **OSI** (Open Systems Interconnection) và mô hình **TCP/IP** (Transmission Control Protocol/Internet Protocol) có thể được phân tích qua những điểm giống và khác nhau cốt lõi như sau:

### 1. Điểm giống nhau giữa hai mô hình
Cả hai mô hình đều là những khung tham chiếu quan trọng trong lĩnh vực mạng máy tính với các đặc điểm chung:
*   **Kiến trúc phân lớp:** Cả hai đều chia quy trình truyền thông mạng thành các tầng (lớp) riêng biệt để giảm thiểu độ phức tạp và dễ quản lý.
*   **Các tầng tương đồng:** Cả hai đều có tầng **Mạng (Network)** và tầng **Giao vận (Transport)** với chức năng tương tự nhau.
*   **Kỹ thuật chuyển mạch:** Cả hai cùng sử dụng kỹ thuật chuyển gói (Packet Switching) để truyền dữ liệu qua mạng.
*   **Cơ chế hoạt động:** Đều sử dụng cơ chế đóng gói (encapsulation) khi gửi dữ liệu và giải nén (decapsulation) khi nhận dữ liệu qua từng tầng.

### 2. Sự khác biệt cơ bản
Mô hình OSI và TCP/IP có những triết lý phát triển và ứng dụng thực tế rất khác biệt:

| Đặc điểm | Mô hình OSI | Mô hình TCP/IP |
| :--- | :--- | :--- |
| **Số tầng** | **7 tầng** (Vật lý, Liên kết dữ liệu, Mạng, Vận chuyển, Phiên, Trình bày, Ứng dụng). | **4 tầng** (Truy cập mạng, Mạng/Internet, Giao vận, Ứng dụng). |
| **Tính chất** | Là mô hình **tham chiếu lý thuyết**, dùng để giáo dục và chuẩn hóa quốc tế. | Là mô hình **thực tế**, được áp dụng rộng rãi và là "bộ xương sống" của Internet hiện nay. |
| **Thứ tự thiết kế** | Phát triển mô hình trước, sau đó mới phát triển các giao thức. | Các giao thức được thiết kế trước, sau đó mới phát triển mô hình để phù hợp. |
| **Phương pháp tiếp cận** | Tiếp cận theo chiều dọc; mỗi tầng thực hiện một nhiệm vụ riêng biệt, không kết hợp. | Tiếp cận theo chiều ngang; các tầng cấp cao (Phiên, Trình bày) được kết hợp vào tầng Ứng dụng. |
| **Độ tin cậy** | Thường được coi là mô hình cũ, chủ yếu dùng để tham khảo. | Được chuẩn hóa toàn cầu, nhiều người tin cậy và sử dụng phổ biến. |

### 3. Mối liên hệ và cách ánh xạ giữa các tầng
Mô hình TCP/IP được coi là phiên bản rút gọn của mô hình OSI nhằm tập trung vào ứng dụng thực tế. Cụ thể:
*   **Tầng Ứng dụng của TCP/IP** tương ứng với sự kết hợp của 3 tầng: **Ứng dụng, Trình bày và Phiên** của mô hình OSI.
*   **Tầng Giao vận** được giữ nguyên tên và chức năng ở cả hai mô hình.
*   **Tầng Internet của TCP/IP** tương ứng với **tầng Mạng** của OSI (đổi tên từ Network thành Internet).
*   **Tầng Truy cập mạng của TCP/IP** là sự kết hợp của 2 tầng thấp nhất trong OSI là **Vật lý và Liên kết dữ liệu**.

### 3. Workflow truyền thông tin từ A đến B (TCP/IP)
![Flow](/ChienNX/01.CCNA/TCP/IP/Img/image.png)

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