Dưới đây là gợi ý các bảng dữ liệu cần có cho chương trình quản lý cửa hàng bán giày, bao gồm các thông tin chi tiết về sản phẩm, khách hàng, hóa đơn, và nhà cung cấp, cùng với một số bảng bổ sung để hỗ trợ các tính năng mở rộng cho nhân viên bán hàng và admin.

### 1. **Bảng SAN_PHAM (Sản phẩm)**
- **Mục đích**: Lưu thông tin chi tiết về các sản phẩm giày trong cửa hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh duy nhất cho từng sản phẩm (Primary Key).
  - **MaSP**: Mã sản phẩm (SKU).
  - **TenSP**: Tên sản phẩm.
  - **LoaiSP**: Mã loại sản phẩm (liên kết tới bảng LOAI_SAN_PHAM).
  - **MauSac**: Màu sắc của giày.
  - **Size**: Kích cỡ giày (38, 39, 40, v.v.).
  - **GiaBan**: Giá bán.
  - **SoLuong**: Số lượng tồn kho.
  - **MaVach**: Mã vạch sản phẩm (dùng để quét mã).
  - **MoTa**: Mô tả chi tiết về sản phẩm.
  - **MaNSX**: Mã nhà sản xuất (liên kết tới bảng NHA_SAN_XUAT).

### 2. **Bảng LOAI_SAN_PHAM (Loại sản phẩm)**
- **Mục đích**: Phân loại các loại sản phẩm giày.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh duy nhất cho loại sản phẩm (Primary Key).
  - **MaLoai**: Mã phân loại sản phẩm.
  - **TenLoai**: Tên loại sản phẩm (giày thể thao, giày cao gót, v.v.).

### 3. **Bảng KHO (Kho hàng)**
- **Mục đích**: Quản lý số lượng sản phẩm tồn kho tại từng chi nhánh hoặc vị trí.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của kho (Primary Key).
  - **MaKho**: Mã kho.
  - **ViTriKho**: Vị trí của kho (chi nhánh hoặc địa chỉ cụ thể).
  - **MaSP**: Mã sản phẩm.
  - **SoLuongTon**: Số lượng tồn kho của từng sản phẩm tại kho cụ thể.

### 4. **Bảng HOA_DON (Hóa đơn)**
- **Mục đích**: Lưu thông tin về các giao dịch bán hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của hóa đơn (Primary Key).
  - **MaHD**: Mã hóa đơn.
  - **NgayLap**: Ngày lập hóa đơn.
  - **MaKH**: Mã khách hàng (liên kết tới bảng KHACH_HANG).
  - **TongTien**: Tổng số tiền của hóa đơn.
  - **TrangThai**: Trạng thái của hóa đơn (đã thanh toán, chờ thanh toán).
  - **PhuongThucTT**: Phương thức thanh toán (tiền mặt, thẻ, chuyển khoản).
  - **LoaiHoaDon**: Loại hóa đơn (tại cửa hàng hoặc trực tuyến).
  - **MaNV**: Mã nhân viên tạo hóa đơn (liên kết tới bảng NHAN_VIEN).

### 5. **Bảng CHI_TIET_HOA_DON (Chi tiết hóa đơn)**
- **Mục đích**: Lưu chi tiết các sản phẩm trong từng hóa đơn, bao gồm số lượng và giá bán.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của chi tiết hóa đơn (Primary Key).
  - **MaHD**: Mã hóa đơn (liên kết tới bảng HOA_DON).
  - **MaSP**: Mã sản phẩm (liên kết tới bảng SAN_PHAM).
  - **SoLuong**: Số lượng sản phẩm trong hóa đơn.
  - **GiaBan**: Giá bán của sản phẩm tại thời điểm mua.

