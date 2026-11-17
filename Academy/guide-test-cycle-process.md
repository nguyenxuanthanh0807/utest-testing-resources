# 🔄 GUIDE — Test Cycle Process at uTest

> ⭐ Toàn bộ quy trình test cycle: MFA, Invitation, Tabs, Reporting, Communication, Tester Emails
> Cập nhật lần cuối: **11/11/2026** · Style: EN = luật gốc · VN = tóm tắt thực chiến

---

## 1. Vòng đời một test cycle

**EN:** Invitation → Testing & Reporting (2–3 ngày) → Locked → Review → Closed

| Giai đoạn | Diễn giải |
|-----------|-----------|
| **Invitation** | uTest gửi email + push notification đến tester matching requirement. Tester phải đọc kỹ Overview rồi Accept. |
| **Testing & Reporting** | Tester thử nghiệm sản phẩm, submit bug report và hoàn thành test case. Duration: thường 2–3 ngày. |
| **End of cycle** | Khi testing phase kết thúc, cycle bị **Locked**. Không thể submit bug/test case thêm. TTL/team/customer tiếp tục review toàn bộ work. |

---

## 2. 🔒 4 trạng thái của test cycle

| Trạng thái | Tester được làm gì? | Tester KHÔNG được làm gì? |
|------------|---------------------|---------------------------|
| **Pending Activation** | Đọc overview, hiểu hướng dẫn, claim slot (nếu có) | ❌ Không thể test, report bug, execute TC, submit review |
| **Active** | ✅ Test product · Report/edit bugs · Execute TC · Submit reviews · Chat trong room | — |
| **Locked** | ✅ Edit bug/TC nếu status là **Info Requested** · Chat trong room | ❌ Không submit bug/TC mới · Work đã submit đang được review |
| **Closed** | Xem lại chi tiết cycle + work đã submit | ❌ Không thể làm gì trong cycle nữa |

---

## 3. 🔐 Multi-Factor Authentication (MFA)

### 3.1 MFA là gì?

Security process yêu cầu ≥2 verification factors khi đăng nhập: username/password + code OTP từ authenticator app trên điện thoại.

### 3.2 Tại sao bắt buộc?

**EN:** All uTest members are required to have MFA enabled. Without it:
- Invitations sẽ bị **redacted** (ẩn tên cycle, company, product, scope...)
- Bạn sẽ **không accept** được cycle invitation
- Email/app notifications cũng bị redacted
- Không thể participate trong các project cần MFA

> 💡 Bật MFA sớm để không bỏ lỡ cơ hội nhận invite.

### 3.3 Hướng dẫn bật MFA

**Bước 1:** Vào platform → Dropdown (tên tester) → **Account Security** → Đọc info → Bấm **Enable MFA**

**Bước 2:** Cài app Authenticator (Google / Microsoft / FreeOTP) trên mobile

#### 3.3a Google Authenticator (quét QR)

1. Mở app → bấm nút **+**
2. Chọn **Scan a QR Code** → cấp quyền camera → quét QR từ trang MFA Setup
3. App hiển thị mục `Applause: email` → gõ code vào field "One-time code"
4. Điền "Device Name" → Submit

#### 3.3b Google Authenticator (nhập key thủ công)

1. Trên MFA Setup page, bấm link **"My device is unable to scan QR codes"**
2. App → **+** → chọn **Enter a setup key**
3. Account Name: tên bất kỳ · Your Key: copy từ MFA Setup · Type of Key: **Time based**
4. Add → gõ OTP code → Device Name → Submit

#### 3.3c Microsoft Authenticator (quét QR)

1. Mở app → Add account → Personal account → Scan a QR Code → quét QR
2. Nhấn thông báo app lock → tap Applause entry → hiện OTP
3. Gõ OTP code → Device Name → Submit

#### 3.3d Microsoft Authenticator (key thủ công)

1. On MFA Setup page: click **"My device is unable to scan QR codes"**
2. App → **+** → Other account → **OR Enter Code Manually**
3. Account Name → Your Key → Finish → hiện OTP → submit

#### 3.3e FreeOTP

1. Open app → Get Started → Create initial password
2. + button → QR icon → quét QR
3. Gõ OTP code → Device Name → Submit

### 3.4 Sau khi bật MFA — cách đăng nhập

1. Mở uTest website/mobile app
2. Nhập email + password → Sign In
3. Nhập **OTP code** từ Authenticator app (code thay đổi mỗi ~30 giây, nhập nhanh trước khi hết hạn)

### 3.5 MFA Important Notes

