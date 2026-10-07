---
name: using-git-worktrees
description: Dùng khi bắt đầu làm một bài hoặc series content mới và cần một không gian nháp cô lập, hoặc trước khi thực thi kế hoạch content - đảm bảo không lẫn nháp giữa các bài
---

# Không Gian Nháp Cô Lập

## Tổng quan

Đảm bảo mỗi bài/series content được làm trong một không gian nháp riêng, không lẫn nháp với bài khác. Ưu tiên công cụ native của nền tảng bạn đang dùng. Chỉ fallback sang cách thủ công khi không có công cụ native.

**Nguyên tắc cốt lõi:** Phát hiện không gian cô lập đã có trước. Rồi dùng công cụ native. Rồi mới fallback thủ công. Không bao giờ chống lại harness.

**Thông báo khi bắt đầu:** "Tôi đang dùng skill using-git-worktrees để chuẩn bị một không gian nháp cô lập."

## Bước 0: Phát hiện không gian cô lập đã có

**Trước khi tạo bất cứ thứ gì, kiểm tra xem bạn đã ở trong một thư mục dự án riêng chưa.**

Nếu dự án của bạn là một git repo, chạy:

```bash
GIT_DIR=$(cd "$(git rev-parse --git-dir)" 2>/dev/null && pwd -P)
GIT_COMMON=$(cd "$(git rev-parse --git-common-dir)" 2>/dev/null && pwd -P)
BRANCH=$(git branch --show-current)
```

**Guard cho submodule:** `GIT_DIR != GIT_COMMON` cũng đúng khi ở trong git submodule. Trước khi kết luận "đã ở trong worktree," xác minh bạn không ở trong submodule:

```bash
# Nếu lệnh này trả về một đường dẫn, bạn đang ở submodule, không phải worktree — coi như repo thường
git rev-parse --show-superproject-working-tree 2>/dev/null
```

**Nếu `GIT_DIR != GIT_COMMON` (và không phải submodule):** Bạn đã ở trong một worktree liên kết. Bỏ qua Bước 1, nhảy tới Bước 2 (Chuẩn bị dự án). KHÔNG tạo thêm worktree nữa.

Báo cáo kèm trạng thái nhánh:
- Đang ở trên một nhánh: "Đã ở trong không gian nháp cô lập tại `<đường dẫn>` trên nhánh `<tên>`."
- Detached HEAD: "Đã ở trong không gian nháp cô lập tại `<đường dẫn>` (detached HEAD, do bên ngoài quản lý). Cần tạo nhánh khi kết thúc."

**Nếu `GIT_DIR == GIT_COMMON` (hoặc ở trong submodule):** Bạn đang ở một checkout repo thường.

Người cộng tác đã bày tỏ ý muốn về không gian nháp trong hướng dẫn của bạn chưa? Nếu chưa, hỏi ý họ trước khi tạo worktree:

> "Bạn có muốn tôi chuẩn bị một không gian nháp cô lập không? Nó giúp bản nháp bài này không lẫn với các bài khác."

Tôn trọng mọi ý muốn đã được nêu mà không hỏi lại. Nếu họ từ chối, làm tại chỗ và nhảy tới Bước 2.

**Nếu dự án KHÔNG phải git repo:** Kiểm tra xem bạn đã ở trong một thư mục riêng của bài này chưa — một thư mục chỉ chứa brief, bản nháp, tư liệu của đúng bài/series này, không lẫn file của bài khác. Nếu rồi, bỏ qua Bước 1, nhảy tới Bước 2. Nếu chưa, sang Bước 1 để tạo.

## Bước 1: Tạo không gian nháp cô lập

### 1a. Dự án là git repo

**Bạn có hai cơ chế. Thử theo thứ tự này.**

#### Cơ chế 1: Công cụ native của nền tảng (ưu tiên)

