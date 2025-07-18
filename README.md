## Lab 5 - Xác Định Đối tượng Trong Ảnh

* Sinh viên thực hiện: Lê Hoài Phương
* MSSV: 207CT10264
* Môn học: Nhập môn Xử lý ảnh số
* Giảng viên: Đỗ Hữu Quân

## Giới thiệu

Bài Lab 5 này tập trung vào việc thực hiện các kỹ thuật xử lý ảnh để gán nhãn, phân vùng, dò tìm cạnh, và xác định các đặc trưng hình học của đối tượng trong ảnh. Các kỹ thuật này rất quan trọng trong việc phân tích và hiểu rõ nội dung hình ảnh.

## Mục tiêu của bài thực hành

Sau khi hoàn thành bài thực hành này, sinh viên có thể:
* [cite_start]Viết được chương trình gán nhãn cho phân vùng ảnh. [cite: 1]
* [cite_start]Viết được chương trình phân vùng ảnh theo Region. [cite: 1]
* [cite_start]Viết được chương trình thay đổi ảnh. [cite: 1]

## Công nghệ sử dụng

* **Python:** Ngôn ngữ lập trình chính.
* **Pillow (PIL):** Để đọc và xử lý ảnh.
* **NumPy:** Xử lý dữ liệu ảnh dưới dạng mảng số hiệu quả.
* **OpenCV:** Thư viện xử lý ảnh.
* **Scikit-image:** Cung cấp các thuật toán xử lý ảnh, bao gồm gán nhãn, thuộc tính vùng (regionprops), dò tìm góc (corner_harris), và chuyển đổi màu (rgb2gray).
* **Scipy:** Hỗ trợ các phép toán hình thái học và bộ lọc như Sobel, Gaussian filter.
* **Matplotlib:** Để hiển thị ảnh trực quan các bước xử lý và kết quả.
* **Imageio:** Để đọc và ghi ảnh.

## Chi tiết các Bài Tập & Công thức

Các bài tập trong Lab 5 này chủ yếu sử dụng ảnh `geometric.png` hoặc `bird.png` để thực hiện các phép xử lý.

### Bài 1: Gán nhãn ảnh (Labeling Image)
* [cite_start]**Mục đích:** Phân biệt các đối tượng khác nhau trong ảnh bằng cách gán cho chúng các giá trị pixel riêng biệt. [cite: 1] [cite_start]Trong một ảnh đã được gán nhãn, tất cả các pixel của một đối tượng có cùng giá trị. [cite: 2]
* **Cách làm:**
    * [cite_start]Mở ảnh `geometric.png` và chuyển sang ảnh grayscale. [cite: 4]
    * [cite_start]Thực hiện ngưỡng Otsu để phân tách đối tượng khỏi nền. [cite: 4]
    * [cite_start]Sử dụng hàm `label` để gán nhãn cho các vùng đối tượng. [cite: 4]
    * [cite_start]Thực hiện `regionprops` để trích xuất các thuộc tính như 'Area', 'Centroid', 'BoundingBox' của các đối tượng đã gán nhãn. [cite: 4]
    * [cite_start]Vẽ các hộp giới hạn (bounding boxes) xung quanh các đối tượng trên ảnh đã gán nhãn. [cite: 4]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "VIẾT CHƯƠNG TRÌNH gán nhãn ẢNH". [cite: 4]

### Bài 2: Dò tìm cạnh theo chiều dọc (Edge Detection - Vertical Shift)
* **Mục đích:** Xác định các cạnh dọc trong ảnh.
* **Cách làm:**
    * [cite_start]Mở ảnh `geometric.png` và chuyển sang grayscale. [cite: 5]
    * [cite_start]Sử dụng phép dịch chuyển (`nd.shift`) ảnh đi một pixel theo chiều ngang và tính hiệu tuyệt đối giữa ảnh gốc và ảnh đã dịch chuyển để làm nổi bật các cạnh. [cite: 5]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "Dò tìm cạnh theo chiều dọc". [cite: 5]

