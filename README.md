# baitaplon
# CHƯƠNG TRÌNH QUẢN LÝ NHÂN VIÊN QUÁN BIA
***

**Tác giả: Nguyễn Hoàng Hiệp**

**MSSV:k215480106094**

**Lớp:k57kmt**

**Ngày hoàn thành :19/6/2024

Mô tả bài toán quản lý : Quản lý nhân viên là một trong những phần quan trọng trong hoạt động của một quán bia. Việc theo dõi thông tin nhân viên, chấm công, lương và hóa đơn là các nhiệm vụ không thể thiếu để đảm bảo hoạt động trơn tru và hiệu quả. Bài toán này yêu cầu xây dựng một hệ quản trị cơ sở dữ liệu để quản lý các thông tin này.
***

## NHỮNG CHỨC NĂNG QUẢN LÝ NHÂN VIÊN QUÁN BIA:
1. Quản lý nhân viên
- Thêm , sửa , xóa thông tin nhân viên
- Lưu trữ và tra cứu thông tin nhân viên
2. Quản lý phòng ban và chức vụ
- Quản lý phòng ban
- quản lý chức vụ
3. Quản lý chấm công
- Ghi nhận chấm công
- Sửa , xóa thông tin chấm công
- Tra cứu chấm công
4. Quản lý lương
- Tính lương thực tế
- Cập nhật và tra cứu lương 
5. Quản lý hóa đơn
- Lập hóa đơn
- Sửa , xóa hóa đơn
- Tra cứu hóa đơn
6. Báo cáo và thống kê
- Báo cáo nhân viên
- Báo cáo chấm công
- Báo cáo lương
- Báo cáo hóa đơn
7. Bảo mật và phân quyền
- Quản lý tài khoản người dùng
- Phân quyền
8. Giao diện người dùng
- Giao diện quản lý
- Giao diện nhân viên
## Lên ý tưởng xây dựng các bảng quản lý quán bia:

1. Bảng nhân viên: Mã nhân viên: MaNV (INT, Primary Key)Tên nhân viên: TenNV (NVARCHAR(50))Ngày sinh: NgaySinh (DATE)Giới tính: GioiTinh (NVARCHAR(10))Địa chỉ: DiaChi (NVARCHAR(100))Mã phòng ban: MaPhongBan(INT, Foreign Key từ bảng PhongBan)Mã chức vụ: MaChucVu (INT, Foreign Key từ bảng ChucVu)Lương cơ bản: LuongCoBan (DECIMAL(10, 2))
2. Bảng phòng ban:Mã phòng ban: MaPhongBan (INT, Primary Key)Tên phòng ban: TenPhongBan (NVARCHAR(50))
3. Bảng chức vụ: Mã chức vụ: MaChucVu (INT, Primary Key)Tên chức vụ: TenChucVu (NVARCHAR(50))Hệ số lương: HeSoLuong (DECIMAL(5, 2))
4. Bảng chấm công: Mã nhân viên: MaNV (INT, Foreign Key từ bảng NhanVien)Ngày: Ngay (DATE)Số giờ làm: SoGioLam (INT)Primary Key: (MaNV, Ngay)
5. Bảng lương: Mã nhân viên: MaNV (INT, Foreign Key từ bảng NhanVien)Tháng: Thang (INT)Năm: Nam (INT)Lương thực tế: LuongThucTe (DECIMAL(10, 2))Primary Key: (MaNV, Thang, Nam)
6. Bảng hóa đơn: Mã hóa đơn: MaHD (INT, Primary Key)Mã nhân viên: MaNV (INT, Foreign Key từ bảng NhanVien)Ngày lập: NgayLap (DATE)Tổng tiền: TongTien (DECIMAL(15, 2))
  
Như vậy , dựa theo những thông tin mà ta đã thu thập được chúng ta sẽ xây dựng các bảng đáp ứng yêu cầu quản lý nhân viên quán bia.

Tạo các bảng như mô tả trong SQL Sever :
1. Bảng nhân viên

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/cebdb97e-4cca-48a1-ad1d-48ea169a8aa0)

2. Bảng phòng ban

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/0d82da12-5ea1-4999-8205-204e91cd4e90)

3. Bảng lương

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/e99dfb75-5909-456f-91cd-3ea67444daf9)

4. Bảng hóa đơn

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/e943d87f-ee10-4817-9f81-eaceffbb9321)

5. Bảng chức vụ

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/e57b4477-5df0-4e7d-83c3-1b35c9683669)

6. Bảng chấm công

