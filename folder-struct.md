# Folder Struct

## App Folder Struct

![App folder struct](assets/folder-struct-app.PNG)

### Console

[Link tham khảo][console-reference]

[console-reference]: https://laravel.com/docs/9.x/structure#the-console-directory

### DTOs

Bao gồm các class đóng gói data để `chuyển giữa client - server`. Mục đích tạo ra DTO là để giảm bớt lượng info không cần thiết phải chuyển đi, và cũng tăng cường độ bảo mật, giảm thiểu code xử lí trong controller.

### Exceptions

[Link tham khảo][exceptions-reference]

[exceptions-reference]: https://laravel.com/docs/9.x/structure#the-exceptions-directory

### Http

![App Http folder struct](assets/folder-struct-app-http.PNG)

- `Controllers`
  [Link tham khảo][controlers-reference]

  [controlers-reference]: https://laravel.com/docs/9.x/structure#the-http-directory

  📌 Lưu ý
  `1. Controllers phải đặt tên theo số nhiều.`
  `2. Cố gắng giữ cho bộ điều khiển đơn
giản và bám vào các từ khóa CRUD mặc định(index, create, store, show, edit,
update, destroy).`

- `Middleware`
  [Link tham khảo][middleware-reference]

  [middleware-reference]: https://laravel.com/docs/9.x/structure#the-http-directory

### Models

[Link tham khảo][models-reference]

[models-reference]: https://laravel.com/docs/9.x/structure#the-models-directory

### Providers

[Link tham khảo][providers-reference]

[providers-reference]: https://laravel.com/docs/9.x/structure#the-providers-directory

### Repositories

Lớp này giao tiếp với DB thông qua model, có thể coi là `cầu nối giữa DB - Serivce`.
Mục đích tạo ra lớp này để cách ly với việc tiếp cận data sao cho những thay đổi không ảnh hưởng trực tiếp đến lớp logic business.
![App folder struct](assets/mvc-struct.PNG)

### Services

Nơi chứa các business logic code, có thể xem đó là nơi luân chuyển giữ liệu giữa `controler - repository`

### Shared

Nơi chứa các class, functions, constants,... sẽ được `sử dụng lại trong toàn bộ chương trình`
![App folder struct](assets/folder-struct-shared.PNG)
