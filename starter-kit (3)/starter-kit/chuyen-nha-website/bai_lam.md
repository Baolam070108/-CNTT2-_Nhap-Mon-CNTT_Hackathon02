# BÀI LÀM – HACKATHON 02

- **Mã đề:** 10
- **Họ tên:** Cao Bảo Lâm
- **Lớp:** CNTT2
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -force
mv .\checklist_chuyen_nha.txt .\dos\
mkdir backup
cp .\data\hop_dong_thang_10.xlsx .\backup\
rm .\temp_010.tmp
cd .\logs\
ls
cd..
get-childitem -recurse -force


```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory: C:\Users\admin\Downloads\starter-kit (3)\starter-kit\chuyen-nha-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---        11/11/2026   1:39 PM                backup
d-r---        11/11/2026   1:35 PM                data
d-r---        11/11/2026   1:37 PM                dos
d-r---        11/11/2026   1:33 PM                evidence
d-r---        11/11/2026   1:35 PM                logs
d-r---        11/11/2026   1:31 PM                web
-a----         11/3/2026   7:08 AM             70 .env
-a----         11/3/2026   7:08 AM           2410 bai_lam.md


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6139 hop_dong_thang_10.xlsx


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6139 hop_dong_thang_10.xlsx


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\dos


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            155 checklist_chuyen_nha.txt


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            973 request.log


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---        11/11/2026   1:31 PM                images
-a----         11/3/2026   7:08 AM            587 app.js
-a----         11/3/2026   7:08 AM            544 index.html
-a----         11/3/2026   7:08 AM            460 style.css


    Directory: C:\Users\admin\Downloads\starter-kit
    (3)\starter-kit\chuyen-nha-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           3054 logo-movefast.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
gc .\logs\request.log | select-string "status=500" >> .\logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-10-28 08:09:39 POST /api/dat-xe status=500
2026-10-28 08:13:50 POST /api/thanh-toan status=500


```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(gc .\logs\request.log | select-string "status=404").count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-10-28 08:28:45 GET /dat-xe-cu status=404
2026-10-28 08:41:29 GET /khuyen-mai-cu status=404
2026-10-28 08:50:02 GET /khuyen-mai-cu status=404
2026-10-28 09:05:46 GET /tin-tuc status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 


```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | network | (failed)net::ERR_FILE_NOT_FOUND | images/logo-movefast.png |
| 2 | console | app.js:18 Uncaught ReferenceError: hienThiGoi is not defined |  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** website ko hiện thị đc bảng
- **Expected:** hiển thị lại bảng
- **Actual:** ko hiện nội dung bảng
- **Log:** app.js:18 Uncaught ReferenceError: hienThiGoi is not defined

### Câu tìm kiếm Google

```text
site:stackoverflow.com "app.js:18 Uncaught ReferenceError: hienThiGoi is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/hop_dong_thang_10.xlsx`, không cần ghi vào đây.
