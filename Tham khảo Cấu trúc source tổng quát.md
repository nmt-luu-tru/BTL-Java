Để xây dựng một ứng dụng quản lý bán hàng cho cửa hàng giày theo mô hình 3-Tier, bạn có thể phân chia các **package** và **chức năng** như sau. Cấu trúc này giúp tổ chức mã rõ ràng, dễ bảo trì và mở rộng.

### Phân chia package theo mô hình 3-Tier

#### 1. **Package structure tổng quát**

```
com.storemanagement
├── dao                   // Tầng Data Layer
│   ├── interfaces        // Interface DAO để truy vấn dữ liệu
│   └── implementations   // Các lớp triển khai DAO
├── dto                   // DTOs (Data Transfer Objects)
├── service               // Tầng Application Layer
│   ├── interfaces        // Interface của các service
│   └── implementations   // Các lớp triển khai service
├── controller            // Tầng Presentation Layer (Controller)
├── view                  // Tầng Presentation Layer (View)
│   ├── main              // Giao diện chính của ứng dụng
│   ├── product           // Giao diện quản lý sản phẩm
│   ├── customer          // Giao diện quản lý khách hàng
│   ├── order             // Giao diện quản lý đơn hàng
├── utils                 // Các tiện ích dùng chung (ví dụ: kết nối DB, format dữ liệu)
└── config                // Cấu hình ứng dụng (ví dụ: cấu hình database)
```

---

### 2. **Chi tiết từng package**

#### **1. `dao` (Data Access Object Layer)**
   - Package này chứa các lớp truy xuất dữ liệu từ cơ sở dữ liệu. Trong mỗi module con của `dao`, nên chia thành hai phần:
     - **interfaces**: Chứa các interface cho từng chức năng, giúp dễ dàng chuyển đổi giữa các nguồn dữ liệu khác nhau (ví dụ: MySQL, Oracle, MongoDB).
     - **implementations**: Chứa các lớp triển khai của các interface, thực hiện các truy vấn trực tiếp đến cơ sở dữ liệu qua JDBC hoặc ORM.
   
   - **Ví dụ các lớp và chức năng**:
     - `ProductDAO`: Gồm các phương thức CRUD cho sản phẩm (`addProduct`, `updateProduct`, `deleteProduct`, `findProductById`, …).
     - `CustomerDAO`: Quản lý dữ liệu khách hàng.
     - `OrderDAO`: Quản lý dữ liệu đơn hàng.
     - `InventoryDAO`: Quản lý dữ liệu tồn kho.

#### **2. `dto` (Data Transfer Objects)**
   - Đây là package chứa các đối tượng trung gian được sử dụng để truyền dữ liệu giữa các tầng. 
   - **Ví dụ các lớp DTO**:
     - `ProductDTO`: Chứa thông tin sản phẩm (mã, tên, giá, số lượng tồn kho).
     - `CustomerDTO`: Chứa thông tin khách hàng (mã, tên, địa chỉ, số điện thoại).
     - `OrderDTO`: Chứa thông tin đơn hàng (mã đơn hàng, mã khách hàng, danh sách sản phẩm, ngày đặt hàng).

#### **3. `service` (Application Layer)**
   - Package này chứa logic nghiệp vụ và được chia thành:
     - **interfaces**: Các interface của service, giúp dễ dàng thay đổi hoặc mở rộng logic nghiệp vụ mà không ảnh hưởng đến tầng khác.
     - **implementations**: Các lớp triển khai của service interface, thực hiện các quy trình nghiệp vụ.
   
   - **Ví dụ các lớp và chức năng**:
     - `ProductService`: Xử lý các nghiệp vụ liên quan đến sản phẩm (kiểm tra số lượng tồn kho trước khi cho phép bán, cập nhật trạng thái sản phẩm, …).
     - `CustomerService`: Xử lý các nghiệp vụ liên quan đến khách hàng (tạo mới khách hàng, cập nhật thông tin khách hàng).
     - `OrderService`: Xử lý các nghiệp vụ liên quan đến đơn hàng (tạo đơn hàng mới, tính tổng giá trị đơn hàng, xử lý hoàn trả hàng).
     - `InventoryService`: Xử lý tồn kho, bao gồm việc cập nhật số lượng tồn sau khi bán hàng hoặc nhập hàng mới.

