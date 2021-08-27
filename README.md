## Navigating the file system
Trong Unix, Command Line Interface (CLI) được gọi là Bash và shell prompt (dấu nhắc lệnh là `$`, nó xuất hiện thể hiện terminal sẵn sàng nhận lệnh). Trong Window sẽ tải Git bash về để dùng cho quen. Mac OS dùng Z shell cũng tương tự.

Thấy hay dùng **sundirectory/** để thể hiện thư mục (mình hay bỏ dấu /).

In ra path của thư mục đang làm việc (print working directory).
```python
pwd
```

Di chuyển đến các thư mục khác, `..` kí hiệu thư mục cha, `.` kí hiệu thư mục hiện tại.
```python
cd direc
cd ..
```

Tạo một thư mục mới (make directory)
```python
mkdir direc
```

Tạo một file mới
```python
touch new.txt
```

Có thể sử dụng `Tab` để tự động hoàn thành lệnh, sử dụng mũi tên lên xuống để di chuyển giữa các commands trước đó.

manipulation: thao tác

**Filesystem**
A filesystem organizes a computer’s files and directories into a tree structure:
- The first directory in the filesystem is the *root directory*. It is the parent of all other directories and files in the filesystem.
- Each parent directory can contain more child directories and files. In the filesystem on the right, blog/ is the parent of 2014/, 2015/, and hardware.txt.
- Each directory can contain more files and child directories. The parent-child relationship continues as long as directories and files are nested.

<img src="images/01.webp">

A command is a directive to the computer to perform a specific task. Lệnh là chỉ thị đến máy tính để thực hiện nhiệm vụ.


## Viewing and Changing the File System
**mv Move**
```python
mv index.html website/
```
`mv` giúp di chuyển file đến directory. File làm argument đầu tiên, destination directory làm argument thứ hai. Move sẽ di chyển file, điều này đồng nghĩa với việc file không còn trong thư mục cũ.

Có thể di chuyển cùng lúc nhiều files:
```python
mv my_file_1.txt my_file_2.txt my_directory/
```
Để đổi tên file có thể sử dụng `mv` như sau:
```python
mv file_origin.txt file_renamed.txt
```

**rm Remove**
```python
rm file_name
```

```python
rm -r directory
```
Muốn xóa directory và files trong đó phải dùng thêm option `-r`.

Nếu chỉ xóa tất cả các files trong directory mà không xóa directory
```python
rm directory/*
```
**ls List**
```python
ls -a
ls -l
ls -t
```
`ls` dùng liệt kê các nội dung trong directory.
- `-a`: liệt kê tất cả nội dung bao gồm cả file ẩn, directories, cả những cái bắt đầu với `.`
- `-l`: liệt kê ở dạng dài
- `t`: liệt kê nội dung theo thời gian sửa đổi.

Có thể kết hợp tất cả
```python
ls -alt
```

```python
drwxr-xr-x 5  cc  eng  4096 Jun 24 16:51  action
drwxr-xr-x 4  cc  eng  4096 Jun 24 16:51  comedy
drwxr-xr-x 6  cc  eng  4096 Jun 24 16:51  drama
-rw-r--r-- 1  cc  eng     0 Jun 24 16:51  genres.txt
```

The `-l` option lists files and directories as a table. **Here there are four rows, with seven columns separated by spaces**. Here’s what each column means:
- Access rights (quyền truy cập). These indicate the read, write, and execute permissions on the file or directory allowed to the owner, the group, and all users. You can read more about file permissions.
- Number of hard links. This number counts the number of child directories and files. This number includes the parent directory link (..) and current directory link (.).
- Tên user sở hữu file `cc`
- Tên của nhóm sở hữu `eng`
- Kích thước inbytes
- Ngày và thời gian lần cuối được sửa đổi
- Tên file hoặc dirctory

**cp Coypy**

copy vẫn giữ nguyên file trong thư mục cũ. Có thể copy nhiều file vào thư mục:
```python
cp file_1 file_2 destination
```
Change directory
```python
cd directory
```
```python
cd path_to_the_directory
```
Có thể copy cả thư mục. 

**Wildcards - Kí tự đại diện**
Thay vì sử dụng chính xác tên file chúng ta có thể sử dụng kí tự đặc biệt như * để chọn một nhóm files (gọi là wildcards - kí tự đại diện). Ví dụ có thể copy tất cả các file trong thư mục hiện tại vào thư mục khác:
```python
cp * my_directory/
```

```python
cp w*.txt my_directory/
```
Copy tất cả các files bắt đăù bằng `w` và kết thúc bằng `.txt` đến thư mục khác.

**cat**
Hiển thị nội dung file trên command line. we copy the contents of a source file into a destination file (copy nội dung từ source file vào destination file)
```python
cp source.txt destination.txt 
```
hoặc copy cả file vào destination directory
```python
cp file destination
```

# Redirecting input and output

What happens when you type this command?
```python
$ echo "Hello"
Hello
```
The echo command accepts the string “Hello” as standard input, and echoes the string “Hello” back to the terminal as standard output. echo nhận vào string làm standard input và trả về string như standard output.

Let’s learn more about standard input, standard output, and standard error:
- **Standard input**, abbreviated as `stdin`, is information inputted into the terminal through the keyboard or input device (thông tin nhận từ bàn phím, thiết bị đầu vào)
- **Standard output**, abbreviated as stdout, is the information outputted after a process is run (thông tin được đưa ra sau quá trình xử lý)
- **Standard error**, abbreviated as stderr, is an error message outputted by a failed process (lời nhắn lỗi được đưa ra bởi quá trình thất bại)

Redirection reroutes standard input, standard output, and standard error to or from a different location.

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
`grep` - global regular expression print.

```python
grep anh file.txt
```
Tìm kiếm các dòng có chứa 'anh' trong `file.txt`. Chúng ta không dùng dấu nháy trong câu lệnh.


```python
grep -R pattern directory
```
Câu lệnh này dùng để tìm kiếm các file trong directory theo mẫu (pattern) bao gồm cả trong subdirectory và đưa ra các tên file và dòng trong files đó chứa kết quả khớp. `-R` là kí hiệu của recursive. **Nó trả về filenames và các dòng khớp**.
```python
$ grep -R Arctic /home/ccuser/workspace/geography
 
/home/ccuser/workspace/geography/deserts.txt:Arctic Desert
/home/ccuser/workspace/geography/oceans.txt:Arctic Ocean
```

Ví dụ
```python
grep -R red ./
```
Nó sẽ tìm tất cả các từ chứa `red` trong các files trong thư mục hiện tại `./` kể các trong các thư mục con.

```python
grep -Rl pattern directory
```
Nó sẽ chỉ trả về các files mà không trả về các lines.
```python
$ grep -Rl Arctic /home/ccuser/workspace/geography
 
/home/ccuser/workspace/geography/deserts.txt
/home/ccuser/workspace/geography/oceans.txt
```

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
Nếu dùng kí hiệu `>>` nó sẽ chuyển output của command bên trái rồi chèn vào cuối file bên phải. Như vậy "Hello" sẽ được chèn vào cuối file. Chính xác là chèn vào dòng mới. Thêm dữ liệu mà không xóa cái cũ.

```python
cat deserts.txt >> forests.txt
```
**<**
```python
$ cat < deserts.txt
```
`<` takes the standard input from the file on the right and inputs it into the program on the left. Here, `deserts.txt` is the standard input for the `cat` command. The standard output appears in the terminal.

`<` laays standard input từ file bên phải và đưa vào chương trình bên trái. Ở đây file `deserts.txt` được làm input cho câu lệnh `cat`.

**| Pipe (ống) shell command**
```python
# First, echo ""HelloWorld" will send Hello World to the standard output.
# Next, pipe | will transfer the standard output to the next command's standard input
# Finally, wc -c will count the number of words from ít standard input, which is 2
echo "Hello World" | wc -c
```
Kí hiệu `|` được gọi là *pipe*. Nó được sử dụng để lấy standard output của câu lệnh phía bên trái thành standard input của câu lệnh phía bên phải.

```python
$ cat volcanoes.txt | wc 
```
Output của `cat volcanoes.txt` thành input cho `wc`. `wc` trả về **số dòng, số từ, số kí tự** trong `volcanoes.txt`.

```python
$ cat volcanoes.txt | wc | cat > islands.txt 
```
Nhiều `|` có thể được nối với nhau. Standard output của `cat volcanoes.txt` được truyền tới (pipe to) `wc` command. Standard output của `wc` lại được truyền tới `cat`. Cuối cùng standard output của cat được truyền tới `islands.txt` (chèn vào file mới).
**>**
```python
$ cat deserts.txt > forests.txt
```
`>` takes the standard output of the command on the left, and redirects it to the file on the right. Here the standard output of cat deserts.txt is redirected to forests.txt. Nội dung của file bên tráu được ghi đè vào file bên phải.

**sort**
```python
$ sort continents.txt 
```
`sort` lấy standaed input rồi sắp xếp chúng để được standard output (file ban đầu không đổi).

```python
$ cat glaciers.txt | sort > sorted-glaciers.txt
```
Lấy standard output từ câu lệnh `cat` và "pipe" nó đến `sort` để sắp xếp. Standard output từ `sort` được chuyển đến file mới có tên là `sorted-glaciers.txt`.

adjacent: /əˈdʒeɪsnt/: liền kề

```python
$ uniq deserts.txt 
```
`uniq` kí hiệu cho "unique". Nó lọc ra (filter out) bản sao liền kề (adjacent duplicate) trong file, **vẫn giữ lại một bản**. Nếu các bản sao không liền kề sẽ được giữ lại. Ở đay hiển thị output ra terminal.

```python
$ sort deserts.txt | uniq
```
Một cách sử dụng hiệu quả (effective way) `uniq` là sử dụng `sort` để sắp xếp sau đó "pipe" standard output đến uniq. Do đó các bản sao sẽ gần nhau và bị loại bỏ ra.

```python
sort deserts.txt | uniq > uniq-deserts.txt
```
Ở đây sẽ gửi nội dung được lọ rồi đến file mới.

**sed**
```python
sed 's/snow/rain/' forests.txt 
```
`sed` là viết tắt của "stream editor" - trình chỉnh sửa luồng. Nó nhận vào standard input và thay đổi nó dựa trên biểu thức trước khi hiển thị nó như standard output. Nó tương tự như tìm kiếm và thay thế.

Cùng xem biểu thức `'s/snow/rain/'`:
- `s`: viết tắt cho `substitution`. Nó luôn được sử dụng cho `sed` trong substitution (sự thay thế)
- `snow`: chuỗi tìm kiếm
- `rain`: chuỗi thay thế

Trong trường hợp này `sed` sẽ tìm kiếm `snow` trong file `forests.txt` và thay thế nó bằng `rain`. **Quan trọng, nó chỉ thay thế từ `snow` ĐẦU TIÊN trong mỗi dòng**.

```python
sed 's/snow/rain/g' forests.txt 
```
Câu lệnh bên trên có sử dụng thêm `g` (global). `sed` sẽ tìm kiếm `snow` trong file `forests.txt` và thay thế bằng từ `rain` globally. Có nghĩa rằng tất cả các từ `snow` đều được thay đổi bằng `rain.

Tuy nhiên `sed` bên trên chúng ta mới ghi lại command line ouput, còn file cũ KHÔNG ĐỔI. Để ghi lại file ban đầu chúng ta cần sử dụng option `-i` ở đầu command như sau:
```python
sed -i 's/snow/rain/g' forests.txt
```

Congratulations! You learned how to use the command line to redirect standard input and standard output. What can we generalize so far?
Redirection reroutes standard input, standard output, and standard error. The common redirection commands are:
- `>` redirects standard output of a command to a file, overwriting previous content.
- `>>` redirects standard output of a command to a file, appending new content to old content.
- `<` redirects standard input to a command.
- `|` redirects standard output of a command to another command.
A number of other commands are powerful when combined with redirection commands:
- `sort`: sorts lines of text alphabetically.
- `uniq`: filters duplicate, adjacent lines of text.
- `grep`: searches for a text pattern and outputs it.
- `sed`: searches for a text pattern, modifies it, and outputs it

## Configuring the environment

indispensible: /ˌɪndɪˈspensəbl/: không thể thiếu

Mỗi khi chúng ta mở Terminal nó tạo ra một session mới. Nó sẽ load các cài đặt và tùy chọn (tạo nên command line environment). Chúng ta có thể cấu hình environment để hỗ trợ các câu lệnh và chương trình chúng ta tạo ra. Điều này cho phép chúng ta tùy chỉnh lời chào, tham chiếu cho các câu lệnh và các biến có thể chia sẻ giữa các ứng dụng.

Đầu tiên chúng ta tim hiểu về `nano`, trình chỉnh sửa file duy nhất trong terminal. Nếu có vấn đề gì với `nano` nhấn `Crtl + C` để thoát. 

```python
nano hello.txt
```
Nó sẽ mở `nano` text editor với file mới `hello.txt`. Gõ vào đó dòng một dòng text. Nhấn `Ctrl + O` để lưu file, nhấn `Enter` để đồng ý và cuối cùng nhấn `Ctrl + X` để thoát. Có thể kiểm tra nội dung vừa nhập vào bằng câu lệnh
```python
cat hello.txt
```

> Chú ý: kí hiệu `^` trong chỉ dẫn tương ứng với Ctrl

**Bash Profile**
A bash profile is a file used to store environment settings for your terminal, and it’s accessible by the name `~/.bash_profile`.

**Bash profile** là file được sử dụng để lưu các cài đặt môi trường cho terminal và nó có thể tiếp cận được thông qua tên `~/.bash_profile`.

Khi session bắt đầu (mở Terminal) nó sẽ load tất cả các nội dung (một số cái chạy) của **bash profile** trước khi thực thi commands.:
- `~` thể hiện user's home directory
- `.` thể hiện file ẩn
- `~/.bash_profile` quan trọng bởi vì đây là cách câu lệnh (command) nhận ra bash profile.

Để mở và chỉnh sửa **bash profile** có thể sử dụng câu lệnh
```python
nano ~/.bash_profile
```

Khi chúng ta chỉnh sửa bash profile chúng ta có thể thêm các commands để thực thi mỗi khi terminal session mới được bắt đầu (terminal được mở thì có những commmands được thực hiện).

Để kích hoạt sự thay đổi được thực hiện trong `~/.bash_profile` cho session hiện tại chúng ta sử dụng câu lệnh dưới đây:
```python
source ~/.bash_profile
```
Câu lệnh này làm cho các thay đổi trong bash profile có hiệu lực ngay lập tức mà không cần đóng terminal và khởi động lại session mới.

**Ví dụ**:
```python
nano ~/.bash_profile 
```
Để mở bash profile. Trong `~/.bash_profile` nhập dòng sau:
```python
echo "Welcome, Jane Doe" 
```

Update sự thay đổi
```python
source ~/.bash_profile 
```
ngay lập túc chúng ta thấy nó hiện ra `"Welcome, Jane Doe"`.

**Aliases**

Như bên trên chúng ta có thể thêm các cài đặt và câu lệnh, cái mà sẽ được thực thi mỗi lần terminal mới được bắt đầu. Một loại cài đặt có thể tạo là **alias**. Đầu tiên vẫn phải mở bash profile đã:
```python
nano ~/.bash_profile 
```
Sau đó chèn thêm dòng sau vào đó
```python
alias pd="pwd"
```
Cho phép gán câu lệnh thành dạng rút gọn hơn (gọi là alias - tham chiếu). Câu lệnh `pd` bây giờ sẽ tương tự `pwd`. 

Nên nhớ thực hiện xong cũng cần phải update thông qua `source ~/.bash_profile` để alias có hiệu lực trong session hiện tại.

Chúng ta có thể thêm nhiều tham chiếu các lệnh cho session hiện tại.

**Environment Variables**

Environment variables là các variable có thể được sử dụng trên tất cả terminal command (dùng chung cho hệ điều hành và ứng dụng) và lưu giữ thông tin về environment (các cài đặt và sở thích - preference).

Điều gì xảy ra nếu chúng ta lưu câu sau trong **~/.bash_profile**.
```python
export USER="Jane Doe"
```
- Dòng `USER="Jane Doe"` sẽ cài đặt environment variable (biến môi trường) USER có tên là "Jane Doe" (như kiểu gán giá trị). Thường USER variable được đặt theo tên của người sở hữu máy tính
- Dòng `export` làm cho biến có giá trị đến tất cả các phiên con (child session) được khởi tạo từ phiên hiện tại mình đang đứng. Đây là cách làm cho biến tồn tại trong các chương trình.
- Ở command line, câu lênh `echo $USER` trra về giá trị của biến. **Chú ý `$` luôn được sử dụng khi trả về giá trị của biến**. 

**PS1 Environment variable**

**PS1** là biến môi trường xác định kiểu dáng và phong của command prompt (dấu nhắc lệnh).

Ví dụ nếu chúng ta lưu dòng này trong **~/.bash_profile**
```python
export PS1=">> "
```
- `export PS1=">> "` sẽ cài đặt command prompt variable và exports the variable. Ở đây chúng ta thay đổi command prompt (dấu nhắc lệnh) mặc định từ `$` sang `>>`.
- Sau khi sử dụng lệnh `source`, command line sẽ hiển thị dấu nhắc lệnh mới.

**HOME environment variable**

Biến môi trường `HOME` là biến hiển thị đường dẫn của home directory. Nhắc lại luôn sử dụng biến môi trường thì luôn kèm `$` phía trước.
```python
echo $HOME
```
Câu lệnh này trả về đường dẫn của *home directory*.

**PATH environment variable**

`PATH` là biến môi trường lưu giữ list của các directories được phân cách nhau bằng dấu hai chấm (colon).
```python
$ echo $PATH
 
/home/huytranvan2010/Nuclear/geant4.10.07.p02-install/bin:/home/huytranvan2010/Nuclear/root/bin:/home/huytranvan2010/miniconda3/condabin:/home/huytranvan2010/.local/bin:/home/huytranvan2010/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

Mỗi thư mục chứa scripts (tập lệnh hay kịch bản) cho command line thực thi. `PATH` đơn giản chứa list các directories có các scripts.

Ví dụ có nhiều câu lệnh chúng ta đã học là các scripts được lưu trong **/bin** directory
```python
/bin/pwd
/bin/ls
```

