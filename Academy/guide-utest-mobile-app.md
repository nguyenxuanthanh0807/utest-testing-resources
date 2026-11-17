# 📱 GUIDE — uTest Mobile App (Android/iOS)

> ⭐ Tính năng, navigation, test cycle management, reporting, chatting trên mobile app
> Cập nhật lần cuối: **11/11/2026** · Style: EN = luật gốc · VN = tóm tắt thực chiến

---

## 1. Giới thiệu & Tính năng chính

Released năm 2020 cho Android và iOS. Cho phép tester trải nghiệm uTest linh hoạt hơn, làm việc "on the go".

### Features của app

| Tính năng | Mô tả |
|-----------|-------|
| Nhận/accept invite | Test cycle invitations trên-the-go |
| Claim slots + TC | Nhận vị trí trong cycle |
| Execute TC + report issue | Làm test case + report bug trực tiếp từ mobile |
| Unclaim / Undo Submission | Hủy slot/test case hoặc hoàn lại submission |
| View/TTL messages + respond info requests | Trả lời yêu cầu thông tin bổ sung |
| Push notifications | Thông báo invite + announcement trong cycle |
| Profile maintenance | Chỉnh sửa basic profile, giữ account up-to-date |
| SRS | Nhận/handle Survey invitations |
| Chat | Cycle chat rooms + project chat rooms |
| Push notification mention | Khi @all/@testername được mention |

⚠️ **Không truy cập được Community** từ mobile app. Luôn bật automatic updates để không bỏ tính năng mới.

📖 Useful info thêm: https://www.utest.com/mobile/

---

## 2. Main Navigation (4 mục chính)

Sau khi đăng nhập, màn hình có 4 tab:

### Home

Hiển thị current test cycle invites + các cycle/case sắp hết hạn trong **24 giờ** → hiện dạng card ngang (scroll được).

- Mở invitation/cycle ending soon/test case bằng cách tap title
- SRS surveys xuất hiện ở đây
- 🔔 Bell icon (góc trái trên) → mở tất cả unread notifications về issues/test cases (vd: Info Requested)

### Projects

Liệt kê tất cả accepted test cycles → tổ chức thành 3 sub-tab: **Active** · **Pending** · **Locked**.

Mỗi cycle là một card hiển thị: tên cycle, ngày start/end, số issues đã report, số tester trong cycle, loại cycle (Functional, Usability...). Tap title → open chi tiết.

### Chat

Truy cập cycle chat rooms → classified theo cycle status (Active/Locked/Pending). Thêm project chatrooms đã được invite, contacts.

Expand category name bằng cách tap vào đó. Dùng Search field tìm nhanh cycle.

Dưới cùng: **My Account section** → Permanently Delete Account link.

### Profile

Sửa basic profile info → tap pencil button. Upload avatar từ thiết bị.

**Settings:** Nút Settings (góc trái trên Profile tab):
- Push notifications toggle
- About uTest, Terms and Conditions, Privacy Policy, End User License Agreement
- Log Out

---

## 3. Test Cycle Page trên Mobile App

Mở **Projects tab** → tap title cycle → mở test cycle details page.

Nếu cycle chưa accept → chỉ xem được Overview + Slots tabs. Sau khi accept → thêm nhiều tabs xuất hiện (horizontal scroll).

### Các tabs của cycle

| Tab | Nội dung | Ghi chú |
|-----|----------|---------|
| **Overview** | Description, In Scope, Out Of Scope, Bug Payout... | Expand/collapse từng section để view dễ dàng trên mobile |
| **Slots** | Available + claimed slots. Bấm Claim để nhận. Join Waitlist nếu slot đầy | Search field lọc theo description |
| **Test Cases** | Available + claimed TCs. Tap TC để xem/chọn bước. | Có BFV TC nếu có request fix |
| **Issues** | Danh sách bugs đã report trong cycle. Search/filter. Tap để xem detail. | Nút xanh bug icon (góc phải dưới) = Report Issue |
| **Attachments** | Attachments đính kèm builds/supplemental info. Tap xem/download | — |
| **Announcements** | Tin nhắn TTL/TE về cycle. Một số cần Acknowledge → bấm nút Acknowledge | Phải đọc kỹ announcements |

---

## 4. Accepting & Declining Invitation

### Nhận notification

Push notification từ app + email khi có cycle invitation mới.

### Quy trình accept

1. Tap notification → mở app vào Home tab (hoặc mở app trực tiếp)
2. Kiểm tra Project Invites section
3. Tap vào title cycle → mở page
4. Accept NDA: tick checkbox + Accept NDA button
5. Sau khi mở page → **đọc kỹ overview**: expand tất cả sections (In Scope, Out of Scope...)
6. Decide: Accept or Decline

| Action | Cách thực hiện |
|--------|----------------|
| **Accept** | Bấm Accept Cycle |
| **Decline** | Bấm Decline Cycle → chọn lý do → comment → Decline |

### Lưu ý đặc biệt

| Trường hợp | Diễn giải |
|------------|-----------|
| Special Requirements active | Nút Accept bị disabled → phải tick xác nhận meets requirements → mới enable Accept |
| Mandatory slotting enabled | Bấm "Accept & Claim Slot" → chuyển đến Slots tab → phải claim slot mới join được |
| Join waitlist | Không phải chính thức accepted → vẫn có thể leave waitlist + decline cycle |

---

## 5. Claiming Slots & Test Cases

### 2 loại slot trên app

| Loại | Miêu tả |
|------|---------|
| **Test Case linked slots** | Gắn với 1+ TC → claim slot = nhận TC tự động |
| **Exploratory slots** | Không có TC → chỉ exploratory testing |

