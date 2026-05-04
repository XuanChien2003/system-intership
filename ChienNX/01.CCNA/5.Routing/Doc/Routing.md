# Routing
## 1. Routing là gì?
### Khái niệm
- Routing (định tuyến) là phương thức mà Router (Bộ định tuyến) hay PC (thiết bị mạng) dùng để chuyển các gói tin đến địa chỉ đích một cách tối ưu nhất, nghĩa là chỉ ra hướng và đường đi tốt nhất cho gói tin. Router thu thập và duy trì các thông tin định tuyến để cho phép truyền và nhận các dữ liệu. Quá trình Routing dựa vào thông tin trên bảng định tuyến (Routing table), là bảng chứa các lộ trình nhanh và tốt nhất đến các mạng khác nhau trên mạng, để hướng các gói dữ liệu đi một cách hiệu quả nhất.
  
  ![Khái niệm](/ChienNX/01.CCNA/5.Routing/Img/Routing.png)

  Máy tính A muốn nhắn tin cho máy tính B có thể đi theo 2 đường dẫn:

- Đường 1: đi qua mạng 1, 3 và 5

- Đường 2: đi qua mạng 2 và 4.

Khi dữ liệu từ máy tính A đến Router nó sẽ phân tích và quyết định lựa chọn đường dẫn tốt nhất trong 2 đường dẫn. Trong trường hợp này, Router sẽ chọn đường 1 vì đường truyền từ mạng 2 đến mạng 4 bị chậm. 

**Router (Bộ định tuyến):**

- Thiết bị mạng chịu trách nhiệm chuyển tiếp gói dữ liệu giữa các mạng khác nhau.
- Sử dụng bảng định tuyến (routing table) để quyết định đường đi cho các gói dữ liệu.

**Bảng định tuyến (Routing Table):** là tập hợp các tuyến đường mà router sử dụng để quyết định nơi gửi gói tin.

- Chứa thông tin về các đường đi có sẵn trong mạng.
- Bao gồm các thông tin như địa chỉ mạng đích, cổng ra (interface), và metric (độ đo để so sánh các đường đi).

```plaintext
Destination      Gateway        Interface
192.168.1.0      0.0.0.0         Eth0
192.168.2.0      192.168.1.1     Eth1
0.0.0.0          192.168.1.254   Eth0 (default route)
```

**Giao thức định tuyến (Routing Protocol):**

- Các giao thức như RIP, OSPF, BGP được sử dụng để tự động cập nhật bảng định tuyến.
- Giúp router học và chia sẻ thông tin về các đường đi trong mạng.

## 2. Chức năng của routing

-Các bộ định tuyến chủ yếu đảm nhận **ba chức năng chính**:

- **Xác định đường dẫn:** Bộ định tuyến cố gắng tìm đường dẫn tốt nhất bằng cách phân tích các chỉ số mạng như độ trì hoãn, bước nhảy và tốc độ.

- **Chuyển tiếp dữ liệu:** Bộ định tuyến chuyển tiếp dữ liệu đến thiết bị tiếp theo trên đường dẫn đã chọn để cuối cùng là đến điểm đích của nó.

- **Cân bằng tải:** Đôi khi, bộ định tuyến có thể gửi bản sao của cùng một gói dữ liệu bằng cách sử dụng nhiều đường dẫn khác nhau. Bộ định tuyến làm thế này để giảm lỗi do tổn thất dữ liệu, tạo khả năng dự phòng và quản lý lưu lượng truy cập.
  
## 3. Phân loại Routing
 Định tuyến (routing) có thể chia thành 3 loại: Static Routing, Deafault Routing, Dynamic Routing.

  ![Phân loại](/ChienNX/01.CCNA/5.Routing/Img/Phanloai.png)

### 1. Định tuyến tĩnh (Static routing)

-Là kiểu định tuyến mà quản trị viên mạng phải thiết lập thủ công đường đi của các gói tin.

-Phù hợp với các mạng nhỏ, có cấu trúc đơn giản và ít thay đổi.
Không tiêu tốn tài nguyên hệ thống nhưng khó mở rộng và thiếu tính linh hoạt.

-Nhược điểm của routing tĩnh:

- Không có khả năng tự động cập nhật đường đi.

- Phải cấu hình thủ công khi mạng có sự thay đổi.

- Khả năng mở rộng kém, phù hợp với mô hình mạng nhỏ.

### 2. Định tuyến mặc định (Default Routing)

-Routing mặc định là một kỹ thuật trong đó một bộ routing được cấu hình để gửi tất cả các gói đến cùng một thiết bị hop và không quan trọng nó có thuộc một mạng cụ thể hay không. Gói được truyền tới thiết bị mà nó được cấu hình trong

-Routing mặc định. Routing mặc định được sử dụng khi mạng xử lý một điểm thoát duy nhất.

