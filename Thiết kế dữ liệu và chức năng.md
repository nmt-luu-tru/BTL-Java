Dưới đây là gợi ý các bảng dữ liệu cần có cho chương trình quản lý cửa hàng bán giày, bao gồm các thông tin chi tiết về sản phẩm, khách hàng, hóa đơn, và nhà cung cấp.

### 1. **Bảng GIAY (Sản phẩm)**
- **Mục đích**: Lưu thông tin chi tiết về các sản phẩm giày trong cửa hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh duy nhất cho từng sản phẩm (Primary Key).
  - **MaSP**: Mã sản phẩm (có thể là SKU - Stock Keeping Unit).
  - **TenSP**: Tên sản phẩm.
  - **LoaiSP**: Loại sản phẩm (giày thể thao, giày cao gót, giày da, v.v.).
  - **MauSac**: Màu sắc của giày.
  - **Size**: Kích cỡ giày (ví dụ: 38, 39, 40, v.v.).
  - **GiaBan**: Giá bán.
  - **SoLuong**: Số lượng tồn kho.
  - **MaNSX**: Mã nhà sản xuất (liên kết tới bảng NHA_SAN_XUAT).

### 2. **Bảng LOAI_SAN_PHAM**
- **Mục đích**: Phân loại các loại sản phẩm giày.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh duy nhất cho loại sản phẩm.
  - **MaLoai**: Mã phân loại (ví dụ: GT cho giày thể thao, CG cho giày cao gót).
  - **TenLoai**: Tên loại sản phẩm (ví dụ: Giày thể thao, Giày cao gót, Giày da).
  
### 3. **Bảng KHO (Kho hàng)**
- **Mục đích**: Quản lý số lượng sản phẩm tồn kho tại từng chi nhánh hoặc vị trí.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của kho.
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

### 5. **Bảng CHI_TIET_HOA_DON (Chi tiết hóa đơn)**
- **Mục đích**: Lưu chi tiết các sản phẩm trong từng hóa đơn, bao gồm số lượng và giá bán.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của chi tiết hóa đơn.
  - **MaHD**: Mã hóa đơn (liên kết tới bảng HOA_DON).
  - **MaSP**: Mã sản phẩm (liên kết tới bảng GIAY).
  - **SoLuong**: Số lượng sản phẩm trong hóa đơn.
  - **GiaBan**: Giá bán của sản phẩm trong hóa đơn (có thể khác với giá hiện tại nếu có khuyến mãi).

### 6. **Bảng KHACH_HANG (Khách hàng)**
- **Mục đích**: Lưu thông tin khách hàng của cửa hàng.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh khách hàng.
  - **MaKH**: Mã khách hàng.
  - **TenKH**: Tên khách hàng.
  - **SDT**: Số điện thoại khách hàng.
  - **Email**: Email khách hàng.
  - **DiaChi**: Địa chỉ khách hàng.
  - **LoaiKH**: Loại khách hàng (bình thường, thành viên VIP, v.v.).

### 7. **Bảng NHA_SAN_XUAT (Nhà sản xuất)**
- **Mục đích**: Quản lý thông tin các nhà cung cấp hoặc nhà sản xuất giày.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh của nhà sản xuất.
  - **MaNSX**: Mã nhà sản xuất.
  - **TenNSX**: Tên nhà sản xuất (như Nike, Adidas).
  - **QuocGia**: Quốc gia của nhà sản xuất.
  - **LienHe**: Thông tin liên hệ (số điện thoại, email).

### 8. **Bảng KHUYEN_MAI (Khuyến mãi)**
- **Mục đích**: Lưu thông tin về các chương trình khuyến mãi.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh khuyến mãi.
  - **MaKM**: Mã khuyến mãi.
  - **TenKM**: Tên chương trình khuyến mãi.
  - **NgayBatDau**: Ngày bắt đầu khuyến mãi.
  - **NgayKetThuc**: Ngày kết thúc khuyến mãi.
  - **MucGiamGia**: Mức giảm giá (theo % hoặc giá trị tiền giảm).
  - **LoaiKM**: Loại khuyến mãi (giảm giá trực tiếp, mua 1 tặng 1, v.v.).

