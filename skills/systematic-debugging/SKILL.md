---
name: systematic-debugging
description: Dùng khi bài flop, bài bị chê, tương tác tụt hoặc số liệu bất thường — trước khi viết lại
---

# Chẩn Đoán Bài Flop Có Hệ Thống

## Tổng quan

**Nguyên tắc cốt lõi:** LUÔN tìm ra nguyên nhân gốc trước khi viết lại. Sửa triệu chứng là thất bại.

**Vi phạm chữ của quy trình này là vi phạm tinh thần của việc chẩn đoán.**

## Luật sắt

```
KHÔNG VIẾT LẠI KHI CHƯA TÌM RA NGUYÊN NHÂN GỐC
```

Nếu bạn chưa hoàn thành Phase 1, bạn không được đề xuất cách viết lại.

## Khi nào dùng

Dùng cho BẤT KỲ vấn đề nào của content:
- Bài flop (reach / view thấp bất thường)
- Bài bị chê trong comment
- Bài vi phạm chính sách nền tảng
- Tương tác tụt dần qua các bài
- Sụt follower sau khi đăng bài

**NHẤT ĐỊNH dùng khi:**
- Đang vội ("sửa nhanh cho kịp đăng")
- "Chỉ cần đổi hook là xong" nghe có vẻ hiển nhiên
- Đã thử 2-3 cách viết lại mà vẫn flop
- Lần viết lại trước không ăn thua
- "Nhìn là biết lỗi ở hook"

**Đừng bỏ qua khi:**
- Bài có vẻ chỉ lỗi nhỏ (lỗi nhỏ cũng có nguyên nhân gốc)
- Đang gấp (vội vàng đảm bảo phải làm lại)
- Bạn muốn đăng NGAY (làm có hệ thống nhanh hơn mò mẫm)

## Bốn Phase

Bạn BẮT BUỘC hoàn thành từng phase trước khi sang phase tiếp theo.

### Phase 1: Điều tra nguyên nhân gốc

**TRƯỚC khi viết lại BẤT CỨ thứ gì:**

1. **Đọc kỹ số liệu**
   - Đừng lướt qua số liệu
   - Retention tụt ở giây thứ mấy? CTR bao nhiêu? Comment nói gì?
   - Số liệu thường chứa sẵn đáp án
   - Ghi lại con số cụ thể, đừng nhớ mang máng

2. **Tái hiện như người lạ**
   - Xem / đọc lại bài từ đầu đến cuối như người chưa từng biết bài này
   - Đọc to thành tiếng
   - Ghi lại: bạn chán ở đâu? Bạn thắc mắc ở đâu?
   - Nếu không tái hiện được cảm giác người xem → thu thập thêm dữ liệu, đừng đoán

3. **Check thay đổi gần đây**
   - Có gì thay đổi mà gây ra flop?
   - Giờ đăng khác mọi khi? Nền tảng đổi thuật toán?
   - Có sự kiện nóng nào đè lên không?
   - Khác biệt môi trường: đăng nhầm khung giờ, sai định dạng?

4. **Thu thập bằng chứng ở từng điểm chạm**

   **KHI bài có nhiều điểm chạm (hook → 3 giây đầu → thân bài → CTA):**

   **TRƯỚC khi đề xuất cách sửa, hãy đo từng điểm chạm:**
   ```
   Với MỖI điểm chạm:
     - Người xem vào với kỳ vọng gì?
     - Người xem ra với cảm xúc gì?
     - Kỳ vọng có được đáp ứng không?
     - Dữ liệu ở điểm chạm này nói gì?

   Đo một lượt để thấy GÃY ở đâu
   RỒI phân tích để xác định điểm chạm lỗi
   RỒI điều tra sâu điểm chạm đó
   ```

   **Ví dụ (video ngắn):**
   ```
   # Điểm chạm 1: Hook (0-3s)
   Kỳ vọng vào: tò mò vì tiêu đề
   Ra: ??? — retention giây 3 còn 40% → GÃY Ở ĐÂY

   # Điểm chạm 2: Thân bài (3-30s)
   Chưa cần xét — người xem đã rời ở điểm chạm 1

   # Điểm chạm 3: CTA (cuối bài)
   Chưa cần xét — không ai xem tới đây
   ```

   **Kết luận:** Gãy ở hook, không phải thân bài hay CTA.

5. **Trace hành trình người xem**

   **KHI vấn đề nằm sâu trong bài:**

   Xem `root-cause-tracing.md` trong thư mục này để biết kỹ thuật trace ngược đầy đủ.

   **Bản nhanh:**
   - Người xem rời đi ở đâu?
   - Điều gì ngay trước đó khiến họ rời đi?
   - Tiếp tục trace ngược cho tới khi tìm ra điểm khởi phát
   - Sửa ở điểm khởi phát, không sửa ở triệu chứng

