# 📔 Nhật ký test — Cycle #563984 (Introduction to Testing)

> File cập nhật HÀNG NGÀY. Deadline: **06/11/2026 09:00**

---

## ✅ Audit test case slot "Computer - Any browser" — 09/11/2026

| Step | Yêu cầu | Trạng thái | Việc còn thiếu |
|------|---------|-----------|----------------|
| 1 | Đọc Terms of Use + AI Guidelines | ✅ Done (02/11) | — |
| 2 | Tester Profile: Personal / Devices / Payment / Subscriptions → Save từng tab | ❓ Không có ghi nhận | Làm xong, ghi giờ Done |
| 3 | Location & Language — địa chỉ THẬT → Save | ❓ Không có ghi nhận | Làm xong, ghi giờ Done |
| 4 | Screenshot Tester ID → upload (≥1) | ❓ Không có ghi nhận | PNG/JPG → upload → mở lại kiểm tra file |
| 5 | Screenshot OS (`Win+R` → `winver`) → upload (≥1) | ❓ Không có ghi nhận | Full màn hình có hộp winver |
| 6 | Học "How to Write Bug Reports" → Done | ❓ Không có ghi nhận | Học xong bấm Done |
| 7 | Test → Report Issue → Done → Submit Results (spent time) → Finish | ⛔ Đang chặn | Chỉ Done SAU KHI issue đã submit |

**Kết luận:** mới có bằng chứng cho **1/7 bước**. Bấm Submit Results lúc này = placeholder → vi phạm ToS.

> ⚠️ Deadline **06/11/2026 09:00** đã qua (hôm nay 09/11). Mở uTest kiểm tra status cycle TRƯỚC khi làm tiếp: nếu cycle đã đóng mà chưa đủ 1 issue approved + 1 test case approved thì = Fail → phải sign up lại đúng cycle 1 (không được nhảy sang Computer Testing).

---

## 📅 02/11/2026 (Thứ 2)

### Việc đã làm
- ✅ Nhận invitation email → đọc kỹ overview/scope
- ✅ Accept cycle (tick 3 checkbox: Special Requirements + Test Cycle Agreement + Commit)
- ✅ Claim slot **"Computer - Any browser"** (397/500 remaining, effort 30 phút)
- ✅ Test case: Step 1 (ToS + AI Guidelines) — Done
- ✅ Kiểm tra máy: không có policy hijack / shortcut hijack / extension lạ (chi tiết mục "Chẩn đoán Chrome")
- ✅ Quiz **Issue Reports: 10/10** 🎉
- ✅ Đọc xong các course: Understanding Issue Report, Write/Edit Issue Report, Info Fields, Severity vs Value, Rejections, +1, Issue Quality Review, Known Issues, Best Practices
- ✅ Lựa chọn bản địa: `underarmour.com.vn` (VN local site — in scope)
- ✅ Khám phá flow tài khoản bản VN: The 1 (phone → OTP SMS/Zalo → Create PIN)

### 🐛 Findings log

| # | Finding | Loại | Quyết định |
|---|---------|------|-----------|
| F1 | **OTP hết hạn (quá 3 phút) vẫn được chấp nhận** — không báo lỗi, đi tiếp sang màn Create PIN (SMS công bố "xac thuc trong 3 phut") | Security-leaning / Functional validation | ⏳ **ĐANG REPORT** (anh quyết định bắn viên đạn vào đây — đã được cảnh báo rủi ro OOS/Security). Verify thêm: chờ 6-10' nhập lại ≥ 2 lần → Frequency "Every Time" |
| F2 | SMS OTP template ghi "...dang ky tai khoan tai **sieuthi GO!**..." trong khi đăng ký trên web Under Armour | Content | ❌ Không report — SMS từ hệ thống The 1/Central Retail (partner platform), template dùng chung khả năng cao WAD/OOS |
| F3 | Web UA **không hỗ trợ đổi điểm** The 1 | Content/WAD | ❌ Không report — có ghi rõ trong modal = documented behavior |

### 📸 Bằng chứng đang chuẩn bị (cho F1)
- [ ] Screenshot SMS nhận OTP: hiện đồng hồ điện thoại, **blur 6 số OTP + SĐT**
- [ ] Screenshot màn Create PIN (từ browser, full màn hình + URL bar, **khung đỏ**)
- [ ] Reproduce lần 2 (chờ 6') + lần 3 (chờ 10') — ghi đúng số phút thật vào steps

### Draft report F1 (bản sửa 09/11/2026 — đã tách bước, sửa Area, bỏ placeholder)

> ⚠️ **RỦI RO OOS:** OTP hết hạn vẫn được chấp nhận dễ bị TTL đọc là lỗi **Security / authentication**, mà overview ghi rõ "Không report: Accessibility / Usability / **Security** issues". Cycle chỉ cho đúng 1 issue → cân nhắc kỹ trước khi bấm Submit. Phương án an toàn hơn: bug functional/visual ở focus area ⭐ (sort/filter PLP, giá khi tăng–giảm số lượng, promo code, size guide).

