# b-i-t-p-3
bài tập 3
BÀI TOÁN: Sửa bài 2 để có csdl như sau:
  + SinhVien(#masv,hoten,NgaySinh)
  + Lop(#maLop,tenLop)
  + GVCN(#@maLop,#@magv,#HK)
  + LopSV(#@maLop,#@maSV,ChucVu)
  + GiaoVien(#magv,hoten,NgaySinh,@maBM)
  + BoMon(#MaBM,tenBM,@maKhoa)
  + Khoa(#maKhoa,tenKhoa)
  + MonHoc(#mamon,Tenmon,STC)
  + LopHP(#maLopHP,TenLopHP,HK,@maMon,@maGV)
  + DKMH(#id_dk, @maLopHP,@maSV,DiemThi,PhanTramThi)
  + Diem(#id, @id_dk, diem)

YÊU CẦU:
1. Sửa bảng DKMH và bảng Điểm từ bài tập 2 để có các bảng như yêu cầu.
2. Nhập dữ liệu demo cho các bảng (nhập có kiểm soát từ tính năng Edit trên UI của mssm)
3. Viết lệnh truy vấn để: Tính được điểm thành phần của 1 sinh viên đang học tại 1 lớp học phần.
4. BÀI LÀM
5.   Sửa bảng DKMH và thêm bảng điểm
![image](https://github.com/user-attachments/assets/08da90bb-50b9-44ac-92f1-fa7d861e5712)
Thêm bảng điểm vào database QLSV
![image](https://github.com/user-attachments/assets/0dde9520-3b68-4fa5-a2d1-21d890a7b658)
Tạo bảng Điểm:

![image](https://github.com/user-attachments/assets/4c13b80f-166b-4a79-8a4a-808857a80f60)
![image](https://github.com/user-attachments/assets/71c55ec9-1117-4e7e-8015-35cb8a6ca4a6)
![image](https://github.com/user-attachments/assets/8101dd6b-22ec-4e9e-bd97-ee90cffb9901)
Tạo khóa ràng buộc (CK) cho cột Diem
![image](https://github.com/user-attachments/assets/a969b54d-2e8e-4301-b841-97cc5ac0a632)

![image](https://github.com/user-attachments/assets/8d532d5a-3f44-4cb9-9bc2-b83e753bb17c)

Nhập dữ liệu cho bảng sinh viên

![image](https://github.com/user-attachments/assets/8a10c864-3b76-482e-aeb7-882a0fdbd4d1)
![image](https://github.com/user-attachments/assets/31a49875-c16a-4b23-9503-2f6017d2a2fd)
![image](https://github.com/user-attachments/assets/ff08333b-ee36-45c8-b03f-18c0c08e9fb1)
![image](https://github.com/user-attachments/assets/2e0f9cc6-bfcf-434e-80df-341aabd6501c)
![image](https://github.com/user-attachments/assets/de89d76c-10f5-42b8-9526-a3e75b597e41)

![image](https://github.com/user-attachments/assets/6533cb36-a547-4e4c-8d79-df8d98d11b6a)

![image](https://github.com/user-attachments/assets/251fdfa2-1c68-4f76-81fa-13c288f2c7a0)


![image](https://github.com/user-attachments/assets/2e645c1a-c97d-4836-85c0-efbd193ab483)

![image](https://github.com/user-attachments/assets/45dad8db-c38c-43be-838c-95ac60fed98e)

![image](https://github.com/user-attachments/assets/a0c1dbb5-9cee-48bd-bcca-1413a36b0c16)


Viết lệnh truy vấn để: Tính được điểm thành phần của 1 sinh viên đang học tại 1 lớp học phần.
SELECT 
      DKMH.MaSV MSSV, 
      LopHP.MaLopHP [Mã lớp HP], 
      LopHP.TenLopHP [Tên lớp HP], 
      DKMH.DiemThi [Điểm thi], 
      DKMH.PhanTramThi [Phần trăm thi], 
  	  COUNT(Diem.diem) AS [Số điểm thành phần],
      AVG(Diem.diem) AS [Điểm thành phần]
  FROM DKMH
  LEFT JOIN Diem ON DKMH.id_dk = Diem.id_dk
  JOIN LopHP ON DKMH.MaLopHP = LopHP.MaLopHP
  GROUP BY DKMH.MaSV, LopHP.MaLopHP, LopHP.TenLopHP, DKMH.DiemThi, DKMH.PhanTramThi
  ORDER BY LopHP.MaLopHP;
  HẾT QUẢ CHUY VẤN







