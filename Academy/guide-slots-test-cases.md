# 🎫 GUIDE — Slots & Test Cases at uTest

> ⭐ Toàn bộ kiến thức về Slot, Test Case execution, BFV, Tester Review, TestRail, Best Practices
> Cập nhật lần cuối: **11/11/2026** · Style: EN = luật gốc · VN = tóm tắt thực chiến

---

## 1. Slot là gì?

**EN:** A slot is a testing reservation within a test cycle with specific requirements (location, language, device, OS, payment method, setup). When claiming a slot, testers must complete testing exactly according to the listed requirements.

### Slot ≠ Test Case

| | Definition | Example |
|---|-----------|---------|
| **Slot** | Define môi trường + điều kiện cần dùng để test | "US tester using iOS 17" |
| **Test Case** | Series of steps/instructions để verify app works as expected | Mở trang, tìm sản phẩm, thêm giỏ hàng... |

⚠️ Khi claim slot → phải dùng đúng env đã yêu cầu. ❌ Không fake environment để claim.

### 3 loại slot

| Loại | Miêu tả | Dấu nhận biết |
|------|---------|---------------|
| **Test Case slot** | Gắn với 1+ test case. Claim slot = nhận TC tự động | Cột Test Case ≥1 |
| **Exploratory slot** | Không có TC. Chỉ làm exploratory testing. Thanh Payout hiện **"Per Bug"** (chỉ trả cho bug approved) | Cột Test Case ghi **"0 Exploratory"**, Payout không cố định |
| **Usability Study slot** | Dùng trong Usability test cycle | Có trong cycle type Usability |

---

## 2. Slots Page Overview

Truy cập bằng cách click tab **Slots** trong cycle.

### Cấu trúc trang Slots

| Section | Nội dung | Ghi chú |
|---------|----------|---------|
| **Slot Instructions** | Hướng dẫn chung cho toàn bộ slotting trong cycle | Đọc kỹ trước khi claim |
| **Available Slots** | Slot còn chỗ, chưa claim | Dùng search field lọc theo description |
| **Claimed Slots** | Slot bạn đã claim | Click mở ra chi tiết |
| **Unclaimed Slots** | Slot từng claim rồi nhưng unclaim | — |

### Các cột trên bảng slots

| Cột | Ý nghĩa | Ghi chú |
|-----|---------|---------|
| **Slot Description** | Mô tả yêu cầu (click mở rộng xem đầy đủ + linked TC) | Có link **Preview** cho phép xem thử TC trước khi claim |
| **Deadline** | Thời hạn hoàn thành + submit tất cả TC của slot | — |
| **Test Case(s)** | Số TC liên kết (Exploratory = "0 Exploratory") | — |
| **Payout** | Tổng payout across TCs (Exploratory = "Per Bug") | — |
| **Effort** | Estimated thời gian hoàn thành TC | — |
| **Slots Remaining** | Còn lại bao nhiêu claims trong tổng available | — |
| **Waitlist Available** | Bao nhiêu chỗ waitlist available (nếu feature được bật) | — |

---

## 3. Claiming a Slot

### Quy trình claim

1. Accept Cycle & Claim a Slot (từ Overview page) → Slots page mở auto
2. Click mở rộng slot → đọc hết description
3. Dùng **Preview** link (nếu có) để xem thử TC, chắc chắn hiểu yêu cầu và có thể hoàn thành đúng hạn
4. Bấm **Claim**

### 💡 Important rules

| Rule | Giải thích |
|------|------------|
| **First come first serve** | Slot limited |
| Đúng environment | Phải match requirement mới claim |
| ❌ Không fake environment | Thêm device/service giả để claim = vi phạm |
| Native app: chọn env chính xác | Android/iOS native → chọn **"Native (No mobile browser)"**. Website → chọn browser đúng |
| Claim slot nhiều TC → hoàn thành ĐỦ | Thiếu 1 TC = không TC nào được APPROVED |
| Nếu không hoàn thành đúng hạn → **Unclaim** slot ngay | Không unclaim nếu đã submit TC → phải Unsubmit TC trước |
| Nếu một TC auto-unclaim do quá hạn → TẤT CẢ TC của slot đó cũng unclaim | — |

💡 Không còn TC slot → có thể claim **Exploratory slot** để vào cycle.

### Multiple slot claiming

