---
name: diagnosing-superpowers
description: Dùng khi quy trình làm content trục trặc và bạn muốn biết tại sao — agent viết lại cùng một đoạn 3 lần, bỏ qua brief, skill không kích hoạt, "sao lâu thế", "sao tốn nhiều thế", "nó đang làm gì vậy" — hoặc khi muốn lập báo cáo sự cố cho team, cho session hiện tại hoặc session cũ đã xác định bằng id hoặc đường dẫn.
---

# Diagnosing Superpowers

## Overview

Cùng bạn chốt xem session làm content trục trặc ở đâu, đọc bản ghi phiên trên đĩa, và báo cáo những gì đã xảy ra kèm bằng chứng. Bạn báo cáo; bạn không chẩn đoán superpowers. Người tiếp nhận bundle hoặc issue quyết định superpowers có thay đổi gì không.

**Core principle:** Mọi phát hiện phải trích dẫn `đường-dẫn:dòng`. Không trích dẫn, không phát hiện. Mọi con số từ bản ghi phiên hoặc lệnh bạn chạy, không từ trí nhớ.

## Workflow

Tạo một todo cho mỗi bước. Bước 5–7 chỉ chạy khi đúng điều kiện đã nêu.

1. **Problem intake.** Hỏi từng câu một cho đến khi viết được câu mô tả: phiên nào, khoảng turn nào nếu biết, bạn kỳ vọng gì, thực tế gì, và chỉ số bạn quan tâm (thời gian, token, hành động lặp lại, một hành động cụ thể). "Sao lâu thế" là phàn nàn, không phải mô tả vấn đề. Ghi rõ mục tiêu có phải là báo cáo sự cố cho team không.
2. **Locate.** Quy mỗi session về đường dẫn filesystem tuyệt đối đã xác minh, dùng `references/session-discovery.md`. Xác nhận session cũ bằng cách trích prompt đầu tiên và timestamp của nó, liệt kê mọi candidate đã loại kèm lý do, hoặc "không có". Liệt kê bản ghi subagent. Tạo `~/.content/diagnosing/<session-id>/`, báo đường dẫn cho bạn, và điền `templates/case.md` ở đó, tuân thủ quy tắc provenance của nó cho quan sát môi trường và skill.
3. **Triage.** Tự đọc vùng quanh sự cố được báo. Rồi dispatch một analyst subagent cho mỗi khía cạnh song song, mỗi subagent được cấp đường dẫn file case, `prompts/analyst-common.md`, và một file khía cạnh từ `prompts/`: `skill-timeline.md`, `plan-adherence.md`, `repeated-work.md`, `stumbles.md`, `quality-evidence.md`, `request-conflicts.md`, `cost-and-time.md`. Chia khía cạnh theo khoảng turn khi bản ghi dài. Loại bỏ mọi phát hiện không có `đường-dẫn:dòng`.
4. **Report.** Điền mọi section của `templates/report.md` theo thứ tự, ghi ra workspace, cho xem, và đưa đường dẫn. Kiểm tra nội dung trích dẫn thực sự chứng minh điều gì và giữ lại case hỗ trợ; symlink alias không phải bản copy dư thừa.
5. **Báo cáo sự cố** — khi report §7 ghi có thể hoặc khả năng cao, hoặc bạn yêu cầu. Tìm trong các issue/sự cố đã ghi nhận xem có triệu chứng trùng khớp không, theo `references/github-issues.md`. Cho xem các match và đề xuất đính kèm report vào cái gần nhất. Nếu không match, điền `templates/issue.md`, ghi ra workspace, cho xem đúng text, và chỉ tạo issue sau khi được duyệt. `gh` không đính kèm file; nếu đã có bundle, đưa đường dẫn để bạn đính kèm trên trình duyệt.
6. **Export** — chỉ khi bạn yêu cầu bundle; không bao giờ build khi chưa được yêu cầu. Nếu mục tiêu intake là báo cáo sự cố, nói một lần rằng bundle đã lược bỏ thông tin nhạy cảm có sẵn khi cần, rồi chờ. Hỏi mức redaction, nêu rõ mỗi mức gồm gì: skeleton (không có body tool-result), evidence (body chỉ cho event được trích dẫn), full. Build bundle theo `templates/bundle-README.md`, dispatch `prompts/scrub.md`, rồi `prompts/scrub-audit.md`, lặp cả hai đến khi audit trả về CLEAN. Hoàn thành evidence check và reconciliation của template bundle trước khi cho xem scrub log cuối, danh sách file, và kết quả privacy/evidence. Nén (`zip -r` hoặc `tar -czf`) chỉ sau khi được duyệt. Kèm đường dẫn archive, nêu nó chứa gì, chỉ vào scrub log cho các chỗ đã thay thế, và nói lược bỏ có thể sót: bạn phải review mọi file trước khi chia sẻ.
7. **Similar sessions** — khi được yêu cầu. Biến phát hiện đã xác nhận thành signature, liệt kê candidate theo mtime và size, tìm số dòng marker, dispatch `prompts/similar-session.md` cho mỗi candidate song song, và append report §9.