- ✅ Chỉ bật được từ **website**, không từ mobile app
- ✅ Sau khi bật MFA → cập nhật **uTest Mobile app** lên bản mới nhất (không cập nhật = không đăng nhập được trên app)
- ✅ Phải bật MFA để thấy nội dung invite/cycle cần MFA
- ⛔ **Một khi bật rồi thì KHÔNG THỂ TẮT** — chỉ Reset MFA
- 🚫 uTest/Applause **không bao giờ** yêu cầu mã OTP của bạn. Nếu ai đó yêu cầu → báo support ngay!

### 3.6 Đổi máy hoặc mất thiết bị MFA

1. **Thử đồng bộ:** Cài cùng Authenticator app trên máy mới → xem có tự import config cũ không
2. **Reset MFA:** Account Security tab → **Reset MFA** button → confirm
3. Xóa config cũ khỏi OTP app (tránh nhầm lẫn)
4. Đăng nhập lại → cài đặt MFA mới trên thiết bị mới
5. Cần uTest ID khi liên hệ Tester Support

> 🆘 Liên hệ hỗ trợ: https://support.utest.com/, category **Login Help**.

---

## 4. Accepting an Invitation

### 4.1 Nhận Invitation

- Email (click link "Review this test cycle")
- Platform → Invited tab / Test Cycle Invites section
- uTest Mobile App (push notification)

### 4.2 NDA (Non-Disclosure Agreement)

Để xem chi tiết cycle → phải chấp nhận NDA trước:

1. Đọc kỹ NDA đính kèm
2. Xác nhận **thông tin tester + địa chỉ mail** đúng (lấy từ profile)
3. Nếu profile thiếu địa chỉ → update profile TRƯỚC khi chấp nhận NDA
4. Bấm **Accept & Proceed** (web) hoặc **Accept NDA** (app)
5. Nếu không muốn tham gia → **Decline invitation** + chọn lý do

💡 Cancel NDA page = giữ invitation pending, vẫn có thể accept/decline sau.

### 4.3 Read Overview BEFORE Accepting

❗ Rất quan trọng: ĐỌC KỸ OVERVIEW trước khi accept. Kiểm tra:
- Có đủ thời gian hoàn thành cycle không?
- Match tất cả requirements không?
- Có hứng thú với project không?

### 4.4 Accept hoặc Decline

| Hành động | Cách thực hiện | Ghi chú |
|-----------|---------------|---------|
| **Accept** | Tick Special Requirements (nếu có) → **Accept Cycle** hoặc **Accept Cycle & Claim a Slot** | Nếu có Slot Waitlist → join nhưng chưa chính thức accepted |
| **Decline** | Bấm **Decline Cycle** → chọn lý do + comment | ✅ **Không có penalty** khi decline sớm |

> ℹ️ "Claim a Slot" = nhận vị trí cụ thể trong cycle. Claim slot Test Case → phải hoàn thành đúng hạn; Join Waitlist = chờ slot trống.

---

## 5. Các tab của Test Cycle

Sau khi accept cycle, mở tab **Slots** → có đầy đủ tabs:

| Tab | Nội dung | Lưu ý |
|-----|----------|-------|
| **Overview** | Description · In Scope · Out Of Scope · Setup Instructions · Issue Reporting Instructions · Test Case Instructions · Special Instructions · Attachments · Team Contact Info (TTL/TE/TA + availability) · Payouts · Specified Environment · Special Requirements · Bonus Instructions | 🎯 Đọc kỹ trước khi test. Some sections ẩn tùy cycle type. |
| **Slots** | Available · Claimed · Unclaimed slots | Đọc description + Preview trước khi claim |
| **Announcements** | Tin nhắn từ TTL/TE/TSM | ⚠️ Một số announcement **phải Acknowledge** mới làm tiếp được |
| **Builds** | Version info + changelog | — |
| **Issues** | Danh sách bug đã report trong cycle | Known issue = bookmark **xanh**. Search/sort/filter |
| **Test Cases** | Available + claimed test cases | Preview/claim/exec/submit |
| **Reviews** | Form viết review về sản phẩm | Có hoặc không tùy cycle |
| **My Earnings** | Số tiền kiếm được trong cycle | — |
| **Tester Scorecard** | Bảng xếp hạng theo điểm tổng | Sắp xếp theo total points |
| **Cycle Feedback** | Survey 5 câu + comment open | Gửi feedback cho TSM |

---

## 6. Reporting

Có **4 loại**: Bug Reports · Test Cases · Reviews · Usability Studies

### 6.1 Submit Bug Report

