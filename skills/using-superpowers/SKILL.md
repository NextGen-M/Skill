---
name: using-superpowers
description: "Dùng khi bắt đầu bất kỳ buổi làm việc nào — thiết lập quy tắc tìm và dùng skill trước MỌI hành động, kể cả câu hỏi làm rõ."
---

<SUBAGENT-STOP>
Nếu bạn được điều phối làm subagent để thực thi một task cụ thể, bỏ qua skill này.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
Nếu bạn nghĩ có dù chỉ 1% khả năng một skill nào đó áp dụng được cho việc bạn đang làm, bạn BẮT BUỘC PHẢI gọi skill đó.

NẾU MỘT SKILL ÁP DỤNG CHO TASK CỦA BẠN, BẠN KHÔNG CÓ LỰA CHỌN. BẠN PHẢI DÙNG NÓ.

Điều này không thể thương lượng. Bạn không thể tự biện minh để né nó.
</EXTREMELY-IMPORTANT>

## Quy Tắc

**Gọi skill liên quan hoặc được yêu cầu TRƯỚC mọi phản hồi hay hành động** — kể cả câu hỏi làm rõ, khám phá kho content, hay đọc file. Nếu hóa ra không hợp, bạn không bắt buộc phải dùng tiếp.

**Trước khi vào chế độ lên kế hoạch:** nếu chưa brainstorm, gọi skill brainstorming trước.

Sau đó tuyên bố "Đang dùng [skill] để [mục đích]" và làm đúng theo skill. Nếu skill có checklist, tạo todo cho từng mục.

## Skill Priority

Khi nhiều skill cùng áp dụng, process skill đi trước — chúng định cách tiếp cận, rồi các skill triển khai (làm video, viết bài...) thực hiện theo. Brainstorming và systematic-debugging là hai process skill phổ biến nhất của Superpowers, nhưng quy tắc đúng với mọi process skill.

- "Viết bài về X" → superpowers:brainstorming trước, rồi đến các skill triển khai.
- "Bài này flop, sửa giúp" → superpowers:systematic-debugging trước, rồi đến các skill chuyên môn.

## Red Flags

Những suy nghĩ này nghĩa là DỪNG — bạn đang tự biện minh:

| Suy nghĩ | Thực tế |
|---------|---------|
| "Đây chỉ là câu hỏi đơn giản" | Câu hỏi cũng là task. Kiểm tra skill. |
| "Tôi cần thêm bối cảnh trước đã" | Kiểm tra skill đến TRƯỚC câu hỏi làm rõ. |
| "Để tôi đọc kho content trước đã" | Skill chỉ bạn CÁCH đọc. Kiểm tra trước. |
| "Tôi xem nhanh file/bản nháp cũ được mà" | File thiếu bối cảnh đối thoại. Kiểm tra skill. |
| "Để tôi thu thập thông tin trước" | Skill chỉ bạn CÁCH thu thập thông tin. |
| "Việc này không cần skill trang trọng" | Nếu có skill tồn tại, dùng nó. |
| "Tôi nhớ skill này rồi" | Skill thay đổi theo thời gian. Đọc bản hiện tại. |
| "Việc này không tính là task" | Hành động = task. Kiểm tra skill. |
| "Skill này là overkill" | Việc đơn giản hay hóa phức tạp. Dùng nó. |
| "Tôi làm nốt việc nhỏ này trước đã" | Kiểm tra TRƯỚC khi làm bất cứ thứ gì. |
| "Làm thế này thấy năng suất" | Hành động thiếu kỷ luật phí thời gian. Skill ngăn điều đó. |
| "Tôi biết khái niệm đó là gì" | Biết khái niệm ≠ dùng skill. Gọi nó. |

## Platform Adaptation

Nếu nền tảng của bạn xuất hiện ở đây, đọc file tham chiếu của nó để biết hướng dẫn đặc biệt:

- Claude Code: `references/claude-code-tools.md`
- Codex: `references/codex-tools.md`
- Pi: `references/pi-tools.md`
- Antigravity: `references/antigravity-tools.md`
- Hermes Agent: `references/hermes-tools.md`
- Muse: `references/muse-tools.md`

## User Instructions

Chỉ dẫn của bạn (CLAUDE.md, AGENTS.md, GEMINI.md..., yêu cầu trực tiếp) được ưu tiên hơn skill, skill ưu tiên hơn hành vi mặc định. Chỉ bỏ qua quy trình hay hướng dẫn của skill khi bạn đã nói rõ là bỏ.
