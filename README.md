# CNN TRANING - NHÓM 666
## Load dữ liệu 
- Lấy dữ liệu từ file .npy
## Xử lý Dữ liệu: 
- Tăng chiều dữ liệu dùng reshape
- Chuẩn hóa dữ liệu để đưa giá trị pixel về khoảng [0, 1], giúp việc học của mô hình được ổn định hơn. Để làm được như vậy hãy chia các giá trị cho 255.
- Xử lý encode cho tập output
- Chia dữ liệu thành tập huấn luyện và tập validation.
## Xác định hàm loss và thuật toán tối ưu
- Hàm loss: Sử dụng categorical cross-entropy loss.
- Thuật toán tối ưu: Sử dụng thuật toán tối ưu Adam với Learning rate bằng 0.001
- Các hàm callback:
+ ReduceLROnPlateau để giảm learning rate khi loss trên tập validation không giảm
+ ModelCheckpoint để lưu các model tốt nhất dựa theo loss của tập validation
## Xây dựng model CNN
- Block CNN đầu tiên:
	+ Conv2D (32 filters, kernel size (3,3))
	+ Batch Normalization
	+ Conv2D (64 filters, kernel size (3,3))
	+ Batch Normalization
	+ MaxPooling2D
	+ Dropout
- Block CNN thứ hai:
	+ Conv2D (64 filters, kernel size (3,3))
	+ Batch Normalization
	+ Conv2D (64 filters, kernel size (3,3))
	+ Batch Normalization
	+ MaxPooling2D
	+ Dropout
- Thực hiện việc huấn luyện mô hình trên tập huấn luyện
- Sử dụng dữ liệu validation để đánh giá hiệu suất mô hình và tránh việc overfitting.
- Quan sát tập validation trong quá trình train. Điều chỉnh mô hình, tăng lượng data để thu được kết quả có độ chính xác cao hơn.
- Đã thử qua các phương pháp rotate, zoom từ ImageDataGenerator, hay việc điều chỉnh số lượng layer, thay đổi kích thước kernel, sử dụng strides, dropout, BatchNormalization cho việc trích xuất đặc trưng của 2 block CNN. 
- Ngoài ra còn có thay đổi batch_size, epochs, các giá trị của hàm ReduceLROnPlateau,..
## Test mô hình với dữ liệu x_test
- Load model tốt nhất đã lưu ở ./weight
- Khởi tạo file Latest_submission.csv
- Lấy hình ảnh ở tập x_test và dự đoán

### Nhóm thực hành trên 2 trang: 
- Colab: Với T4 GPU
- Kaggle: Với GPU T4x2
- Kết quả train thu được khi train trên Kaggle.
- Các đường link thư mục được sử dụng theo kaggle
- Khi bắt đầu train phải hạ version tensorflow theo đúng version là 2.8.0
