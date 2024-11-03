Trong một dự án web theo mô hình **MVC (Model-View-Controller)**, có nhiều lớp chuyên biệt với các từ chuyên ngành khác nhau để mô tả chức năng cụ thể của từng loại lớp. Dưới đây là danh sách phổ biến và chức năng của chúng trong một dự án web MVC:

### 1. **Controller**
   - **Chức năng**: Điều khiển luồng xử lý của ứng dụng, nhận yêu cầu từ người dùng, gọi các lớp `Service` để xử lý dữ liệu, và trả về kết quả cho người dùng.
   - **Vai trò trong MVC**: Là phần **Controller** trong mô hình MVC, chịu trách nhiệm điều hướng và xử lý các yêu cầu HTTP (GET, POST, PUT, DELETE).

### 2. **Service**
   - **Chức năng**: Chứa logic nghiệp vụ của ứng dụng. Đây là nơi thực hiện các thao tác xử lý chính mà không liên quan trực tiếp đến tầng dữ liệu.
   - **Vai trò**: Tách biệt logic nghiệp vụ khỏi `Controller`, giúp dễ dàng tái sử dụng và kiểm thử. Lớp `Service` thường gọi đến các lớp `Repository` hoặc `DAO` để thao tác với dữ liệu.

### 3. **Repository**
   - **Chức năng**: Chịu trách nhiệm truy xuất và quản lý dữ liệu từ cơ sở dữ liệu. Lớp này chứa các phương thức CRUD (Create, Read, Update, Delete) để làm việc với dữ liệu.
   - **Vai trò**: Cung cấp lớp trừu tượng cho các thao tác với cơ sở dữ liệu. `Repository` giúp tách biệt logic truy vấn khỏi các lớp `Service`.
   - **Lưu ý**: Trong một số dự án, `Repository` và `DAO` có thể sử dụng thay thế cho nhau.

### 4. **DAO (Data Access Object)**
   - **Chức năng**: Là một lớp hoặc interface chứa các phương thức truy xuất dữ liệu. `DAO` tập trung vào việc thao tác với cơ sở dữ liệu và không chứa logic nghiệp vụ.
   - **Vai trò**: Tách biệt thao tác dữ liệu khỏi các phần khác của ứng dụng. `DAO` thường được sử dụng trong các dự án không sử dụng framework quản lý dữ liệu tự động như JPA hoặc Spring Data.
   - **Phân biệt với Repository**: `DAO` tập trung vào các thao tác truy vấn trực tiếp với dữ liệu thô, trong khi `Repository` có thể mang tính trừu tượng hơn và thường sử dụng trong các framework như Spring Data.

### 5. **Model / Entity**
   - **Chức năng**: Đại diện cho dữ liệu hoặc thực thể trong ứng dụng, thường là các lớp chứa các thuộc tính tương ứng với các cột trong bảng cơ sở dữ liệu.
   - **Vai trò**: Là phần **Model** trong mô hình MVC. `Model` cung cấp các thuộc tính và các phương thức getter/setter để lưu trữ và xử lý dữ liệu trong ứng dụng.
   - **Lưu ý**: Trong các ứng dụng sử dụng ORM (Object-Relational Mapping) như JPA, các lớp `Entity` được ánh xạ trực tiếp đến các bảng trong cơ sở dữ liệu.

### 6. **Utils / Utility**
   - **Chức năng**: Chứa các hàm tiện ích, các phương thức hỗ trợ không thuộc về logic nghiệp vụ chính của ứng dụng. Ví dụ: các phương thức xử lý chuỗi, định dạng ngày tháng, mã hóa, giải mã, v.v.
   - **Vai trò**: Giúp chia sẻ các chức năng tiện ích chung, có thể tái sử dụng trong nhiều lớp khác nhau.

### 7. **DTO (Data Transfer Object)**
   - **Chức năng**: Là một lớp chứa dữ liệu đơn giản, thường dùng để truyền dữ liệu giữa các tầng trong ứng dụng (giữa Controller và Service, giữa Service và View).
   - **Vai trò**: Tối ưu hóa quá trình truyền dữ liệu, bảo mật dữ liệu, và giảm sự phụ thuộc trực tiếp vào các lớp `Entity`. DTO thường được dùng trong các API để trả dữ liệu cho client mà không tiết lộ toàn bộ chi tiết của `Entity`.