Người cộng tác đã muốn một không gian cô lập (đồng ý ở Bước 0). Bạn đã có sẵn cách tạo worktree chưa? Có thể là một tool tên kiểu `EnterWorktree`, `WorktreeCreate`, một lệnh `/worktree`, hay một flag `--worktree`. Nếu có, dùng nó và nhảy tới Bước 2.

Công cụ native tự lo vị trí thư mục, tạo nhánh, và dọn dẹp. Dùng `git worktree add` khi đã có công cụ native sẽ tạo ra trạng thái ma mà harness của bạn không thấy hay quản lý được.

Chỉ sang cơ chế 2 khi bạn không có công cụ native.

#### Cơ chế 2: Git worktree fallback

**Chỉ dùng khi cơ chế 1 không áp dụng** — bạn không có công cụ native. Tạo worktree thủ công bằng git.

##### Chọn thư mục

Theo thứ tự ưu tiên. Ý muốn rõ ràng của người dùng luôn thắng trạng thái filesystem quan sát được.

1. **Kiểm tra hướng dẫn của bạn xem có nêu thư mục worktree mong muốn không.** Nếu có, dùng nó mà không hỏi.

2. **Kiểm tra thư mục worktree nội bộ của dự án đã có:**
   ```bash
   ls -d .worktrees 2>/dev/null     # Ưu tiên (ẩn)
   ls -d worktrees 2>/dev/null      # Thay thế
   ```
   Nếu có thì dùng. Nếu cả hai đều có, `.worktrees` thắng.

3. **Nếu không có hướng dẫn nào khác**, mặc định dùng `.worktrees/` ở root dự án.

##### Xác minh an toàn (chỉ với thư mục nội bộ dự án)

**BẮT BUỘC xác minh thư mục đã được ignore trước khi tạo worktree:**

```bash
git check-ignore -q .worktrees 2>/dev/null || git check-ignore -q worktrees 2>/dev/null
```

**Nếu CHƯA ignore:** Thêm vào .gitignore, lưu bản nháp (commit) thay đổi đó, rồi tiếp tục.

**Vì sao quan trọng:** Ngăn vô tình đưa cả nội dung worktree vào repository.

##### Tạo worktree

```bash
# Xác định đường dẫn theo vị trí đã chọn
path="$LOCATION/$BRANCH_NAME"

git worktree add "$path" -b "$BRANCH_NAME"
cd "$path"
```

Đặt tên nhánh theo bài/series (ví dụ `bai-huong-dan-chup-anh`, `series-ai-ky`), không đặt tên chung chung.

**Sandbox fallback:** Nếu `git worktree add` thất bại vì lỗi quyền (sandbox từ chối), báo với người dùng là sandbox đã chặn tạo worktree và bạn làm trong thư mục hiện tại. Rồi chạy setup và kiểm tra baseline tại chỗ.

### 1b. Dự án không phải git repo

Tạo một thư mục riêng cho bài/series này:

```bash
mkdir -p "content/<ten-bai>/"
```

Thư mục này chứa brief, bản nháp, tư liệu tham khảo của đúng bài này — mọi file của bài này chỉ sống trong đó, không lẫn với bài khác. Đặt tên thư mục theo bài/series (ví dụ `content/huong-dan-chup-anh-chan-dung/`, `content/series-7-dau-hieu-ai-ky/`), không đặt tên chung chung kiểu `content/bai-moi/`.

## Bước 2: Chuẩn bị dự án

Chuẩn bị guideline và tư liệu tham khảo trước khi viết:

- **Guideline:** tone of voice, độ dài mục tiêu, quy tắc chính tả (ví dụ viết hoa, dấu câu), những từ/cụm cần tránh
- **Tư liệu tham khảo:** brief của bài, các nguồn research, bài mẫu cùng series để giữ nhất quán giọng văn
- Nếu là git repo, chạy setup kỹ thuật phù hợp nếu có (ví dụ cài dependency cho tooling hỗ trợ viết)