### Claim slot qua app

1. Mở cycle page > navigate to Slots tab
2. Check available slots → chọn slot match requirements → Bấm **Claim**
3. Claim Test Case slot → TC assigned → kiểm tra Test Cases tab để xem TC

Nếu không còn TC slot available: Join Waitlist bằng nút **Join Waitlist**. Leave bằng **Leave Waitlist**.

Cũng có thể claim TC directly từ Test Cases tab (VD: BFV TC khi slot feature bị disable).

### Unclaim slot (app)

Apps → open cycle (Projects tab) → Slots tab → Section Claimed → Bấm **Unclaim**

---

## 6. Reporting Issues on Mobile App

### Issue/Bug là gì?

Bug = unexpected behavior hoặc malfunction trong thiết kế/functionality của product. Mobile app cho phép report issue + upload attachment trực tiếp.

### Steps reporting issue

Form chia 4–5 steps. Mỗi step có Next để chuyển sang step tiếp theo.

1. Navigate đến Issues tab của cycle
2. Bấm nút xanh **Report Bug** (góc phải dưới) → form mở ra
3. Điền thông tin bắt buộc từng step → Next để tiếp
4. Hoàn thành tất cả steps → Submit

### Edit/Discard Issue

Action: Trên Issues tab → Mở issue → ⋮ (ba chấm) góc phải trên → chọn hành động:

| Hành động | Chi tiết |
|-----------|----------|
| **Edit Issue** | Sửa thông tin → submit lại |
| **Discard Issue** | Xóa hẳn issue |

### Responding to Messages/Info Requests (mobile)

App → Home/Projects tab → bell icon góc phải trên (notifications) → tap message cần respond → Fix report/TC theo yêu cầu → **Send Confirmation** (khi hoàn thành). Hoặc view message → reply trực tiếp.

Cũng có thể mở TC/issue có message từ TTL → nhấn icon Notifications góc phải trên → đọc → xử lý.

---

## 7. Executing Test Cases (Mobile)

### Viewing test cases

- Mở cycle page → Test Cases tab → Available + claimed
- Tap title TC → xem steps
- Đầu trang: progress bar, tester name, build, environment details
- Tiếp đó: instructions + all steps cần execute
- ⚠️ Dùng đúng environment đã claim

### Executing & submitting

1. Mở TC → tap từng step để mở → bắt đầu từ Step 1
2. Đọc instruction → hoàn thành step bằng cách mark: **Done** / **Pass** / **Fail**
3. Nếu upload attachment → tap dấu `+` ở Results attachments
4. Vuốt ngang giữa các steps
5. Mark Pass/Fail → popup yêu cầu comment: comment **optional** khi Pass, **bắt buộc** khi Fail
6. Khi Fail → prompt report issue: kiểm tra issues đã có trước. Nếu bug đã report → Cancel popup. Nếu bug mới → report issue
7. Hoàn thành TẤT CẢ steps → bấm **Submit Test Case**
8. Nhập thời gian spend + optional comments → Submit

### Unclaim/Undo Submission (mobile)

App → Home/Projects tab → Notifications icon (góc phải trên) → đọc TTL message

**Case 1 – Message:** View message → reply trực tiếp

**Case 2 – Info Request:**
1. Mở message → đọc TTL's message kỹ
2. Back (icon `<`) → TC page → cuộn xuống → bấm **Unsubmit Test Case** → confirm message
3. Sửa TC theo yêu cầu
4. Back → TC page → bấm **Submit Test Case**
5. Nhập thời gian spend + optional comments → Submit
6. Notifications icon → **Send Confirmation** → Confirm all requested info provided

Hoặc mở TC có TTL message → Notifications icon → xử lý tương tự.

---

## 8. Special Requirement Survey (SRS) trên App

### Truy cập SRS

App Home → Requirement Survey Requested section

### Take Survey

1. Bấm **Take Survey** button
2. Trả lời tất cả câu hỏi một cách trung thực
3. Next để chuyển câu tiếp theo
4. Review đáp án
5. Submit Survey

### Decline SRS

Home → Requirement Survey Requested → Bấm **Decline**

⚠️ **Decline SRS = hủy NGAY lập tức**, không hỏi lại confirmation → cẩn thận đừng bấm nhầm.

---

## 9. Chat trên Mobile App

### Accessing chat

Chat tab → select category (Projects, Active Test Cycles, Pending Test Cycles, Locked Test Cycles, Contacts) → tap để mở.

Cycle chat có 2 room mặc định:
| Room | Nội dung |
|------|----------|
| **Announcements** | Tất cả chat announcements gửi bởi TTL/TE |
| **Questions** | Hỏi về cycle, request help, xem tin nhắn từ tester/TTL/TE |

### Sending Message & @Tagging

Tương tự web version, support @tag feature:

Tag | Ai thấy | Ghi chú
----|--------|---------
`@testername` | Tester đó + push notification | Mention cá nhân
`@ttl` | Chỉ các TTL assigned vào cycle + push notification | Mention quản lý
`@all` | TẤT CẢ users trong room + push notification | TTL dùng thông báo chung

### Reply Thread

Trên message → ba chấm bên phải → Reply → Typing → Send. Tap Replies link bên dưới message → mở thread.

### Reactions

Tap ba chấm cạnh message → chọn reaction icon preset.

### Search

Icon search (góc phải trên chat room) → gõ keyword → Search → Left/Right arrows chuyển kết quả.

### Chat @ Mentions Notification

Enable: Profile → Settings → Push notifications → Bật toggle **Chat @ Mentions**

⚠️ Tuân thủ ToU khi giao tiếp trong chat rooms. Xem Academy Communication course.