### 8. **VO (Value Object)**
   - **Chức năng**: Là một đối tượng chỉ mang giá trị và thường là bất biến (immutable). `VO` chứa dữ liệu mà không có định danh duy nhất, thường được sử dụng trong các lớp nghiệp vụ.
   - **Vai trò**: Giúp biểu diễn dữ liệu chỉ đọc, không thay đổi, chẳng hạn như thông tin địa chỉ hoặc tiền tệ.

### 9. **Mapper**
   - **Chức năng**: Chứa các phương thức để chuyển đổi giữa các lớp (thường là giữa `Entity` và `DTO` hoặc `VO`).
   - **Vai trò**: Giúp đơn giản hóa quá trình chuyển đổi dữ liệu giữa các tầng của ứng dụng, đảm bảo rằng dữ liệu được truyền đi một cách nhất quán và rõ ràng.

### 10. **Config / Configuration**
   - **Chức năng**: Chứa các cấu hình ứng dụng, chẳng hạn như cấu hình kết nối cơ sở dữ liệu, cấu hình bảo mật, cấu hình các dịch vụ bên ngoài, v.v.
   - **Vai trò**: Cung cấp các tham số cấu hình cho ứng dụng, giúp tách biệt cấu hình khỏi mã nguồn chính, tạo tính linh hoạt cho ứng dụng khi triển khai trên các môi trường khác nhau.

### 11. **Interceptor**
   - **Chức năng**: Chứa các logic để can thiệp vào quá trình xử lý của ứng dụng. Các lớp `Interceptor` thường được sử dụng để thực hiện các tác vụ trước hoặc sau khi một yêu cầu được xử lý, chẳng hạn như xác thực, ghi log, hoặc kiểm tra quyền truy cập.
   - **Vai trò**: Cải thiện tính linh hoạt của ứng dụng bằng cách thêm các chức năng phụ trợ mà không làm thay đổi mã nguồn chính trong `Controller` hoặc `Service`.

### 12. **Filter**
   - **Chức năng**: Lọc các yêu cầu đến trước khi chúng được xử lý bởi `Controller`. `Filter` có thể dùng để xử lý các yêu cầu như xác thực, ghi log, nén dữ liệu, v.v.
   - **Vai trò**: Kiểm tra và xử lý các yêu cầu HTTP ở tầng đầu vào, tạo điều kiện cho các yêu cầu hợp lệ trước khi chúng đi vào `Controller`.

### 13. **Aspect (AOP - Aspect-Oriented Programming)**
   - **Chức năng**: Là một lớp dùng để xử lý các chức năng xuyên suốt (cross-cutting concerns) như logging, bảo mật, giao dịch.
   - **Vai trò**: Giúp tách biệt các tác vụ phụ trợ khỏi logic chính của ứng dụng. `Aspect` có thể được sử dụng trong Spring AOP để áp dụng logic tại các điểm khác nhau trong ứng dụng (before, after, around).

### 14. **Exception Handler**
   - **Chức năng**: Xử lý các lỗi và ngoại lệ xảy ra trong ứng dụng. `Exception Handler` sẽ trả về phản hồi hợp lý cho người dùng thay vì để ứng dụng bị lỗi.
   - **Vai trò**: Cải thiện trải nghiệm người dùng và duy trì tính ổn định của ứng dụng bằng cách xử lý lỗi một cách có tổ chức.

### 15. **Validator**
   - **Chức năng**: Chứa các logic kiểm tra và xác thực dữ liệu đầu vào để đảm bảo dữ liệu hợp lệ trước khi được lưu vào cơ sở dữ liệu hoặc xử lý bởi lớp `Service`.
   - **Vai trò**: Đảm bảo tính toàn vẹn của dữ liệu và giảm thiểu lỗi do dữ liệu không hợp lệ.

### 16. **Job / Scheduler**
   - **Chức năng**: Định nghĩa các tác vụ được lên lịch chạy tự động theo thời gian. Thường dùng cho các tác vụ nền như làm mới dữ liệu, gửi email hàng ngày, hoặc các tác vụ định kỳ khác.
   - **Vai trò**: Tự động hóa các quy trình và đảm bảo các tác vụ được thực hiện đúng thời gian mà không cần sự can thiệp của người dùng.