### 6. **Bảng KHACH_HANG (Khách hàng)**
- **Mục đích**: Lưu thông tin khách hàng của cửa hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh khách hàng (Primary Key).
  - **MaKH**: Mã khách hàng.
  - **TenKH**: Tên khách hàng.
  - **SDT**: Số điện thoại khách hàng.
  - **Email**: Email của khách hàng.
  - **DiaChi**: Địa chỉ khách hàng.
  - **LoaiKH**: Loại khách hàng (VIP, thường).
  - **DiemTichLuy**: Điểm tích lũy của khách hàng (hỗ trợ chương trình khách hàng thân thiết).

### 7. **Bảng NHA_SAN_XUAT (Nhà sản xuất)**
- **Mục đích**: Quản lý thông tin các nhà cung cấp hoặc nhà sản xuất giày.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của nhà sản xuất (Primary Key).
  - **MaNSX**: Mã nhà sản xuất.
  - **TenNSX**: Tên nhà sản xuất (như Nike, Adidas).
  - **QuocGia**: Quốc gia của nhà sản xuất.
  - **LienHe**: Thông tin liên hệ (số điện thoại, email).

### 8. **Bảng KHUYEN_MAI (Chương trình khuyến mãi)**
- **Mục đích**: Lưu thông tin về các chương trình khuyến mãi.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh khuyến mãi (Primary Key).
  - **MaKM**: Mã khuyến mãi.
  - **TenKM**: Tên chương trình khuyến mãi.
  - **NgayBatDau**: Ngày bắt đầu khuyến mãi.
  - **NgayKetThuc**: Ngày kết thúc khuyến mãi.
  - **MucGiamGia**: Mức giảm giá (% hoặc giá trị tiền giảm).
  - **LoaiKM**: Loại khuyến mãi (giảm giá trực tiếp, mua 1 tặng 1, v.v.).

### 9. **Bảng CHI_TIET_KHUYEN_MAI (Chi tiết khuyến mãi)**
- **Mục đích**: Áp dụng chi tiết các chương trình khuyến mãi cho từng sản phẩm cụ thể.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh chi tiết khuyến mãi (Primary Key).
  - **MaKM**: Mã khuyến mãi (liên kết tới bảng KHUYEN_MAI).
  - **MaSP**: Mã sản phẩm (liên kết tới bảng SAN_PHAM).
  - **DieuKienApDung**: Điều kiện áp dụng khuyến mãi (nếu có).

### 10. **Bảng GIO_HANG (Giỏ hàng tạm)**
- **Mục đích**: Lưu trữ thông tin giỏ hàng tạm cho khách hàng trước khi chuyển thành hóa đơn.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của giỏ hàng (Primary Key).
  - **MaKH**: Mã khách hàng (liên kết tới bảng KHACH_HANG).
  - **TongTien**: Tổng giá trị giỏ hàng.
  - **TrangThai**: Trạng thái giỏ hàng (đang xử lý, đã thanh toán).

### 11. **Bảng CHI_TIET_GIO_HANG (Chi tiết giỏ hàng)**
- **Mục đích**: Quản lý chi tiết các sản phẩm trong giỏ hàng trước khi chuyển thành hóa đơn.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh chi tiết giỏ hàng (Primary Key).
  - **MaGH**: Mã giỏ hàng (liên kết tới bảng GIO_HANG).
  - **MaSP**: Mã sản phẩm (liên kết tới bảng SAN_PHAM).
  - **SoLuong**: Số lượng sản phẩm trong giỏ hàng.
  - **GiaBan**: Giá bán của sản phẩm tại thời điểm thêm vào giỏ hàng.

### 12. **Bảng NHAN_VIEN (Nhân viên)**
- **Mục đích**: Quản lý thông tin nhân viên bán hàng và admin của cửa hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của nhân viên (Primary Key).
  - **MaNV**: Mã nhân viên.
  - **TenNV**: Tên nhân viên.
  - **ChucVu**: Chức vụ (thu ngân, bán hàng, quản lý).
  - **SDT**: Số điện thoại của nhân viên.
  - **Email**: Email của nhân viên.