1. Reproduce bug → xác nhận **valid** (có reproduce + in scope)
2. Verify bug là **unique** (check Issues tab)
3. Xem hướng dẫn report (từ Overview)
4. Chuẩn bị attachment (screenshots, logs, Charles log...)
5. Bấm nút xanh **Report Issue** (ở header của cycle, KHÔNG phải trong test case)
6. Điền form review → submit

### 6.2 Submit Test Case

1. Làm đúng từng bước → upload attachment theo yêu cầu
2. Mark step: **Pass** (không lỗi) / **Fail** (có lỗi)
3. Nếu Fail:
   - Bug đã report → ghi issue ID + click **Fail Step**
   - Bug chưa report → click **Fail & Report Issue** → điền form → submit bug
4. Upload attachments → kiểm tra
5. Click **Submit Results** → nhập thời gian spend → click **Finish**
6. 👀 Đọc message từ TTL, phản hồi nhanh

### 6.3 Submit Review

- Mở **Review tab** → trả lời các câu hỏi → đảm bảo trả lời bằng câu hoàn chỉnh
- ⚠️ **Phải bấm Submit** trong platform → không bấm = mất câu trả lời

### 6.4 Submit Usability Study

- Đọc yêu cầu (trong Overview/Slots/Slot Description)
- Trả lời survey questions đầy đủ
- Narrate video đầy đủ
- Click **Study Complete** → upload screenshots/videos

---

## 7. 💬 Communication Channels

Có **4 kênh** giao tiếp trong/uTest:

### 7.1 Test Cycle Chat

- Access: https://chat.utest.com/ hoặc biểu tượng chat trên thanh Top Navigation
- **NÊN làm:** Hỏi scope/steps/blocker · Giữ thái độ chuyên nghiệp · Kiểm tra tin nhắn cũ trước khi hỏi · Dùng tiếng Anh
- **KHÔNG làm:** ❌ Hỏi payout · ❌ Xin TTL/customer approve/reject bug · ❌ Dispute rejected issues · ❌ Thảo luận bug đã reject · ❌ Tất cả chữ hoa (ALL CAPS)

#### @Tagging trong Chat

| Tag | Ai thấy? | Ghi chú |
|-----|----------|---------|
| `@testername` | Tester đó nhận notification | Mention cá nhân |
| `@ttl` | Chỉ TTLs assigned vào cycle | Mention nhóm quản lý |
| `@all` | ALL users trong cycle (đã join) | TTL dùng để thông báo chung |

#### Search trong Chat

Click search textbox bên cạnh tên cycle → gõ keyword → Enter → highlight orange = exact match. Partial match = bold text.

#### Threaded Messages (Reply thread)

Click icon ba chấm → Reply → reply xuất hiện bên phải màn hình → click Reply/Replies link để mở thread.

#### Chat Reactions

Trên tin nhắn → ba chấm → chọn reaction preset: 👍👎✔✖👀+1. Blue bubble = chính mình, gray = người khác. React lại tăng counter. Giúp tránh spam tin nhắn lặp.

#### Private Message (PM) với TTL

Chỉ PM cho TTL khi nói chuyện matter sensitive (report misbehavior...). Trước đó phải xin phép trong Questions room (@TTL), nếu TTL OK họ sẽ request add contact → mở Contacts → tick checkmark green → đợi TTL initiate conversation.

### 7.2 Project Chat Channel

Dành cho trao đổi giữa các cycle hoặc coordination trước khi test launch. Có trong Projects section bên trái navigation của chat.

### 7.3 Messages Tab

Trong issue report / test case / review — TTL, TE, TSM, customer có thể send message.

⚠️ Communicate professionally. ❌ Không dùng Messages tab để dispute/reject — dùng nút **Dispute** riêng.

### 7.4 Email

Dùng email **CHỈ KHI**:
- Urgent: không vào được chat, lỗi khi claim slot
- Sensitive: report tester misconduct, payout issues
- Câu hỏi trong chat không được trả lời > 24h
- TLQ ở Team Contact Info yêu cầu escalate qua email

**Escalation path:** CE trước → TSM

**KHÔNG EMAIL khi:** Bug bị reject → dùng **Dispute** · Câu scope/instructions → dùng **Chat** · Câu chung uTest → xem **Academy course**

#### Email template

- Subject: `[Cycle ID] Short description of problem`
- Body: Brief, precise, include all relevant info
- Keep communication professional

### 7.5 Best Practices for Communication

- Đọc hết instructions → hỏi trong chat nếu không rõ
- Tuân thủ ToU & Guidelines
- Don't make noise — check threads trước khi hỏi (tránh hỏi lặp)
- Không hỏi payout trong chat/messages tab → chuyển tới PM
- Luôn tôn trọng và lịch sự

---