### 17. **Helper**
   - **Chức năng**: Tương tự như `Utils`, lớp `Helper` cung cấp các hàm tiện ích hỗ trợ cho các tác vụ cụ thể. Ví dụ: tính toán, chuyển đổi dữ liệu, v.v.
   - **Vai trò**: Giúp đơn giản hóa mã nguồn bằng cách cung cấp các phương thức trợ giúp có thể tái sử dụng.

### 18. **Component**
   - **Chức năng**: Là một lớp có thể được sử dụng lại trong toàn bộ ứng dụng. `Component` thường là các phần độc lập, có thể được chia sẻ giữa các phần khác nhau của ứng dụng.
   - **Vai trò**: Tăng tính tái sử dụng và giảm trùng lặp mã. Trong Spring, các lớp được đánh dấu là `@Component` để tự động quản lý bởi Spring Container.

### Tóm tắt:
Trên đây là danh sách các từ chuyên ngành phổ biến trong các dự án web MVC, mỗi từ mô tả một loại lớp hoặc vai trò riêng biệt trong ứng dụng. Mỗi loại lớp này đều có chức năng cụ thể, giúp tổ chức và duy trì mã nguồn của dự án một cách dễ hiểu, có tổ chức, và dễ bảo trì.  

---

Dưới đây là nội dung đã bổ sung thêm các lớp của tầng **View** để hoàn thiện mối quan hệ giữa các thành phần trong một ứng dụng MVC, dựa trên ví dụ về ứng dụng web bán giày trực tuyến.

---

Trong một ứng dụng web theo mô hình **MVC (Model-View-Controller)**, các thành phần như **Controller**, **Service**, **Repository**, **DAO**, **Model**, **DTO**, **Utils**, và các thành phần khác có mối quan hệ chặt chẽ và hỗ trợ nhau trong quá trình xử lý yêu cầu của người dùng. Dưới đây là mối quan hệ giữa các thành phần này, mô tả cách chúng tương tác với nhau để hoàn thành một yêu cầu trong ứng dụng bán giày, bao gồm các lớp của tầng View.

### 1. Mối quan hệ tổng quan
Trong mô hình **MVC (Model-View-Controller)**, các thành phần được chia làm ba tầng chính:
- **Controller Layer** (Tầng điều khiển)
- **Service Layer** (Tầng nghiệp vụ)
- **Data Access Layer** (Tầng truy cập dữ liệu)
- **View Layer** (Tầng giao diện)

Ngoài ra còn có **Utility Layer** (Tầng tiện ích) và các thành phần khác (như **Configuration**, **Filter**, **Validator**), giúp hỗ trợ các chức năng phụ trợ. Các tầng này làm việc cùng nhau để xử lý dữ liệu và cung cấp nội dung đến **View** (giao diện người dùng).

### 2. Quan hệ giữa các thành phần chính trong ứng dụng bán giày

#### 2.1. **Controller** và **Service**
- **Controller** là điểm đầu tiên xử lý yêu cầu từ người dùng (HTTP request). Ví dụ, khi người dùng gửi yêu cầu **xem thông tin giày** bằng cách truy cập vào trang sản phẩm, `ProductController` sẽ:
  - Xác định logic nghiệp vụ cần thiết để lấy thông tin giày dựa trên yêu cầu.
  - Gọi các phương thức của `ProductService` để truy xuất danh sách giày và trả về cho giao diện.
- **Service** là nơi chứa các logic nghiệp vụ chính của ứng dụng. `Controller` chỉ làm nhiệm vụ điều phối và không xử lý nghiệp vụ phức tạp. Điều này giúp:
  - Tách biệt các logic nghiệp vụ khỏi lớp `Controller`, giúp mã nguồn gọn gàng, dễ bảo trì.
  - Ví dụ: `ProductService` có thể có phương thức `getAllProducts()` để lấy danh sách giày, hoặc `getProductDetails(productId)` để lấy chi tiết về một đôi giày dựa trên ID. `Controller` chỉ đơn giản gọi `ProductService` và nhận dữ liệu trả về để hiển thị cho người dùng.

#### 2.2. **Service** và **Repository** / **DAO**
- **Service** sẽ gọi các lớp `Repository` hoặc `DAO` để truy xuất hoặc thao tác với dữ liệu.
  - **Repository** hoặc **DAO** chịu trách nhiệm tương tác trực tiếp với cơ sở dữ liệu, thực hiện các thao tác như tìm kiếm, thêm mới, cập nhật, hoặc xóa dữ liệu.
  - Ví dụ: `ProductRepository` sẽ có các phương thức như `findAll()` để lấy danh sách tất cả các giày, `findById(productId)` để lấy một giày cụ thể, hoặc `save(product)` để lưu một giày mới.
