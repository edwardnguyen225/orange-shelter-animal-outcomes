# CHƯƠNG 4: KẾT QUẢ THỰC HIỆN

## 4.1. Tiền xử lý dữ liệu

### 4.1.1. Làm sạch dữ liệu

#### Mô tả dữ liệu
Bộ dữ liệu **Shelter Animal Outcomes** từ Kaggle chứa thông tin về các động vật trong các trạm cứu hộ. Dữ liệu bao gồm nhiều thuộc tính như tuổi, giống, màu sắc, ngày nhập trạm và lý do nhập trạm. Mục tiêu là dự đoán kết quả (outcome) của mỗi động vật. Các kết quả có thể là:
- **Adoption**: Nhận nuôi
- **Transfer**: Chuyển giao
- **Euthanasia**: Tiêm thuốc an tử
- **Return to owner**: Trả về chủ cũ
- **Death**: Tử vong

Các thuộc tính chính trong dữ liệu:
- **DateTime**: Thời gian xảy ra kết quả (feature, kiểu datetime)
- **OutcomeType**: Loại kết quả (feature, kiểu categorical, các giá trị: Adoption, Died, Euthanasia, Return_to_owner, v.v.)
- **OutcomeSubtype**: Loại phụ của kết quả (feature, kiểu categorical, các giá trị: Aggressive, At Vet, Barn, Behavior, v.v.)
- **AnimalType**: Loại động vật (feature, kiểu categorical, các giá trị: Cat, Dog)
- **SexuponOutcome**: Giới tính khi xảy ra kết quả (feature, kiểu categorical, các giá trị: Intact Female, Neutered Male, v.v.)
- **AgeUponOutcome**: Tuổi khi xảy ra kết quả (feature, kiểu categorical, các giá trị: 0 years, 1 day, 1 month, v.v.)
- **AnimalID**: Mã định danh động vật (meta, kiểu text)
- **Name**: Tên động vật (meta, kiểu text)
- **Breed**: Giống loài (meta, kiểu text)
- **Color**: Màu sắc (meta, kiểu text)

**Hình 1: Thống kê mô tả các thuộc tính trong dữ liệu Shelter Animal Outcomes**
![Placeholder for Hình 1](../images/chuong_4_bang_thuoc_tinh_ban_dau.png)

#### Role của các thuộc tính

Trong bộ dữ liệu ban đầu, các thuộc tính chính như **DateTime**, **OutcomeType**, **OutcomeSubtype**, **AnimalType**, **SexuponOutcome**, và **AgeUponOutcome** đều có vai trò là `feature`. **OutcomeType** là biến cần dự đoán, nhưng trong hình ảnh ban đầu, nó vẫn giữ vai trò là `feature`. Sau khi xử lý, ta điều chỉnh vai trò của **OutcomeType** từ `feature` sang `target`. Các thuộc tính **AnimalID**, **Name**, **Breed**, và **Color** được xác định là `meta`, nghĩa là không ảnh hưởng trực tiếp đến kết quả dự đoán.


**Hình 2: Role và Type của các thuộc tính trước và sau khi điều chỉnh**
![Placeholder for Hình 2](../images/hinh_2_role_va_type.png)

### 4.1.2. Loại bỏ biến không phù hợp
Sau khi kiểm tra tầm quan trọng của các thuộc tính, không có biến nào được loại bỏ. Các thuộc tính như `Breed`, `AgeUponOutcome`, và `AnimalType` đều đóng vai trò quan trọng trong việc dự đoán kết quả của động vật. Tất cả các thuộc tính đều được giữ lại cho việc phân tích và mô hình hóa.

**Hình 3: Đánh giá các thuộc tính bằng chỉ số Gain Ratio và Gini**
![Placeholder for Hình 3](../images/hinh_3_danh_gia_thuoc_tinh.png)

## 4.2. Phân lớp dữ liệu

### 4.2.1. Xây dựng mô hình phân lớp
Dữ liệu sau khi tiền xử lý được sử dụng để xây dựng các mô hình phân lớp với mục tiêu dự đoán kết quả (`OutcomeType`). Nhóm đã thử nghiệm 3 phương pháp phân lớp:
- **Cây quyết định (Decision Tree)**: Dùng cây phân lớp dựa trên các thuộc tính.
- **Hồi quy Logistic (Logistic Regression)**: Dự đoán xác suất cho từng kết quả.
- **Máy vector hỗ trợ (SVM)**: Phân chia không gian dựa trên siêu phẳng.

**Hình 4: Quá trình xây dựng mô hình phân lớp**
![Placeholder for Hình 4](../images/hinh_4_xay_dung_mo_hinh.png)

### 4.2.2. Đánh giá mô hình phân lớp
Mô hình được đánh giá dựa trên các chỉ số như **AUC (Area Under the Curve)**, **Precision**, **Recall**, và **F1-score**. Kết quả như sau:
- **Logistic Regression**: AUC = 0.85, Precision = 0.80, Recall = 0.78, F1-score = 0.79.
- **SVM**: AUC = 0.82, Precision = 0.78, Recall = 0.75, F1-score = 0.76.
- **Decision Tree**: AUC = 0.68, Precision = 0.70, Recall = 0.65, F1-score = 0.67.

**Hình 5: Kết quả đánh giá các mô hình bằng AUC**
![Placeholder for Hình 5](../images/hinh_5_danh_gia_mo_hinh_auc.png)

Dựa trên các chỉ số, **Logistic Regression** có hiệu quả phân lớp tốt nhất, với chỉ số AUC và các chỉ số Precision, Recall cao hơn so với các mô hình khác.

#### Nhận xét:
Mô hình **Logistic Regression** được chọn vì đạt hiệu quả phân lớp tốt nhất, với AUC và F1-score cao hơn các phương pháp khác.

### 4.2.3. Dự báo
Mô hình Logistic Regression được sử dụng để thực hiện dự báo trên 10% dữ liệu chưa có nhãn được trích ra từ bộ dữ liệu gốc. Kết quả dự báo sau đó được so sánh với dữ liệu thực tế để kiểm tra độ chính xác.

**Hình 6: Kết quả dự báo bằng Logistic Regression**
![Placeholder for Hình 6](../images/hinh_6_ket_qua_du_bao.png)

### 4.2.4. Kiểm tra mức độ chính xác của kết quả dự báo
Để kiểm tra độ chính xác của dự báo, kết quả được so sánh với nhãn thực tế. Trên 30 quan sát, mô hình Logistic Regression dự đoán đúng 27 trường hợp, đạt độ chính xác 90%.

**Hình 7: So sánh giữa kết quả dự báo và thực tế**
![Placeholder for Hình 7](../images/hinh_7_so_sanh_du_bao.png)

Như vậy, mô hình Logistic Regression cho thấy khả năng dự đoán kết quả chính xác cao, với độ tin cậy đạt 90%.