### 13. **Bảng LICH_SU_GIA (Lịch sử giá)**
- **Mục đích**: Theo dõi lịch sử thay đổi giá của sản phẩm.
- **Các trường dữ liệu**:
- **ID**: Mã định danh lịch sử giá (Primary Key).
- **MaSP**: Mã sản phẩm (liên kết tới bảng SAN_PHAM).
- **GiaBan**: Giá bán của sản phẩm tại thời điểm cập nhật.
- **NgayCapNhat**: Ngày cập nhật giá.

### 14. **Bảng PHAN_QUYEN (Phân quyền)**
- **Mục đích**: Quản lý quyền hạn cho từng nhân viên trong hệ thống.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh phân quyền (Primary Key).
  - **MaNV**: Mã nhân viên (liên kết tới bảng NHAN_VIEN).
  - **Quyen**: Loại quyền của nhân viên (chỉ xem, chỉnh sửa, quản lý toàn quyền).


## Mô tả quan hệ giữa các bảng
- **Quan hệ một-nhiều (1-N)**:
  - **SAN_PHAM - CHI_TIET_HOA_DON**: Một sản phẩm có thể xuất hiện trong nhiều chi tiết hóa đơn.
  - **HOA_DON - CHI_TIET_HOA_DON**: Một hóa đơn có thể chứa nhiều sản phẩm trong chi tiết hóa đơn.
  - **KHUYEN_MAI - CHI_TIET_KHUYEN_MAI**: Một chương trình khuyến mãi có thể áp dụng cho nhiều sản phẩm.
  - **KHACH_HANG - HOA_DON**: Một khách hàng có thể có nhiều hóa đơn.

- **Quan hệ nhiều-nhiều (N-N)**:
  - **SAN_PHAM - KHUYEN_MAI**: Một sản phẩm có thể nằm trong nhiều chương trình khuyến mãi và ngược lại. Mối quan hệ này được quản lý qua **CHI_TIET_KHUYEN_MAI**.
  - **NHAN_VIEN - PHAN_QUYEN**: Một nhân viên có thể có nhiều quyền khác nhau trong hệ thống.

Với cấu trúc này, chương trình quản lý cửa hàng giày sẽ hỗ trợ đầy đủ các hoạt động quản lý bán hàng, tồn kho, khuyến mãi, khách hàng, và nhân viên.

---


## Giao diện và Tính năng cho **Nhân viên bán hàng**

#### 1. **Giao diện Bán hàng**
   - **Tính năng**:
     - **Tạo hóa đơn**: Nhân viên có thể quét mã vạch sản phẩm để tự động thêm sản phẩm vào hóa đơn. 
     - **Tính tổng tiền và áp dụng khuyến mãi**: Tự động tính tổng giá trị hóa đơn và kiểm tra các chương trình khuyến mãi áp dụng.
     - **Thanh toán**: Chọn phương thức thanh toán (tiền mặt, thẻ) và lưu hóa đơn sau khi thanh toán.
     - **In hóa đơn**: In hóa đơn giấy cho khách hàng ngay sau khi hoàn tất thanh toán.
   - **Mục đích**: Tạo quy trình thanh toán nhanh chóng, dễ dàng và tiện lợi cho khách hàng tại cửa hàng.

#### 2. **Giao diện Giỏ hàng tạm**
   - **Tính năng**:
     - **Quản lý giỏ hàng**: Nhân viên có thể tạo giỏ hàng tạm thời cho khách hàng, thêm/sửa/xóa sản phẩm trong giỏ hàng trước khi chuyển sang hóa đơn.
     - **Kiểm tra tồn kho**: Hiển thị số lượng tồn kho của từng sản phẩm khi thêm vào giỏ hàng để đảm bảo đủ hàng.
     - **Lưu giỏ hàng**: Lưu giỏ hàng tạm để tiếp tục giao dịch khi cần thiết.
   - **Mục đích**: Cho phép nhân viên bán hàng quản lý các giao dịch chưa hoàn thành và giúp khách hàng lựa chọn sản phẩm dễ dàng hơn.

