---
name: requesting-code-review
description: Dùng khi hoàn thành một bản nháp content, viết xong bài quan trọng, chuẩn bị xuất bản/đăng bài, hoặc sau mỗi task trong quy trình làm content nhiều bước — để editor review bài trước khi lỗi lan rộng
---

# Requesting Content Review

Dispatch một subagent editor review bài content trước khi đăng, để bắt lỗi trước khi lỗi lan rộng. Reviewer được cung cấp ngữ cảnh được chuẩn bị chính xác để đánh giá — không bao giờ là lịch sử session của bạn.

**Core principle:** Review sớm, review thường xuyên.

## When to Request Review

**Bắt buộc:**
- Sau mỗi task trong superpowers:subagent-driven-development
- Sau khi viết xong bài quan trọng
- Trước khi đăng bài / xuất bản

**Nên làm:**
- Khi bí (cần góc nhìn mới)
- Trước khi viết lại toàn bộ (lấy baseline)
- Sau khi sửa bài flop

## How to Request

**1. Xác định phạm vi:**
- Đường dẫn bản nháp: file bài viết / content cần review
- Brief tương ứng: file content brief mà bài phải tuân theo

**2. Dispatch subagent editor:**

Dispatch một subagent `general-purpose`, điền template content-reviewer.

**Placeholders:**
- `{DESCRIPTION}` - Bài gì (chủ đề, định dạng, độ dài, đăng ở đâu)
- `{BRIEF_AND_CHECKLIST}` - Brief + checklist review: hook, fact, tone, CTA
- `{DRAFT_PATH}` - Đường dẫn file bản nháp cần review
- `{BRIEF_PATH}` - Đường dẫn file content brief tương ứng

**3. Xử lý feedback:**
- Lỗi nghiêm trọng (sai fact, vi phạm chính sách): sửa ngay
- Lỗi quan trọng (hook yếu, lệch tone): sửa trước khi đăng
- Lỗi nhỏ: ghi lại, sửa sau
- Reviewer sai: bật lại có lý lẽ

## Example

```
[Vừa xong bản nháp bài "7 dấu hiệu nhận biết người ái kỷ"]

Bạn: Để tôi nhờ editor review trước khi đăng.

DRAFT_PATH: drafts/ai-ky-7-dau-hieu.md
BRIEF_PATH: briefs/ai-ky-7-dau-hieu.md

[Dispatch subagent editor]
  DESCRIPTION: Bài Facebook 900 chữ về 7 dấu hiệu nhận biết người ái kỷ, kèm caption đăng video doodle
  BRIEF_AND_CHECKLIST: Brief briefs/ai-ky-7-dau-hieu.md + checklist: hook có gây tò mò trong 3 dòng đầu không, fact có chính xác không, tone có thân thiện chia sẻ không, CTA có rõ không
  DRAFT_PATH: drafts/ai-ky-7-dau-hieu.md
  BRIEF_PATH: briefs/ai-ky-7-dau-hieu.md

[Subagent trả về]:
  Điểm mạnh: Hook đặt câu hỏi đúng nỗi đau, cấu trúc 7 mục rõ ràng
  Issues:
    Quan trọng: Dấu hiệu 4 trích dẫn nghiên cứu không có nguồn
    Quan trọng: CTA cuối bài lệch tone (nghe như bán hàng, brief yêu cầu tone chia sẻ)
    Nhỏ: Câu mở đầu đoạn 5 hơi dài
  Đánh giá: Đăng được sau khi sửa

Bạn: [Sửa fact dấu hiệu 4 + viết lại CTA theo tone chia sẻ]
[Đăng bài]
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "Tôi tự đọc lại là được, không cần dispatch editor" | Bạn là người điều phối — tự đọc lại trong luồng chính đốt cửa sổ ngữ cảnh bạn cần để tiếp tục điều phối công việc. Dispatch subagent editor: bản nháp và việc đánh giá nằm trong ngữ cảnh của nó, chỉ kết quả review quay về với bạn. Hơn nữa, mắt bạn đã quen với bài mình viết — editor mới bắt được lỗi bạn không thấy. |
| "Reviewer cần đọc hết lịch sử chat của tôi mới hiểu bài" | Đưa cho nó ngữ cảnh được chuẩn bị chính xác (bài gì, brief nào, checklist nào), không bao giờ là lịch sử session của bạn. Việc đó giữ reviewer tập trung vào bản nháp, không phải quá trình suy nghĩ của bạn. |

## Red Flags

**Không bao giờ:**
- Bỏ review vì "bài đơn giản"
- Lờ lỗi nghiêm trọng (sai fact, vi phạm chính sách)
- Đăng bài khi còn lỗi quan trọng chưa sửa
- Cãi feedback đúng

**Nếu reviewer sai:**
- Bật lại với lý lẽ về mặt nội dung
- Chỉ ra brief/bản nháp chứng minh bài hiện tại đúng
- Yêu cầu làm rõ