### Phase 2: Phân tích mẫu

**Tìm ra mẫu trước khi sửa:**

1. **Tìm bài đã thành công**
   - Tìm bài cùng kênh, cùng chủ đề đã từng lên
   - Bài nào tương tự mà không flop?

2. **Đối chiếu kỹ**
   - Nếu học theo một format, xem lại bài mẫu TỪNG CHI TIẾT
   - Đừng đọc lướt — xem từng giây, đọc từng câu
   - Hiểu format thật sự trước khi áp dụng

3. **Liệt kê điểm khác biệt**
   - Bài flop khác bài lên ở những điểm nào?
   - Liệt kê MỌI điểm khác biệt, dù nhỏ: độ dài hook, nhịp câu, CTA, giờ đăng, thumbnail...
   - Đừng cho rằng "cái này chắc không quan trọng"

4. **Hiểu bối cảnh**
   - Bài lên lúc đó cần điều kiện gì?
   - Giờ đăng, trend, tâm lý người xem lúc đó?
   - Bài flop đang giả định điều gì mà không đúng nữa?

### Phase 3: Giả thuyết & kiểm chứng

**Phương pháp khoa học:**

1. **Nêu một giả thuyết duy nhất**
   - Nói rõ: "Tôi nghĩ X là nguyên nhân gốc vì Y"
   - Viết ra
   - Cụ thể, không chung chung
   - Ví dụ: "Hook hứa hẹn X nhưng thân bài nói về Y → người xem thoát ở giây 5"

2. **Kiểm chứng với thay đổi nhỏ nhất**
   - Sửa ĐÚNG 1 biến để kiểm chứng giả thuyết (viết lại hook, giữ nguyên thân bài)
   - Một biến một lúc
   - Đừng sửa nhiều thứ cùng lúc

3. **Xác minh trước khi đi tiếp**
   - Được? → Sang Phase 4
   - Không được? → Nêu giả thuyết MỚI
   - KHÔNG chồng thêm cách sửa lên trên

4. **Khi không biết**
   - Nói "Tôi không hiểu X"
   - Đừng giả vờ biết
   - Hỏi bạn
   - Tìm hiểu thêm

### Phase 4: Viết lại

**Sửa nguyên nhân gốc, không sửa triệu chứng:**

1. **Chốt hook + luận điểm mới**
   - Viết hook và luận điểm cho bản viết lại
   - Theo skill `superpowers:test-driven-development` để chốt hook đúng cách
   - BẮT BUỘC có trước khi viết lại

2. **Sửa một thứ một lúc**
   - Sửa đúng nguyên nhân gốc đã xác định
   - MỘT thay đổi một lúc
   - Không "tiện tay" sửa thêm chỗ khác
   - Không gộp cải tiến linh tinh

3. **Kiểm chứng bản viết lại**
   - Đọc lại toàn bộ?
   - Số liệu (nếu đã đăng thử) có cải thiện?
   - Vấn đề thật sự được giải quyết?
   - Dùng skill `superpowers:verification-before-completion` trước khi tuyên bố xong

4. **Nếu vẫn flop**
   - DỪNG
   - Đếm: Đã thử bao nhiêu cách?
   - Nếu < 3: Quay lại Phase 1, phân tích lại với thông tin mới
   - **Nếu ≥ 3: DỪNG và đặt câu hỏi về concept (xem bước 5)**
   - KHÔNG thử cách thứ 4 nếu chưa bàn về concept

5. **Nếu 3+ cách đều flop: Đặt câu hỏi về concept**

   **Dấu hiệu concept sai từ đầu:**
   - Mỗi lần sửa lại lộ ra vấn đề mới ở chỗ khác
   - Sửa thì phải "đập đi xây lại" mới được
   - Mỗi lần sửa lại sinh ra triệu chứng mới ở chỗ khác

   **DỪNG và đặt câu hỏi nền tảng:**
   - Góc nhìn này có đúng không?
   - Có phải đang cố đấm ăn xôi vì "đã đầu tư công sức"?
   - Nên đổi concept / format thay vì tiếp tục vá?

   **Bàn với bạn trước khi thử thêm cách nào**

   Đây KHÔNG phải giả thuyết sai — đây là concept sai.

## Red Flags - DỪNG LẠI và làm theo quy trình

