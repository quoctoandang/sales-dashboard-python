# 📊 Sales Dashboard Python

> Phân tích dữ liệu doanh số bán hàng & Dashboard tương tác với Python

## 📋 Giới Thiệu

Dự án phân tích dữ liệu doanh số bán hàng giày dép của cửa hàng **AVA SPORT** (thuộc tập đoàn Mobile World Investment Corporation - MWG) trong giai đoạn từ **02/06/2022 đến 04/06/2022**.

## 🎯 Mục Tiêu Dự Án

Phân tích và trực quan hóa dữ liệu bán hàng để trả lời các câu hỏi kinh doanh quan trọng:

1. Người tiêu dùng thường mua hàng qua hình thức nào (Online/Cửa hàng)?
2. Hãng sản xuất nào được ưa chuộng nhất?
3. Nhóm hàng nào được bán ra nhiều nhất?
4. Sự phân phối của hình thức giao hàng?
5. Sự tương quan giữa giá gốc và giá bán?
6. Doanh thu theo khu vực (tỉnh/thành phố)?
7. Phân tích độ ưa chuộng hãng giày/dép theo thành phố?
8. Top 10 sản phẩm bán chạy nhất?
9. Doanh thu theo từng ngày dựa vào nhóm hàng?
10. Siêu thị có doanh thu cao nhất theo ngày?

## 📁 Cấu Trúc Dự Án

```
sales-dashboard-python/
├── Nhom3.ipynb          # Jupyter Notebook chính chứa phân tích
├── assets/
│   └── reset.css        # CSS cho Dashboard
└── README.md            # Tài liệu dự án
```

## 🛠️ Công Nghệ Sử Dụng

| Thư viện | Mục đích |
|----------|----------|
| **Pandas** | Xử lý và thao tác dữ liệu |
| **NumPy** | Tính toán số học |
| **Matplotlib** | Trực quan hóa dữ liệu cơ bản |
| **Seaborn** | Trực quan hóa dữ liệu nâng cao |
| **Plotly** | Biểu đồ tương tác |
| **Dash** | Xây dựng Dashboard |
| **Dash Bootstrap Components** | Giao diện Dashboard |

## 📊 Dữ Liệu

### Nguồn Dữ Liệu
- **Nguồn:** Doanh số bán hàng từ 02/06/2022 - 04/06/2022 của AVA SPORT
- **Thu thập bởi:** Thảo (từ công ty MWG)
- **Thời gian thu thập:** 20/11/2022

### Các Thuộc Tính Chính (34 cột)
| # | Thuộc tính | Mô tả |
|---|------------|-------|
| 1 | Mã đơn hàng | Mã định danh duy nhất cho mỗi đơn hàng |
| 2 | Hình thức xuất | Loại hình bán hàng (Online Shopee, tại siêu thị, trả góp,...) |
| 3 | Ngày tạo | Thời gian đặt hàng |
| 4 | Tên khách hàng | Thông tin khách hàng |
| 5 | Phải thu | Tổng số tiền (bao gồm phí giao hàng, VAT) |
| 6 | Đã thu | Khách hàng đã thanh toán |
| 7 | Nhóm hàng | Giày nam, Giày nữ, Giày Unisex, Dép Unisex |
| 8 | Nhà sản xuất | Nike, Adidas, Biti's,... |
| 9 | Siêu thị xuất | Siêu thị thực hiện xuất hàng |
| 10 | Tỉnh | TP.HCM, Bình Phước, Kiên Giang |

## 🔧 Quy Trình Xử Lý Dữ Liệu

### 1. Đọc và Khám Phá Dữ Liệu
```python
df = pd.read_excel('02-04_06 Giày Dép.xlsx')
df.info()
df.describe()
```

### 2. Tiền Xử Lý Dữ Liệu
- **Loại bỏ cột không cần thiết:** Ngày, Khoảng cách giao hàng, Còn nợ,...
- **Xử lý Missing Values:**
  - Loại bỏ cột có > 30% giá trị null (CTKM_1)
  - Thay thế giá trị null bằng 'Unknown' cho các cột khác
- **Xử lý Outliers:** Sử dụng phương pháp IQR (Interquartile Range)

### 3. Phân Tích & Trực Quan Hóa
- Biểu đồ Pie Chart, Bar Chart, Scatter Plot
- Heatmap tương quan
- Boxplot phát hiện outliers

### 4. Dashboard Tương Tác
Dashboard được xây dựng bằng **Dash** với các tính năng:
- Chọn ngày để xem doanh thu
- Lọc theo các thuộc tính khác nhau
- Biểu đồ tương tác với Plotly

## 🚀 Cài Đặt & Chạy Dự Án

### Yêu Cầu
- Python 3.8+
- Jupyter Notebook hoặc VS Code

### Cài Đặt Thư Viện
```bash
pip install pandas numpy matplotlib seaborn plotly dash dash-bootstrap-components dash-bootstrap-templates openpyxl
```

### Chạy Notebook
1. Mở file `Nhom3.ipynb` trong Jupyter Notebook hoặc VS Code
2. Chạy từng cell theo thứ tự

### Chạy Dashboard
Chạy cell cuối cùng trong notebook để khởi động server:
```python
if __name__ == '__main__':
    app.run_server(debug=True, use_reloader=False)
```
Sau đó truy cập: `http://127.0.0.1:8050`

## 📈 Kết Quả Phân Tích Chính

### Hình Thức Mua Hàng
- Phần lớn khách hàng mua trực tiếp tại cửa hàng

### Nhà Sản Xuất Được Ưa Chuộng
- **Top 1:** Nike
- TP.HCM ưa chuộng Nike, Bình Phước ưa chuộng Adidas

### Doanh Thu Theo Khu Vực
- **Cao nhất:** TP.HCM
- **Thứ 2:** Bình Phước
- **Thấp nhất:** Kiên Giang

## 📝 License

Dự án này được thực hiện cho mục đích học tập trong môn **Lập Trình Phân Tích Dữ Liệu**.

---
⭐ Nếu thấy hữu ích, hãy cho project một star nhé!
