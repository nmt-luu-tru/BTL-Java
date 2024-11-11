Dưới đây là các câu lệnh SQL để thêm dữ liệu mẫu vào các bảng mà bạn đã yêu cầu:

```sql
-- Thêm dữ liệu vào bảng LOAI_SAN_PHAM
INSERT INTO LOAI_SAN_PHAM (MaLoai, TenLoai) VALUES
('LSP01', 'Giày thể thao'),
('LSP02', 'Giày cao gót'),
('LSP03', 'Giày sandal');

-- Thêm dữ liệu vào bảng NHA_SAN_XUAT
INSERT INTO NHA_SAN_XUAT (MaNSX, TenNSX, QuocGia, LienHe) VALUES
('NSX01', 'Nike', 'USA', 'Tel: +1-800-NIKE, Email: contact@nike.com'),
('NSX02', 'Adidas', 'Germany', 'Tel: +49-800-ADIDAS, Email: support@adidas.com'),
('NSX03', 'Puma', 'Germany', 'Tel: +49-1800-PUMA, Email: service@puma.com');

-- Thêm dữ liệu vào bảng SAN_PHAM
INSERT INTO SAN_PHAM (MaSP, TenSP, LoaiSP, MauSac, Size, GiaBan, SoLuong, MaVach, MoTa, MaNSX) VALUES
('SP001', 'Nike Air Max', 1, 'Đen', '42', 1200.00, 50, '1234567890', 'Giày thể thao Nike Air Max, độ bền cao', 1),
('SP002', 'Adidas Superstar', 1, 'Trắng', '40', 1000.00, 40, '1234567891', 'Giày thể thao Adidas Superstar, phong cách thời trang', 2),
('SP003', 'Puma Basket', 1, 'Xanh', '41', 800.00, 30, '1234567892', 'Giày thể thao Puma Basket, thiết kế năng động', 3),
('SP004', 'Giày cao gót 1000', 2, 'Đỏ', '37', 1500.00, 20, '1234567893', 'Giày cao gót cao cấp, thiết kế sang trọng', 2),
('SP005', 'Giày sandal nữ', 3, 'Vàng', '39', 500.00, 60, '1234567894', 'Giày sandal thoải mái cho mùa hè', 1);

-- Thêm dữ liệu vào bảng KHO
INSERT INTO KHO (MaKho, ViTriKho, MaSP, SoLuongTon) VALUES
('KHO01', 'Chi nhánh 1', 'SP001', 30),
('KHO02', 'Chi nhánh 2', 'SP002', 20),
('KHO03', 'Chi nhánh 3', 'SP003', 10),
('KHO01', 'Chi nhánh 1', 'SP004', 15),
('KHO02', 'Chi nhánh 2', 'SP005', 50);

-- Thêm dữ liệu vào bảng KHACH_HANG
INSERT INTO KHACH_HANG (MaKH, TenKH, SDT, Email, DiaChi, LoaiKH, DiemTichLuy) VALUES
('KH001', 'Nguyễn Thị Mai', '0987654321', 'mai@gmail.com', 'Hà Nội', 'VIP', 120),
('KH002', 'Trần Văn Hoan', '0976543210', 'hoan@yahoo.com', 'Hồ Chí Minh', 'Thường', 30),
('KH003', 'Lê Thị Thu', '0936543210', 'thu@hotmail.com', 'Đà Nẵng', 'VIP', 200);

-- Thêm dữ liệu vào bảng NHAN_VIEN
INSERT INTO NHAN_SU (MaNV, TenNV, ChucVu, SDT, Email) VALUES
('NV001', 'Nguyễn Hữu Quang', 'NV Kho', '0912345678', 'quang@shop.com'),
('NV002', 'Lê Minh Tâm', 'NV Thu ngan', '0923456789', 'tam@shop.com'),
('NV003', 'Trần Quang Vinh', 'Quan ly', '0934567890', 'vinh@shop.com');

-- Thêm dữ liệu vào bảng HOA_DON
INSERT INTO HOA_DON (MaHD, NgayLap, MaKH, TongTien, TrangThai, PhuongThucTT, LoaiHoaDon, MaNV) VALUES
('HD001', '2024-11-01', 'KH001', 1200.00, 'Đã thanh toán', 'Tiền mặt', 'Tại cửa hàng', 'NV001'),
('HD002', '2024-11-02', 'KH002', 2000.00, 'Chờ thanh toán', 'Thẻ tín dụng', 'Trực tuyến', 'NV002'),
('HD003', '2024-11-03', 'KH003', 1500.00, 'Đã thanh toán', 'Chuyển khoản', 'Tại cửa hàng', 'NV003');

-- Thêm dữ liệu vào bảng CHI_TIET_HOA_DON
INSERT INTO CHI_TIET_HOA_DON (MaHD, MaSP, SoLuong, GiaBan) VALUES
('HD001', 'SP001', 1, 1200.00),
('HD002', 'SP002', 2, 1000.00),
('HD003', 'SP004', 1, 1500.00);


### Giải thích:
1. **LOAI_SAN_PHAM**: Thêm các loại sản phẩm giày như giày thể thao, giày cao gót, và giày sandal.
2. **NHA_SAN_XUAT**: Thêm dữ liệu cho các nhà sản xuất như Nike, Adidas, và Puma.
3. **SAN_PHAM**: Thêm các sản phẩm giày, bao gồm các thông tin như mã sản phẩm, loại sản phẩm, màu sắc, size, giá bán, và mô tả.
4. **KHO**: Thêm dữ liệu kho hàng cho từng chi nhánh, cùng với số lượng tồn kho của từng sản phẩm.
5. **KHACH_HANG**: Thêm thông tin khách hàng, bao gồm tên, số điện thoại, email, địa chỉ và loại khách hàng.
6. **NHAN_VIEN**: Thêm thông tin nhân viên, bao gồm chức vụ và thông tin liên hệ.
7. **HOA_DON**: Thêm các hóa đơn với thông tin về ngày lập, khách hàng, tổng tiền, trạng thái thanh toán, phương thức thanh toán và loại hóa đơn.
8. **CHI_TIET_HOA_DON**: Thêm chi tiết về các sản phẩm trong mỗi hóa đơn, bao gồm số lượng và giá bán.

Dữ liệu trên chỉ mang tính minh họa và có thể được thay đổi tùy theo nhu cầu thực tế của bạn.
