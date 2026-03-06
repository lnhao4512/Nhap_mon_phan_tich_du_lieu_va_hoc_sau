Lab 5 – Titanic Data Cleaning & Exploratory Data Analysis
1. Công nghệ sử dụng

Bài lab được thực hiện bằng Python và các thư viện phân tích dữ liệu phổ biến:

Python

Pandas – xử lý và phân tích dữ liệu

NumPy – tính toán số học

Matplotlib – vẽ biểu đồ

Seaborn – trực quan hóa dữ liệu

Jupyter Notebook – môi trường chạy code và trình bày kết quả

Dataset sử dụng: Titanic Dataset (titanic_disaster.csv).

2. Cách hoạt động

Bài lab thực hiện quy trình Data Cleaning + Feature Engineering + Exploratory Data Analysis (EDA) trên dữ liệu Titanic.

Bước 1: Tải dữ liệu

Sử dụng pandas.read_csv() để đọc file dữ liệu Titanic.

Hiển thị 10 dòng đầu tiên để quan sát cấu trúc dữ liệu.

Bước 2: Kiểm tra dữ liệu thiếu

Sử dụng:

df.isnull().sum()

để thống kê dữ liệu bị thiếu.

Sử dụng Heatmap (Seaborn) để trực quan hóa vị trí dữ liệu bị thiếu.

Các cột thiếu nhiều dữ liệu:

Age

Cabin

Embarked

Bước 3: Xử lý cột Name

Cột Name được tách thành các thành phần:

LastName

Title

FirstName

Sau đó xóa cột Name ban đầu để giảm kích thước dữ liệu.

Bước 4: Chuẩn hóa dữ liệu giới tính

Cột Sex được rút gọn:

Giá trị cũ	Giá trị mới
male	M
female	F
Bước 5: Xử lý dữ liệu thiếu của Age

Phân tích phân bố tuổi theo Pclass bằng Boxplot.

Sau đó thay thế giá trị Age bị thiếu bằng median theo từng nhóm Pclass:

df['Age'] = df.groupby('Pclass')['Age'].transform(
    lambda x: x.fillna(x.median())
)

Cách này giúp dữ liệu hợp lý hơn so với dùng trung bình toàn bộ.

Bước 6: Tạo biến AgeGroup

Phân loại độ tuổi thành các nhóm:

Age	AgeGroup
≤ 12	Kid
12–18	Teen
18–60	Adult
> 60	Older
Bước 7: Tạo đặc trưng Name Prefix

Tách danh xưng từ tên hành khách:

Mr

Mrs

Miss

Master

Other (các danh xưng hiếm)

Bước 8: Tạo biến Family Size

Tính số người đi cùng:

familySize = 1 + SibSp + Parch
Bước 9: Tạo biến Alone

Xác định hành khách đi một mình hay không.

Alone = 1 nếu familySize = 0
Alone = 0 nếu đi theo nhóm
Bước 10: Xử lý Cabin

Tách loại cabin bằng chữ cái đầu tiên.

Ví dụ:

C85 → C

E46 → E

Các cabin bị thiếu được thay bằng Unknown.

3. Khai thác dữ liệu (EDA)

Sau khi xử lý dữ liệu, tiến hành trực quan hóa để tìm hiểu các yếu tố ảnh hưởng đến tỷ lệ sống sót.

1. Tỷ lệ sống sót theo giới tính

Biểu đồ Countplot

Kết quả:

Nữ có tỷ lệ sống sót cao hơn nam rất nhiều.

2. Tỷ lệ sống sót theo hạng vé (Pclass)

Kết quả:

Hạng 1 sống sót nhiều nhất

Hạng 3 có tỷ lệ tử vong cao nhất

3. Tỷ lệ sống sót theo giới tính và độ tuổi

Phân tích theo:

Sex

AgeGroup

Kết quả:

Trẻ em và phụ nữ được ưu tiên cứu trước.

4. Tỷ lệ sống sót theo số người đi cùng

Biểu đồ Family Size vs Survival

Kết quả:

Người đi một mình thường có tỷ lệ sống sót thấp hơn.

Nhóm gia đình nhỏ có tỷ lệ sống sót cao hơn.

5. Tỷ lệ sống sót theo giá vé (Fare)

Fare được chia thành 4 nhóm:

Low

Medium

High

Very High

Kết quả:

Giá vé càng cao → xác suất sống sót càng lớn.

6. Tỷ lệ sống sót theo Pclass và cảng lên tàu (Embarked)

Phân tích mối quan hệ giữa:

Pclass

Embarked

Survived

4. Kết quả đạt được

Sau khi thực hiện lab:

Làm sạch dữ liệu Titanic

Xử lý dữ liệu thiếu

Tạo thêm các đặc trưng mới:

AgeGroup

namePrefix

familySize

Alone

typeCabin

Thông qua EDA, rút ra các yếu tố ảnh hưởng đến khả năng sống sót:

Giới tính – nữ sống sót nhiều hơn nam

Hạng vé (Pclass) – hạng cao sống sót nhiều hơn

Độ tuổi – trẻ em được ưu tiên cứu

Giá vé – giá vé cao có tỷ lệ sống sót cao

Gia đình đi cùng – nhóm nhỏ có cơ hội sống tốt hơn