### 9. **Bảng CHI_TIET_KHUYEN_MAI (Chi tiết khuyến mãi)**
- **Mục đích**: Áp dụng chi tiết các chương trình khuyến mãi cho từng sản phẩm cụ thể.
- **Các trường dữ liệu**:
  - **ID**: Mã định danh chi tiết khuyến mãi.
  - **MaKM**: Mã khuyến mãi (liên kết tới bảng KHUYEN_MAI).
  - **MaSP**: Mã sản phẩm (liên kết tới bảng GIAY).
  - **DieuKienApDung**: Điều kiện áp dụng khuyến mãi (nếu có).

### Mô tả quan hệ giữa các bảng
- **Quan hệ một-nhiều (1-N)**:
  - **GIAY - CHI_TIET_HOA_DON**: Một sản phẩm (GIAY) có thể xuất hiện trong nhiều chi tiết hóa đơn (CHI_TIET_HOA_DON).
  - **HOA_DON - CHI_TIET_HOA_DON**: Một hóa đơn (HOA_DON) có thể chứa nhiều sản phẩm trong chi tiết hóa đơn (CHI_TIET_HOA_DON).
  - **KHUYEN_MAI - CHI_TIET_KHUYEN_MAI**: Một chương trình khuyến mãi (KHUYEN_MAI) có thể áp dụng cho nhiều sản phẩm (GIAY).
  - **KHACH_HANG - HOA_DON**: Một khách hàng (KHACH_HANG) có thể thực hiện nhiều hóa đơn mua hàng (HOA_DON).

- **Quan hệ nhiều-nhiều (N-N)**:
  - **GIAY - KHUYEN_MAI**: Một sản phẩm có thể nằm trong nhiều chương trình khuyến mãi khác nhau, và một chương trình khuyến mãi có thể áp dụng cho nhiều sản phẩm khác nhau. Mối quan hệ này được quản lý qua bảng trung gian là **CHI_TIET_KHUYEN_MAI**.

### Ví dụ Giao diện và Tính năng
Dựa trên các bảng dữ liệu trên, chương trình quản lý cửa hàng bán giày có thể có các giao diện và tính năng sau:
1. **Quản lý sản phẩm**:
   - Thêm, sửa, xóa sản phẩm giày.
   - Tìm kiếm sản phẩm theo mã, tên, loại, hoặc nhà sản xuất.
   - Kiểm tra tồn kho và số lượng hiện có của từng sản phẩm.

2. **Quản lý hóa đơn**:
   - Tạo hóa đơn mới khi khách hàng mua sản phẩm.
   - Lưu chi tiết sản phẩm trong hóa đơn, tính tổng tiền và áp dụng khuyến mãi.
   - Xem lịch sử giao dịch, tìm kiếm hóa đơn theo mã hoặc khách hàng.

3. **Quản lý khách hàng**:
   - Thêm, sửa, xóa thông tin khách hàng.
   - Phân loại khách hàng (thành viên VIP, khách hàng thường).
   - Xem lịch sử mua hàng của từng khách hàng.

4. **Quản lý khuyến mãi**:
   - Tạo các chương trình khuyến mãi mới, áp dụng cho các sản phẩm cụ thể.
   - Quản lý thời gian áp dụng, mức

 giảm giá và loại khuyến mãi.
   - Áp dụng khuyến mãi vào hóa đơn tự động khi sản phẩm thuộc diện giảm giá.

5. **Báo cáo và thống kê**:
   - Thống kê doanh thu bán hàng theo ngày, tháng, năm.
   - Báo cáo sản phẩm bán chạy, hàng tồn kho thấp.
   - Thống kê khách hàng thường xuyên và hiệu quả của các chương trình khuyến mãi.

Với cấu trúc này, chương trình quản lý cửa hàng giày sẽ có khả năng theo dõi và quản lý các hoạt động của cửa hàng một cách hiệu quả, từ quản lý hàng hóa, khuyến mãi đến quản lý khách hàng và bán hàng.
