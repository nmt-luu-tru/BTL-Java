Trong mô hình Three-Tier, các thành phần chính được tổ chức theo ba tầng:

### 1. **Tầng Giao Diện (Presentation Layer)**:
   - **Thành phần giao diện người dùng (UI)**: Gồm các thành phần hiển thị để người dùng có thể tương tác với ứng dụng. Điều này có thể là website, ứng dụng di động, hoặc các giao diện phần mềm khác.
   - **Quản lý trình bày (Presentation Logic)**: Xử lý cách thông tin được hiển thị trên màn hình và quản lý dữ liệu đầu vào của người dùng (như nút bấm, nhập liệu).
   - **API (nếu cần)**: Tầng này có thể kết nối với API để truyền tải yêu cầu từ người dùng xuống tầng logic.

### 2. **Tầng Logic (Application Layer hoặc Business Logic Layer)**:
   - **Business Logic**: Chứa toàn bộ các quy tắc và quy trình nghiệp vụ cần thiết để xử lý yêu cầu của người dùng. Đây là nơi các quy tắc được xác định và thực hiện (như xử lý đơn hàng, tính toán điểm số, quy trình đăng ký…).
   - **API và Dịch vụ**: Các API và dịch vụ trung gian kết nối tầng logic với tầng giao diện và tầng dữ liệu, đảm bảo tính bảo mật và quản lý luồng dữ liệu.
   - **Xử lý lỗi và bảo mật**: Các quy trình để quản lý lỗi và bảo vệ ứng dụng khỏi các nguy cơ bảo mật.

### 3. **Tầng Dữ Liệu (Data Layer)**:
   - **Database Management System (DBMS)**: Quản lý lưu trữ, truy xuất và cập nhật dữ liệu, thường sử dụng các hệ quản trị cơ sở dữ liệu như MySQL, SQL Server, PostgreSQL, Oracle hoặc các hệ NoSQL như MongoDB.
   - **Data Access Layer (DAL)**: Lớp truy cập dữ liệu để thực hiện các truy vấn từ tầng logic đến cơ sở dữ liệu. Lớp này cũng bao gồm các quy tắc truy xuất dữ liệu và quản lý kết nối.
   - **Cơ chế bảo mật và sao lưu dữ liệu**: Đảm bảo an toàn cho dữ liệu, bao gồm các biện pháp như mã hóa, phân quyền và các quy trình sao lưu dự phòng.

### Mối liên hệ giữa các tầng
- **Tầng giao diện** tương tác với **tầng logic** thông qua các giao thức API hoặc HTTP, giúp truyền tải yêu cầu người dùng xuống và nhận lại kết quả.
- **Tầng logic** sau đó gửi yêu cầu truy xuất dữ liệu đến **tầng dữ liệu**, nơi thực hiện các truy vấn và trả kết quả về.
- **Tầng dữ liệu** chỉ giao tiếp với tầng logic, không trực tiếp tương tác với tầng giao diện, giúp đảm bảo an toàn dữ liệu.

Mô hình Three-Tier giúp tạo ra một cấu trúc hệ thống dễ quản lý, bảo trì và mở rộng khi cần thiết, rất phổ biến trong các ứng dụng web, di động và các hệ thống thông tin quy mô lớn.

---

Trong mô hình **3-Tier (3 tầng)**, các thành phần được tổ chức theo ba tầng chính: **Presentation Layer (Giao diện)**, **Application Layer (Logic ứng dụng)**, và **Data Layer (Dữ liệu)**. Mỗi tầng có các thành phần khác nhau để xử lý chức năng riêng biệt của mình. Dưới đây là các thành phần thường có trong mỗi tầng:


### 1. **Presentation Layer (Tầng Giao Diện)**
   - **Controller**: Đây là phần xử lý các yêu cầu từ người dùng, thường là qua giao diện người dùng (GUI). Controller nhận yêu cầu, xác định hành động cần thực hiện và gửi yêu cầu này đến Application Layer.
   - **View**: Thành phần này chịu trách nhiệm hiển thị dữ liệu cho người dùng. Đối với ứng dụng desktop như Java Swing, View sẽ là các cửa sổ hoặc panel hiển thị dữ liệu, các form nhập liệu.
   - **Helper Classes**: Các lớp trợ giúp xử lý những tác vụ liên quan đến giao diện như format dữ liệu trước khi hiển thị.

