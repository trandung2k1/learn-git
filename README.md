# Learn Git

## Git Commands Cheat Sheet

### Lệnh cơ bản

- `git fetch origin dev:dev`

  - Lấy code từ nhánh `dev` trên remote repository về máy cục bộ nhưng không merge hoặc áp dụng thay đổi.

- `git merge --squash dev`

  - Gộp tất cả các commit từ nhánh `dev` thành một commit duy nhất và sạch sẽ trên nhánh hiện tại.

### So sánh Git Merge và Git Rebase

- **`git merge`**:

  - Gộp toàn bộ các commit cũ từ nhánh nguồn vào nhánh hiện tại và tạo thêm một commit mới để lưu trạng thái merge.

- **`git rebase`**:

  - Lấy tất cả các commit mới nhất từ nhánh `main` và đưa chúng vào nhánh `dev` để đồng bộ.
  - Quy trình sử dụng:

    - Chạy `git fetch main` để cập nhật code mới nhất từ nhánh `main`.
    - Sau đó, sử dụng `git rebase main` để áp dụng các thay đổi.

  - **Lưu ý**: Cần cẩn thận khi rebase vì có thể xảy ra conflict (xung đột).

### Fetch và Pull

- **`git fetch`**:

  - Chỉ tải code từ remote repository về local repository mà không thực hiện merge.

- **`git pull`**:

  - Kết hợp `git fetch` và `git merge`. Ví dụ, khi pull nhánh `main` vào nhánh `dev`, code sẽ được tải về và tự động merge vào nhánh `dev`, tạo ra một commit mới lưu trạng thái.

### Kiểm tra sự thay đổi

- **`git diff`**:

  - Hiển thị các thay đổi:

    - Giữa thư mục làm việc và vùng staging (index).
    - Giữa các commit hoặc nhánh.

  - Kiểm tra thay đổi giữa index (staging) và commit cuối:

    ```
    git diff --staged
    ```

  - So sánh thay đổi giữa hai nhánh:

    ```
    git diff branch1 branch2
    ```

### Quản lý tệp

- **Xóa tệp trong Git**:

  ```
  git rm <file>
  ```

  - Lệnh này xóa file khỏi thư mục làm việc và staging area.

- **Đưa nhánh về trạng thái commit cụ thể**:

  ```
  git reset --hard <commit-id>
  ```

  - Lệnh này xóa tất cả các commit sau commit được chỉ định và đưa nhánh về trạng thái trước đó.

### Lệnh khác

- **`git stash`**:

  - Lưu tạm thời toàn bộ thay đổi (trên các file được theo dõi) và trả lại thư mục làm việc về trạng thái sạch sẽ.

- **`git show`**:

  - Hiển thị chi tiết thông tin commit hiện tại hoặc commit cụ thể (nếu chỉ định).

- **`git cherry-pick <commit-id>`**:

  - Áp dụng một commit cụ thể từ một nhánh khác vào nhánh hiện tại.
  - Ví dụ:

    ```
    git cherry-pick abc1234
    ```

  - Hữu ích khi bạn muốn chọn một thay đổi cụ thể mà không cần merge toàn bộ nhánh.

## Mẹo sử dụng

- Dùng `git rebase` để giữ lịch sử commit sạch sẽ, nhưng cần cẩn thận với xung đột.
- Dùng `git merge --squash` khi muốn gộp nhiều commit thành một commit duy nhất.
- Kiểm tra thay đổi bằng `git diff` hoặc `git diff --staged` trước khi commit.
- Dùng `git stash` khi cần lưu lại công việc đang làm dở để chuyển nhánh hoặc pull code.
