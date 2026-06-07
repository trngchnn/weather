# Ho Chi Minh City Weather: EDA & Predictive Modeling

## 1. Giới thiệu đề tài
Tên dự án: Phân tích mối quan hệ giữa nhiệt độ, độ ẩm và lượng mưa tại Thành phố Hồ Chí Minh giai đoạn 2009 - 2020 bằng mô hình hồi quy tuyến tính.

Dự án tập trung vào việc nghiên cứu mối quan hệ giữa các yếu tố khí tượng lịch sử tại Thành phố Hồ Chí Minh và xây dựng mô hình học máy (Machine Learning) để dự báo trạng thái thời tiết. Đây là sản phẩm nghiên cứu thực hành được triển khai bởi nhóm 2 người trong khuôn khổ hoạt động của Câu lạc bộ Nghiên cứu Khoa học.

* **Bối cảnh:** Dự án thực hành với bối cảnh là thành viên của Câu lạc bộ Nghiên cứu Khoa học Sinh Viên (Nhóm 2 người).
* **Vai trò cá nhân:** Chịu trách nhiệm chính trong việc Phân tích khám phá dữ liệu (EDA), Xử lý biến thời gian, Trực quan hóa xu hướng và Tối ưu hóa mô hình học máy nâng cao.

## 2. Mục tiêu nghiên cứu
* Xử lý và chuẩn bị dữ liệu thời tiết lịch sử tại TP. Hồ Chí Minh giai đoạn 2009-2020.
* Khai thác tính mùa vụ, xu hướng thời tiết biến đổi theo các tháng trong năm và các khung giờ trong ngày.
* Xây dựng, tối ưu hóa và đánh giá hiệu suất mô hình Machine Learning dự báo trạng thái thời tiết đô thị.

## 3. Dữ liệu sử dụng (Dataset)
Bộ dữ liệu sử dụng là *Historical Weather Analysis Data – Ho Chi Minh City* giai đoạn 2009 - 2020 với quy mô khoảng 35,000 quan sát. Tập dữ liệu gốc đã được đính kèm trực tiếp dưới dạng file `Weather_Data.csv` trong repository này.

### Các thuộc tính chính:
* **Biến độc lập:** Nhiệt độ (Temperature), độ ẩm (Humidity), lượng mưa (Rainfall), áp suất (Pressure), tốc độ gió (Wind Speed), và các yếu tố thời gian được trích xuất từ Datetime (Month, Hour).
* **Biến mục tiêu (`Weather_Label`):** Trạng thái thời tiết (Clear, Cloudy, Mist, Overcast, Rain, Sunny).

## 4. Kỹ năng và Công cụ sử dụng
* **Ngôn ngữ lập trình:** Python
* **Thư viện phân tích & Trực quan hóa:** pandas, numpy, matplotlib, seaborn
* **Môi trường phát triển:** Jupyter Notebook / Google Colab
* **Thuật toán áp dụng:** RandomForestClassifier kết hợp công cụ tối ưu tham số GridSearchCV và kiểm chứng chéo cross_val_score từ thư viện scikit-learn.

## 5. Quy trình xử lý dữ liệu (Workflow)

| Bước | Nội dung công việc | Kỹ thuật áp dụng |
|---|---|---|
| 1 | Phân tích khám phá dữ liệu (EDA) | Trực quan hóa phân phối biến, phân tích mối tương quan nhiệt độ - độ ẩm |
| 2 | Kỹ thuật tính năng (Feature Engineering) | Trích xuất đặc trưng Datetime (`Month`, `Hour`), chuẩn hóa bằng StandardScaler |
| 3 | Huấn luyện mô hình cơ sở | Triển khai mô hình phân loại với thuật toán Random Forest |
| 4 | Tối ưu hóa siêu tham số | Áp dụng GridSearchCV để tìm bộ tham số tốt nhất (`n_estimators`, `max_depth`) |
| 5 | Đánh giá & Kiểm chứng chéo | Sử dụng K-Fold Cross Validation (`cv=5`) để kiểm tra hiện tượng Overfitting |
| 6 | Phân tích chuyên sâu | Xuất ma trận nhầm lẫn (Confusion Matrix) và Feature Importance |

## 6. Kết quả mô hình và Đánh giá

### Kết quả các mô hình thử nghiệm:
| Mô hình | Accuracy |
|---|---|
| Logistic Regression | 82.89% |
| SVM (RBF Kernel) | 84.02% |
| **Random Forest (Sau tuning)** | **92.15%** |

### Đánh giá chi tiết mô hình Random Forest:
* **Tính ổn định:** Kết quả chạy Cross Validation 5 lần cho thấy độ lệch chuẩn cực kỳ thấp, chứng minh mô hình hoạt động ổn định trên dữ liệu thực tế.
* **Mức độ quan trọng của tính năng (Feature Importance):** Kết quả phân tích chỉ ra rằng Độ ẩm (Humidity) và Yếu tố thời gian (Hour/Month) là những biến có ảnh hưởng lớn nhất đến việc quyết định trạng thái thời tiết tại khu vực TP.HCM.
<img width="1810" height="865" alt="image" src="https://github.com/user-attachments/assets/24bf1113-2a3b-4407-8668-0082564272ce" />

