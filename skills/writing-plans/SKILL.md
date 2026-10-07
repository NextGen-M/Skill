---
name: writing-plans
description: "Dùng khi đã có content brief hoặc yêu cầu cho một task nhiều bước, trước khi động tay viết bài."
---

# Viết Kế Hoạch Content

## Tổng Quan

Viết kế hoạch content cho một người thực thi chưa từng thấy kho content
này hay brief này. Giả định họ viết tốt một khi biết chính xác hook,
outline và cách kiểm chứng cho từng bài, và họ sẽ tự chọn hợp lý ở
những chỗ kế hoạch để ngỏ. Điều họ không thể biết là những gì bạn đã
quyết: bài nào viết gì, hook nào đã chốt, tư liệu nào dùng, tiêu chí
kiểm chứng nào chứng minh từng bài đạt yêu cầu. Ghi lại tất cả. Chia
toàn bộ kế hoạch thành các task nhỏ vừa miệng. DRY. YAGNI. Kiểm chứng
mọi bài. Lưu bản nháp thường xuyên.

**Tuyên bố khi bắt đầu:** "Mình đang dùng skill writing-plans để tạo kế hoạch content."

**Bối cảnh:** Nếu làm trong không gian nháp cô lập, nó nên được tạo qua
skill `superpowers:using-git-worktrees` lúc thực thi.

**Lưu kế hoạch vào:** `docs/content/plans/YYYY-MM-DD-<ten-chien-dich>.md`
- (Bạn có thể ghi đè vị trí kế hoạch mặc định này theo ý mình)

## Kiểm Tra Phạm Vi

Nếu brief bao trùm nhiều cụm bài độc lập, lẽ ra đã được tách thành các
brief con trong lúc brainstorming. Nếu chưa, đề xuất tách thành nhiều kế
hoạch riêng — một kế hoạch cho mỗi cụm. Mỗi kế hoạch nên cho ra content
hoàn chỉnh, kiểm chứng được, đứng độc lập.

## Cấu Trúc Tài Liệu

Trước khi định nghĩa task, vạch ra những tài liệu nào sẽ được tạo hoặc
sửa và mỗi tài liệu chịu trách nhiệm gì. Đây là nơi các quyết định tách
nhỏ được chốt.

- Thiết kế các bài với ranh giới rõ và liên kết mạch lạc. Mỗi bài nên có một mục đích rõ ràng.
- Bạn suy luận tốt nhất về bản nháp mà mình nắm trọn trong bối cảnh, và bản nháp của bạn đáng tin hơn khi mỗi bài tập trung. Ưu tiên các bài nhỏ, tập trung hơn là một bài ôm đồm quá nhiều ý.
- Các bài thay đổi cùng nhau nên ở gần nhau. Tách theo trách nhiệm nội dung, không theo format kỹ thuật.
- Trong kho content hiện có, theo pattern đã thiết lập. Nếu kho content dùng format lớn, đừng đơn phương tái cấu trúc - nhưng nếu một bài bạn đang sửa đã phình quá mức, đưa việc tách bài vào kế hoạch là hợp lý.

Cấu trúc này định hướng việc tách task. Mỗi task nên cho ra thay đổi
khép kín, đứng độc lập vẫn có nghĩa.

## Định Cỡ Task Vừa Phải

Một task là đơn vị nhỏ nhất mang chu trình kiểm chứng riêng và đáng để
một reviewer mới kiểm tra. Khi vẽ ranh giới task: gộp các bước chuẩn bị,
research tư liệu, dựng khung vào task mà sản phẩm của nó cần; chỉ tách
ở chỗ reviewer có thể từ chối một task mà vẫn duyệt task bên cạnh. Mỗi
task kết thúc bằng một bản nháp kiểm chứng độc lập được.

## Độ Hạt Của Step

**Mỗi step là một hành động với kết quả kiểm tra được:**
- "Viết hook + luận điểm" - step
- "Kiểm chứng hook (đọc to, check fact)" - step
- "Viết bản nháp" - step
- "Đọc kiểm chứng toàn bài" - step
- "Lưu bản nháp" - step

## Header Của Tài Liệu Kế Hoạch

**Mọi kế hoạch PHẢI bắt đầu bằng header này:**