-Nó cũng hữu ích khi phần lớn các mạng truyền tải phải truyền dữ liệu đến cùng một thiết bị hp.

-Khi một tuyến đường cụ thể được đề cập trong bảng routing, bộ routing sẽ chọn tuyến đường cụ thể hơn là tuyến đường mặc định. Tuyến đường mặc định chỉ được chọn khi một tuyến đường cụ thể không được đề cập trong bảng routing.

### 3.Định tuyến động (Dynamic routing)

-Các router sẽ tự động trao đổi thông tin để tính toán đường đi tốt nhất cho gói tin.

-Sử dụng các giao thức định tuyến động như RIP, OSPF, EIGRP, BGP.
  Phù hợp với các mạng lớn, có sự thay đổi thường xuyên.

| Giao thức                                          | Loại            | Tốc độ hội tụ | Sử dụng                  |
| -------------------------------------------------- | --------------- | ------------- | ------------------------ |
| RIP (Routing Information Protocol)                 | Distance Vector | Chậm          | Mạng nhỏ                 |
| OSPF (Open Shortest Path First)                    | Link-State      | Nhanh         | Mạng lớn, doanh nghiệp   |
| EIGRP (Enhanced Interior Gateway Routing Protocol) | Hybrid          | Nhanh         | Cisco, doanh nghiệp      |
| BGP (Border Gateway Protocol)                      | Path-Vector     | Chậm          | Định tuyến trên internet |

  ![](/ChienNX/01.CCNA/5.Routing/Img/dinhtuyen.png)

## 4. Các thuật toán routing

Các giao thức định tuyến sử dụng các thuật toán khác nhau để tìm ra đường đi tối ưu.

- Distance Vector (Khoảng cách – hướng đi)
  - Dựa vào số lượng bước nhảy (hop count).
  - Mỗi router chỉ biết thông tin từ router lân cận.
  - Ví dụ: RIP (giới hạn 15 bước nhảy).
- Link-State (Trạng thái liên kết)
  - Mỗi router có thông tin đầy đủ về toàn bộ mạng.
  - Sử dụng thuật toán Dijkstra để tìm đường đi ngắn nhất.
  - Ví dụ: OSPF.
- Path-Vector (Định tuyến theo đường dẫn)
  - Dùng trong định tuyến giữa các hệ thống mạng lớn.
  - Ví dụ: BGP (dùng trên Internet).

## 5. Nguyên lý hoạt động của Routing
  ![](/ChienNX/01.CCNA/5.Routing/Img/nguyenli.png)

- **Khởi động phiên giao tiếp**: Quá trình bắt đầu khi một nút mạng(máy khách hoặc máy chủ) khởi tạo một phiên giao tiếp qua mạng, sử dụng giao thức HTTP. Đây là bước đầu tiên để thiết lập kết nối giữa hai thiết bị.
- **Phân tách gói tin**: Thiết bị nguồn chia thông tin lớn thành các gói tin nhỏ để đảm bảo việc truyền tải đáng tin cậy và hiệu quả. Quá trình này được gọi là phân tách và đóng gói dữ liệu. Mỗi gói tin được gán nhãn với:
  - **Địa chỉ IP đích**: Địa chỉ của nút mạng mà gói tin cần đến.
  - **Thông tin khác**: Như địa chỉ nguồn, số thứ tự gói tin để hỗ trợ tái tạo lại dữ liệu sau này.
- **Bảng định tuyến**: Là một cấu trúc dữ liệu logic lưu trữ thông tin về các địa chỉ IP và các router lân cận. Bảng định tuyến được lưu trữ trong router, một thiết bị mạng chịu trách nhiệm xác định đường đi ngắn nhất và chuyển tiếp gói tin. Thiết bị nguồn tra cứu bảng định tuyến để:
  - Xác định các nút mạng có thể truyền gói tin đến đích.
  - Chọn đường đi ngắn nhất bằng cách sử dụng thuật toán đường đi ngắn nhất
  - Sau đó, gói tin được định tuyến theo đường đi đã chọn.
- **Quá trình nhảy**: Trong quá trình định tuyến, gói tin sẽ đi qua nhiều nút mạng(routers, switches,v.v.) trước khi đến đích. Số lượng nút mà gói tin phải đi qua được gọi là số bước nhảy(hop count).
  - **Tiêu chí nhảy**:
    - Một gói tin có giới hạn số bước nhảy tối đa( thường được xác định bởi TTL).
    - Nếu gói tin vượt quá số bước nhảy cho phép, nó sẽ bị coi là mất gói và được gửi lại từ nguồn.
- **Đến nút đích**
- Khi tất cả các gói tin đến được nút đích:
  - Các gói tin được tái tạo lại để trở thành thông tin hoàn chỉnh như lúc gửi đi từ nguồn.
  - Thiết bị đích thực hiện các cơ chế kiểm tra lỗi để đảm bảo tính toàn vẹn và xác thực của dữ liệu.
