# Lab 1 – Nhập môn Phân tích dữ liệu  
**Môn học:** Nhập môn Phân tích dữ liệu và Học sâu  
**Họ tên:** Lương Nhật Hào  
**MSSV:** 2374802010128  
**Tuần:** 1  

## Mô tả bài lab

Đây là bài thực hành đầu tiên trong môn học, tập trung vào việc làm quen với quy trình **phân tích dữ liệu khám phá (Exploratory Data Analysis – EDA)** bằng Python.

Mục tiêu chính:
- Làm quen với các thư viện phân tích dữ liệu phổ biến
- Đọc, làm sạch và khám phá dữ liệu
- Trực quan hóa dữ liệu bằng các biểu đồ cơ bản
- Rút ra một số nhận xét/insight ban đầu từ dữ liệu

## Công nghệ & Thư viện sử dụng

| Thư viện       | Phiên bản đề xuất | Công dụng chính                              |
|----------------|-------------------|----------------------------------------------|
| pandas         | ≥ 1.5             | Xử lý và phân tích dữ liệu dạng bảng         |
| numpy          | ≥ 1.23            | Tính toán số học, mảng                       |
| matplotlib     | ≥ 3.7             | Vẽ biểu đồ cơ bản                            |
| seaborn        | ≥ 0.12            | Trực quan hóa thống kê đẹp và dễ dùng hơn    |
| (tùy chọn) sklearn | ≥ 1.2         | Một số hàm hỗ trợ EDA hoặc chia dữ liệu      |

Môi trường chạy đề xuất:
- **Jupyter Notebook** / **JupyterLab**
- **Google Colab** (không cần cài đặt)
- Python 3.9 – 3.11

## Cấu trúc notebook

Notebook được chia thành các phần chính sau:

1. **Import thư viện**  
   Khai báo tất cả các package cần thiết.

2. **Đọc dữ liệu**  
   - Load file dữ liệu (thường là .csv) bằng `pd.read_csv()`

3. **Khám phá dữ liệu ban đầu (Initial Exploration)**  
   - Xem 5 dòng đầu/cuối: `.head()`, `.tail()`  
   - Thông tin tổng quan: `.info()`, `.describe()`  
   - Kích thước dữ liệu: `.shape`  
   - Kiểm tra giá trị thiếu: `.isnull().sum()`

4. **Làm sạch dữ liệu cơ bản (nếu cần)**  
   - Xử lý missing values (điền trung bình, loại bỏ dòng/cột...)  
   - Chuyển đổi kiểu dữ liệu  
   - Xử lý giá trị bất thường/outliers (nếu có)

5. **Phân tích đơn biến (Univariate Analysis)**  
   - Biểu đồ phân bố cho biến số (histogram, KDE plot)  
   - Biểu đồ đếm cho biến phân loại (countplot, barplot)  
   - Boxplot để phát hiện outliers

6. **Ph
