### Singleton Pattern
- Dùng để tối ưu hiệu xuất, task manager của ứng dụng
- Khi chúng ta tạo 2 instance cùng 1 class thì chúng chỉ tạo ra 1 instance thôi điều này giúp tối ưu tài nguyên.
``` PHP
class dog (){
    set ...
    get ...
}

$dog1 = new dog();
$dog2 =  new dog();

if ($dog1 === $dog2){
    return true; // nếu chúng chỉ tạo ra 1 instance thì đã đúng với nguyên tắc Singleton
}
```
- Trong laravel chúng ta thường xử dụng chúng trong quản lý service container