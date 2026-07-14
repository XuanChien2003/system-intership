# Thực hành chmod trên Linux 
### Bước 1. Đăng nhập root

```bash
sudo -i
```
---

### Bước 2. Kiểm tra các User

```bash
cat /etc/passwd | grep -E "chien2003|nxc|appuser"
```

Kết quả

![altimage](../5.Lab/Img/Chmod1.png)
---

### Bước 3. Tạo Group

```bash
groupadd developers
```
---

### Bước 4. Thêm User vào Group

```bash
usermod -aG developers chien2003
usermod -aG developers nxc
```

Kiểm tra

![altimage](../5.Lab/Img/Chmod2.png)
---

### Bước 5. Tạo thư mục thực hành

```bash
mkdir -p /labchmod
```

Đổi Owner và Group

```bash
chown chien2003:developers /labchmod
```

Phân quyền

```bash
chmod 775 /labchmod
```

Kiểm tra

```bash
ls -ld /labchmod
```

Ví dụ

![altimage](../5.Lab/Img/Chmod3.png)
---

### Bước 6. Chuyển sang User

```bash
su - chien2003
```

Di chuyển

```bash
cd /labchmod
```
---

# Ví dụ 1. Thêm quyền Execute cho Owner

### Tạo file

```bash
touch script.sh
chmod 644 script.sh
echo 'echo "script.sh da chay thanh cong"' > script.sh
```

### Trước

```bash
ls -l script.sh
```

![altimage](../5.Lab/Img/Chmod5.png)

Owner: `rw-` · Group: `r--` · Others: `r--`

**Test quyền (owner `chien2003`)**

```bash
./script.sh
```

Kết quả:

![altimage](../5.Lab/Img/Chmod90.png)

---

### Thực hiện

```bash
chmod u+x script.sh
```

---

### Sau

```bash
ls -l script.sh
```

![altimage](../5.Lab/Img/Chmod6.png)

**Test lại**

```bash
./script.sh
```

Kết quả:

![altimage](../5.Lab/Img/Chmod7.png)

Giải thích

- Owner được thêm quyền Execute → chạy được file.
- Group và Others giữ nguyên.

---

# Ví dụ 2. Xóa quyền Write của Owner

### Tạo file

```bash
touch report.txt
chmod 644 report.txt
```

### Trước

```bash
ls -l report.txt
```
![altimage](../5.Lab/Img/Chmod8.png)

**Test quyền (owner)**

```bash
echo "noi dung test" >> report.txt
```

---

### Thực hiện

```bash
chmod u-w report.txt
```

---

### Sau

```bash
ls -l report.txt
```
![altimage](../5.Lab/Img/Chmod9.png)

**Test lại**

```bash
echo "noi dung test" >> report.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod10.png)

Giải thích

Owner chỉ còn quyền đọc, không ghi được nữa.

---

# Ví dụ 3. Owner chỉ được Read

### Tạo file

```bash
touch secret.txt
chmod 644 secret.txt
```

### Trước

```bash
ls -l secret.txt
```
![altimage](../5.Lab/Img/Chmod11.png)

---

### Thực hiện

```bash
chmod u=r secret.txt
```

---

### Sau

```bash
ls -l secret.txt
```
![altimage](../5.Lab/Img/Chmod12.png)

**Test lại**

```bash
cat secret.txt        # vẫn đọc được
echo "test2" >> secret.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod13.png)

Giải thích

Owner chỉ được đọc, không còn ghi được.

---

# Ví dụ 4. Thêm quyền Write cho Group

### Tạo file

```bash
touch file1.txt
chmod 644 file1.txt
```

### Trước

```bash
ls -l file1.txt
```

![altimage](../5.Lab/Img/Chmod14.png)

**Test quyền — chuyển sang `nxc` (thành viên group developers)**

