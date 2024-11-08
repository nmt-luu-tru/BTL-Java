Dưới đây là cấu trúc phân chia **package** cho dự án quản lý cửa hàng giày theo mô hình **3-Tier**, dựa trên các bảng dữ liệu mà bạn đã cung cấp. Cấu trúc này giúp tổ chức mã nguồn rõ ràng và dễ dàng bảo trì trong quá trình phát triển.

### Phân chia Package cho Dự án

#### 1. **Package Structure Tổng Quát**

```
com.shoestoremanagement
├── dao                   // Tầng Data Layer
│   ├── interfaces        // Interface DAO
│   └── implementations   // Triển khai DAO cho các bảng
├── dto                   // DTOs (Data Transfer Objects)
├── service               // Tầng Application Layer
│   ├── interfaces        // Interface của các service
│   └── implementations   // Triển khai service cho các chức năng
├── controller            // Tầng Presentation Layer (Controller)
├── view                  // Tầng Presentation Layer (View)
│   ├── main              // Giao diện chính của ứng dụng
│   ├── product           // Giao diện quản lý sản phẩm
│   ├── customer          // Giao diện quản lý khách hàng
│   ├── order             // Giao diện quản lý đơn hàng
│   ├── promotion         // Giao diện quản lý khuyến mãi
│   ├── employee          // Giao diện quản lý nhân viên
│   ├── inventory         // Giao diện quản lý tồn kho
│   └── report            // Giao diện báo cáo
├── utils                 // Các tiện ích dùng chung
└── config                // Cấu hình ứng dụng
```

---

### 2. **Chi tiết từng package**

#### **1. `dao` (Data Access Object Layer)**
- **Mục đích**: Quản lý các lớp truy xuất dữ liệu từ cơ sở dữ liệu.
- **Chi tiết**:
  - **interfaces**:
    - `ProductDAO`: Interface cho các thao tác CRUD với sản phẩm.
    - `CustomerDAO`: Interface cho các thao tác CRUD với khách hàng.
    - `OrderDAO`: Interface cho các thao tác CRUD với hóa đơn.
    - `SupplierDAO`: Interface cho các thao tác CRUD với nhà sản xuất.
    - `PromotionDAO`: Interface cho các thao tác CRUD với khuyến mãi.
    - `EmployeeDAO`: Interface cho các thao tác CRUD với nhân viên.
    - `InventoryDAO`: Interface cho các thao tác CRUD với tồn kho.
  - **implementations**:
    - `ProductDAOImpl`: Triển khai các phương thức từ `ProductDAO`.
    - `CustomerDAOImpl`: Triển khai các phương thức từ `CustomerDAO`.
    - `OrderDAOImpl`: Triển khai các phương thức từ `OrderDAO`.
    - `SupplierDAOImpl`: Triển khai các phương thức từ `SupplierDAO`.
    - `PromotionDAOImpl`: Triển khai các phương thức từ `PromotionDAO`.
    - `EmployeeDAOImpl`: Triển khai các phương thức từ `EmployeeDAO`.
    - `InventoryDAOImpl`: Triển khai các phương thức từ `InventoryDAO`.

#### **2. `dto` (Data Transfer Objects)**
- **Mục đích**: Đối tượng dùng để truyền dữ liệu giữa các tầng.
- **Chi tiết**:
  - `ProductDTO`: DTO cho sản phẩm.
  - `CustomerDTO`: DTO cho khách hàng.
  - `OrderDTO`: DTO cho hóa đơn.
  - `SupplierDTO`: DTO cho nhà sản xuất.
  - `PromotionDTO`: DTO cho khuyến mãi.
  - `EmployeeDTO`: DTO cho nhân viên.
  - `InventoryDTO`: DTO cho tồn kho.

#### **3. `service` (Application Layer)**
- **Mục đích**: Chứa logic nghiệp vụ và xử lý các thao tác liên quan đến dữ liệu.
- **Chi tiết**:
  - **interfaces**:
    - `ProductService`: Interface cho các nghiệp vụ liên quan đến sản phẩm.
    - `CustomerService`: Interface cho các nghiệp vụ liên quan đến khách hàng.
    - `OrderService`: Interface cho các nghiệp vụ liên quan đến hóa đơn.
    - `SupplierService`: Interface cho các nghiệp vụ liên quan đến nhà sản xuất.
    - `PromotionService`: Interface cho các nghiệp vụ liên quan đến khuyến mãi.
    - `EmployeeService`: Interface cho các nghiệp vụ liên quan đến nhân viên.
    - `InventoryService`: Interface cho các nghiệp vụ liên quan đến tồn kho.
  - **implementations**:
    - `ProductServiceImpl`: Triển khai các phương thức từ `ProductService`.
    - `CustomerServiceImpl`: Triển khai các phương thức từ `CustomerService`.
    - `OrderServiceImpl`: Triển khai các phương thức từ `OrderService`.
    - `SupplierServiceImpl`: Triển khai các phương thức từ `SupplierService`.
    - `PromotionServiceImpl`: Triển khai các phương thức từ `PromotionService`.
    - `EmployeeServiceImpl`: Triển khai các phương thức từ `EmployeeService`.
    - `InventoryServiceImpl`: Triển khai các phương thức từ `InventoryService`.