- **Repository** và **DAO**:
  - `Repository` cung cấp một lớp trừu tượng cho việc truy cập dữ liệu và thường được sử dụng trong các framework như Spring Data JPA. **Repository** được dùng khi có hỗ trợ ORM và tích hợp sẵn trong các framework.
  - **DAO** có chức năng tương tự `Repository`, nhưng thường được dùng trong các dự án không sử dụng framework ORM và có thể truy vấn dữ liệu trực tiếp từ cơ sở dữ liệu. DAO được dùng khi không có ORM hỗ trợ tự động.

#### 2.3. **Service** và **Model** / **DTO**
- **Model (Entity)**: 
  - `Model` đại diện cho thực thể dữ liệu trong hệ thống và thường ánh xạ trực tiếp đến các bảng trong cơ sở dữ liệu. Ví dụ, `Product` là một `Model` cho bảng sản phẩm, chứa các thuộc tính như `productId`, `name`, `price`, `description`, `brand`, `category`, v.v.
  - `Service` có thể lấy `Model` từ `Repository`, thao tác với `Model` theo logic nghiệp vụ và trả về cho `Controller`.
- **DTO (Data Transfer Object)**:
  - `DTO` là lớp để truyền dữ liệu giữa các tầng. `Service` thường chuyển đổi dữ liệu từ `Model` sang `DTO` trước khi trả về cho `Controller`, giúp bảo vệ và giới hạn dữ liệu được trả về cho phía người dùng. Ví dụ, `ProductDTO` có thể chỉ chứa các thuộc tính cần thiết như `name`, `price`, và `description`, bỏ qua các thông tin nhạy cảm hoặc không cần thiết như `createdDate`, `updatedDate`.
  - `DTO` giúp ẩn đi các chi tiết thừa trong `Model` mà phía client không cần phải biết.

#### 2.4. **Service** và **Utils / Helper**
- **Utils / Helper**:
  - Là các lớp tiện ích hỗ trợ `Service` trong việc xử lý các tác vụ chung như định dạng dữ liệu, tính toán, mã hóa, hoặc các hàm chuyển đổi.
  - Ví dụ: `PriceUtils` có thể cung cấp các phương thức để tính toán khuyến mãi hoặc định dạng giá hiển thị cho người dùng.
  - `Service` có thể gọi các phương thức của `Utils` hoặc `Helper` để xử lý các công việc phụ trợ mà không cần viết lại mã. Điều này giúp giảm thiểu trùng lặp và tăng tính tái sử dụng của mã nguồn.
  - **Utils** thường được dùng cho các phương thức đơn giản, ít biến đổi. **Helper** có thể là các phương thức hỗ trợ cụ thể cho từng chức năng hơn.

### 3. Các thành phần hỗ trợ khác và mối quan hệ với các lớp chính trong ứng dụng bán giày

#### 3.1. **Validator** và **Exception Handler**
- **Validator**: 
  - `Validator` được sử dụng để kiểm tra và xác thực dữ liệu đầu vào trước khi `Service` xử lý. `Controller` có thể gọi `Validator` trước khi chuyển dữ liệu cho `Service`.
  - Ví dụ, khi người dùng đăng ký tài khoản, `UserValidator` sẽ kiểm tra tính hợp lệ của các thông tin như email, số điện thoại, mật khẩu trước khi gọi `UserService` để tạo tài khoản.
  - `Validator` thường được dùng để xử lý dữ liệu đầu vào nhằm tránh lỗi từ phía client.
- **Exception Handler**:
  - `Exception Handler` giúp quản lý các lỗi xảy ra trong quá trình xử lý yêu cầu.
  - Nếu xảy ra lỗi trong `Service` hoặc `Repository`, `Exception Handler` sẽ bắt và xử lý lỗi, trả về phản hồi hợp lý cho người dùng thay vì để ứng dụng bị lỗi. Ví dụ, khi có lỗi kết nối cơ sở dữ liệu, `ExceptionHandler` sẽ trả về thông báo lỗi thân thiện với người dùng.
  - `Exception Handler` thường dùng cho các lỗi không mong muốn hoặc ngoại lệ xảy ra trong ứng dụng.