```
Title: Windows 11 - Sign Up - Expired OTP code is still accepted after the 3-minute validity period
Type: Functional | Frequency: Every Time (chỉ chọn sau khi reproduce ≥2 lần) | Priority: Medium | Source: Exploratory
Environment: Windows 11 Home - Chrome

Precondition: A phone number that has not been registered on the site yet. Browser cache and cookies cleared, ad-blocker disabled.

1. Go to https://underarmour.com.vn/en
2. Click the account icon in the header.
3. Enter the unregistered phone number into the "Enter phone number" field.
4. Click the "CONTINUE" button.
5. Select the "Receive Verification Code Via SMS" option.
6. Receive the 6-digit OTP code via SMS.
7. Wait for <<số phút thật>> minutes after receiving the OTP code without requesting a new one (the SMS states the code is valid for 3 minutes).
8. Enter the OTP code received in step 6 into the OTP field.
9. Click the submit button of the OTP verification step.

Expected Result: The system displays an error message that the OTP code has expired and asks the user to request a new verification code, as the code is only valid for 3 minutes.
Actual Result: The expired OTP code is accepted without any error message and the system proceeds to the "Create PIN" step of the sign up flow.
Error Message: (để trống — màn hình không hiển thị lỗi)
```

**2 ô BẮT BUỘC lấy từ lần test thật trước khi submit** (không được để nguyên khi submit):
- [ ] `<<số phút thật>>` — số phút đã chờ ở lần reproduce 2 (6') và lần 3 (10'); ghi đúng số đo được
- [ ] Nhãn thật của nút submit ở bước 9 (UI đang ghi gì: "VERIFY" / "CONTINUE" / khác)

**Attachment (tối đa 2 ảnh/issue):**
- [ ] Ảnh 1: browser full màn hình **có URL bar**, khung đỏ quanh màn Create PIN
- [ ] Ảnh 2: SMS có đồng hồ điện thoại, **blur 6 số OTP + SĐT**