#### **4. `controller` (Presentation Layer - Controller)**
- **Mục đích**: Xử lý sự kiện từ người dùng và tương tác với service.
- **Chi tiết**:
  - `ProductController`: Điều khiển cho các chức năng liên quan đến sản phẩm.
  - `CustomerController`: Điều khiển cho các chức năng liên quan đến khách hàng.
  - `OrderController`: Điều khiển cho các chức năng liên quan đến hóa đơn.
  - `SupplierController`: Điều khiển cho các chức năng liên quan đến nhà sản xuất.
  - `PromotionController`: Điều khiển cho các chức năng liên quan đến khuyến mãi.
  - `EmployeeController`: Điều khiển cho các chức năng liên quan đến nhân viên.
  - `InventoryController`: Điều khiển cho các chức năng liên quan đến tồn kho.

#### **5. `view` (Presentation Layer - View)**
- **Mục đích**: Chứa các giao diện của ứng dụng.
- **Chi tiết**:
  - `main`: Giao diện chính của ứng dụng, có thể chứa menu điều hướng.
  - `product`: Giao diện cho quản lý sản phẩm (thêm, sửa, xóa, xem danh sách).
  - `customer`: Giao diện cho quản lý khách hàng (thêm, sửa, xóa, xem danh sách).
  - `order`: Giao diện cho quản lý đơn hàng (thêm, sửa, xem danh sách).
  - `promotion`: Giao diện cho quản lý khuyến mãi (thêm, sửa, xem danh sách).
  - `employee`: Giao diện cho quản lý nhân viên (thêm, sửa, xem danh sách).
  - `inventory`: Giao diện cho quản lý tồn kho (thêm, sửa, xem danh sách).
  - `report`: Giao diện cho báo cáo và thống kê.

#### **6. `utils` (Utilities)**
- **Mục đích**: Chứa các lớp tiện ích dùng chung cho toàn bộ ứng dụng.
- **Chi tiết**:
  - `DBConnection`: Quản lý kết nối cơ sở dữ liệu.
  - `DateUtils`: Xử lý các tác vụ liên quan đến ngày tháng.
  - `ValidationUtils`: Xác thực dữ liệu đầu vào.

#### **7. `config` (Configuration)**
- **Mục đích**: Chứa các lớp cấu hình cho ứng dụng.
- **Chi tiết**:
  - `DatabaseConfig`: Thông tin cấu hình cơ sở dữ liệu (URL, username, password).
  - `AppConfig`: Các thông số cấu hình khác cho ứng dụng.

---

### Ví dụ Cấu trúc Package và Lớp
```css
com.shoestoremanagement
├── dao
│   ├── interfaces
│   │   ├── ProductDAO.java
│   │   ├── CustomerDAO.java
│   │   ├── OrderDAO.java
│   │   ├── SupplierDAO.java
│   │   ├── PromotionDAO.java
│   │   ├── EmployeeDAO.java
│   │   └── InventoryDAO.java
│   └── implementations
│       ├── ProductDAOImpl.java
│       ├── CustomerDAOImpl.java
│       ├── OrderDAOImpl.java
│       ├── SupplierDAOImpl.java
│       ├── PromotionDAOImpl.java
│       ├── EmployeeDAOImpl.java
│       └── InventoryDAOImpl.java
├── dto
│   ├── ProductDTO.java
│   ├── CustomerDTO.java
│   ├── OrderDTO.java
│   ├── SupplierDTO.java
│   ├── PromotionDTO.java
│   ├── EmployeeDTO.java
│   └── InventoryDTO.java
├── service
│   ├── interfaces
│   │   ├── ProductService.java
│   │   ├── CustomerService.java
│   │   ├── OrderService.java
│   │   ├── SupplierService.java
│   │   ├── PromotionService.java
│   │   ├── EmployeeService.java
│   │   └── InventoryService.java
│   └── implementations
│       ├── ProductServiceImpl.java
│       ├── CustomerServiceImpl.java
│       ├── OrderServiceImpl.java
│       ├── SupplierServiceImpl.java
│       ├── PromotionServiceImpl.java
│       ├── EmployeeServiceImpl.java
│       └── InventoryServiceImpl.java
├── controller
│   ├── ProductController.java
│   ├── CustomerController.java
│   ├── OrderController.java
│   ├── SupplierController.java
│   ├── PromotionController.java
│   ├── EmployeeController.java
│   └── InventoryController.java
├── view
│   ├── main
│   │   └── MainView.java
│   ├── product
│   │   ├── ProductListView.java
│   │   ├── AddProductView.java
│   │   ├── UpdateProductView.java
│   │   └── ProductDetailView.java
│   ├── customer
│   │   ├── CustomerListView.java
│   │   ├── AddCustomerView.java
│   │   ├── UpdateCustomerView.java
│   │   └── CustomerDetailView.java
│   ├── order
│   │   ├── OrderListView.java
│   │   ├── AddOrderView.java
│   │   ├── UpdateOrderView.java
│   │   └── OrderDetailView.java
│   ├── supplier
│   │   ├── SupplierListView.java
│   │   ├── AddSupplierView.java
│   │   └── UpdateSupplierView.java
│   ├── promotion
│   │   ├── PromotionListView.java
│   │   ├── AddPromotionView.java
│   │   └── UpdatePromotionView.java
│   ├── employee
│   │   ├── EmployeeListView.java
│   │   ├── AddEmployeeView.java
│   │   └── UpdateEmployeeView.java
│   ├── inventory
│   │   ├── InventoryListView.java
│   │   ├── AddInventoryView.java
│   │   └── UpdateInventoryView.java
│   └── report
│       ├── SalesReportView.java
│       └── InventoryReportView.java
├── utils
│   ├── DBConnection.java
│   ├── DateUtils.java
│   └── ValidationUtils.java
└── config
    ├── DatabaseConfig.java
    └── AppConfig.java
```