## 8. Tester Emails

Email mới từ uTest format: `tester-emails@utest.com`, banner "**DIRECT MESSAGE FROM TESTING SERVICES TEAM**".

**Reply options:**
- **Reply Directly:** Reply button trong email (giữ thread cũ — recommended)
- **Contact via Email:** Soạn mới + copy email TE/TSM/CM từ signature hoặc Reply-to field

Nếu không muốn nhận emails này: Advanced Settings → Off option dưới Email Preferences.

---

## 9. End of the Test Cycle

### 9.1 Test Cycle Lock

Khi hết time limit → cycle **Locked**:
- ✅ Tester được edit bug/test case đã submit (chỉ khi status Info Requested)
- ✅ Tester được chat trong cycle
- ❌ Không submit bug/test case mới
- ⏱️ Submission được review trong **15 ngày** sau khi Locked
- Quá 15 ngày chưa được review → liên hệ staff theo Team Contact Info

### 9.2 Test Cycle Close

Sau khi review xong + gửi kết quả cho khách hàng → cycle **Closed**. Tester chỉ có thể xem lại chi tiết.

---

## 10. Importance of Reading — Đọc kỹ hướng dẫn

Đọc và hiểu yêu cầu giúp tester nắm mục tiêu cycle, tìm bug có giá trị, viết report đúng chuẩn và thực hiện test case chính xác. Hãy đọc kỹ trước khi nhận việc, rồi xem lại hướng dẫn liên quan ngay trước mỗi nhiệm vụ.

### 10.1 Trước khi vào cycle

- **SRS:** Đọc kỹ từng câu hỏi và trả lời trung thực, chính xác; không đoán hoặc khai thông tin sai. Nếu được yêu cầu cập nhật profile, hãy cập nhật đúng thông tin.
- **Projects Board:** Đọc yêu cầu và chi tiết dự án trước khi apply. Chỉ apply nếu đáp ứng yêu cầu; điền biểu mẫu đầy đủ, chính xác và kiểm tra lại trước khi gửi.
- **Cycle invitation:** Đọc Overview và xác nhận bạn đáp ứng yêu cầu, có đủ thời gian và hiểu điều cần làm trước khi accept.

### 10.2 Trước từng nhiệm vụ trong cycle

| Thời điểm | Cần đọc |
|-----------|---------|
| Trước khi claim slot | Slotting Instructions và mô tả slot cụ thể; mở rộng mô tả trước khi claim để nắm điều kiện, quy tắc và deadline |
| Trước khi bắt đầu test, report bug hoặc execute test case | **Setup Instructions** về môi trường, cách truy cập test environment và cài ứng dụng |
| Trước khi report bug | **In Scope**, **Out of Scope**, **Known Issues** và **Issue Reporting Instructions** |
| Trước khi execute test case | **Test Case Instructions** và yêu cầu riêng của từng bước |
| Trước khi trả lời UX survey | Đọc toàn bộ hướng dẫn survey, kể cả thời điểm bắt đầu quay video và thứ tự cần làm trước khi trả lời |

Issue Reporting Instructions có thể quy định format title, attachment bắt buộc, thông tin environment bổ sung và custom fields. Luôn đối chiếu form với yêu cầu của cycle.

### 10.3 Trong suốt cycle

- Đọc ngay **Cycle Announcements**; làm theo yêu cầu và acknowledge khi được yêu cầu.
- Theo dõi **Info Requests** và tin nhắn trong report/test case. Trả lời hoặc sửa work theo yêu cầu, sau đó bấm **Confirm all requested info is added** để báo rằng nội dung đã sẵn sàng review.
- Đọc cả **Team Contact Information**, **Special Instructions**, **Tester Special Requirement**, **Bonus Instructions**, review questions (nếu có) và email từ TE/uTest.
- Nếu hướng dẫn chưa rõ, tìm câu trả lời đã có trong cycle chat trước; nếu vẫn chưa rõ, hỏi TTL trong chat room.

### 10.4 Thói quen nên có và điều cần tránh

- Đọc đầy đủ, chú ý chi tiết và xem lại hướng dẫn trước khi bắt đầu từng việc.
- Kiểm tra lại work và attachment để bảo đảm đúng yêu cầu, đúng environment và đầy đủ.
- Không đọc lướt, bỏ qua chi tiết, claim slot khi chưa hiểu yêu cầu hoặc nhận slot mà không có tiến độ.
- Không dùng thông tin sai khi apply, trả lời SRS hoặc execute test case.
- Không bỏ qua announcements, Info Requests hay tin nhắn; các lỗi do không làm theo hướng dẫn có thể khiến work bị reject.
