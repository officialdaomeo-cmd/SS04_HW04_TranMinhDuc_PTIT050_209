# Báo cáo Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Cách gỡ bỏ file khỏi cache của Git
Khi lỡ commit file `credentials.txt` chứa thông tin bảo mật, để loại bỏ file này khỏi sự theo dõi của Git mà vẫn giữ lại file vật lý trên đĩa cứng, ta sử dụng lệnh sau:

```bash
git rm --cached credentials.txt
```
Lệnh `--cached` giúp gỡ bỏ file khỏi Staging Area (index) của Git, do đó Git sẽ không theo dõi sự thay đổi của file này nữa, trong khi file vẫn tồn tại an toàn trong thư mục làm việc cục bộ.

Sau đó, để đảm bảo file này không bị thêm vào ở những lần commit sau, ta cần đưa tên file `credentials.txt` vào tập tin `.gitignore`.

## 2. Kết quả sửa đổi lịch sử (Amend)
Để sửa đổi nội dung và thông điệp của commit gần nhất (gỡ bỏ file bị nhầm và thay thế bằng `.gitignore` mới), ta sử dụng lệnh:

```bash
git commit --amend -m "Initial configuration with .gitignore"
```

Dưới đây là kết quả của lệnh `git log -n 1` để kiểm tra lịch sử commit đã được sửa:

```
commit 97107e34409aa4c539211f58a256295c2b9ba52b
Author: Tamidu <officialdaomeo@gmail.com>
Date:   Tue Oct 6 05:26:00 2026 +0700

    Initial configuration with .gitignore
```
Như kết quả trên, commit cũ chứa file bảo mật đã được ghi đè bằng commit mới với lời nhắn đã được làm sạch, và thông tin bảo mật không còn tồn tại trong lịch sử commit.