```bash
su - nxc
cd /labchmod
echo "test group" >> file1.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod15.png)

---

### Thực hiện (với owner `chien2003`)

```bash
chmod g+w file1.txt
```

---

### Sau

```bash
ls -l file1.txt
```

![altimage](../5.Lab/Img/Chmod16.png)

**Test lại (vẫn với `nxc`)**

```bash
echo "test group" >> file1.txt
cat file1.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod17.png)

Giải thích

Group được phép sửa file.

---

# Ví dụ 5. Thêm quyền Execute cho Group

### Tạo file

```bash
touch file2.txt
chmod 644 file2.txt
```

### Trước

```bash
ls -l file2.txt
```

![altimage](../5.Lab/Img/Chmod18.png)

**Test quyền (`nxc`)**

```bash
./file2.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod19.png)

---

### Thực hiện (owner)

```bash
chmod g+x file2.txt
```

---

### Sau

```bash
ls -l file2.txt
```

![altimage](../5.Lab/Img/Chmod20.png)

**Test lại (`nxc`)**

```bash
./file2.txt
```

![altimage](../5.Lab/Img/Chmod21.png)

Giải thích

Group được phép thực thi file.

---

# Ví dụ 6. Xóa quyền Read của Group

### Tạo file

```bash
touch file3.txt
chmod 644 file3.txt
```

### Trước

```bash
ls -l file3.txt
```

![altimage](../5.Lab/Img/Chmod22.png)

Ý nghĩa: Owner `rw-` · Group `r--` · Others `r--`

**Test quyền (`nxc`)**

```bash
cat file3.txt
```

![altimage](../5.Lab/Img/Chmod23.png)

---

### Thực hiện (owner)

```bash
chmod g-r file3.txt
```

---

### Sau

```bash
ls -l file3.txt
```

![altimage](../5.Lab/Img/Chmod24.png)

**Test lại (`nxc`)**

```bash
cat file3.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod25.png)

Giải thích

- Group bị xóa quyền đọc.
- Owner và Others không thay đổi.

---

# Ví dụ 7. Thêm quyền Read cho Others

### Tạo file

```bash
touch file4.txt
chmod 644 file4.txt
```

### Trước

```bash
ls -l file4.txt
```

![altimage](../5.Lab/Img/Chmod26.png)

**Test quyền — chuyển sang `appuser` (không thuộc group developers → đại diện others)**

```bash
su - appuser
cd /labchmod
cat file4.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod27.png)

---

### Thực hiện (owner)

```bash
chmod o+r file4.txt
```

---

### Sau

```bash
ls -l file4.txt
```

![altimage](../5.Lab/Img/Chmod28.png)

**Test lại (`appuser`)**

```bash
cat file4.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod29.png)

Giải thích

- Others đã có quyền đọc (`r`) từ trước nên hành vi không đổi.

---

# Ví dụ 8. Thêm quyền Execute cho Others

### Tạo file

```bash
touch file5.txt
chmod 644 file5.txt
```

### Trước

```bash
ls -l file5.txt
```

![altimage](../5.Lab/Img/Chmod30.png)

**Test quyền (`appuser`)**

```bash
./file5.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod31.png)

---

### Thực hiện (owner)

```bash
chmod o+x file5.txt
```

---

### Sau

```bash
ls -l file5.txt
```

![altimage](../5.Lab/Img/Chmod32.png)

**Test lại (`appuser`)**

```bash
./file5.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod33.png)

Giải thích

- Others được thêm quyền thực thi (`x`).
- Owner và Group giữ nguyên.

---

# Ví dụ 9. Xóa quyền Write của Others

### Tạo file

```bash
touch demo.txt
chmod 644 demo.txt
```

### Trước

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod34.png)

**Test quyền (`appuser`)**

```bash
echo "test" >> demo.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod35.png)

(others vốn chưa từng có quyền ghi)

---

### Thực hiện (owner)

```bash
chmod o-w demo.txt
```

---

### Sau

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod36.png)

**Test lại (`appuser`)**

```bash
echo "test" >> demo.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod37.png)