## Quick reference

Cả bảy analyst luôn chạy. Bảng này cho biết ở bước 3 nên tự đọc vùng nào trước và trong verdict nên dẫn phát hiện nào.

| Complaint | Đọc trước, dẫn đầu bằng |
|---|---|
| "Sao lâu thế" | cost-and-time, stumbles |
| "Sao nó làm thêm việc này?" | repeated-work, plan-adherence |
| "Sao tốn nhiều thế?" | cost-and-time |
| "Nó đang làm gì vậy?" (vẫn đang chạy) | skill-timeline; ghi chú in-progress trong coverage |
| "Nó bỏ qua kế hoạch content" | plan-adherence, đọc dòng compaction trước |
| "Skill X không kích hoạt" | skill-timeline |

## Hard rules

- **Context safety.** Một dòng transcript có thể nặng cả megabyte. Tuân thủ `references/context-safety.md` với mọi file session, mọi lần.
- **Read-only.** Không bao giờ sửa, di chuyển hay xóa file session.
- **Đường dẫn tuyệt đối cho subagent.** "Session hiện tại" của subagent là của chính nó. Truyền đường dẫn tuyệt đối và id.
- **Chỉ tính lời của bạn.** Output của hook, system reminder và tool result không phải lời của bạn. Trong bản ghi subagent, "user" là parent agent.
- **Không chẩn đoán superpowers.** Report §7 nêu mức liên quan rồi dừng. Không bao giờ nêu defect của skill hay đề xuất thay đổi. Bạn có ép sửa cũng không được miễn; chỉ vào bước issue và nhắc rằng bundle có sẵn khi cần. Không khuyên bạn làm gì khác nữa.
- **Approval gates.** Không nén archive trước khi bạn đã xem scrub log và danh sách file. Không tạo issue hay comment trước khi bạn duyệt đúng text.
- **Intake trước analysis.** Không có gì ở bước 2–7 bắt đầu trước khi bạn đã trả lời. Nếu bạn vắng mặt, viết câu hỏi ra rồi dừng. Câu mô tả bạn tự dựng lại cho họ không phải câu trả lời. Yêu cầu đã được scope sẵn — một event cụ thể, cái gì đang chạy ngay lúc này, hoặc phân tích cần chạy — bản thân nó là câu mô tả: trả lời nó, rồi hỏi tiếp. Một câu "tại sao" cho cả session là phàn nàn.

## Red Flags

| Thought | Reality |
|---------|---------|
| "Vấn đề rõ quá, bỏ qua intake" | Câu mô tả vấn đề định phạm vi mọi thứ. Hỏi đi. |
| "Bạn vắng mặt, tôi tự dựng câu mô tả" | Bạn không thể dựng lại cái họ muốn. Viết câu hỏi ra rồi dừng. |
| "Tôi quét hết một lượt rồi hỏi sau" | Quét không scope đốt ngân sách của họ vào câu hỏi sai. Hỏi trước. |
| "Họ muốn báo cáo sự cố, tôi build bundle luôn" | Bundle là dữ liệu session của họ, đóng gói lại. Chỉ build khi họ yêu cầu. |
| "Sửa nhỏ có định hướng, không cần cấu trúc lại" | Không phải việc của bạn quyết, dù nhỏ đến đâu. Báo cáo bằng chứng; người triage quyết định. |
| "Giá mỗi token ai cũng biết" | Con số bạn không tính từ bản ghi là bịa. Trích dẫn hoặc bỏ. |
