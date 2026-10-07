---
name: verification-before-completion
description: Dùng khi sắp tuyên bố công việc xong, đúng hoặc ổn — trước khi lưu bản nháp, đăng bài hay chuyển việc cho agent; bằng chứng trước tuyên bố, luôn luôn
---

# Kiểm Chứng Trước Khi Tuyên Bố Xong

## Tổng quan

**Nguyên tắc cốt lõi:** Bằng chứng trước tuyên bố, luôn luôn.

**Vi phạm chữ của luật này là vi phạm tinh thần của luật này.**

## Luật sắt

```
KHÔNG TUYÊN BỐ XONG KHI CHƯA CÓ BẰNG CHỨNG KIỂM CHỨNG MỚI
```

Nếu bạn chưa chạy bước kiểm chứng trong lượt này, bạn không được tuyên bố nó đạt.

## Hàm cổng (Gate Function)

```
TRƯỚC khi tuyên bố bất kỳ trạng thái nào hoặc tỏ vẻ hài lòng:

1. XÁC ĐỊNH: Bằng chứng nào chứng minh tuyên bố này?
2. THỰC HIỆN: Đọc / kiểm tra thật (mới, đầy đủ, ngay trong lượt này)
3. ĐỌC: Đọc hết output, đếm lỗi, ghi nhận con số
4. ĐỐI CHIẾU: Kết quả có xác nhận tuyên bố không?
   - Nếu KHÔNG: Nêu trạng thái thật kèm bằng chứng
   - Nếu CÓ: Nêu tuyên bố KÈM bằng chứng
5. CHỈ SAU ĐÓ: Mới được tuyên bố

Bỏ bước nào = nói dối, không phải kiểm chứng
```

## Các lỗi thường gặp

| Tuyên bố | Cần | Không đủ |
|----------|-----|----------|
| "Bài xong rồi" | Đọc lại full bản cuối từ đầu đến cuối, 0 lỗi chính tả | "Viết xong", "chắc ổn" |
| "Fact đúng" | Đối chiếu từng số liệu với nguồn, ghi nguồn | "Tôi nhớ là..." |
| "Hook dính" | Đọc to + tự chấm theo checklist hook | "Nghe hay đấy" |
| "Sửa flop xong" | Chỉ ra nguyên nhân gốc đã sửa + đọc lại | Đổi vài câu rồi đăng |
| "Agent làm xong" | Mở file diff / bản nháp kiểm tra thật | Agent báo "xong" |
| "Đúng brief" | Checklist từng mục brief | "Nhìn chung đúng" |

## Red Flags - DỪNG LẠI

- Dùng các từ "chắc", "có lẽ", "có vẻ", "hình như"
- Tỏ vẻ hài lòng trước khi kiểm chứng ("Tuyệt!", "Hoàn hảo!", "Xong!", v.v.)
- Sắp lưu bản nháp / đăng bài mà chưa kiểm chứng
- Tin báo cáo thành công của agent
- Chỉ kiểm chứng một phần
- Nghĩ "chỉ lần này thôi"
- Mệt và muốn cho xong việc
- **BẤT KỲ cách diễn đạt nào ngụ ý thành công mà chưa chạy kiểm chứng**

## Ngăn ngụy biện

| Ngụy biện | Sự thật |
|-----------|---------|
| "Chắc ổn rồi" | Đọc lại bản cuối đi |
| "Tôi tự tin" | Tự tin ≠ bằng chứng |
| "Chỉ lần này thôi" | Không ngoại lệ |
| "Đọc lướt qua thấy ổn" | Đọc lướt ≠ đọc kỹ |
| "Agent báo xong" | Kiểm tra độc lập |
| "Tôi mệt" | Mệt mỏi ≠ lý do |
| "Check một phần là đủ" | Một phần không chứng minh được gì |
| "Diễn đạt khác đi thì luật không áp dụng" | Tinh thần quan trọng hơn chữ |

## Các mẫu chính

**Bài xong:**
```
✅ [Đọc lại full bản cuối] [Thấy: 0 lỗi chính tả] "Bài xong"
❌ "Viết xong rồi" / "Chắc ổn"
```

**Fact:**
```
✅ [Đối chiếu từng số liệu với nguồn] [Ghi nguồn] "Fact đúng"
❌ "Tôi nhớ là..." / "Số này quen quen"
```

**Hook:**
```
✅ [Đọc to] [Chấm theo checklist hook] "Hook dính"
❌ "Nghe hay đấy" / "Hook này ổn mà"
```

**Sửa flop:**
```
✅ [Chỉ ra nguyên nhân gốc đã sửa] [Đọc lại bản mới] "Sửa flop xong"
❌ "Đổi vài câu rồi" / "Đăng thử xem sao"
```

**Đúng brief:**
```
✅ Đọc lại brief → checklist từng mục → đối chiếu từng mục → báo thiếu hoặc đủ
❌ "Nhìn chung đúng brief"
```

**Giao việc cho agent:**
```
✅ Agent báo xong → Mở bản nháp kiểm tra thật → Đối chiếu với yêu cầu → Báo trạng thái thật
❌ Tin báo cáo của agent
```

## Khi nào áp dụng

**LUÔN áp dụng trước:**
- MỌI tuyên bố xong / đúng / ổn (dù diễn đạt kiểu gì)
- MỌI biểu hiện hài lòng về công việc
- MỌI câu nói tích cực về trạng thái bài viết
- Lưu bản nháp, đăng bài, hoàn thành task
- Chuyển sang task tiếp theo
- Giao việc cho agent

**Luật áp dụng cho:**
- Cụm từ chính xác
- Diễn đạt khác nhưng cùng ý
- Ngụ ý thành công
- BẤT KỲ câu nào gợi ý hoàn thành / đúng đắn