#### 3.2. **Aspect** và **Interceptor**
- **Aspect (AOP)**: 
  - Aspect-Oriented Programming (AOP) cho phép áp dụng các chức năng như logging, bảo mật, hoặc kiểm soát giao dịch mà không làm thay đổi mã nguồn của `Controller` hay `Service`.
  - Ví dụ: Một `Aspect` có thể tự động log lại tất cả các thao tác liên quan đến giỏ hàng, hoặc kiểm soát giao dịch thanh toán để đảm bảo tính nhất quán.
  - `Aspect` thường được dùng cho các chức năng mang tính chất xuyên suốt, áp dụng cho nhiều lớp hoặc phương thức.
- **Interceptor**:
  - `Interceptor` có thể can thiệp vào các yêu cầu trước khi đến `Controller` và sau khi `Controller` xử lý xong, trước khi trả lại cho người dùng.
  - Ví dụ: Một `Interceptor` có thể xác thực quyền truy cập trước khi cho phép người dùng thêm sản phẩm vào giỏ hàng.
  - `Interceptor` được dùng cho các yêu cầu cần kiểm tra hoặc điều chỉnh trước khi xử lý logic chính.

#### 3.3. **Mapper**
- **Mapper**:
  - Mapper giúp chuyển đổi dữ liệu giữa các lớp `Entity` và `DTO`.
  - `Service` sử dụng `Mapper` để chuyển đổi `Entity` sang `DTO` trước khi trả về dữ liệu cho `Controller`, hoặc chuyển đổi từ `DTO` sang `Entity` khi nhận dữ liệu từ `Controller` để lưu vào cơ sở dữ liệu.
  - Ví dụ, `ProductMapper` chuyển đổi dữ liệu từ `Product` sang `ProductDTO` để đảm bảo dữ liệu trả về cho người dùng là an toàn và tối ưu.
  - `Mapper` dùng khi cần chuyển đổi từ thực thể dữ liệu gốc sang dữ liệu đã qua xử lý cho các tầng khác nhau trong ứng dụng.

#### 3.4. **Job / Scheduler**
- **Job / Scheduler**:
  - `Job` hoặc `Scheduler` thực hiện các tác vụ nền (background tasks) mà không phụ thuộc vào các lớp khác.
  - `Service` có thể gọi `Job` để thực hiện các tác vụ định kỳ như làm mới dữ

 liệu, gửi email hoặc xóa các bản ghi cũ.
  - Ví dụ: `EmailScheduler` có thể gửi email thông báo khuyến mãi đến người dùng vào mỗi sáng thứ Hai.
  - `Scheduler` thường dùng cho các tác vụ lặp đi lặp lại theo lịch cố định, còn `Job` có thể thực hiện các tác vụ nền không cố định.

### 4. **View Layer** trong ứng dụng bán giày
Tầng View chịu trách nhiệm hiển thị dữ liệu cho người dùng và nhận tương tác từ họ. Các thành phần thường thấy trong tầng này bao gồm:

- **Templates**: Các tệp HTML hoặc JSP, sử dụng để định nghĩa giao diện của từng trang, như trang **danh sách sản phẩm**, **chi tiết sản phẩm**, hoặc **giỏ hàng**. Ví dụ: `product-list.html` hiển thị danh sách giày với thông tin về tên, giá, hình ảnh.
  
- **CSS/JavaScript**: Định dạng và tăng tính tương tác cho trang web, như tạo hiệu ứng xem chi tiết giày khi người dùng nhấn vào một sản phẩm, hoặc kiểm tra dữ liệu nhập vào form trước khi gửi đi.
  
- **View Models**: Chứa các lớp được sử dụng trong View để hiển thị dữ liệu. Ví dụ, `ProductViewModel` chứa thông tin cơ bản về giày như tên, giá, màu sắc để hiển thị cho người dùng. Các `ViewModel` này có thể sử dụng dữ liệu từ `DTO` hoặc chuyển đổi từ `DTO`.

- **Frontend Frameworks**: Một số dự án sử dụng các framework frontend như React, Vue, hoặc Angular để tăng tính tương tác của ứng dụng. Chẳng hạn, Vue có thể được dùng để xây dựng các chức năng như cập nhật giỏ hàng theo thời gian thực.

### 5. Quy trình xử lý một yêu cầu từ người dùng trong ứng dụng bán giày
Dưới đây là quy trình xử lý cơ bản của một yêu cầu từ người dùng qua các thành phần trong mô hình MVC của ứng dụng bán giày:

