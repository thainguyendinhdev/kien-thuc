### innerText và innerHTML trong JavaScript.
Cả hai thuộc tính innerText và innerHTML đều được dùng để thay đổi hoặc lấy nội dung của một phần tử HTML. Tuy nhiên, chúng có sự khác biệt quan trọng!
- innerText là gì?
    - Chỉ lấy hoặc thay đổi nội dung văn bản (text) của phần tử, bỏ qua mọi thẻ HTML bên trong.
```HTML
<div id="demo">Hello <b>World</b>!</div>

<script>
    let div = document.getElementById("demo");
    console.log(div.innerText); // Kết quả: "Hello World!"
    
    div.innerText = "Chào bạn!"; // Thay đổi nội dung
</script>
```
Kết quả hiển thị:
```CSS
Chào bạn!
```
Lưu ý:
- Không hiển thị thẻ HTML bên trong (`<b>` bị loại bỏ).
- Không render HTML khi gán giá trị mới.

- innerHTML là gì?
Lấy hoặc thay đổi cả nội dung và thẻ HTML bên trong phần tử.
```HTML
<div id="demo">Hello <b>World</b>!</div>

<script>
    let div = document.getElementById("demo");
    console.log(div.innerHTML); // Kết quả: "Hello <b>World</b>!"
    
    div.innerHTML = "Chào <i>bạn</i>!"; // Thay đổi nội dung
</script>
```
Kết quả hiển thị:
Chào bạn! (Chữ "bạn" sẽ in nghiêng vì <i> được render).

Lưu ý:
- Giữ nguyên thẻ HTML khi lấy nội dung (<b>World</b> vẫn tồn tại).
- Render HTML khi gán giá trị mới (<i>bạn</i> sẽ được hiển thị dưới dạng chữ nghiêng)

| Thuộc tính    | Chức năng                            | Giữ lại thẻ HTML? | Khi thay đổi nội dung |
|--------------|----------------------------------|----------------|------------------|
| `innerText`  | Lấy/chỉnh sửa **chỉ văn bản**    | ❌ Không       | Chỉ hiển thị văn bản |
| `innerHTML`  | Lấy/chỉnh sửa **văn bản + HTML** | ✅ Có          | Render HTML nếu có |