![image](https://github.com/hiepga123jiodf/baitaplon/assets/173077320/5d760878-f280-42d1-96a5-69526a7eef04)

Thâm dữ liệu vào các bảng
1. Dữ liệu vào bảng NhanVieN
```SQL

CREATE TABLE NhanVien (
    MaNV INT PRIMARY KEY,
    TenNV NVARCHAR(50),
    NgaySinh DATE,
    GioiTinh NVARCHAR(10),
    DiaChi NVARCHAR(100),
    MaPhongBan INT,
    MaChucVu INT,
    LuongCoBan DECIMAL(10, 2)
);
```

2. Dữ liệu vào bảng phòng ban
```SQL
CREATE TABLE PhongBan (
    MaPhongBan INT PRIMARY KEY,
    TenPhongBan NVARCHAR(50)
);
```

3. Dữ liệu vào bảng chức vụ
```SQL
CREATE TABLE ChucVu (
    MaChucVu INT PRIMARY KEY,
    TenChucVu NVARCHAR(50),
    HeSoLuong DECIMAL(5, 2)
);
```

4. Dữ liệu vào bảng lương
```SQL
CREATE TABLE Luong (
    MaNV INT,
    Thang INT,
    Nam INT,
    LuongThucTe DECIMAL(10, 2),
    PRIMARY KEY (MaNV, Thang, Nam),
    FOREIGN KEY (MaNV) REFERENCES NhanVien(MaNV)
);
```

5. Dữ liệu vào bảng chấm công
```SQL
CREATE TABLE ChamCong (
    MaNV INT,
    Ngay DATE,
    SoGioLam INT,
    PRIMARY KEY (MaNV, Ngay),
    FOREIGN KEY (MaNV) REFERENCES NhanVien(MaNV)
);
```

6. Dữ liệu vào bảng hóa đơn
```SQL
CREATE TABLE HoaDon (
    MaHD INT PRIMARY KEY,
    MaNV INT,
    NgayLap DATE,
    TongTien DECIMAL(15, 2),
    FOREIGN KEY (MaNV) REFERENCES NhanVien(MaNV)
);
```

## XÂY DỰNG CÁC THỦ TỰC THEO CÁC CHỨC NĂNG MONG MUỐN
1. Thủ tục quản lý nhân viên
  Thêm nhân viên
```SQL
CREATE PROCEDURE ThemNhanVien
    @TenNV NVARCHAR(50),
    @NgaySinh DATE,
    @GioiTinh NVARCHAR(10),
    @DiaChi NVARCHAR(100),
    @MaPhongBan INT,
    @MaChucVu INT,
    @LuongCoBan DECIMAL(10, 2)
AS
BEGIN
    INSERT INTO NhanVien (TenNV, NgaySinh, GioiTinh, DiaChi, MaPhongBan, MaChucVu, LuongCoBan)
    VALUES (@TenNV, @NgaySinh, @GioiTinh, @DiaChi, @MaPhongBan, @MaChucVu, @LuongCoBan);
END;
```
Cập nhật thông tin  nhân viên
```SQL
CREATE PROCEDURE CapNhatNhanVien
    @MaNV INT,
    @TenNV NVARCHAR(50),
    @NgaySinh DATE,
    @GioiTinh NVARCHAR(10),
    @DiaChi NVARCHAR(100),
    @MaPhongBan INT,
    @MaChucVu INT,
    @LuongCoBan DECIMAL(10, 2)
AS
BEGIN
    UPDATE NhanVien
    SET TenNV = @TenNV,
        NgaySinh = @NgaySinh,
        GioiTinh = @GioiTinh,
        DiaChi = @DiaChi,
        MaPhongBan = @MaPhongBan,
        MaChucVu = @MaChucVu,
        LuongCoBan = @LuongCoBan
    WHERE MaNV = @MaNV;
END;
```
Xóa nhân viên
```SQL
CREATE PROCEDURE XoaNhanVien
    @MaNV INT
AS
BEGIN
    DELETE FROM NhanVien
    WHERE MaNV = @MaNV;
END;
```

2. Thủ tục quanr lý chấm công
Ghi nhận chấm công
```SQL
CREATE PROCEDURE GhiNhanChamCong
    @MaNV INT,
    @Ngay DATE,
    @SoGioLam INT
AS
BEGIN
    INSERT INTO ChamCong (MaNV, Ngay, SoGioLam)
    VALUES (@MaNV, @Ngay, @SoGioLam);
END;
```
Cập nhật chấm công
```SQL
CREATE PROCEDURE CapNhatChamCong
    @MaNV INT,
    @Ngay DATE,
    @SoGioLam INT
AS
BEGIN
    UPDATE ChamCong
    SET SoGioLam = @SoGioLam
    WHERE MaNV = @MaNV AND Ngay = @Ngay;
END;
```
Xóa chấm công
```SQL
CREATE PROCEDURE XoaChamCong
    @MaNV INT,
    @Ngay DATE
AS
BEGIN
    DELETE FROM ChamCong
    WHERE MaNV = @MaNV AND Ngay = @Ngay;
END;
```

3. Thủ tục tính lương
 Tính lương thức tế
```SQL
CREATE PROCEDURE TinhLuongThucTe
    @MaNV INT,
    @Thang INT,
    @Nam INT
AS
BEGIN
    DECLARE @SoGioLam INT;
    DECLARE @LuongCoBan DECIMAL(10, 2);
    DECLARE @HeSoLuong DECIMAL(5, 2);
    DECLARE @LuongThucTe DECIMAL(10, 2);

    SELECT @SoGioLam = SUM(SoGioLam), @LuongCoBan = LuongCoBan, @HeSoLuong = HeSoLuong
    FROM ChamCong cc
    JOIN NhanVien nv ON cc.MaNV = nv.MaNV
    JOIN ChucVu cv ON nv.MaChucVu = cv.MaChucVu
    WHERE MONTH(Ngay) = @Thang AND YEAR(Ngay) = @Nam AND cc.MaNV = @MaNV
    GROUP BY LuongCoBan, HeSoLuong;

    SET @LuongThucTe = @SoGioLam * @HeSoLuong * @LuongCoBan;

    INSERT INTO Luong (MaNV, Thang, Nam, LuongThucTe)
    VALUES (@MaNV, @Thang, @Nam, @LuongThucTe);
END;
```

4. Thủ tực quản lý hóa đơn
   Lập hóa đơn
   ```SQL
   CREATE PROCEDURE LapHoaDon
    @MaNV INT,
    @NgayLap DATE,
    @TongTien DECIMAL(15, 2)
   AS
   BEGIN
    INSERT INTO HoaDon (MaNV, NgayLap, TongTien)
    VALUES (@MaNV, @NgayLap, @TongTien);
   END;
   ```
   Cập nhật hóa đơn
   ```SQL
   CREATE PROCEDURE CapNhatHoaDon
    @MaHD INT,
    @MaNV INT,
    @NgayLap DATE,
    @TongTien DECIMAL(15, 2)
    AS
   BEGIN
    UPDATE HoaDon
    SET MaNV = @MaNV,
        NgayLap = @NgayLap,
        TongTien = @TongTien
    WHERE MaHD = @MaHD;
   END;
   ```
   Xóa hóa đơn
   ```SQL
   CREATE PROCEDURE XoaHoaDon
    @MaHD INT
   AS
   BEGIN
    DELETE FROM HoaDon
    WHERE MaHD = @MaHD;
   END;
   ```

   5. Thủ tục quản lý đặt bàn
      Đặt bàn
      ```SQL
      CREATE PROCEDURE DatBan
      @MaKH INT,
      @NgayDat DATE,
      @ThoiGianDat TIME,
      @SoLuongKhach INT
      AS
      BEGIN
      INSERT INTO DatBan (MaKH, NgayDat, ThoiGianDat, SoLuongKhach)
      VALUES (@MaKH, @NgayDat, @ThoiGianDat, @SoLuongKhach);
      END;
      ```
      Cập nhật đặt bàn
      ```SQL
      CREATE PROCEDURE CapNhatDatBan
      @MaDB INT,
      @MaKH INT,
      @NgayDat DATE,
      @ThoiGianDat TIME,
      @SoLuongKhach INT
      AS
      BEGIN
      UPDATE DatBan
      SET MaKH = @MaKH,
        NgayDat = @NgayDat,
        ThoiGianDat = @ThoiGianDat,
        SoLuongKhach = @SoLuongKhach
      WHERE MaDB = @MaDB;
      END;
      ```
      Xóa đặt bàn
      ```SQL
      CREATE PROCEDURE XoaDatBan
      @MaDB INT
      AS
      BEGIN
      DELETE FROM DatBan
      WHERE MaDB = @MaDB;
      END;
      ```
      Chương trình quản lý nhân viên quán bia được xây dựng bằng SQL đóng vai trò quan trọng trong việc tối ưu hoá và quản lý hiệu quả các hoạt động kinh doanh của quán. Bằng cách tổ chức thông tin nhân viên, quản lý chấm công, tính lương, hóa đơn và đặt bàn, chương trình không chỉ giúp cải thiện trải nghiệm khách hàng mà còn hỗ trợ quản lý đưa ra các quyết định chiến lược dựa trên dữ liệu và phân tích. Với vai trò đa năng và chi tiết, chương trình giúp quán bia tối ưu hoá hoạt động và nâng cao hiệu quả kinh doanh trong môi trường cạnh tranh ngày càng gay gắt.



 




















   