Nếu cycle cho phép claim nhiều slot → hoàn thành slot đang hold TRƯỚC khi claim slot khác. Navigate đến Slots tab → check claimed → claim thêm.

---

## 4. Slot Features

### 4.1 Slot Waitlist Feature

Dành khi slot đã hết chỗ claim. Tester join waitlist → khi slot trống → nhận notification (email + push) → được quyền claim sớm (exclusivity period) trước khi mở cho mọi người.

| Điều khoản | Nội dung |
|------------|----------|
| Giới hạn số lần join | Khi đạt giới hạn → nút Join Waitlist disabled (grayed out) |
| Giới hạn số người/waitlist | Khi đạt → không ai join thêm được |
| Người join waitlist | ⚠️ Chỉ người CHƯA có TC slot được join (có Exploratory thì OK) |
| Đã có TC slot | Tự remove khỏi TẤT CẢ waitlists |
| Exclusivity period | Tester waitlist có thời gian nhất định để claim; nếu không → mở cho tất cả eligible tester |
| Fairness | Không biết ai đứng waitlist, không thể chọn người cụ thể |
| Thay đổi criteria | Nếu criteria thay đổi → người không match nữa bị remove khỏi waitlist + notification |
| Cách Leave | Bấm "Leave Waitlist" |

> 💡 Join waitlist ≠ chính thức chấp nhận cycle. Vẫn có thể decline cycle. Cần claim Exploratory slot nếu muốn join cycle.

### 4.2 Slot Claim Criteria Feature

Chỉ tester match requirements mới thấy slot ở Available Slots. Profile phải chính xác. ❌ Không falsify info.

Nếu criteria thay đổi giữa cycle:
- Người không match nữa → slot biến mất từ Available Slots
- Người match tiêu chí mới → sẽ thấy slot nếu còn chỗ

### 4.3 Slot Credentials Feature

TMs có thể thêm test credentials cho slot mỗi tester cần dùng tài khoản riêng.

| Tính năng | Chi tiết |
|-----------|----------|
| Credential visibility | ⚠️ Chỉ visible sau khi **đã claim slot** + cycle **active** |
| Sau unclaim hoặc locked | Biến mất (visible lại khi TC được Info Requested) |
| Đa slot claim | Mỗi slot có credential riêng → dùng đúng slot đang làm |

---

## 5. Test Cases

### 5.1 Test Case là gì?

Series bước được yêu cầu tester làm theo để kiểm tra product hoạt động như mong đợi. Giúp tester kiểm tra mà không cần hiểu sâu trước về product.

### 5.2 Cách thực thi Test Case

| Bước | Hướng dẫn |
|------|-----------|
| 1 | Mở TC → đọc hướng dẫn. Không rõ → hỏi TTL trong chat room, chờ xác nhận trước khi làm tiếp |
| 2 | ❌ Không đoán bừa Pass/Fail để chuyển sang bước tiếp |
| 3 | Check **Preconditions** (dưới Slot Description nếu có): thiết bị setup, initial instructions — bỏ qua = invalid results |
| 4 | Làm từ bước 1→n, KHÔNG bỏ sót |
| 5 | Follow environment đúng yêu cầu trong Slot Description |
| 6 | Có Expected Result → so sánh Actual Result. Match → **Pass**; Khớp → **Fail** |
| 7 | **Khi Fail:** <br>• Bug đã có → click **+1 Confirm** → ghi issue ID vào Actual Result → click **Fail Step**<br>• Bug chưa report → ghi giải thích ngắn trong Actual Result → click **Fail & Report Issue** → điền form → submit<br>• Xóa text prefilled trong Action Performed / Expected Result / Actual Result |
| 8 | Bước không có Expected Result → đánh dấu **Done** |
| 9 | Upload attachments đúng yêu cầu: Screenshot vs video (đọc kỹ bước — nếu yêu cầu screenshot, đừng upload video) |
| 10 | Blur **PII** (Personally Identifiable Information) trong attachment. Dùng Handbrake nếu file video quá lớn |
| 11 | Click **Submit Results** → nhập thời gian spent → click **Finish** |

⚠️ Tất cả step phải được hoàn thành → TC mới submit được. Không submit bước còn thiếu.

### 5.3 Attachments in Test Case