Giải thích

- Others vốn không có quyền ghi (`w`) nên quyền không thay đổi.

---

# Ví dụ 10. Thêm quyền Execute cho tất cả

### Tạo file

```bash
touch project.txt
chmod 644 project.txt
```

### Trước

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod38.png)

**Test quyền (cả 3 user)**

```bash
# chien2003 (owner)
./project.txt   # Permission denied

# nxc (group)
./project.txt   # Permission denied

# appuser (others)
./project.txt   # Permission denied
```

---
![altimage](../5.Lab/Img/Chmod39.png)

### Thực hiện (owner)

```bash
chmod a+x project.txt
```

---

### Sau

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod40.png)

**Test lại (cả 3 user)**

```bash
./project.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod41.png)

![altimage](../5.Lab/Img/Chmod42.png)

![altimage](../5.Lab/Img/Chmod43.png)

Giải thích

- Owner, Group, Others đều được thêm quyền Execute.

Kết quả: Owner `rwx` · Group `r-x` · Others `r-x`

---

# Ví dụ 11. Xóa quyền Write của tất cả

> Dùng lại `project.txt` từ Ví dụ 10 (không tạo file mới).

### Trước

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod44.png)

Ý nghĩa: Owner `rwx` · Group `r-x` · Others `r-x`

**Test quyền (owner)**

```bash
echo "test" >> project.txt
```
---

### Thực hiện

```bash
chmod a-w project.txt
```

---
### Sau

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod45.png)

**Test lại (owner)**

```bash
echo "test" >> project.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod46.png)

Giải thích

- Owner bị xóa quyền ghi (thay đổi thực sự).
- Group, Others vốn không có quyền ghi nên không đổi (test bằng `nxc`/`appuser` vẫn `Permission denied` như trước).

Kết quả: Owner `r-x` · Group `r-x` · Others `r-x`

---

# Ví dụ 12. Owner toàn quyền, Group đọc & thực thi, Others không có quyền

> Dùng lại `script.sh` từ Ví dụ 1 (không tạo file mới).

### Trước

```bash
ls -l script.sh
```

![altimage](../5.Lab/Img/Chmod47.png)

Ý nghĩa: Owner `rwx` · Group `r--` · Others `r--`

**Test quyền trước**

```bash
# nxc: ./script.sh -> Permission denied (group chưa có x)
# appuser: cat script.sh -> đọc được (others đang có r)
```
![altimage](../5.Lab/Img/Chmod49.png)

![altimage](../5.Lab/Img/Chmod50.png)
---

### Thực hiện (owner)

```bash
chmod u+rwx,g+rx,o-rwx script.sh
```

---

### Sau

```bash
ls -l script.sh
```

![altimage](../5.Lab/Img/Chmod51.png)

**Test lại**

```bash
# chien2003 (owner): ./script.sh -> chạy thành công
# nxc (group): ./script.sh -> chạy thành công
# appuser (others): cat script.sh -> Permission denied
```
![altimage](../5.Lab/Img/Chmod53.png)

![altimage](../5.Lab/Img/Chmod54.png)

Giải thích

- Owner có toàn quyền.
- Group được đọc và thực thi.
- Others bị xóa toàn bộ quyền, kể cả đọc.

---

# Ví dụ 13. Owner đọc ghi, Group chỉ đọc, Others không có quyền

> Dùng lại `report.txt` từ Ví dụ 2 (không tạo file mới).

### Trước

```bash
ls -l report.txt
```

![altimage](../5.Lab/Img/Chmod55.png)

Ý nghĩa: Owner `r--` · Group `r--` · Others `r--`

**Test quyền trước (owner)**