### 2. **Application Layer (Tầng Logic Ứng Dụng)**
   Đây là tầng xử lý các nghiệp vụ của ứng dụng. Tầng này có thể bao gồm các thành phần:

   - **Service**: Các lớp Service chịu trách nhiệm thực hiện logic nghiệp vụ. Service là nơi quy tụ các quy trình, tính toán và kiểm tra logic phức tạp của ứng dụng. Service nhận yêu cầu từ tầng Presentation, xử lý các quy trình nghiệp vụ và tương tác với tầng Data khi cần.
   
   - **Business Logic**: Đôi khi được tách ra như một phần riêng biệt từ Service, đây là nơi tập trung logic nghiệp vụ chính (ví dụ: các quy tắc xử lý đơn hàng, tính toán chiết khấu).
   
   - **DTO (Data Transfer Object)**: Các đối tượng trung gian chứa dữ liệu cần thiết để chuyển từ tầng này sang tầng khác, đặc biệt là giữa Presentation và Application Layer. DTO giúp tối ưu hóa dữ liệu gửi giữa các tầng.
   
   - **Validator**: Các lớp Validator đảm nhận chức năng kiểm tra và xác thực dữ liệu đầu vào từ tầng Presentation trước khi chuyển đến tầng Logic. Ví dụ, kiểm tra tính hợp lệ của dữ liệu nhập vào trước khi thêm vào cơ sở dữ liệu.

### 3. **Data Layer (Tầng Dữ Liệu)**
   Đây là tầng làm việc trực tiếp với cơ sở dữ liệu và lưu trữ dữ liệu của ứng dụng. Các thành phần chính gồm:

   - **DAO (Data Access Object)**: Các lớp DAO chịu trách nhiệm truy xuất, lưu trữ, cập nhật và xóa dữ liệu trong cơ sở dữ liệu. DAO tương tác trực tiếp với JDBC hoặc ORM (nếu dùng Hibernate) để thực hiện các thao tác trên cơ sở dữ liệu.
   
   - **Entity/Model**: Các lớp này biểu diễn cấu trúc của dữ liệu trong cơ sở dữ liệu, thường là các đối tượng ánh xạ tới bảng trong cơ sở dữ liệu. Ví dụ, một đối tượng `Product` có thể ánh xạ tới bảng `Products` trong cơ sở dữ liệu, với các thuộc tính tương ứng với các cột trong bảng.
   
   - **Repository (tuỳ chọn)**: Nếu sử dụng ORM framework như Hibernate, JPA, Repository có thể là một lớp trừu tượng bao bọc quanh DAO để cung cấp các phương thức truy vấn dữ liệu phức tạp hơn.
   
   - **Database Connection Pool**: Quản lý các kết nối tới cơ sở dữ liệu để tối ưu hóa hiệu suất, đặc biệt trong ứng dụng có nhiều người dùng.

### Tổng kết các thành phần của mô hình 3-Tier

| Tầng                | Thành phần                                     | Mô tả                                                                                           |
|---------------------|------------------------------------------------|------------------------------------------------------------------------------------------------|
| Presentation Layer  | Controller                                     | Xử lý yêu cầu từ người dùng, điều hướng các hành động cần thiết.                                 |
|                     | View                                           | Hiển thị dữ liệu cho người dùng, giao diện người dùng (UI).                                     |
|                     | Helper Classes                                 | Hỗ trợ các tác vụ format và xử lý dữ liệu để hiển thị trên giao diện.                           |
| Application Layer   | Service                                        | Xử lý các logic nghiệp vụ của ứng dụng.                                                         |
|                     | Business Logic                                 | Thực hiện các quy tắc nghiệp vụ chính.                                                          |
|                     | DTO (Data Transfer Object)                     | Truyền tải dữ liệu giữa các tầng, giúp giảm dữ liệu dư thừa.                                    |
|                     | Validator                                      | Kiểm tra và xác thực dữ liệu đầu vào.                                                           |
| Data Layer          | DAO (Data Access Object)                       | Thực hiện truy vấn dữ liệu, lưu trữ, cập nhật, xóa dữ liệu từ cơ sở dữ liệu.                    |
|                     | Entity/Model                                   | Biểu diễn cấu trúc của dữ liệu, ánh xạ tới các bảng trong cơ sở dữ liệu.                        |
|                     | Repository (nếu dùng ORM)                      | Bao bọc quanh DAO để cung cấp các phương thức truy vấn phức tạp hơn.                            |
|                     | Database Connection Pool                       | Quản lý các kết nối cơ sở dữ liệu, tối ưu hiệu suất truy xuất dữ liệu.                           |


### Lưu ý khi chọn mô hình
- **Mô hình 3-Tier** phù hợp với các ứng dụng lớn, yêu cầu tính mở rộng cao, dễ bảo trì và dễ tích hợp với các nền tảng khác.
- Nếu ứng dụng quản lý bán hàng của bạn đơn giản, bạn có thể giảm bớt một số thành phần như DTO, Repository để mô hình gọn nhẹ hơn.
- **Kết hợp MVC với 3-Tier**: Nếu cần rõ ràng hơn trong giao diện và logic xử lý, bạn có thể sử dụng **MVC trong Presentation Layer**, chia rõ View, Controller và Model, còn tầng Business Logic và Data Access sẽ đặt trong Application và Data Layer của mô hình 3-Tier.