### Bài 3: Dò tìm cạnh với Sobel Filter (Edge Detection - Sobel)
* [cite_start]**Mục đích:** Dò tìm các cạnh trong ảnh bằng cách sử dụng Sobel Filter, một phương pháp hiệu quả hơn so với phép dịch chuyển đơn giản. [cite: 6]
* **Cách làm:**
    * [cite_start]Mở ảnh `geometric.png`. [cite: 6]
    * [cite_start]Áp dụng Sobel Filter theo cả hai trục (ngang và dọc) để tính đạo hàm cường độ ảnh. [cite: 6]
    * [cite_start]Kết hợp kết quả từ hai hướng để có được ảnh cạnh tổng thể. [cite: 6]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "Dò tìm cạnh với Sobel Filter". [cite: 6]

### Bài 4: Xác định góc của đối tượng (Corner Detection - Harris Corner Detector)
* [cite_start]**Mục đích:** Xác định các điểm góc (corners) trên đối tượng trong ảnh, là những điểm có sự thay đổi cường độ lớn theo nhiều hướng. [cite: 7]
* **Cách làm:**
    * [cite_start]Mở ảnh `geometric.png`. [cite: 7]
    * [cite_start]Sử dụng thuật toán Harris Corner Detector để tính "độ đáp ứng góc" (corner response) cho mỗi pixel. [cite: 7]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "Xác định góc của đối tượng". [cite: 7]

### Bài 5: Dò tìm hình dạng cụ thể trong ảnh với Hough Transform
#### Bài 5.1: Dò tìm đường thẳng trong ảnh (Hough Line Transform)
* [cite_start]**Mục đích:** Tìm và xác định các đường thẳng trong ảnh. [cite: 8]
* **Cách làm:**
    * [cite_start]Tạo một ảnh đen với một điểm trắng duy nhất. [cite: 8]
    * [cite_start]Sử dụng thuật toán Hough Transform cho đường thẳng để biến đổi ảnh từ không gian Descartes sang không gian Hough (Hough space), nơi các đường thẳng được biểu diễn bằng các điểm. [cite: 8]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "Dò tìm đường thẳng trong ảnh". [cite: 8]

#### Bài 5.2: Dò tìm đường tròn trong ảnh (Hough Circle Transform)
* [cite_start]**Mục đích:** Tìm và xác định các đường tròn trong ảnh. [cite: 9]
* **Cách làm:**
    * [cite_start]Đọc ảnh `bird.png`. [cite: 9]
    * [cite_start]Chuyển đổi ảnh sang ảnh grayscale. [cite: 9]
    * [cite_start]Sử dụng thuật toán Harris Corner Detector để xác định các điểm đặc trưng trong ảnh, có thể được dùng làm cơ sở cho việc tìm đường tròn (mặc dù đoạn code này chỉ dừng lại ở Harris Corner, việc áp dụng Hough Circle sẽ cần thêm hàm chuyên biệt). [cite: 9]
* [cite_start]**Code tham khảo:** Đoạn mã trong tài liệu `Lab_5_Image_Measure.docx` cho phần "Dò tìm đường tròn trong ảnh". [cite: 9]

### Bài 6: So khớp ảnh (Image Matching)
* [cite_start]**Mục đích:** Tìm điểm tương đồng giữa hai ảnh. [cite: 10]
* **Các bước chính:**
    * [cite_start]Tìm điểm cần so sánh (ví dụ: sử dụng Harris Corner Detector). [cite: 10]
    * [cite_start]Xem xét vùng chọn hình chữ nhật xung quanh những điểm cần so sánh. [cite: 10]
    * [cite_start]Tính mô tả đặc trưng cục bộ cho mỗi điểm của mỗi ảnh. [cite: 10]
    * [cite_start]Kiểm tra độ tương đồng giữa hai ảnh. [cite: 10]
* **Lưu ý:** Phần này chỉ mô tả các bước lý thuyết, không có đoạn mã cụ thể được cung cấp trong tài liệu cho chức năng này.

## Hướng dẫn sử dụng

### 1. Cài đặt môi trường
Đảm bảo bạn đã cài đặt các thư viện cần thiết. Nếu chưa, hãy chạy lệnh sau:
```bash
[cite_start]pip install opencv-python [cite: 3]
pip install Pillow numpy imageio scikit-image scipy matplotlib
