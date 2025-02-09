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

### Class và Object
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

### Khi nào làm việc với Class, khi nào làm việc với Object?
- Làm việc với Class khi:
    - Định nghĩa cấu trúc chung cho một loại đối tượng.
    - Tạo các phương thức dùng chung mà không cần dữ liệu cụ thể.
    - Sử dụng thuộc tính hoặc phương thức tĩnh (static).
    - Lập trình hướng đối tượng (OOP): Class giúp tái sử dụng mã dễ dàng hơn.

- Làm việc với Object khi:
    - Cần thao tác với dữ liệu thực tế.
    - Muốn truy cập các thuộc tính và phương thức cụ thể của một đối tượng.
    - Tạo ra nhiều thực thể (instance) từ một class với dữ liệu khác nhau.

### Có mấy mức độ truy cập trong lớp (Class)?
Trong lập trình hướng đối tượng (OOP), có 3 mức độ truy cập (Access Modifier) chính:
- `public` – Công khai (ai cũng có thể truy cập).
- `protected` – Bảo vệ (chỉ class và lớp con truy cập được).
- `private` – Riêng tư (chỉ class đó có thể truy cập).

### Tính Đa Hình (Polymorphism) trong OOP là gì?
🔹 Định nghĩa

Đa hình (Polymorphism) là một tính chất trong lập trình hướng đối tượng (OOP) cho phép một phương thức (method) có thể hoạt động khác nhau tùy thuộc vào đối tượng gọi nó.

🚀 Nói đơn giản:

- Cùng một phương thức, nhưng hành vi có thể thay đổi trong từng lớp con.
- Giúp mở rộng tính linh hoạt của chương trình.

**Các Loại Đa Hình**
- Đa hình qua Ghi đè phương thức (`Method Overriding`)
    - Lớp con định nghĩa lại phương thức của lớp cha nhưng có cách thực thi riêng.

- Đa hình qua Nạp chồng phương thức (`Method Overloading` - PHP không hỗ trợ trực tiếp)
    - Một class có thể có nhiều phương thức cùng tên nhưng khác tham số.
    - PHP không hỗ trợ `Overloading` theo cách truyền thống như Java hay C++, nhưng có thể mô phỏng bằng __call().

```PHP
<?php
class MathHelper {
    public function __call($name, $arguments) {
        if ($name == 'add') {
            if (count($arguments) == 2) {
                return $arguments[0] + $arguments[1]; // add(2, 3)
            } elseif (count($arguments) == 3) {
                return $arguments[0] + $arguments[1] + $arguments[2]; // add(2, 3, 4)
            }
        }
        return "Phương thức không tồn tại";
    }
}

$math = new MathHelper();
echo $math->add(2, 3); // Kết quả: 5
echo "\n";
echo $math->add(2, 3, 4); // Kết quả: 9
?>
```
Cùng một tên add(), nhưng số lượng tham số khác nhau sẽ cho kết quả khác nhau.

-  Đa hình qua Interface
    - Các lớp khác nhau có thể triển khai cùng một giao diện nhưng cách thực hiện riêng.
    - Dùng khi cần đảm bảo các lớp con đều có chung phương thức nhưng cách hoạt động khác nhau.
```php
<?php
interface Animal {
    public function makeSound(); // Tất cả lớp triển khai phải có phương thức này
}

class Dog implements Animal {
    public function makeSound() {
        return "Gâu Gâu";
    }
}

class Cat implements Animal {
    public function makeSound() {
        return "Meo Meo";
    }
}

$animals = [new Dog(), new Cat()];

foreach ($animals as $animal) {
    echo $animal->makeSound() . "\n"; // Gâu Gâu, Meo Meo
}
?>
```
Cả Dog và Cat đều triển khai makeSound(), nhưng cách thực hiện khác nhau.
- Đa hình qua Abstract Class
    - Lớp trừu tượng giúp định nghĩa các phương thức nhưng không có thực thi sẵn.
    - Lớp con phải override lại các phương thức trừu tượng này.
```php
<?php
abstract class Animal {
    abstract public function makeSound(); // Lớp con bắt buộc phải triển khai
}

class Dog extends Animal {
    public function makeSound() {
        return "Gâu Gâu";
    }
}

class Cat extends Animal {
    public function makeSound() {
        return "Meo Meo";
    }
}

$dog = new Dog();
$cat = new Cat();

echo $dog->makeSound(); // Gâu Gâu
echo "\n";
echo $cat->makeSound(); // Meo Meo
?>
```
| **Loại Đa Hình**       | **Mô tả**                                      | **Hỗ trợ trong PHP?** |
|------------------------|-----------------------------------------------|----------------------|
| **Method Overriding**  | Lớp con ghi đè phương thức của lớp cha        | ✅ Có               |
| **Method Overloading** | Cùng tên nhưng khác số lượng/tham số          | 🚫 Không trực tiếp, có thể mô phỏng với `__call()` |
| **Interface**         | Nhiều lớp triển khai cùng một giao diện        | ✅ Có               |
| **Abstract Class**    | Lớp cha chỉ định nghĩa, lớp con phải triển khai | ✅ Có               |

**Khi nào dùng Đa Hình?**
-  `Method Overriding`: Khi cần cho phép lớp con có cách thực hiện riêng mà vẫn giữ tên phương thức.
-  `Method Overloading`: Khi muốn tạo phương thức linh hoạt với nhiều cách gọi khác nhau (mô phỏng trong PHP).
- `Interface`: Khi cần đảm bảo nhiều lớp có chung một phương thức nhưng có cách triển khai khác nhau.
- `Abstract Class`: Khi muốn định nghĩa các phương thức bắt buộc mà các lớp con phải thực hiện.

### `DongVat a = new Concho()`; này nghĩa là gì?
```java
class DongVat {
    void keu() {
        System.out.println("Động vật phát ra âm thanh");
    }
}

class Concho extends DongVat {
    @Override
    void keu() {
        System.out.println("Gâu Gâu!");
    }
}

public class Main {
    public static void main(String[] args) {
        DongVat a = new Concho(); // 👈 a tham chiếu đến đối tượng Concho
        a.keu(); // Kết quả: Gâu Gâu!
    }
}
```
a thực chất là gì?
- a không phải là đối tượng, mà là biến tham chiếu (reference variable).
- Nó được khai báo có kiểu DongVat, nhưng nó trỏ đến một đối tượng Concho trên Heap.

Tính Đa Hình (Polymorphism)
- Mặc dù a có kiểu DongVat, nhưng vì nó tham chiếu đến Concho, nên khi gọi a.keu(), phương thức của Concho được thực thi.
- Nếu gọi a.keu();, Java tìm phương thức keu() trong Concho (lớp con) thay vì DongVat (lớp cha).
Kết quả: "Gâu Gâu!" thay vì "Động vật phát ra âm thanh".

Điều gì sẽ xảy ra nếu gọi phương thức không có trong DongVat?
```java
class Concho extends DongVat {
    void suaTo() {
        System.out.println("Gâu Gâu thật to!");
    }
}
```
Nếu ta viết:
```java
a.suaTo(); // ❌ Lỗi biên dịch! 
```
Lỗi: Vì a có kiểu DongVat, mà DongVat không có phương thức suaTo().

Cách khắc phục: Ép kiểu về Concho
```java
((Concho) a).suaTo(); // ✅ Ép kiểu thành Concho, bây giờ gọi được suaTo()
```

### Class ko kế thừa interface mà chỉ implement interface