```markdown
# Kế Hoạch Content [Tên Chiến Dịch]

> **Dành cho người thực thi:** SUB-SKILL BẮT BUỘC: Dùng superpowers:subagent-driven-development (khuyên dùng) hoặc superpowers:executing-plans để thực thi kế hoạch này task-by-task. Các step dùng cú pháp checkbox (`- [ ]`) để theo dõi.

**Goal:** [Một câu mô tả chiến dịch này tạo ra gì]

**Cách tiếp cận:** [2-3 câu về hướng làm]

**Kênh đăng:** [Các kênh sẽ đăng: Facebook, TikTok, blog...]

**Brief:** [đường dẫn tới content brief mà kế hoạch này triển khai — kế
hoạch lập luận từ brief, nên brief đi cùng kế hoạch; người thực thi đọc cả hai]

## Ràng Buộc Chung

[Các yêu cầu chung của brief — tone, độ dài, quy tắc chính tả, giới hạn
nền tảng, quy tắc đặt tên file — mỗi dòng một ý, giá trị chính xác copy
nguyên văn từ brief. Mọi task mặc nhiên bao gồm cả mục này.]

## Điểm Rủi Ro

[Năm loại input hoặc chế độ lỗi mà brief ngầm chứa nhưng không bài nào
kiểm chứng trực tiếp, dễ khiến người đọc gặp vấn đề nhất — mỗi dòng một
ý, nêu rõ điều kiện và hành vi mà một người bình thường mong đợi, xếp
dòng dễ gặp nhất lên đầu. Brief là tài liệu tầm nhìn: nó nói content
phải làm gì, không nói hết mọi thứ nó sẽ gặp, và sự im lặng của brief
về một trường hợp không phải là giấy phép để bài viết hỏng ở trường
hợp đó. Viết danh sách ở đây một lần, brief trước mặt. Rồi với mỗi dòng,
thêm cách kiểm chứng tương ứng vào task sở hữu bài đó, theo đúng kiểu
step của task.]

---
```

## Cấu Trúc Task

````markdown
### Task N: [Tên Bài]

**Tài liệu:**
- Tạo: `content/bai-viet/exact-duong-dan.md`
- Sửa: `content/bai-viet/bai-cu.md:12-30`
- Kiểm chứng: đọc to thành tiếng + check fact theo checklist

**Kế thừa:**
- Dùng từ task trước: [hook đã chốt ở Task 1, tư liệu đã research ở Task 2 — ghi chính xác]
- Để lại cho task sau: [hook/CTA/tư liệu mà task sau dựa vào — ghi chính xác câu chữ, số liệu, nguồn]

- [ ] **Step 1: Viết hook + luận điểm chính**

Hook: "<câu hook chính xác>"
Luận điểm: 3 gạch đầu dòng, mỗi ý một câu.

- [ ] **Step 2: Kiểm chứng hook**

Đọc to hook, check: gây tò mò trong 3 giây đầu? đúng fact? đúng tone?
Kết quả mong đợi: hook đạt cả ba.

- [ ] **Step 3: Viết bản nháp đầy đủ trong `content/bai-viet/exact-duong-dan.md`**

Dàn ý: [mở bài → 3 luận điểm → CTA], độ dài [X từ/phút], CTA chính xác:
"<câu CTA>".

- [ ] **Step 4: Đọc kiểm chứng toàn bài**

Đọc to thành tiếng toàn bài; check fact từng số liệu với nguồn; check
chính tả. Kết quả mong đợi: không vấp khi đọc to, mọi số liệu có nguồn,
không lỗi chính tả.

- [ ] **Step 5: Lưu bản nháp**

```bash
git add content/bai-viet/exact-duong-dan.md
git commit -m "draft: ten bai viet"
```
````

## Một Step Chứa Gì

Một step hoàn thành khi người thực thi chỉ có thể viết đúng một thứ hợp
lý từ nó. Đó là toàn bộ yêu cầu: không mơ hồ, không cần đầy đủ. Mỗi
loại step mang đúng thứ làm nó không mơ hồ, không hơn:

- **Step kiểm chứng:** nêu rõ kiểm chứng gì (đọc to? check fact nguồn nào? đọc thử với đối tượng nào?) và tiêu chí đạt là gì.
- **Step viết:** hook chính xác, dàn ý, file chứa nó, và các giá trị cụ thể brief đã chốt. Người thực thi viết phần thân bài. Thân bài chỉ xuất hiện nguyên văn khi brief đã chốt câu chữ.
- **Step đọc kiểm chứng:** cách kiểm chứng và kết quả thế nào là đạt.
- **Tham chiếu tới task khác:** block Kế thừa của task đó nói dùng gì; kế hoạch không lặp lại nội dung của task khác.

Kế hoạch là tập hợp những quyết định mà người thực thi không thể tự đưa
ra. Một kế hoạch dài hơn chính bài viết nó mô tả là đã viết hộ bài thay
vì lên kế hoạch. Những dòng không quyết định gì ("TBD", "xử lý các
trường hợp biên", "viết cho hay", "kiểm chứng các ý trên", một hook hay
CTA không task nào định nghĩa) là lỗi ngược lại, và phần tự review sẽ
bắt cả hai.

