### Sử dụng REPOSITORY.
Context hiện tại:
Hiện tại, tôi đang có một ứng dụng Laravel với các tính năng:
- Sử dụng Route Model Binding để tự động resolve các model
- Implement các Policy để quản lý authorization
- Sử dụng Form Request để validate dữ liệu
Có nhiều Eloquent relationships phức tạp giữa các model

**Vấn đề đang gặp phải**:

**Route Model Binding:**
Nếu implement Repository Pattern, liệu có cách nào để tận dụng được tính năng này mà không phải viết thêm nhiều code?
Có nên để Repository layer handle việc resolve model thay vì dùng Route Model Binding?

**Authorization & Policy:**
Policy trong Laravel được thiết kế để làm việc trực tiếp với Model
Khi đưa Repository vào giữa, chúng ta nên handle authorization ở đâu?
Làm sao để không duplicate logic giữa Policy và Repository?

**Form Request Validation:**
Khi sử dụng Repository Pattern, các rule như unique, exists đang truy cập trực tiếp vào database, điều này có vi phạm nguyên tắc của pattern không?
Nếu Repository là layer duy nhất tương tác với database, vậy những validation rule này nên được xử lý như thế nào?
Có nên tạo các custom validation rule để gọi qua Repository layer không? Điều này có tạo ra quá nhiều boilerplate code không?

**Eloquent Relationships:**
Làm sao để handle efficiently các relationship khi dùng Repository?
Có nên wrap tất cả relationship queries trong Repository method?
Vấn đề N+1 query nên được giải quyết ở layer nào?

### Giaỉ đáp
- Route Model Binding: Nếu dùng Repository Pattern thì không nên dùng Route Model Binding. Lúc này route của mình sẽ gọn, có lỗi ở route kiểm tra cũng nhanh hơn.
- Form Request Validation: Laravel có layer Request riêng để viết rules và messeages. Controller dùng chung hoặc dùng riêng đều được.
- Eloquent Relationships: Dùng ở layer Model. Vấn đề N+1 query: em xử lý logic ở service - sẽ gọi các query mà mình tạo ở repository

**Như vậy các layer:**
- Route: xử lý uri, gọi fn controller, name
- Controller: gọi các service, xử lý xem nó trả về kiểu dữ liệu gì hay trả về view.
- Service: xử lý logic, xử lý các trường dữ liệu
- Repository: truy vấn dữ liệu - ORM
- Request: Viết rules, messges
- Model: handle relationship