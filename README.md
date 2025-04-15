# BT4HQTCSDL
## Bài làm  
Truy cập vào [TMS.tnut.edu.vn](https://tms.tnut.edu.vn/tkb/lop.html) để lấy dữ liệu, ở đây ta sẽ lấy ví dụ là thời khóa biểu Tuần: 33 (14/04/2025 → 20/04/2025) của lớp K58KTP.K01
![image](https://github.com/user-attachments/assets/5bf0fa55-bceb-413a-974b-7581dafc944d)  
Tạo database có tên là __TKB-K58KTP.K01__, sau đó tiến hành tạo các bảng có tên là __GiangVien, Lop, MonHoc, Phong, TietHoc, LichDay__
![image](https://github.com/user-attachments/assets/c52ae6db-e174-4d33-a256-9a193b70beca)  
Các bảng khác làm tương tự, lưu ý các bảng tạo ra phải đạt chuẩn 3NF. Chuẩn 3NF (*Third Normal Form*) là một cấp độ chuẩn hóa cơ sở dữ liệu nhằm loại bỏ sự dư thừa dữ liệu và đảm bảo tính toàn vẹn.  
Nhập demo bảng GiangVien
![image](https://github.com/user-attachments/assets/f92fc0e1-c98a-4a20-9948-c59db441bd16)  
Nhập demo bảng Lop
![image](https://github.com/user-attachments/assets/e3ba57ea-66c2-414b-aff8-dc8ab032aa0b)  
Nhập demo bảng Phong 
![image](https://github.com/user-attachments/assets/c4a3bfc1-889e-4f29-8be2-64970835a1c1)
Nhập demo bảng MonHoc  
![image](https://github.com/user-attachments/assets/d7bdbbfa-b838-4de0-bf3b-19ea890a608b)
Nhập demo bảng TietHoc  
![image](https://github.com/user-attachments/assets/b587e09f-3f7c-42ec-afb0-78d38bcf8515)
Nhập demo bảng LịchDay  
![image](https://github.com/user-attachments/assets/84ad5aff-0d49-4561-b962-5631846d4261)  
Khi hoàn thành các bước trên ta có được sơ đồ sau.  
![image](https://github.com/user-attachments/assets/3f72ca77-bb8b-4ae4-8431-0c86c6aa6632)  
## Tạo query truy vẫn thông tin  
![image](https://github.com/user-attachments/assets/8283d758-a6aa-4b56-ab2c-bad1559ce779) 

```
USE TKB
GO 

DECLARE @datetime1 DATETIME = '2025-04-16 06:30:00';
DECLARE @datetime2  DATETIME = '2025-04-16 09:10:00';

SELECT DISTINCT
    GV.TenGV      AS N'Họ tên GV',
    MH.TenMon      AS N'Môn dạy',
    L.TenLop             AS N'Lớp học',
    LD.MaPhong    AS N'Phòng học',
    LD.GioVao    AS N'tiết bắt đầu',
    LD.GioRa    AS N'tiết kết thúc'
FROM dbo.LichDay LD
JOIN dbo.GiangVien GV  ON LD.MaGV = GV.Magv
JOIN dbo.MonHoc MH  ON LD.MaMon = MH.MaMon
JOIN dbo.Lop L ON LD.MaLop = l.MaLop 
WHERE
    CAST(LD.Ngay AS DATETIME) + CAST(LD.GioRa AS DATETIME) > @datetime1
AND CAST(LD.Ngay AS DATETIME) + CAST(LD.GioVao AS DATETIME) < @datetime2;
```





 
 


  

- 
