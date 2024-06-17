# baitaplon
baitaplon
#CHƯƠNG TRÌNH QUẢN LÝ QUÁN BIA
Mô tả bài toán quản lý : Bài toán quản lý quán bia yêu cầu xây dựng một hệ thống cơ sở dữ liệu để quản lý các hoạt động hằng ngày của quán bia. Hệ thống này cần phải xử lý thông tin về khách hàng, nhân viên, các loại bia, nguyên liệu, đơn hàng, bàn và các báo cáo doanh thu .
##Những chức năng quản lý quán bia:
1.Quản lý khách hàng .
2.Quản lý nhân viên .
3.Quản lý bia và nguyên liệu .
4. Quản lý đơn hàng .
5.Quản lý bàn .
6, Báo cáo và thống kê .
##Các thông tin liên quan đến quán bia:
1.Thông tin khách hàng.
-Mã khách hàng.
-Tên khách hàng.
-Số điện thoại.
-Địa chỉ. 
-Lịch sử mua hàng.
-Yêu thích và phản hổi.
2.Thông tin nhân viên.
-Mã nhân viên.
-Tên nhân viên.
-Chức vụ.
-Lương.
-Thông tin liên lạc.
-Ca làm việc.
-Hiệu suất công việc.
3.Thông tin về bia.
-Mã bia.
-Tên bia.
-Loại bia.
-Giá.
-Số lượng tồn kho.
-Nhà cung cấp.
4.Thông tin nguyên liệu.
-Mã nguyên liệu.
-Tên nguyên liệu.
-Số lượng tồn kho.
-Nhà cung cấp.
-Ngày nhập kho.
5.Thông tin đơn hàng.
-Mã đơn hàng.
-Ngày đặt hàng.
-Mã khách hàng.
-Mã nhân viên.
-Tổng giá trị đơn hàng.
6.Thông tin chi tiết đơn hàng.
-Mã đơn hàng
-Mã bia.
-Số lượng .
-Giá.
7.Thông tin bàn.
-Mã bàn.
-Số bàn.
-Tình trạng.
-Sức chứa.
8,Thông tin đặt bàn.
-Mã đặt bàn.
-Ngày và giờ đặt bàn.
-Mã khách hàng.
-Mã bàn.
Như vậy, dựa theo những thông tin mà ta đã thu thập được chúng ta sẽ xây dựng các bảng đáp ứng yếu cầu quản lí quán bia Tạo các bảng như mô tả trong SQL sever: 
 1.Bảng khách hàng CREATE TABLE KhachHang (MaKH INT PRIMARY KEY, TenKH NVARCHAR(100), SoDienThoai NVARCHAR(15), DiaChi NVARCHAR(255) );

 2.Bảng nhân viên CREATE TABLE NhanVien ( MaNV INT PRIMARY KEY, TenNV NVARCHAR(100), ChucVu NVARCHAR(50), Luong DECIMAL(18, 2), SoDienThoai NVARCHAR(15), Email NVARCHAR(100) ); 

3.Bảng bia CREATE TABLE Bia ( MaBia INT PRIMARY KEY, TenBia NVARCHAR(100), LoaiBia NVARCHAR(50), Gia DECIMAL(18, 2), SoLuongTonKho INT );

4.Bảng nguyên liệu CREATE TABLE NguyenLieu ( MaNL INT PRIMARY KEY, TenNL NVARCHAR(100), SoLuongTonKho INT, NhaCungCap NVARCHAR(100) ); 

5.Bảng đơn hàng CREATE TABLE DonHang ( MaDH INT PRIMARY KEY, NgayDat DATE, MaKH INT, MaNV INT, FOREIGN KEY (MaKH) REFERENCES KhachHang(MaKH),  FOREIGN KEY (MaNV) REFERENCES NhanVien(MaNV) ); 

6.Bảng chi tiết đơn hàng CREATE TABLE ChiTietDonHang ( MaDH INT, MaBia INT, SoLuong INT, Gia DECIMAL(18, 2), PRIMARY KEY (MaDH, MaBia), FOREIGN KEY (MaDH) REFERENCES DonHang(MaDH), FOREIGN KEY (MaBia) REFERENCES Bia(MaBia) ); 

7.Bảng bàn CREATE TABLE Ban ( MaBan INT PRIMARY KEY, TinhTrang NVARCHAR(50) ); 

8.Bảng đặt bàn CREATE TABLE DatBan ( MaDatBan INT PRIMARY KEY, NgayDat DATETIME, MaKH INT, MaBan INT, FOREIGN KEY (MaKH) REFERENCES KhachHang(MaKH), FOREIGN KEY (MaBan) REFERENCES Ban(MaBan) );

Thêm dữ liệu vào bảng.

1.Bảng khachhang INSERT INTO KhachHang (MaKH, TenKH, SoDienThoai, DiaChi) VALUES (1, N'Nguyễn Văn A', '0901234567', N'123 Đường ABC, TP.HCM'); INSERT INTO KhachHang (MaKH, TenKH, SoDienThoai, DiaChi) VALUES (2, N'Trần Thị B', '0987654321', N'456 Đường XYZ, Hà Nội'); 

2.Bảng nhanvien INSERT INTO NhanVien (MaNV, TenNV, ChucVu, Luong, SoDienThoai, Email) VALUES (1, N'Phạm Văn C', N'Bồi bàn', 15000000, '0978123456', 'phamvanC@example.com'); INSERT INTO NhanVien (MaNV, TenNV, ChucVu, Luong, SoDienThoai, Email) VALUES (2, N'Nguyễn Thị D', N'Quản lý', 25000000, '0987654321', 'nguyenthid@example.com'); 

3.Bảng bia INSERT INTO Bia (MaBia, TenBia, LoaiBia, Gia, SoLuongTonKho) VALUES (1, N"Bia Sài Gòn", N'Lager', 25000, 100); INSERT INTO Bia (MaBia, TenBia, LoaiBia, Gia, SoLuongTonKho) VALUES (2, N"Bia Hà Nội", N'Lager', 23000, 80); 

4.Bảng nguyenlieu INSERT INTO NguyenLieu (MaNL, TenNL, SoLuongTonKho, NhaCungCap) VALUES (1, N'Nguyên liệu A', 500, N'ABC Company'); INSERT INTO NguyenLieu (MaNL, TenNL, SoLuongTonKho, NhaCungCap) VALUES (2, N'Nguyên liệu B', 800, N'XYZ Supplier'); 

5,Bảng donhang và chitietdonhang NSERT INTO DonHang (MaDH, NgayDat, MaKH, MaNV) VALUES (1, '2024-06-17', 1, 1); - INSERT INTO ChiTietDonHang (MaDH, MaBia, SoLuong, Gia) VALUES (1, 1, 2, 25000); INSERT INTO ChiTietDonHang (MaDH, MaBia, SoLuong, Gia) VALUES (1, 2, 3, 23000); 

6.Bảng ban INSERT INTO Ban (MaBan, TinhTrang) VALUES (1, N'Trống'); INSERT INTO Ban (MaBan, TinhTrang) VALUES (2, N'Đã đặt trước'); INSERT INTO Ban (MaBan, TinhTrang) VALUES (3, N'Đang sử dụng'); 

7.Bảng datban INSERT INTO DatBan (MaDatBan, NgayDat, MaKH, MaBan) VALUES (1, '2024-06-18 10:00:00', 2, 2); INSERT INTO DatBan (MaDatBan, NgayDat, MaKH, MaBan) VALUES (2, '2024-06-19 19:00:00', 1, 3); 