- Chỉ upload khi có yêu cầu
- Upload đúng thứ tự số lượng (vd "Minimum 1") → không hiển thị = optional
- Tên file phải clear/appropriate: tên area tested, feature, vị trí bug. Nếu overview/yêu cầu cụ thể naming convention → làm theo
- ❌ Không upload nhiều attachment cùng tên

---

## 6. Test Case Progress (Results) & Status

### 6.1 Results (tiến độ thực thi)

| Result | Ý nghĩa |
|--------|---------|
| **New** | Chưa làm gì (không bước nào được mark Pass/Fail/Done) |
| **Started** | Đã bắt đầu (ít nhất 1 bước marked), chưa submit. ⚠️ Quên submit TC này = không được trả tiền, không được approve/reject, TTL có thể unclaim |
| **Passed** | Submit rồi, tất cả bước đều Passed. Không tìm ra lỗi |
| **Failed** | Submit rồi, ≥1 bước Fail. ⚠️ **FAILED ≠ BỊ REJECT!** chỉ phản ánh việc bạn chọn Fail status |
| **Completed** | Submit rồi, tất cả Done (không có step nào có Expected Result) |
| **Unclaimed** | Bạn hoặc TTL unclaim (parentheses có lý do như Unclaimed (Time)/Unclaimed (Blocked)) |
| **Closed By TestCycle** | System unclaim vì cycle đã đóng |

### 6.2 Approval Status (trạng thái phê duyệt)

| Status | Ý nghĩa |
|--------|---------|
| **Pending** | Chưa được review (bao gồm cả unclaimed TC). TC vừa submit thường Pending |
| **Info Requested** | TTL reviewed + cần sửa bổ sung. ⚠️ **Bắt buộc fix + bấm "Confirm all requested info is added"** để chuyển về Pending + thông báo TTL |
| **Approved** | ✅ Được phê duyệt. Gửi payout (trừ Academy training TC = không có payout) |
| **Rejected** | ❌ Bị từ chối. Không được trả tiền. Xem comment tại sao reject → tránh repeat mistake |

---

## 7. Editing & Updating a Test Case

### 7.1 Khi nào được edit?

| Trạng thái | Editable? | Cách thực hiện |
|------------|-----------|----------------|
| **Pending** | ✅ Có | Open TC → **Undo Submission** → Sửa → **Submit Results** |
| **Info Requested** | ✅ Có | Open TC → Undo Submission → Fix theo TTL request → Submit Results → Bấm link **"Confirm all requested info is added"** → Send Response comment trong Comments field |

### 7.2 Khi nào KHÔNG được edit?

| Trạng thái | Lý do |
|------------|-------|
| **Unclaimed** | Chưa có work để chỉnh |
| **Pending (approval/rejection)** | Đang chờ TTL review → chỉ xem được |
| **Rejected** | Đã final |
| **Approved** | Đã final |

### 7.3 Responding to Messages & Info Requests

Khi TTL/customer gửi message trong TC → email notification + dashboard popup "New Message on Test Case".

**Reply message:** Dashboard/Tiles open TC → Messages tab → New Message → viết câu reply → Add button

**Respond to Info Request:**
1. Dashboard → More Information Requested section → View test case button
2. Mở TC → Info Requested panel (cạnh trái có red bar) → đọc TTL's message
3. Click **Undo Submission** → Fix steps → Submit Results → entered time → Finished
4. Bấm **"Confirm all requested info is added"** → alert TTL/customer → Status chuyển Pending
5. Viết comment trong reply message box → Send Response

---

## 8. Unclaiming a Slot

### Quy trình unclaim

1. TC tab → mở test case của slot muốn unclaim
2. Nếu đã submit TC → **Unsubmit** (với TẤT CẢ TC liên kết)
3. Slots tab → Unclaim → chọn reason → Confirm

### Notes quan trọng

- Unclaim slot → **unclaim luôn TẤT CẢ TC liên kết**
- Không thể unclaim nếu bất kỳ TC nào đã submitted → phải unsubmit hết trước
- Một TC auto-unclaim do quá hạn → tất cả TC slot đó cũng unclaim

---

## 9. Bug Fix Verification (BFV)

### BFV là gì?

Quá trình xác minh một bug đã fix sau khi customer release bản fix/new build. Tester re-test để kiểm tra bug còn tái diễn hay đã khắc phục.

### Quy trình BFV

