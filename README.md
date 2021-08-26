## Navigating the file system

In ra path của thư mục đang làm việc.
```python
pwd
```

Ci chuyển đến các thư mục khác, `..` kí hiệu thư mục cha, `.` kí hiệu thư mục hiện tại.
```python
cd direc
cd ..
```

Tạo một thư mục mới
```python
mkdir direc
```

Tạo một file mới
```python
touch new.txt
```

Có thể sử dụng `Tab` để tự động hoàn thành lệnh, sử dụng mũi tên lên xuống để di chuyển giữa các commands trước đó.

## Viewing and Changing the File System
**mv Move**
```python
mv index.html website/
```
`mv` giúp di chuyển file đến directory. File làm argument đầu tiên, destination directory làm argument thứ hai. Move sẽ di chyển file, điều này đồng nghĩa với việc file không còn trong thư mục cũ.

**rm Remove**
```python
rm file_name
```

```python
rm -r directory
```
Muốn xóa directory và files trong đó phải dùng thêm option `-r`.

**ls List**
```python
ls -a
ls -l
ls -t
```
`ls` dùng liệt kê các nội dung trong directory.
- `-a`: liệt kê tất cả nội dung bao gồm cả file ẩn
- `-l`: liệt kê ở dạng dài
- `t`: liệt kê nội dung theo thời gian sửa đổi.

**cp Coypy**
```python
cp file destination
```
copy vẫn giữ nguyên file trong thư mục cũ. Có thể copy nhiều file vào thư mục:
```python
cp file_1 file_2 destination
```