Mọi file guideline và tư liệu của bài này nằm trong không gian nháp vừa tạo — không đọc guideline của bài khác vào đây.

## Bước 3: Xác minh baseline sạch

Kiểm tra thư mục trống/sạch, không còn nháp cũ của bài khác lẫn vào:

```bash
ls -la "<không-gian-nháp>/"
```

**Nếu còn file lạ** (nháp của bài khác, file tạm không rõ nguồn gốc): Báo lại, hỏi có dọn hay điều tra trước khi viết.

**Nếu sạch:** Báo sẵn sàng.

### Báo cáo

```
Không gian nháp sẵn sàng tại <đường-dẫn-đầy-đủ>
Thư mục sạch, không lẫn nháp bài khác
Sẵn sàng viết <tên-bài/series>
```

## Quick Reference

| Tình huống | Hành động |
|-----------|-----------|
| Đã ở trong thư mục dự án riêng của bài này | Bỏ qua tạo mới (Bước 0) |
| Đã ở trong linked worktree | Bỏ qua tạo mới (Bước 0) |
| Ở trong submodule | Coi như repo thường (guard ở Bước 0) |
| Có công cụ native tạo worktree | Dùng nó (Bước 1a, cơ chế 1) |
| Không có công cụ native | Git worktree fallback (Bước 1a, cơ chế 2) |
| Không phải git repo | Tạo thư mục `content/<tên-bài>/` (Bước 1b) |
| `.worktrees/` đã tồn tại | Dùng nó (xác minh đã ignore) |
| `worktrees/` đã tồn tại | Dùng nó (xác minh đã ignore) |
| Cả hai đều tồn tại | Dùng `.worktrees/` |
| Không có cái nào | Kiểm tra file hướng dẫn, rồi mặc định `.worktrees/` |
| Thư mục chưa được ignore | Thêm vào .gitignore + lưu bản nháp |
| Lỗi quyền khi tạo | Sandbox fallback, làm tại chỗ |
| Còn file lạ trong thư mục | Báo lại + hỏi trước khi viết |
| Chưa có guideline/tư liệu | Chuẩn bị ở Bước 2 trước khi viết |

## Các lý do bào chữa thường gặp

| Lời bào chữa | Thực tế |
|--------|---------|
| "Tôi nhớ rõ đang ở thư mục nào mà, khỏi kiểm tra" | Chạy Bước 0. Không gian do harness tạo và submodule đều đánh lừa mắt thường; lệnh phát hiện mới kết luận được. |
| "Tạo thư mục/worktree riêng mất công, viết luôn cho nhanh" | Nháp lẫn nhau là cách bài flop ra đời: nhầm brief, nhầm tone, đăng nhầm bản. Cô lập ngay từ đầu rẻ hơn gỡ rối sau. |
| "`git worktree add` nhanh hơn mò công cụ native" | Công cụ native (ví dụ `EnterWorktree`) sở hữu vị trí, nhánh, và dọn dẹp. Bỏ qua nó là lỗi số 1 — tạo trạng thái ma mà harness không thấy hay quản lý được. |
| "Thư mục worktree chắc đã ignore rồi" | Chạy `git check-ignore`. Thư mục worktree không ignore sẽ đưa cả cây vào repo. |
| "Tên thư mục/nhánh nào cũng được" | Đặt tên theo bài/series. Tên chung chung (`bai-moi`, `test`) là cách nhầm lẫn bắt đầu. |
| "Thư mục trống rồi, khỏi xác minh baseline" | Nháp cũ của bài khác lẫn vào là nguồn của mọi nhầm lẫn sau này. Kiểm tra rồi mới viết; dọn hay giữ là quyết định của người cộng tác. |
| "Chưa có guideline cũng viết được" | Viết không guideline là viết hai lần: một lần viết, một lần sửa cho khớp tone. Chuẩn bị ở Bước 2. |
