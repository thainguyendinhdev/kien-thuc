### Sử dụng mảng
**Bài toán:**
Đối với bài toán xây dựng thời khóa biểu cho giao viên, tiết thứ mấy dạy môn gì, do ai dạy thì dùng mảng mấy chiều

**Phân tích bài toán thời khóa biểu**
Bài toán xây dựng thời khóa biểu cho giáo viên có các yếu tố chính sau:
- Thời gian: Tiết học (1, 2, 3, ...) theo từng ngày.
- Môn học: Mỗi tiết sẽ có một môn học cụ thể.
- Giáo viên: Mỗi môn học có một giáo viên giảng dạy.

=>Vậy ta cần quản lý dữ liệu theo 3 chiều chính:
- Ngày học (thứ 2, thứ 3, ...).
- Tiết học (tiết 1, tiết 2, ...).
- Thông tin tiết học (môn học, giáo viên).

---

### Sự khác nhau giữa Class và Object

| **Thuộc tính** | **Class** | **Object** |
|--------------|---------|---------|
| **Định nghĩa** | Là một **khuôn mẫu** (blueprint) để tạo ra các object. | Là một **thực thể (instance)** được tạo ra từ class. |
| **Chức năng** | Xác định thuộc tính (properties) và phương thức (methods). | Chứa dữ liệu thực tế và có thể thực thi các phương thức. |
| **Bộ nhớ** | Không chiếm bộ nhớ cho dữ liệu cụ thể. | Chiếm bộ nhớ khi được tạo ra. |
| **Số lượng** | Một class có thể có nhiều object. | Một object chỉ thuộc về một class. |

- Class là bản thiết kế chung, không lưu dữ liệu cụ thể.
- Object là phiên bản cụ thể của class, có dữ liệu riêng.
- Một class có thể tạo ra nhiều object khác nhau.
- Class và Object có phương thức và thuộc tính

So sánh Thuộc tính và Phương thức của Class vs Object

| **Đặc điểmh** | **Class** | **Object** |
|--------------|---------|---------|
| **Thuộc tính** | Được khai báo bên trong class nhưng chưa có giá trị cụ thể. | Mỗi object có giá trị riêng cho thuộc tính.|
| **Phương thức** | Được khai báo trong class, có thể dùng chung cho nhiều object. | Dùng phương thức của class để thao tác với dữ liệu của object. |
| **Truy cập** | 	Dùng self::$property (trong class) hoặc Class::$property nếu là static. | Dùng $object->property để truy cập. |