1. Read cycle overview → accept invitation
2. Tab Test Cases → scroll đến Available Test Cases
3. Click **Claim** (hoặc Preview trước)
4. BFV TC thường tên dạng "Fix Verification for bug: ___", có sẵn Bug ID cần verify
5. Thực hiện với **cùng environment** như ban đầu
6. Debug vẫn còn → **Fail step** + giải thích + **bắt buộc có comment** (không submit được nếu không comment)
7. Bug đã fix → **Pass step** + attachment chứng minh

⏰ BFV TC bị **auto-unclaim sau 2 giờ** nếu không submit → tester khác có thể claim.

Cột **Verification** trong Issues list: trạng thái `Requested` = có BFV TC được tạo → tester có thể claim.

---

## 10. Tester Review

### What is it?

Phương pháp thu thập feedback về sản phẩm trong Functional Test Cycle. Customer cần real-world perspective từ nhiều tester.

### How to write

1. Đọc overview → test sản phẩm kỹ
2. Bấm **Write a Review** (góc trên bên phải)
3. Trả lời câu hỏi **trung thực + đầy đủ câu**
4. ⭐ Star rating phải khớp mô tả (VD: 2 star → mô tả lý do tại sao đáng 2 sao)
5. **❌ KHÔNG DÙNG AI VIẾT REVIEW** — vi phạm = ban account
6. Click Submit → (cycle Locked rồi → không submit/edit được)

Best practices: Trả lời trung thực (đừng ngại feedback tiêu cực), câu đầy đủ ("The app is good/bad" = vô dụng).

---

## 11. TestRail

TestRail là web-based tool dùng bởi một số Applause customers để quản lý test suites, execute tests, track results.

### Terminologies

Term | Định nghĩa
---- | -----------
Dashboard | Trang đầu tiên sau login
Test Case | Tập bước kiểm tra product
Test Suite | Nhóm TC kiểm thử một tính năng/nhóm tính năng
Test Run | Hành động chạy TC trong môi trường + phiên bản cụ thể
Test Plan | Tập nhiều Test Run
Milestone | Stage/target của project (planned release, completed internal testing...)
Project | Top-level organizational unit

### TestRail statuses

Status | Ý nghĩa
------ | ---------
**Passed** | Kết quả đúng Expected
**Failed** | Kết quả không khớp Expected
**Blocked** | Không thể test vì tính năng bị broken / không khả dụng
**Retest** | TC fail vì bug, bug đã fix → cần test lại
**Untested** | Chưa chạy, không có result

### Quy trình thực thi TC trong TestRail

1. Truy cập link → login bằng credential cung cấp trong cycle
2. Bên trái menu → mở folder chứa TC assigned cho mình
3. Mở từng step → làm theo instruction
4. Click **Add Result** → chọn Status (Passed/Failed/Blocked)
5. Click icon ảnh → upload screenshot nếu yêu cầu
6. Comment field → miêu tả kết quả / thông tin cần
7. Bước fail → Defects field → ghi Bug ID (nếu yêu cầu)
8. Click Add Result → bước tiếp theo
9. Sau khi hoàn thành → quay về uTest Platform → submit TC bình thường

⚠️ Tài khoản TestRail thuộc **customer**:
- Đăng xuất sau khi test xong
- ❌ Không login nhiều lần
- ❌ Không đổi password/settings
- Chỉ chạy TC được phân công
- Hỏi TTL nếu nghi ngờ/có vấn đề

---

## 12. Best Practices cho Slots & Test Cases

| Vấn đề | Khuyến nghị |
|--------|-------------|
| Hoàn thành đúng hạn | Đọc kỹ cycle/slot instructions → chỉ claim slot match + có thời gian hoàn thành → nếu không kịp → **unclaim ngay** + nói TTL trong chat |
| Delay impact | Không giữ TC idle, unclaim chậm, hoặc TTL phải unclaim → trừ rating, giảm cơ hội invite sau |
| Environment chuẩn | Claim slot đúng env → không fake environment → thực thi TC đúng env đã chọn → sai env = rejection |
| Execute chất lượng | Làm từng bước thật sự → attach đúng yêu cầu → comment nếu cần → mỗi failed step phải có bug ID |
| Phản hồi nhanh | Trả lời Info Request message ASAP → attach nhỏ (nén nếu cần) → submit bằng **Submit Results** + **time spend** (quên submit = không được thanh toán) |
| Accuracy | Điền thời gian chính xác |