### 📌 TODO tiếp theo
- [ ] Hoàn tất Create PIN (test: PIN 5 số / 123456 / chứa chữ / 2 field không khớp / submit không tick checkbox / **bấm 2 link T&C** — 404 = bug candidate)
- [ ] Sau tạo PIN: kiểm tra trạng thái logged-in, F5 giữ login, account page, điểm The 1 = 0
- [ ] PLP "Hàng mới" (87 sản phẩm): filter Giới Tính + Danh Mục (12+71+4=87 khớp tổng), sort giá ⭐
- [ ] PDP: size guide, chọn size/màu, add to bag
- [ ] Cart: tăng/giảm số lượng → giá, promo 250K cho hóa đơn từ 1.4tr, checkout đến bước cuối DỪNG
- [ ] Submit issue F1 → Done Step 7 → **Submit Results → Finish**
- [ ] Theo dõi Info Request hằng ngày (quá 48h = reject!)
- [ ] ⭐ Chuyển tài liệu/project sang thư mục `F:\UTest\Academy\` làm trung tâm lưu trữ

---

## 📅 (ngày tiếp theo — điền tại đây)

---

## 📋 Checklist test case 5 bước (bản mới — ToU → Review)

> Phiên bản test case khác với audit 7-step trên. Thực thi từng bước + tick khi làm xong.

### ✅ Bước 1 — Đọc Terms of Use & AI Guidelines

| Hành động | Link | Ghi nhớ | Trạng thái |
|-----------|------|---------|-----------|
| Đọc ToU | https://www.utest.com/terms-of-use | Tuân thủ toàn bộ chính sách → vi phạm = suspending hoặc terminate account | ❏ Done |
| Đọc AI Guidelines | https://www.utest.com/ai-guidelines | Nắm rõ boundary generative AI được dùng/không dùng | ❏ Done |

Không cần upload attachment. Bấm **Done** sau khi hoàn thành.

---

### ✅ Bước 2 — Xem video Writing Bug Reports

| Hành động | Link | Ghi nhớ | Trạng thái |
|-----------|------|---------|-----------|
| Xem video + đọc bug report fields | https://www.utest.com/academy/tracks/17/courses/writing-bug-reports | Nắm format title, Issue Classifications, Actions Performed, Expected/Actual Result | ❏ Done |

Không cần upload attachment. Bấm **Done**.

---

### ✅ Bước 3 — Xem video thu thập Desktop Browser Logs

| Hành động | Link | Ghi nhớ | Trạng thái |
|-----------|------|---------|-----------|
| Basics of Logs | https://www.utest.com/academy/tracks/39/courses/basics-logs | Format `.chls`/`.chlz` (Charles), `.saz` (Fiddler) | ❏ Done |
| Desktop Browser Logs | https://www.utest.com/academy/tracks/39/courses/desktop-browser-logs | Decrypt SSL proxy, cài root cert, reproduce từ homepage | ❏ Done |

Không cần upload attachment. Bấm **Done**.

---

### ✅ Bước 4 — Reporting một Bug thật

| # | Hành động | Hướng dẫn | Trạng thái |
|---|-----------|-----------|-----------|
| 1 | Mở testing website trong Overview | Test với environment in-scope → tìm bug VALID phù hợp hướng dẫn | ❏ |
| 2 | Bấm nút xanh **"Report Issue"** | Ở header của test cycle (KHÔNG phải bên trong test case) | ❏ |
| 3 | Điền đầy đủ các field | Theo đúng hướng dẫn trong Overview + xem `Report_Example.png` đính kèm tại bước này | ❏ |
| 4 | Submit bug report | Recheck tất cả → Submit Issue | ❏ |
| 5 | Bấm **Done** | Sau khi issue đã submit → Done được luôn (ngay cả khi status issue còn "New") | ❏ |

> 💡 Vẫn phải trả lời **Info Request messages** nếu TTL gửi yêu cầu sửa đổi bổ sung.

---

### ✅ Bước 5 — Submitting a Review

⚠️ **TUYỆT ĐỐI KHÔNG DÙNG AI viết review.** Vi phạm = bị ban account!

| # | Hành động | Hướng dẫn | Trạng thái |
|---|-----------|-----------|-----------|
| 1 | Học cách viết review | Course 1: [Impact of AI on uTesters](https://www.utest.com/academy/tracks/46/courses/the-impact-of-AI-on-uTesters)<br>Course 2: [Tester Review](https://www.utest.com/academy/tracks/33/courses/tester-review) | ❏ |
| 2 | Bấm **Write a Review** | Ở góc trên phải của test cycle page | ❏ |
| 3 | Trả lời các câu hỏi | Dựa trên trải nghiệm THẬT khi test sản phẩm + học qua Academy<br>Xem `Review_Example.jpg` đính kèm để tham khảo quality | ❏ |
| 4 | **Phải bấm Submit** trong platform | Nếu không bấm = mất TẤT CẢ câu trả lời | ❏ |
| 5 | Bấm **Done** | Sau khi hoàn thành review | ❏ |
| 6 | **Submit Results** + nhập thời gian spend + bấm **Finish** | ⭐ BẮT BUỘC cuối cùng → không làm = TC không được chấm | ❏ |

**Gợi ý trả lời cho anh/chị (Viết bằng TIẾNG ANH bằng lời mình):**

Q1. First impressions — Course Catalog > *Trang hiển thị rõ ràng, dễ thao tác*  
Q2. Satisfaction with experience > *Đã học được nhiều quy trình log bug chuẩn quốc tế mà thực tế có thể chưa tiếp xúc*  
Q3. UI confusing or difficult to navigate? > *Các nút dễ thấy nhưng nên làm button cho nổi hơn, hạn chế dùng dạng hyperlink*  
Q4. What learned in Academy courses? > *Rất nhiều kiến thức mới, tool mã nguồn mở hỗ trợ rất tốt quá trình test — cần tool nào thì quay lại Academy tìm, rất tiện; nhưng nên có thêm list index để search nhanh hơn*  
Q5. Experience providing browser console log > *Trải nghiệm rất dễ thực hiện, trước giờ tôi chỉ dùng DevTools chụp ảnh rồi xong, nhờ Academy học thêm được nhiều điều*  
Q6. Design/performance/functionality of testing website > *Website được xây dựng rất chặt chẽ, khá khó để tìm bug nghiêm trọng — chỉ có bug về UI; nhìn chung website khá ổn*  
Q7. Overall Rating > **⭐ 4.5 / 5**

---

## 🔧 Phụ lục: Chẩn đoán Chrome 02/11/2026 (tab mới nhảy vào google search "dich")

**Hiện tượng:** Mở tab mới cứ nhảy vào `google.com/search?q=dich&oq=d&...&sourceid=chrome`

**Kết luận: máy SẠCH, không bị hijack.** Bằng chứng:
- Registry `HKLM/HKCU\SOFTWARE\Policies\Google\Chrome` — không tồn tại
- Shortcuts Desktop/Taskbar — target/args bình thường
- Search engine (Secure Preferences) — template Google chuẩn ở mọi profile
- Extensions — chỉ có component extensions của Chrome (Bookmark Manager `ibplnj...`, Google Wallet `nmmhkk...`) + tool testing ở Profile 3, KHÔNG cái nào override newtab
- URL "dich" nằm ở `prefetch.search_prefetch.cache` trong Preferences Profile 3 = **bộ đệm search prefetch bình thường của Chrome** (omnibox gõ "d" → gợi ý "dich" từ lịch sử)

**Kế hoạch khắc phục (nếu còn gặp):** (1) quan sát omnibox khi mở tab mới có tự gõ "d" không; (2) tắt UniKey thử; (3) thử cửa sổ ẩn danh Ctrl+Shift+N; (4) dùng profile Chrome RIÊNG tên "Academy" không cài extension để test.

**⚠️ Quan trọng cho cycle:** Profile "Thanh" (Profile 3) có ~30 extension gồm Google Translate + Ddict → phải tắt/không dùng khi test (cycle cấm công cụ dịch). Khuyến nghị: tạo profile mới sạch dành riêng cho testing.
