# API_Testing_Practice
# Báo Cáo Thực Hành Kiểm Thử API Bằng Postman

## Thông tin sinh viên
- **Họ và tên:** Nguyễn Ngọc Trọng[cite: 1]
- **Mã sinh viên:** 23010763[cite: 1]
- **Tên dự án:** API_Testing_Practice
- **Môn học:** Đánh giá và kiểm định chất lượng phần mềm

---

## 1. Mục tiêu bài thực hành
- Sử dụng công cụ Postman để thực hiện gửi các phương thức HTTP Request (GET, POST, PUT, DELETE) tới API thực tế[cite: 1, 4, 5, 8, 9].
- Viết các kịch bản kiểm thử tự động (Test Scripts) bằng JavaScript để kiểm tra Status Code và nội dung phản hồi.
- Lưu trữ kịch bản kiểm thử và cập nhật báo cáo chi tiết lên repository GitHub[cite: 1].

---

## 2. Môi trường & Phương pháp kiểm thử
- **Môi trường:** Postman Desktop App / Web Client.
- **Phương pháp:** Kiểm thử tự động và thủ công trên Postman.
- **API Endpoint chính:** `https://jsonplaceholder.typicode.com`

---

## 3. Cấu trúc Repository
```text
.
├── Postman_Collection.json          # File collection export chứa toàn bộ Request & Test Scripts
├── README.md                        # Báo cáo chi tiết quá trình thực hiện
└── images/                          # Thư mục chứa hình ảnh minh họa kết quả
    ├── getapi.png                   # Kết quả gửi GET request
    ├── postbody.png                 # Cấu hình Body POST request
    ├── postscripts.png              # Kết quả gửi POST request & Test scripts
    ├── putbody.png                  # Cấu hình Body PUT request
    ├── putscr.png                   # Kết quả gửi PUT request & Test scripts
    └── xóa.png                      # Kết quả gửi DELETE request & Test scripts
## 4. Kịch bản kiểm thử chi tiết & Kết quả thực hiện
4.1. Kịch bản 1: Lấy danh sách dữ liệu (GET Request)
Tên kịch bản: Kiểm thử lấy danh sách bài viết

Phương thức HTTP: GET


URL: https://jsonplaceholder.typicode.com/posts


Test Script:

JavaScript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});

pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
Kết quả thực tế: Trang phản hồi mã 200 OK, thời gian phản hồi 266 ms, trả về danh sách dữ liệu dạng JSON.

Trạng thái: Thành công (PASS)


Hình ảnh minh họa:


4.2. Kịch bản 2: Tạo mới dữ liệu (POST Request)
Tên kịch bản: Kiểm thử tạo mới bài viết

Phương thức HTTP: POST


URL: https://jsonplaceholder.typicode.com/posts


Headers: Content-Type: application/json

Body Data (JSON):

JSON
{
  "title": "Kiem thu API voi Postman",
  "body": "Noi dung bai viet kiem thu",
  "userId": 1
}
```[cite: 5, 6]
Test Script:

JavaScript
pm.test("Status code is 201 Created", function () {
    pm.response.to.have.status(201);
});

pm.test("Response contains correct title", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.title).to.eql("Kiem thu API voi Postman");
});
```
Kết quả thực tế: Tạo mới dữ liệu thành công, API trả về mã 201 Created kèm id: 101.

Trạng thái: Thành công (PASS)


Hình ảnh minh họa:

Cấu hình Body:
[cite: 5]

Kết quả kiểm thử:

[cite: 6]

4.3. Kịch bản 3: Cập nhật dữ liệu (PUT Request)
Tên kịch bản: Kiểm thử cập nhật bài viết

Phương thức HTTP: PUT


URL: https://jsonplaceholder.typicode.com/posts/1


Headers: Content-Type: application/json

Body Data (JSON):

JSON
{
  "id": 1,
  "title": "Cap nhat tieu de bài viet",
  "body": "Noi dung da duoc cap nhat",
  "userId": 1
}
```[cite: 7, 8]
Test Script:

JavaScript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});
```
Kết quả thực tế: Cập nhật thành công, API trả về thông tin mới cùng mã 200 OK.

Trạng thái: Thành công (PASS)


Hình ảnh minh họa:

Cấu hình Body:
[cite: 7]

Kết quả kiểm thử:

[cite: 8]

4.4. Kịch bản 4: Xóa dữ liệu (DELETE Request)
Tên kịch bản: Kiểm thử xóa bài viết

Phương thức HTTP: DELETE


URL: https://jsonplaceholder.typicode.com/posts/1


Test Script:

JavaScript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});
```
Kết quả thực tế: Thực hiện lệnh xóa thành công, API trả về object rỗng {} kèm mã 200 OK.

Trạng thái: Thành công (PASS)


Hình ảnh minh họa:

[cite: 9]

5. Tổng kết kết quả kiểm thử
Tổng số kịch bản đã kiểm thử: 4 kịch bản (GET, POST, PUT, DELETE).

Số kịch bản thành công (PASS): 4.

Số kịch bản thất bại (FAIL): 0.

Tỷ lệ thành công: 100%.

6. Kết luận
Đã hoàn thành khởi tạo Collection và viết các request đầy đủ cho cả 4 phương thức CRUD cơ bản[cite: 4, 6, 8, 9].

Các kịch bản kiểm thử tự động (Test Scripts) hoạt động chính xác và đều xác nhận phản hồi thành công từ hệ thống[cite: 4, 6, 8, 9].
