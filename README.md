## 1. Tạo Named Volume

```bash
docker volume create easy-volume
```

Kết quả minh họa (log mô phỏng, chưa chạy Docker thực tế):

```text
easy-volume
```

## 2. Ghi dữ liệu vào volume

```bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
```

Volume `easy-volume` được gắn vào thư mục `/data` trong container. Lệnh ghi nội dung `Luu tru du lieu Docker` vào tệp `/data/test.txt`. Container tự động bị xóa sau khi lệnh kết thúc nhờ tùy chọn `--rm`.

Chuỗi dữ liệu giữ nguyên không dấu theo yêu cầu của đề bài.

## 3. Đọc dữ liệu bằng container thứ hai

```bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
```

Kết quả minh họa (log mô phỏng, chưa chạy Docker thực tế):

```text
Luu tru du lieu Docker
```

Container thứ hai sử dụng cùng volume nên có thể đọc lại tệp đã được container đầu tiên ghi vào. Dữ liệu trong Named Volume vẫn tồn tại sau khi container ghi dữ liệu kết thúc và bị xóa.

## 4. Kiểm tra danh sách volume

```bash
docker volume ls
```

Kết quả minh họa (log mô phỏng, chưa chạy Docker thực tế):

```text
DRIVER    VOLUME NAME
local     easy-volume
```
