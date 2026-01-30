# Lab 3 – Làm sạch và tiền xử lý dữ liệu (Data Cleaning & Preprocessing)  
**Môn học:** Nhập môn Phân tích dữ liệu và Học sâu  
**Họ tên:** Lương Nhật Hào  
**MSSV:** 2374802010128  
**Tuần:** 3  

## Mô tả bài lab

Bài thực hành Tuần 3 tập trung vào các kỹ thuật **làm sạch dữ liệu** và **tiền xử lý** (data wrangling) để biến dữ liệu thô thành dạng sạch, sẵn sàng cho phân tích hoặc mô hình hóa.

**Dataset:** Dữ liệu đo nhịp tim bệnh nhân (`patient_heart_rate.csv`)  
- Nguồn: Dữ liệu mẫu thực hành (thường dùng trong các khóa học về data cleaning)  
- Đặc điểm ban đầu: Không có header, cột đo nhịp tim theo giới tính + khung giờ được pivot rộng (wide format), nhiều missing values, đơn vị không thống nhất, trùng lặp, ký tự đặc biệt...  
- Sau xử lý: Dạng tidy/long format với các cột chính: `Id`, `Firstname`, `Lastname`, `Age`, `Weight` (kg), `sex`, `Time`, `PulseRate`  
- Số lượng mẫu cuối: ≈ 65 dòng (sau khi loại bỏ trùng lặp và một số dòng thiếu nghiêm trọng)  

**Mục tiêu chính:**
- Xử lý các vấn đề phổ biến trong dữ liệu thực tế: thiếu header, missing values, đơn vị không đồng nhất, trùng lặp, ký tự non-ASCII, dữ liệu wide → long format.
- Áp dụng các kỹ thuật imputation (điền giá trị thiếu) theo thứ tự ưu tiên logic.
- Biến dữ liệu thành dạng **tidy data** (mỗi biến một cột, mỗi quan sát một hàng).

## Công nghệ & Thư viện sử dụng

| Thư viện   | Công dụng chính                              |
|------------|----------------------------------------------|
| pandas     | Đọc dữ liệu, xử lý bảng, melt/pivot, xử lý missing, drop duplicates, string manipulation |
| numpy      | Hỗ trợ tính toán (dùng ít trong lab này)     |

**Môi trường chạy đề xuất:**
- Jupyter Notebook / JupyterLab
- Google Colab
- Python 3.8+

## Cấu trúc notebook (theo các vấn đề được giao)

Notebook được tổ chức theo từng **vấn đề** cụ thể:

1. **Vấn đề 1** – Tải dữ liệu & xử lý thiếu header  
   → `pd.read_csv(..., header=None, names=[...])`

2. **Vấn đề 2** – Tách cột `Name` thành `Firstname` và `Lastname`

3. **Vấn đề 3** – Chuẩn hóa đơn vị cân nặng (`Weight`) từ lbs → kg (chia 2.2)

4. **Vấn đề 4** – Xóa các dòng hoàn toàn rỗng (`dropna(how='all')`)

5. **Vấn đề 5** – Loại bỏ bản ghi trùng lặp dựa trên `Firstname`, `Lastname`, `Age`, `Weight`

6. **Vấn đề 6** – Xử lý ký tự non-ASCII / đặc biệt trong tên (regex)

7. **Vấn đề 7** – Xử lý missing values ở `Age` và `Weight` (mean imputation, xóa dòng thiếu cả hai)

8. **Vấn đề 8** – Phân rã các cột đo nhịp tim (`m0006`, `m0612`, ..., `f1218`) bằng `pd.melt` → tạo cột `sex`, `Time`, `PulseRate`

9. **Vấn đề 11** – Xử lý missing values trên `PulseRate` theo thứ tự ưu tiên:  
   - Giá trị trước/sau gần nhất  
   - Trung bình 2 giá trước/sau  
   - Mean theo cá nhân → theo giới tính → toàn bộ dữ liệu  
   - Giá trị mặc định y học (75 bpm nếu không còn cách nào)

10. **Vấn đề 12** – Rút gọn cột, sắp xếp lại, reset index, làm tròn số, lưu file sạch: `patient_heart_rate_clean.csv`

## Cách chạy notebook

**Cách 1 – Google Colab (khuyến nghị)**  
1. Mở link notebook trên GitHub:  
   https://github.com/lnhao4512/Nhap_mon_phan_tich_du_lieu_va_hoc_sau/blob/main/Tuan_3/0301_LuongNhatHao_2374802010128_Lab3.ipynb  
2. Nhấn **Open in Colab** (góc phải trên)  
3. Chạy lần lượt các cell (Shift + Enter)

**Cách 2 – Local**  
```bash
# Clone repo nếu chưa có
git clone https://github.com/lnhao4512/Nhap_mon_phan_tich_du_lieu_va_hoc_sau.git
cd Nhap_mon_phan_tich_du_lieu_va_hoc_sau/Tuan_3

# Cài đặt (thường không cần vì chỉ dùng pandas + numpy)
pip install pandas numpy

# Chạy jupyter
jupyter notebook