1. **Người dùng** gửi yêu cầu (HTTP request) đến ứng dụng, ví dụ: yêu cầu xem danh sách giày.
2. **Interceptor** có thể xử lý trước khi yêu cầu vào `Controller` (ví dụ: kiểm tra xác thực, phân quyền).
3. **Controller** nhận yêu cầu và chuyển dữ liệu đến lớp **Service** để thực hiện logic nghiệp vụ, ví dụ `ProductController` gọi `ProductService` để lấy danh sách giày.
4. **Service** có thể gọi đến **Validator** để kiểm tra dữ liệu trước khi xử lý, hoặc gọi **Utils** để thực hiện các thao tác phụ trợ.
5. **Service** gọi **Repository** hoặc **DAO** để truy xuất hoặc cập nhật dữ liệu trong cơ sở dữ liệu, ví dụ `ProductRepository` tìm kiếm danh sách giày.
6. **Repository** hoặc **DAO** sử dụng **Model** (Entity) để thao tác với cơ sở dữ liệu.
7. Sau khi nhận dữ liệu từ `Repository`, `Service` có thể sử dụng **Mapper** để chuyển đổi `Entity` sang `DTO` trước khi trả về cho `Controller`.
8. **Controller** nhận `DTO` từ `Service`, chuyển đến **View Layer** để hiển thị dữ liệu trên giao diện người dùng (HTML/CSS/JavaScript).
9. **Exception Handler** sẽ xử lý nếu có bất kỳ lỗi nào xảy ra trong quá trình xử lý yêu cầu.

### Tóm tắt
- **Controller** nhận và điều phối yêu cầu, gọi các **Service** để xử lý logic nghiệp vụ.
- **Service** thực hiện các thao tác nghiệp vụ và gọi các **Repository/DAO** để tương tác với dữ liệu.
- **Repository/DAO** truy xuất hoặc thao tác dữ liệu, thường sử dụng **Entity/Model** để ánh xạ với cơ sở dữ liệu.
- **DTO** giúp chuyển dữ liệu giữa các tầng, còn **Mapper** giúp chuyển đổi dữ liệu giữa `Entity` và `DTO`.
- **View** hiển thị dữ liệu cho người dùng, gồm các lớp như Template, View Model, CSS/JavaScript và có thể sử dụng các frontend frameworks.
- **Validator**, **Exception Handler**, **Aspect**, **Interceptor**, **Utils**, và các thành phần hỗ trợ khác giúp xử lý các chức năng phụ trợ, nâng cao tính linh hoạt, bảo mật, và hiệu quả của ứng dụng.

Mô hình MVC với các lớp và thành phần được phân tách rõ ràng giúp mã nguồn dễ hiểu, dễ bảo trì, tăng tính tái sử dụng và cải thiện hiệu suất của ứng dụng. 

---

Trong một ứng dụng web MVC, **View Model**, **Model**, và **DTO** đều là các lớp chứa dữ liệu, nhưng chúng phục vụ các mục đích khác nhau và được sử dụng ở những vị trí khác nhau trong quy trình xử lý dữ liệu. Dưới đây là sự phân biệt giữa **View Model**, **Model (Entity)**, và **DTO**.

### 1. **Model (Entity)**
   - **Mục đích**: Đại diện cho các thực thể trong hệ thống và ánh xạ trực tiếp đến các bảng trong cơ sở dữ liệu.
   - **Chức năng**: `Model` thường là một **Entity** trong hệ thống, chứa các thuộc tính tương ứng với các cột của bảng dữ liệu. Nó được sử dụng để thao tác dữ liệu trực tiếp với cơ sở dữ liệu thông qua các lớp `Repository` hoặc `DAO`.
   - **Ví dụ trong ứng dụng bán giày**: `Product` có thể là một `Model` đại diện cho bảng sản phẩm, với các thuộc tính như `productId`, `name`, `price`, `description`, `brand`, và `category`. `Product` được sử dụng trong tầng truy cập dữ liệu (Data Access Layer) và qua các thao tác CRUD trực tiếp với cơ sở dữ liệu.

   - **Khi nào sử dụng**: `Model` được dùng khi cần lưu trữ hoặc thao tác dữ liệu trực tiếp từ cơ sở dữ liệu, không phải để trao đổi dữ liệu giữa các tầng trong hệ thống hoặc hiển thị trực tiếp cho người dùng.