#### 3. **Giao diện Tra cứu Sản phẩm**
   - **Tính năng**:
     - **Tìm kiếm sản phẩm**: Tìm kiếm sản phẩm theo mã, tên, hoặc mã vạch.
     - **Xem chi tiết sản phẩm**: Hiển thị chi tiết về giá, màu sắc, kích cỡ, mô tả, và khuyến mãi đang áp dụng.
     - **Kiểm tra tồn kho**: Xem số lượng tồn kho của từng sản phẩm tại các kho khác nhau.
   - **Mục đích**: Giúp nhân viên tra cứu nhanh thông tin sản phẩm để tư vấn và hỗ trợ khách hàng.

#### 4. **Giao diện Quản lý Khách hàng tại cửa hàng**
   - **Tính năng**:
     - **Tìm kiếm khách hàng**: Tìm kiếm khách hàng theo mã hoặc tên.
     - **Đăng ký thành viên mới**: Đăng ký tài khoản thành viên cho khách hàng, lưu lại thông tin liên hệ và địa chỉ.
     - **Xem lịch sử mua hàng**: Xem các hóa đơn trước đó của khách hàng để tư vấn.
   - **Mục đích**: Tạo sự thuận tiện cho nhân viên trong việc quản lý thông tin khách hàng và hỗ trợ tư vấn mua hàng.

## Giao diện và Tính năng cho **Admin (Quản lý, chủ cửa hàng)**

#### 1. **Giao diện Quản lý Sản phẩm**
   - **Tính năng**:
     - **Thêm, sửa, xóa sản phẩm**: Admin có thể cập nhật thông tin sản phẩm bao gồm tên, giá, mã vạch, mô tả, và hình ảnh.
     - **Phân loại sản phẩm**: Gán sản phẩm vào các loại sản phẩm phù hợp.
     - **Cập nhật tồn kho**: Điều chỉnh số lượng tồn kho của từng sản phẩm khi có thay đổi.
   - **Mục đích**: Giúp admin quản lý kho sản phẩm hiệu quả và đảm bảo tính chính xác của thông tin sản phẩm.

#### 2. **Giao diện Quản lý Tồn kho**
   - **Tính năng**:
     - **Theo dõi số lượng tồn kho**: Xem số lượng tồn kho của từng sản phẩm tại các kho khác nhau.
     - **Điều chỉnh tồn kho**: Nhập thêm hàng vào kho khi số lượng tồn kho thấp.
     - **Chuyển kho**: Chuyển hàng giữa các kho hoặc chi nhánh khi cần thiết.
   - **Mục đích**: Đảm bảo hàng hóa luôn có sẵn và đủ số lượng để phục vụ khách hàng.

#### 3. **Giao diện Quản lý Hóa đơn**
   - **Tính năng**:
     - **Xem danh sách hóa đơn**: Xem tất cả hóa đơn bao gồm hóa đơn trực tuyến và hóa đơn tại cửa hàng.
     - **Lọc và tìm kiếm hóa đơn**: Tìm kiếm hóa đơn theo mã, khách hàng, trạng thái, và ngày tạo.
     - **Xem chi tiết hóa đơn**: Xem chi tiết từng hóa đơn và sản phẩm trong hóa đơn.
   - **Mục đích**: Giúp admin kiểm soát các giao dịch bán hàng và hỗ trợ việc theo dõi doanh thu.

#### 4. **Giao diện Quản lý Khách hàng**
   - **Tính năng**:
     - **Thêm, sửa, xóa thông tin khách hàng**: Cập nhật thông tin cá nhân và loại khách hàng (VIP, thường).
     - **Xem lịch sử mua hàng**: Xem các giao dịch của khách hàng để phân tích thói quen mua sắm.
     - **Quản lý điểm tích lũy**: Theo dõi và cập nhật điểm tích lũy của khách hàng, giúp triển khai chương trình khách hàng thân thiết.
   - **Mục đích**: Quản lý thông tin khách hàng một cách hiệu quả và cung cấp dịch vụ chăm sóc khách hàng tốt hơn.

