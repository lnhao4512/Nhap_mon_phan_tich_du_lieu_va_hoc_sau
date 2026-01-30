
# Lab 2 – Thống kê và trình bày dữ liệu xét tuyển đại học  
**Môn học:** Nhập môn Phân tích dữ liệu và Học sâu  
**Họ tên:** Lương Nhật Hào  
**MSSV:** 2374802010128  
**Tuần:** 2  

## Mô tả bài lab

Bài thực hành Tuần 2 tập trung vào kỹ năng **thống kê mô tả** và **trình bày dữ liệu** bằng Python (chủ yếu sử dụng pandas và numpy).

**Dataset:** Dữ liệu xét tuyển đại học (sau khi đã xử lý sơ bộ)  
- Tên file: `processed_dulieuxettuyendaihoc.csv`  
- Số lượng mẫu: 100 thí sinh  
- Số lượng cột: 66 cột (bao gồm thông tin cá nhân, khu vực, đối tượng ưu tiên, khối thi, điểm các môn thi, điểm tổng các tổ hợp xét tuyển DH1, DH2, DH3, v.v.)  

**Mục tiêu chính của lab:**
- Thực hành sắp xếp dữ liệu theo nhiều tiêu chí
- Tính toán các thống kê mô tả (count, sum, mean, median, min, max, std, tứ phân vị) trên các nhóm
- Sử dụng pivot table để tổng hợp dữ liệu đa chiều
- Trình bày phân bố của biến phân loại (giới tính) bằng bảng tần số và biểu đồ

## Công nghệ & Thư viện sử dụng

| Thư viện   | Công dụng chính                              |
|------------|----------------------------------------------|
| pandas     | Xử lý dữ liệu bảng, groupby, pivot_table, thống kê mô tả |
| numpy      | Hỗ trợ tính toán số học (không dùng nhiều trong lab này) |
| matplotlib | Vẽ biểu đồ cột và biểu đồ tròn (thông qua pandas plotting) |

**Môi trường chạy đề xuất:**
- Jupyter Notebook / JupyterLab
- Google Colab (mở trực tiếp từ GitHub)
- Python 3.8+

## Cấu trúc notebook

Notebook được chia thành hai phần chính:

### Phần 1: Thống kê dữ liệu
1. Sắp xếp dữ liệu theo điểm DH1 tăng dần
2. Sắp xếp điểm DH2 tăng dần theo nhóm giới tính (GT)
3. Pivot table thống kê DH1 theo khối thi (KT): count, sum, mean, median, min, max, std, Q1, Q2, Q3
4. Pivot table DH1 theo KT và khu vực (KV)
5. Pivot table DH1 theo KT, KV và đối tượng ưu tiên (DT)

### Phần 2: Trình bày dữ liệu
1. Thống kê biến giới tính (GT):
   - Bảng tần số (frequency table)
   - Tần suất tương đối (%)
   - Biểu đồ cột (bar chart)
   - Biểu đồ tròn (pie chart)

## Cách chạy notebook

**Cách 1 – Google Colab (dễ nhất)**
1. Mở link notebook trên GitHub:  
   https://github.com/lnhao4512/Nhap_mon_phan_tich_du_lieu_va_hoc_sau/blob/main/Tuan_2/0301_LuongNhatHao_2374802010128_Lab2%20(1).ipynb
2. Nhấn nút **Open in Colab** (góc trên bên phải)
3. Chạy lần lượt các cell (Shift + Enter)

**Cách 2 – Local**
```bash
# Clone repo (nếu chưa có)
git clone https://github.com/lnhao4512/Nhap_mon_phan_tich_du_lieu_va_hoc_sau.git
cd Nhap_mon_phan_tich_du_lieu_va_hoc_sau/Tuan_2

# Cài đặt (nếu cần)
pip install pandas matplotlib

# Chạy jupyter
jupyter notebook