#### **4. `controller` (Presentation Layer - Controller)**
   - Package này chứa các controller xử lý sự kiện từ người dùng và tương tác với tầng Service để lấy hoặc xử lý dữ liệu.
   - **Ví dụ các lớp và chức năng**:
     - `ProductController`: Nhận yêu cầu từ giao diện liên quan đến sản phẩm, như thêm mới, cập nhật, xóa sản phẩm.
     - `CustomerController`: Xử lý các yêu cầu từ giao diện quản lý khách hàng.
     - `OrderController`: Xử lý các yêu cầu từ giao diện quản lý đơn hàng (tạo đơn hàng, hiển thị chi tiết đơn hàng, …).
     - `InventoryController`: Xử lý các yêu cầu từ giao diện quản lý tồn kho.

#### **5. `view` (Presentation Layer - View)**
   - Package này chứa giao diện của ứng dụng được xây dựng bằng **Java Swing** hoặc công cụ GUI khác.
   - **Phân chia theo module**:
     - `view.main`: Giao diện chính của ứng dụng, như màn hình Dashboard.
     - `view.product`: Giao diện quản lý sản phẩm, bao gồm form thêm mới, cập nhật và danh sách sản phẩm.
     - `view.customer`: Giao diện quản lý khách hàng, bao gồm form thêm mới, chỉnh sửa và danh sách khách hàng.
     - `view.order`: Giao diện quản lý đơn hàng, bao gồm form tạo đơn hàng, hiển thị danh sách và chi tiết đơn hàng.
     - Mỗi phần view này sẽ gọi các phương thức từ `controller` tương ứng để thực hiện các chức năng theo yêu cầu người dùng.

#### **6. `utils` (Utilities)**
   - Package này chứa các lớp tiện ích hoặc helper dùng chung trong toàn bộ ứng dụng.
   - **Ví dụ các lớp**:
     - `DBConnection`: Quản lý kết nối cơ sở dữ liệu (tạo, đóng kết nối).
     - `DateUtils`: Định dạng ngày tháng.
     - `ValidationUtils`: Xử lý các kiểm tra tính hợp lệ của dữ liệu (chẳng hạn, kiểm tra mã sản phẩm phải đúng định dạng, số lượng không được âm, …).

#### **7. `config` (Configuration)**
   - Package này chứa các lớp và tệp cấu hình của ứng dụng.
   - **Ví dụ các lớp**:
     - `DatabaseConfig`: Chứa thông tin cấu hình cơ sở dữ liệu (URL, username, password).
     - `AppConfig`: Cấu hình chung cho ứng dụng, như các thông số mặc định, đường dẫn tệp log, thông tin phiên bản, hoặc các biến môi trường.

---

### Ví dụ cấu trúc package và lớp

```
com.storemanagement
├── dao
│   ├── interfaces
│   │   ├── ProductDAO.java
│   │   ├── CustomerDAO.java
│   │   └── OrderDAO.java
│   └── implementations
│       ├── ProductDAOImpl.java
│       ├── CustomerDAOImpl.java
│       └── OrderDAOImpl.java
├── dto
│   ├── ProductDTO.java
│   ├── CustomerDTO.java
│   └── OrderDTO.java
├── service
│   ├── interfaces
│   │   ├── ProductService.java
│   │   ├── CustomerService.java
│   │   └── OrderService.java
│   └── implementations
│       ├── ProductServiceImpl.java
│       ├── CustomerServiceImpl.java
│       └── OrderServiceImpl.java
├── controller
│   ├── ProductController.java
│   ├── CustomerController.java
│   └── OrderController.java
├── view
│   ├── main
│   │   └── MainView.java
│   ├── product
│   │   ├── ProductListView.java
│   │   ├── AddProductView.java
│   │   └── UpdateProductView.java
│   ├── customer
│   │   ├── CustomerListView.java
│   │   ├── AddCustomerView.java
│   │   └── UpdateCustomerView.java
│   └── order
│       ├── OrderListView.java
│       ├── AddOrderView.java
│       └── OrderDetailView.java
├── utils
│   ├── DBConnection.java
│   ├── DateUtils.java
│   └── ValidationUtils.java
└── config
    ├── DatabaseConfig.java
    └── AppConfig.java
```

---

### Lợi ích của cách phân chia này
- **Dễ dàng bảo trì và mở rộng**: Với việc tách các chức năng vào các package riêng, mỗi phần có thể dễ dàng mở rộng mà không ảnh hưởng đến phần còn lại.
- **Rõ ràng, dễ đọc**: Cấu trúc phân tầng giúp người đọc mã dễ dàng nắm bắt luồng xử lý, các chức năng của từng phần.
- **Đảm bảo tính module hóa**: Các tầng giao diện, xử lý nghiệp vụ và dữ liệu được tách biệt, dễ thay đổi mà không làm ảnh hưởng lẫn nhau.

Cách phân chia này đảm bảo tuân thủ mô hình 3-Tier và giúp ứng dụng hoạt động hiệu quả, dễ bảo trì và mở rộng khi cần.
