# Vấn đề làm như nào để biết 1 phần tử tồn tại trong hàng triệu bản ghi ví dụ như user đã tồn tại, email đã tồn tại trong DB.
Check username không tồn tại (tùy hướng sử dụng) trong database quá lớn (1 triệu/tỷ username).
- Dùng query như bình thường quá tốn thời gian query của DB
- Dùng redis để lưu nhiều bản ghi chi phí tốn kém cao, tốn memory.
- Dùng bloom filter: tốt nhất
## Định hướng
Làm gọn quy trình duyệt và check bằng cách dùng băm và một mảng bit duy nhất.

## Giải pháp
- Xây dựng một mảng bit có sẵn trước cả khi database có dữ liệu, đảm bảo việc đồng bộ và trọn vẹn dữ liệu. Khi thêm dữ liệu mới, có thể thêm vào luôn mà không lo bị bỏ sót.
- Kích thước của mảng bit phải được tính toán trước tùy theo số lượng username dự định lưu trữ. Nếu kích thước quá bé, dễ trùng vị trí bit, dẫn đến False Positive.
## Xây dựng cấu trúc Bloom Filter
- Thiết lập thông số: Xác định kích cỡ mảng bit và số lượng hàm băm.
- Băm dữ liệu: Mỗi lần băm tạo ra một vị trí bit, càng nhiều lần băm càng nhanh đầy mảng, tăng False Positive. Ngược lại, ít lần băm khiến xác suất trùng vị trí bit cao hơn.
- Ghi vào mảng bit: Các vị trí băm được điền bit 1 vào mảng bit.
- Kiểm tra tồn tại:
    - Nếu thiếu ít nhất một bit trong tập hợp kết quả băm → Chắc chắn chưa tồn tại.
    - Nếu đủ tất cả vị trí bit → Chưa chắc tồn tại, cần kiểm tra lại database do có thể bị False Positive.
## Lưu ý:
- Bloom Filter có thể xảy ra False Positive (báo tồn tại nhưng thực tế không có), nhưng không bao giờ có False Negative (báo không tồn tại trong khi thực tế có).
- Khi thêm dữ liệu mới vào database, cũng cần băm và ghi vào mảng bit ban đầu.
## Kết luận
- Hiệu quả trong việc kiểm tra nhanh username, cache, spam filter, DNS mà không cần truy vấn database.
- Giúp tăng hiệu suất vì tránh duyệt database nếu dữ liệu không tồn tại.
## Mở rộng
- Counting Bloom Filter: Thêm bộ đếm ở mỗi bit để hỗ trợ khi xóa dữ liệu.
- Distributed Bloom Filter: Sử dụng trong hệ thống phân tán để hỗ trợ xử lý dữ liệu trên nhiều máy chủ.