## Tự Review

Sau khi viết xong toàn bộ kế hoạch, nhìn lại brief bằng con mắt mới và
đối chiếu kế hoạch với nó. Đây là checklist bạn tự chạy — không phải
điều subagent đi làm.

**1. Bao phủ brief:** Lướt từng mục/yêu cầu trong brief. Có chỉ ra được
task nào thực hiện nó không? Liệt kê chỗ hổng nếu có.

**2. Quét step:** Mỗi step phải để người thực thi chỉ viết được đúng một
thứ hợp lý, và không step nào mang nhiều hơn thế: dòng không quyết định
gì là một lỗ hổng, đoạn văn mà hook và dàn ý đã quyết xong là bản chép
lại. Sửa cả hai.

**3. Nhất quán kế thừa:** Hook, CTA, số liệu, tên bài bạn dùng ở task sau
có khớp với những gì đã định nghĩa ở task trước không? Task 3 dùng hook
"3 sai lầm" nhưng Task 7 nhắc hook "5 sai lầm" là một bài flop chờ sẵn.

**4. Điểm rủi ro:** Với mỗi loại input hay chế độ lỗi mà brief ngầm chứa,
có task nào kiểm chứng nó không? Năm cái chưa được bao phủ mà dễ khiến
người đọc gặp vấn đề nhất đi vào mục Điểm Rủi Ro, và mỗi dòng ở đó được
thêm cách kiểm chứng vào task sở hữu bài, theo đúng kiểu step của task.
Mục trống nghĩa là bạn đã kiểm và thấy không có, không phải bạn bỏ qua.

**5. Tỷ lệ:** So độ dài kế hoạch với brief. Một kế hoạch dài gấp nhiều lần
brief nó triển khai là bản chép lại bài viết, không phải kế hoạch. Nếu
phần lớn tài liệu là các đoạn văn mẫu, thay thân bài bằng hook, dàn ý và
tiêu chí kiểm chứng, rồi kiểm tra mỗi step còn không mơ hồ không.

Nếu phát hiện vấn đề, sửa ngay trong file. Không cần review lại — sửa rồi
đi tiếp. Nếu thấy yêu cầu trong brief chưa có task nào làm, thêm task.

## Bàn Giao Thực Thi

Sau khi lưu và tự review kế hoạch, gửi link cho bạn đọc. Nếu bạn đã nói
rõ phương thức thực thi từ trước, mời bạn đọc kế hoạch và xác nhận nó
đúng ý bạn; chờ bạn duyệt rồi mới triển khai theo phương thức đã giữ.
Nếu chưa, mời bạn đọc kế hoạch và chọn phương thức thực thi trước khi
triển khai.

**Khi chưa có phương thức thực thi được chỉ định:**

**"Kế hoạch đã xong, lưu ở `docs/content/plans/<tên-file>.md`. Bạn đọc giúp mình. Bạn muốn thực thi theo cách nào?**

- **Subagent-driven** - Một subagent mới thực thi từng task và một reviewer mới kiểm tra trước khi sang task tiếp theo, rồi review toàn bộ ở cuối. Kỹ nhất; tốn một context mới cho mỗi task và mỗi lần review.
- **Native** - Mình tự thực thi mọi task trong phiên này, theo cách nền tảng này chạy việc, rồi một reviewer mới trên model mạnh nhất kiểm tra toàn bộ ở cuối. Rẻ nhất và nhanh nhất; không có review độc lập cho đến cuối. Chạy tốt với model phiên tầm trung, vì kế hoạch đã gánh phần thiết kế.

**Với kế hoạch này mình đề xuất <một trong hai>, vì <một câu rút từ kế hoạch: các task phụ thuộc lẫn nhau thế nào, có bao nhiêu task, đăng sai thì thiệt hại gì>. Kế hoạch đã đúng ý bạn chưa, và mình thực thi theo cách nào?"**

**Khi đã có phương thức thực thi được chỉ định:**

**"Kế hoạch đã xong, lưu ở `docs/content/plans/<tên-file>.md`. Bạn đọc giúp mình. Nó đã đúng ý bạn chưa?"**

**Nếu chọn Subagent-driven:**
- **SUB-SKILL BẮT BUỘC:** Dùng superpowers:subagent-driven-development

**Nếu chọn Native:**
- **SUB-SKILL BẮT BUỘC:** Dùng superpowers:executing-plans