Nếu bạn thấy mình đang nghĩ:
- "Sửa nhanh cho kịp đăng, điều tra sau"
- "Cứ thử đổi hook xem có lên không"
- "Sửa nhiều chỗ một lúc cho nhanh"
- "Khỏi cần đọc số liệu, tôi tự xem là biết"
- "Chắc là do hook, sửa nó đi"
- "Tôi chưa hiểu rõ nhưng cứ thử cách này"
- "Format mẫu là vậy nhưng tôi biến tấu chút"
- "Đây là các vấn đề chính: [liệt kê cách sửa mà chưa điều tra]"
- Đề xuất cách viết lại trước khi trace hành trình người xem
- **"Thử thêm một cách nữa" (khi đã thử 2+)**
- **Mỗi lần sửa lại lộ vấn đề mới ở chỗ khác**

**TẤT CẢ những dấu hiệu trên đều có nghĩa: DỪNG. Quay lại Phase 1.**

**Nếu 3+ cách đều flop:** Đặt câu hỏi về concept (xem Phase 4.5)

## Tín hiệu cho thấy bạn đang làm sai

**Để ý những lần bạn nhắc:**
- "Số liệu đâu?" — Bạn đang kết luận mà chưa kiểm chứng
- "Đừng đoán mò nữa" — Bạn đang đề xuất cách sửa mà chưa hiểu vấn đề
- "Đọc to bài lên xem" — Bạn nên tái hiện như người lạ
- "Chốt lại nguyên nhân là gì?" — Bạn đang sửa triệu chứng, không phải nguyên nhân gốc
- "Thử cách thứ mấy rồi?" (mất kiên nhẫn) — Cách tiếp cận của bạn không hiệu quả

**Khi thấy những tín hiệu này:** DỪNG. Quay lại Phase 1.

## Những lời ngụy biện thường gặp

| Ngụy biện | Sự thật |
|-----------|---------|
| "Bài này lỗi đơn giản, không cần quy trình" | Lỗi đơn giản cũng có nguyên nhân gốc. Quy trình xử lý lỗi đơn giản rất nhanh. |
| "Đang gấp, không có thời gian làm quy trình" | Chẩn đoán có hệ thống NHANH HƠN mò mẫm đoán-sửa. |
| "Cứ sửa thử trước, điều tra sau" | Cách sửa đầu tiên định hình cả quá trình. Làm đúng ngay từ đầu. |
| "Đăng thử xem lên không rồi tính" | Bài đăng thử không qua chẩn đoán thì flop cũng không cho bạn biết vì sao. |
| "Sửa nhiều chỗ một lúc cho nhanh" | Không biết cái nào có tác dụng. Còn gây thêm lỗi mới. |
| "Bài mẫu dài quá, tôi biến tấu theo ý mình" | Hiểu nửa vời đảm bảo flop. Xem kỹ toàn bộ. |
| "Nhìn là biết lỗi ở hook" | Nhìn thấy triệu chứng ≠ hiểu nguyên nhân gốc. |
| "Thử thêm một cách nữa" (sau 2+ lần thất bại) | 3+ lần thất bại = concept sai. Đặt câu hỏi về concept, đừng sửa tiếp. |

## Tham khảo nhanh

| Phase | Việc chính | Tiêu chí xong |
|-------|-----------|---------------|
| **1. Nguyên nhân gốc** | Đọc số liệu, tái hiện, check thay đổi, thu thập bằng chứng | Hiểu flop Ở ĐÂU và VÌ SAO |
| **2. Mẫu** | Tìm bài đã lên, đối chiếu | Liệt kê được điểm khác biệt |
| **3. Giả thuyết** | Nêu 1 giả thuyết, sửa 1 biến để kiểm chứng | Giả thuyết được xác nhận hoặc có giả thuyết mới |
| **4. Viết lại** | Chốt hook mới, sửa 1 thứ, kiểm chứng | Bài hết flop, số liệu cải thiện |

## Khi điều tra kết luận "không có nguyên nhân"

Nếu điều tra có hệ thống cho thấy vấn đề thật sự do yếu tố bên ngoài, thời điểm, hoặc nền tảng:

1. Bạn đã hoàn thành quy trình
2. Ghi lại những gì đã điều tra
3. Xử lý phù hợp (đổi giờ đăng, né sự kiện nóng, điều chỉnh kỳ vọng)
4. Theo dõi số liệu để điều tra tiếp khi cần

**Nhưng:** 95% trường hợp "không có nguyên nhân" là điều tra chưa đủ sâu.

## Kỹ thuật hỗ trợ

Các kỹ thuật này là một phần của chẩn đoán có hệ thống, có trong thư mục này:

- **`root-cause-tracing.md`** - Trace ngược hành trình người xem để tìm điểm khởi phát
- **`defense-in-depth.md`** - Thêm điểm kiểm tra ở nhiều lớp sau khi tìm ra nguyên nhân gốc
- **`condition-based-waiting.md`** - Thay "đăng bừa xem sao" bằng chờ đủ điều kiện (đủ dữ liệu, đúng thời điểm)
