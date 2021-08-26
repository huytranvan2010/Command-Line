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

# Redirecting input and output

**Command line redirection**

Redirection là quá trình sử dụng input/output của file hoặc câu lệnh để làm input cho file khác. Redirection có thể sử dụng `>` để ghi đè, `>>` để chèn vào cuối.
Ví dụ
```python
ls > directories.txt
```
Lệnh ls sẽ liệt kê tất cả cá files và thư mục trong current directory, sau đó nó sẽ ghi tên các files, thư mục đó vào directories. Ngoài ra có thể sử dụng câu lệnh sau để chèn vào file.
```python
ls >> directories.txt
```

**Tìm kiếm theo pattern**

```python
grep 'anh' file.txt
```
Tìm kiếm các dòng có chứa 'anh' trong `file.txt`.


```python
grep -R pattern directory
```
Câu lệnh này dùng để tìm kiếm các file trong directory theo mẫu (pattern) bao gồm cả trong subdirectory và đưa ra các tên file và dòng trong files đó chứa kết quả khớp.

Ví dụ
```python
grep -R red ./
```
Nó sẽ tìm tất cả các từ chứa `red` trong các files trong thư mục hiện tại `./` kể các trong các thư mục con.

**Case insensitive search - tìm kiếm không phân biệt hoa thường**

```python
grep -i pattern filename
```
Chúng ta có thể search file theo pattern. Nó tìm kiếm lines trong files khớp với mẫu, không phân việt hoa thường và trả về kết quả.



**cat Display**
```python
cat file1.txt
cat file1.txt file2.txt
```

Lệnh `cat` giúp hiển thị nội dung một hoặc nhiều file trên terminal.

**Redirecting output - chuyển hướng (chuyển đến) đầu ra**

```python
echo "Hello" > hello.txt
```
Kí hiệu `>` dùng để chuyển hướng output bằng cách lấy output ở bên trái và truyền vào như input đến file bên phải.

>Chú ý: nội dung file cũ bị xóa đi (ghi đè - overwrite), thay vào đó là "Hello"

**Append redirect shell command**

```python
echo "Hello" >> xinchao.txt
```
Nếu dùng kí hiệu `>>` nó sẽ chuyển output của command bên trái rồi chèn vào cuối file bên phải. Như vậy "Hello" sẽ được chèn vào cuối file. Chính xác là chèn vào dòng mới.

**Pipe (ống) shell command**
```python
# First, echo ""HelloWorld" will send Hello World to the standard output.
# Next, pipe | will transfer the standard output to the next command's standard input
# Finally, wc -c will count the number of words from ít standard input, which is 2
echo ""Hello World" | wc -c
```
Kí hiệu `|` được gọi là *pipe*. Nó được sử dụng để truyền standard output của lệnh phía bên trái thành standard input của câu lệnh phía bên phải.

## Configuring the environment
Environment variables là các variable có thể đươc sử dụng trên tất cả terminal command (dùng chung cho hệ điều hành và ứng dụng).

Dấu `~` trong là viết tắt cho `$HOME` (đường dẫn của home directory). Nên lệnh `cd $HOME` và `cd ~` hoàn toàn giống nhau. Nếu dùng mỗi `cd` nó cũng đưa về thư mục home.

```python
history
```
Nó giúp hiển thị tất cả các câu lệnh đã được thực thi trong phiên hiện tại (current session).

Biến môi trường `$HOME`.
```python
echo $HOME
```
Câu lệnh này trả về đường dẫn của *home directory*.

```python
env
```
Câu lệnh này trả về tất cả environment variables cho current session.

```python
alias pd="pwd"
```
Cho phép gán câu lệnh thành dạng rút gọn hơn (gọi là alias - tham chiếu).