Chúng ta có thể chạy một số câu lệnh như trên, kết quả nó như `pwd` hay `ls`. Chúng ta có thể customize (tùy chỉnh) PATH variable khi thêm các scripts vào.

**env**
```python
env
```
Câu lệnh này trả về list of environment variables cho current user. Thấy không khi gõ lệnh này chúng ta sẽ thấy các environment variables như `PATH`, `USER`...

Có thể chọn giá trị của biến môi trường cụ thể ví dụ `PATH` thông qua lệnh sau:
```python
env | grep PATH
```
Như chúng ta đã biết standard output của `env` sẽ được pipe đến `grep`. Sau đó nó tìm kiến giá trị của `PATH` và được ra terminal. Cái này tương tự như `echo $PATH`.


Dấu `~` trong là viết tắt cho `$HOME` (đường dẫn của home directory). Nên lệnh `cd $HOME` và `cd ~` hoàn toàn giống nhau. Nếu dùng mỗi `cd` nó cũng đưa về thư mục home.

```python
history
```
Nó giúp hiển thị tất cả các câu lệnh đã được thực thi trong phiên hiện tại (current session).




Kí hiệu `/` trong Unix chỉ thư mục `root`, nó chứa tất cả các thư mục khác.
```python
cd /`
```
sẽ chuyển đến thư mục `root.

Lệnh wc (word count) trong các hệ điều hành Unix/ Linux được sử dụng để đếm số dòng mới, đếm số từ, đếm byte và ký tự trong một tệp được chỉ định bởi các file arguments. Cú pháp của lệnh wc như dưới đây.
```python
wc [options] filenames
```
Sau đây là các tùy chọn và cách sử dụng được cung cấp bởi lệnh.
- `wc -l`: prints số dòng trong một file. 
- `wc -w`: prints số từ trong một file. 
- `wc -c`: hiển thị số bytes trong một file. 
- `wc -m`: prints số kí tự trong một file. 
- `wc -L`: prints độ dài của dòng dài nhất trong một file