```bash
echo "x" >> report.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod56.png)

 (owner chưa có `w`).

---

### Thực hiện

```bash
chmod u=rw,g=r,o= report.txt
```

---

### Sau

```bash
ls -l report.txt
```

![altimage](../5.Lab/Img/Chmod57.png)

**Test lại**

```bash
# chien2003 (owner): echo "x" >> report.txt -> thành công
# nxc (group): cat report.txt -> đọc được; echo "x" >> report.txt -> Permission denied
# appuser (others): cat report.txt -> Permission denied
```
![altimage](../5.Lab/Img/Chmod58.png)

Giải thích

- Owner được đọc và ghi.
- Group chỉ được đọc.
- Others không còn quyền gì.

---

# Ví dụ 14. Numeric Mode 777

> Dùng lại `demo.txt` từ Ví dụ 9 (không tạo file mới).

### Trước

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod59.png)

Ý nghĩa: Owner `rw-` · Group `r--` · Others `r--`

**Test quyền trước (`appuser`)**

```bash
echo "x" >> demo.txt    # Permission denied
./demo.txt               # Permission denied
```

![altimage](../5.Lab/Img/Chmod60.png)

---

### Thực hiện (owner)

```bash
chmod 777 demo.txt
```
---

### Sau

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod61.png)

**Test lại (`appuser`)**

```bash
echo "x" >> demo.txt    # thành công
./demo.txt               # thành công
```
![altimage](../5.Lab/Img/Chmod62.png)

Giải thích

Tất cả người dùng đều đọc, ghi và thực thi được — kể cả `appuser` là others.

---

# Ví dụ 15. Numeric Mode 755

> Dùng lại `script.sh` từ Ví dụ 12 (không tạo file mới).

### Trước

```bash
ls -l script.sh
```
![altimage](../5.Lab/Img/Chmod63.png)

Ý nghĩa: Owner `rwx` · Group `r-x` · Others `---`

**Test quyền trước (`appuser`)**

```bash
cat script.sh   # Permission denied
```
![altimage](../5.Lab/Img/Chmod64.png)
---

### Thực hiện (owner)

```bash
chmod 755 script.sh
```

---

### Sau

```bash
ls -l script.sh
```

![altimage](../5.Lab/Img/Chmod65.png)

**Test lại (`appuser`)**

```bash
cat script.sh    # đọc được
./script.sh       # chạy được
echo "x" >> script.sh   # Permission denied (others không có w)
```
![altimage](../5.Lab/Img/Chmod66.png)

Giải thích

- Owner toàn quyền, Group và Others đọc + thực thi được, nhưng không ai ngoài owner ghi được.

---

# Ví dụ 16. Numeric Mode 700

> Dùng lại `secret.txt` từ Ví dụ 3 (không tạo file mới).

### Trước

```bash
ls -l secret.txt
```

![altimage](../5.Lab/Img/Chmod67.png)

Ý nghĩa: Owner `r--` · Group `r--` · Others `r--`

**Test quyền trước**

```bash
# nxc: cat secret.txt -> đọc được
# appuser: cat secret.txt -> đọc được
```
![altimage](../5.Lab/Img/Chmod68.png)
---

### Thực hiện (owner)

```bash
chmod 700 secret.txt
```

---

### Sau

```bash
ls -l secret.txt
```

![altimage](../5.Lab/Img/Chmod69.png)

**Test lại**

```bash
# chien2003 (owner): cat secret.txt -> OK; echo "x">>secret.txt -> OK; ./secret.txt -> OK
# nxc (group): cat secret.txt -> Permission denied
# appuser (others): cat secret.txt -> Permission denied
```
![altimage](../5.Lab/Img/Chmod70.png)

Giải thích

- Chỉ owner có toàn quyền; group và others bị chặn hoàn toàn, kể cả đọc.

---

# Ví dụ 17. Numeric Mode 644

> Dùng lại `report.txt` từ Ví dụ 13 (không tạo file mới).

### Trước

```bash
ls -l report.txt
```

![altimage](../5.Lab/Img/Chmod71.png)

Ý nghĩa: Owner `rw-` · Group `r--` · Others `---`

**Test quyền trước (`appuser`)**

```bash
cat report.txt   # Permission denied
```

![altimage](../5.Lab/Img/Chmod73.png)
---

### Thực hiện (owner)

```bash
chmod 644 report.txt
```

---

### Sau

```bash
ls -l report.txt
```

![altimage](../5.Lab/Img/Chmod74.png)

**Test lại (`appuser`)**

```bash
cat report.txt   # đọc được
echo "x" >> report.txt   # Permission denied
```
![altimage](../5.Lab/Img/Chmod75.png)

Giải thích

Đây là quyền phổ biến nhất đối với file văn bản: ai cũng đọc được, chỉ owner ghi được.

---

# Ví dụ 18. Numeric Mode 600

> Dùng lại `secret.txt` từ Ví dụ 16 (không tạo file mới).

### Trước

```bash
ls -l secret.txt
```

![altimage](../5.Lab/Img/Chmod76.png)

Ý nghĩa: Owner `rwx` · Group `---` · Others `---`

**Test quyền trước (owner)**

```bash
./secret.txt   # chạy được (owner có x)
```

![altimage](../5.Lab/Img/Chmod77.png)
---

### Thực hiện

```bash
chmod 600 secret.txt
```

---

### Sau

```bash
ls -l secret.txt
```

![altimage](../5.Lab/Img/Chmod78.png)

**Test lại (owner)**

```bash
./secret.txt
```

Kết quả:

![altimage](../5.Lab/Img/Chmod80.png)

Giải thích

Owner chỉ còn đọc/ghi, quyền thực thi bị xóa. Group/Others vẫn không có quyền gì (test `nxc`/`appuser` → `Permission denied` khi đọc).

---

# Ví dụ 19. Numeric Mode 555

> Dùng lại `project.txt` từ Ví dụ 11 (không tạo file mới).

### Trước

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod81.png)

Ý nghĩa: Owner `r-x` · Group `r-x` · Others `r-x`

**Test quyền trước (owner)**

```bash
echo "x" >> project.txt   # Permission denied (đã không có w từ trước)
```
![altimage](../5.Lab/Img/Chmod82.png)

---

### Thực hiện

```bash
chmod 555 project.txt
```

---

### Sau

```bash
ls -l project.txt
```

![altimage](../5.Lab/Img/Chmod83.png)

**Test lại**

```bash
# chien2003, nxc, appuser: cat project.txt -> OK; ./project.txt -> OK; echo "x">>project.txt -> Permission denied
```
![altimage](../5.Lab/Img/Chmod84.png)

Giải thích

File đã có quyền 555 từ trước nên hành vi không đổi: ai cũng đọc/thực thi được, không ai ghi được.

---

# Ví dụ 20. Numeric Mode 000

> Dùng lại `demo.txt` từ Ví dụ 14 (không tạo file mới).

### Trước

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod85.png)

Ý nghĩa: Owner `rwx` · Group `rwx` · Others `rwx`

**Test quyền trước (owner)**

```bash
cat demo.txt   # đọc được
```
![altimage](../5.Lab/Img/Chmod86.png)
---

### Thực hiện

```bash
chmod 000 demo.txt
```

---

### Sau

```bash
ls -l demo.txt
```

![altimage](../5.Lab/Img/Chmod87.png)

**Test lại**

```bash
# chien2003 (owner): cat demo.txt -> Permission denied
# nxc (group): cat demo.txt -> Permission denied
# appuser (others): cat demo.txt -> Permission denied
```

![altimage](../5.Lab/Img/Chmod88.png)

**Test riêng với root**

```bash
exit   # thoát về root nếu đang ở user khác
cat /labchmod/demo.txt
```

Kết quả: 

![altimage](../5.Lab/Img/Chmod89.png)

Giải thích

- Không ai (owner, group, others) đọc/ghi/thực thi được, kể cả chính owner.
- Riêng **root** vẫn có thể truy cập và thay đổi quyền của file nếu cần, vì root bỏ qua kiểm tra quyền file thông thường.

---