#### 5. **Giao diện Quản lý Khuyến mãi**
   - **Tính năng**:
     - **Tạo và quản lý chương trình khuyến mãi**: Tạo mới, chỉnh sửa hoặc xóa chương trình khuyến mãi.
     - **Áp dụng điều kiện khuyến mãi**: Thiết lập các điều kiện áp dụng khuyến mãi cho từng sản phẩm hoặc nhóm sản phẩm.
     - **Theo dõi hiệu quả khuyến mãi**: Xem số lượng sản phẩm được mua theo từng chương trình khuyến mãi để đánh giá hiệu quả.
   - **Mục đích**: Hỗ trợ chiến lược bán hàng qua các chương trình khuyến mãi nhằm thúc đẩy doanh thu.

#### 6. **Giao diện Báo cáo và Thống kê Doanh thu**
   - **Tính năng**:
     - **Báo cáo doanh thu**: Xem báo cáo doanh thu theo ngày, tháng, và năm.
     - **Thống kê sản phẩm bán chạy**: Xem danh sách sản phẩm bán chạy nhất trong một khoảng thời gian.
     - **Thống kê tồn kho thấp**: Xem danh sách sản phẩm có tồn kho thấp để có kế hoạch nhập hàng.
     - **Phân tích khách hàng**: Thống kê số lượng khách hàng thường xuyên và khách hàng VIP.
   - **Mục đích**: Hỗ trợ admin trong việc đưa ra quyết định kinh doanh dựa trên dữ liệu.

#### 7. **Giao diện Quản lý Nhân viên**
   - **Tính năng**:
     - **Thêm, sửa, xóa tài khoản nhân viên**: Quản lý tài khoản của nhân viên bán hàng, bao gồm thông tin cá nhân và chức vụ.
     - **Phân quyền nhân viên**: Cấp quyền truy cập cho nhân viên dựa trên vai trò của họ.
     - **Theo dõi hiệu suất nhân viên**: Xem số lượng hóa đơn mà nhân viên tạo ra hoặc doanh thu do nhân viên tạo ra.
   - **Mục đích**: Quản lý đội ngũ nhân viên hiệu quả, đảm bảo an ninh hệ thống và đánh giá hiệu quả làm việc.

#### 8. **Giao diện Cấu hình và Thiết lập hệ thống**
   - **Tính năng**:
     - **Cập nhật thông tin cửa hàng**: Cập nhật tên cửa hàng, địa chỉ, số điện thoại liên hệ.
     - **Thiết lập phương thức thanh toán**: Cấu hình các phương thức thanh toán chấp nhận tại cửa hàng.
     - **Thiết lập chính sách đổi trả**: Đặt các điều khoản về đổi trả hàng hóa để hiển thị cho nhân viên và khách hàng.
   - **Mục đích**: Cung cấp khả năng tùy chỉnh và quản lý hệ thống phù hợp với nhu cầu cụ thể của cửa hàng.

### Tổng kết giao diện và tính năng

| Đối tượng              | Giao diện và tính năng chính                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------------------------|
| **Nhân viên bán hàng** | Tạo hóa đơn, quản lý giỏ hàng tạm, tra cứu sản phẩm, đăng ký khách hàng mới, quản lý khách hàng tại cửa hàng.  |
| **Admin (Quản lý)**    | Quản lý sản phẩm, tồn kho, hóa đơn, khách hàng, khuyến mãi, nhân viên, báo cáo doanh thu, và cấu hình hệ thống.|

### Kết luận
Với các giao diện và tính năng trên, hệ thống quản lý cửa hàng giày có thể hỗ trợ toàn diện các hoạt động kinh doanh tại cửa hàng, từ quản lý sản phẩm, bán hàng, và tồn kho đến khuyến mãi, khách hàng, và báo cáo doanh thu. Hệ thống này đảm bảo cả nhân viên bán hàng và admin đều có các công cụ cần thiết để hoạt động hiệu quả và hỗ trợ tốt nhất cho khách hàng.