### 2. **DTO (Data Transfer Object)**
   - **Mục đích**: Truyền dữ liệu giữa các tầng trong hệ thống (thường là giữa Controller và Service) và giảm phụ thuộc trực tiếp vào các lớp `Model`.
   - **Chức năng**: `DTO` không ánh xạ trực tiếp với bảng trong cơ sở dữ liệu mà chỉ chứa các dữ liệu cần thiết để trao đổi giữa các tầng. Nó giúp bảo vệ các chi tiết thừa của `Model` (chẳng hạn như các trường nhạy cảm hoặc không cần thiết cho mục đích cụ thể) và tối ưu hóa dữ liệu truyền đi.
   - **Ví dụ trong ứng dụng bán giày**: `ProductDTO` có thể chứa các trường như `name`, `price`, `category`, và `description`, nhưng loại bỏ các trường không cần thiết như `createdDate` hay `updatedDate` khi trả dữ liệu về cho client.
   - **Khi nào sử dụng**: `DTO` thường được sử dụng khi truyền dữ liệu qua lại giữa các tầng khác nhau trong hệ thống mà không muốn sử dụng trực tiếp `Model`, giúp giảm tải dữ liệu và tăng tính bảo mật.

### 3. **View Model**
   - **Mục đích**: Chuẩn bị và cấu trúc dữ liệu cho tầng giao diện người dùng (View) để hiển thị.
   - **Chức năng**: `View Model` chứa dữ liệu ở dạng đã được xử lý và định dạng theo yêu cầu của giao diện người dùng. `View Model` có thể chứa dữ liệu từ nhiều nguồn khác nhau (có thể bao gồm dữ liệu từ nhiều `DTO` hoặc `Model`) và sắp xếp lại chúng để dễ dàng hiển thị trong `View`. Nó cũng có thể chứa các thuộc tính bổ sung phục vụ cho mục đích trình bày (chẳng hạn như dữ liệu định dạng lại hoặc các thuộc tính bổ sung không có trong `Model` hay `DTO`).
   - **Ví dụ trong ứng dụng bán giày**: `ProductViewModel` có thể chứa các trường `name`, `priceFormatted`, `brand`, và `discountedPrice`. `priceFormatted` có thể là giá đã được định dạng (thêm dấu phân cách hàng nghìn), và `discountedPrice` là giá đã tính giảm giá nếu có. `View Model` có thể thêm cả thuộc tính `inStock` (còn hàng) để dễ hiển thị trên trang sản phẩm.
   - **Khi nào sử dụng**: `View Model` được dùng ở tầng `View` để chuẩn bị dữ liệu cụ thể cho giao diện, đảm bảo người dùng nhận được dữ liệu ở dạng phù hợp và dễ sử dụng nhất.

### Tóm tắt sự khác biệt
| Loại          | Mục đích                                             | Chức năng                                                    | Ví dụ                                                      |
|---------------|------------------------------------------------------|--------------------------------------------------------------|------------------------------------------------------------|
| **Model (Entity)** | Ánh xạ với cơ sở dữ liệu, quản lý các thực thể | Lưu trữ dữ liệu và ánh xạ với các bảng trong cơ sở dữ liệu   | `Product` với `productId`, `name`, `price`, `category`     |
| **DTO**       | Truyền dữ liệu giữa các tầng, ẩn chi tiết không cần thiết | Chỉ chứa dữ liệu cần thiết để trao đổi giữa Controller và Service | `ProductDTO` với `name`, `price`, `category`               |
| **View Model**| Chuẩn bị dữ liệu cho tầng View, phục vụ hiển thị     | Chứa dữ liệu đã định dạng và sắp xếp cho giao diện người dùng | `ProductViewModel` với `name`, `priceFormatted`, `inStock` |

**Tóm lại**:
- `Model` là đối tượng trực tiếp liên kết với dữ liệu trong cơ sở dữ liệu và được dùng trong tầng truy cập dữ liệu.
- `DTO` là đối tượng trung gian giúp truyền dữ liệu giữa các tầng trong ứng dụng, không phải trực tiếp phục vụ cho giao diện.
- `View Model` là đối tượng cuối cùng chuẩn bị dữ liệu để hiển thị cho người dùng, với dữ liệu đã được định dạng và tổ chức phù hợp với giao diện.
