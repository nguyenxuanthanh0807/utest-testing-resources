# 01 — Introduction to Testing (Cycle #563984)

> Sản phẩm: **Under Armour Việt Nam** — `underarmour.com.vn`
> Nhận invitation: 02/11/2026 · **Deadline: 06/11/2026 09:00**
> Testing Type: Functional + Exploratory with test cases · Payout: KHÔNG (training only)

---

## 🎯 Điều kiện PASS

- ✅ Tối thiểu **1 bug report Approved**
- ✅ Tối thiểu **1 test case Approved**
- Thiếu 1 trong 2 = Fail. Pass grade nhận sau **12–24h** kể từ khi đủ cả 2 được approve (hoặc khi cycle đóng)

## 💻 Environment trong scope (khai báo trong invitation)

- Windows 11 Home — Chrome / Firefox / Edge
- Apple iPhone 15, iOS 26.5 — Chrome / Edge / Firefox / Safari (MobiFone)
- ❌ Internet Explorer, emulator/simulator — cấm

## 🌐 Quy tắc local site

- **Local sites are in scope** → chỉ test bản phù hợp location của mình
- Việt Nam có sẵn → **chỉ test `underarmour.com.vn`** (đã chọn VN)
- Không test các bản quốc gia khác; không dùng Google Translate khi test
- Lưu ý: một số tính năng có thể không có ở bản local — chỉ test cái CÓ trên bản local

## ✅ IN SCOPE — Focus Areas

### 1. Account Creation & Onboarding
- Tạo account bằng email *(bản VN: thực tế là SĐT + The 1 — xem mục "Hệ thống tài khoản bản VN")*
- Profile: cập nhật thông tin, settings, địa chỉ, dashboard
- Login/Logout: thành công mỗi lần
- Forgot Password: flow khôi phục đáng tin cậy

### 2. Navigation & UI + Search
- Toàn bộ menu chính + submenu — mọi link hoạt động
- Search với nhiều loại query — hoạt động đúng kỳ vọng

### 3. Category pages (PLP)
- Duyệt hết categories — mọi link/button hoạt động
- **Toàn bộ filter + sort** ⭐
- Add to bag / Save to list từ PLP

### 4. Product details pages (PDP)
- Ảnh đúng sản phẩm; details + specs & care rõ ràng
- Size guide chính xác; chọn size/màu dễ dàng
- Add to bag; save to list; xóa khỏi saved items; share; reviews

### 5. Bag & Checkout flow ⭐ (customer quan tâm nhất)
- Thêm số lượng đơn/đôi — **tăng/giảm số lượng → giá tính đúng**
- Edit sản phẩm; Save for later
- Promo code hợp lệ giảm đúng vào subtotal/total
- Checkout đi đến bước cuối — **KHÔNG hoàn tất đặt hàng** (không hoàn tiền)

### 6. Hành vi bất thường
- Bug làm freeze website
- Bug chỉ xảy ra trên browser/device nhất định
- Bug chặn user hoàn thành mua hàng

## ❌ OUT OF SCOPE

- **Khu vực:** Feedback, Help Center (Live Chat, Call Us), partner/external sites
- **Hành động:** đặt hàng thật, thêm thẻ tín dụng/payment method, Google Translate
- **Không report:** Accessibility / Usability / **Security** issues; lỗi không reproduce được ≥ 2 lần; lỗi không nằm trên testing website; lỗi không visible với user thường (gồm console logs)
- **Minor (bỏ qua):** landscape mobile, desktop view trên mobile browser

## 📋 Issue Reporting Instructions (riêng cycle này)

- **Title format:** PC: `Operating System - Area - Issue Description` · Mobile: `Device Name - Area - Issue Description`
  - VD: `Windows 10 - PLP - Sorting products by price, High to Low, gives incorrect results`
  - VD: `iPhone 14 Pro Max - Search Results Page - Searching for 'Trousers' gives incorrect results`
- **Attachment bắt buộc: 1 highlighted screenshot** (.jpg/.png, khung đỏ quanh bug) — blur PII
- Chỉ submit **1 issue** (không submit issue thứ 2)
- Trả lời Info Request: quá **48h / 2 lần nhắc TTL → reject ngay lập tức**
- Setup: clear cache/cookies + tắt ad-blocker trước khi test
- Không dùng chữ "tester"/"test" làm tên trên site — hành xử như user thật

## 🧪 Test case (slot: Computer - Any browser) — 7 steps

| Step | Nội dung | Attachment |
|------|----------|-----------|
| 1 | Đọc Terms of Use + AI Guidelines → Done | ❌ |
| 2 | Hoàn thiện Tester Profile (Personal/Devices/Payment/Subscriptions) → Save từng tab | ❌ |
| 3 | Location & Language — địa chỉ THẬT → Save → Done | ❌ |
| 4 | Screenshot Tester ID → upload | ✅ Min 1 |
| 5 | Screenshot OS (`Win+R` → `winver`) → upload | ✅ Min 1 |
| 6 | Học "How to Write Bug Reports" → Done | ❌ |
| 7 | Test web → tìm bug → Report Issue → Done → **Submit Results → Finish** | ❌ |

⚠️ Chỉ được Done Step 7 SAU KHI đã submit issue. Sau đó mới Submit Results (điền spent time) → Finish.

## 🔐 Hệ thống tài khoản bản VN (phát hiện 02/11/2026)

- UA VN thuộc **Central Retail**; tài khoản = thẻ thành viên **The 1** dùng chung hệ thống
- **KHÔNG đăng ký bằng email** — flow: icon 👤 → modal Log In/Sign Up → nhập **số điện thoại** → validation → chọn kênh OTP (**SMS hoặc Zalo**) → nhập OTP (hạn 3 phút, sai có đếm số lượt còn lại: "Invalid OTP. You have 2 attempts remaining") → **Create PIN** (6 số, tick 2 checkbox T&C: Under Armour Viet Nam and The 1 + Data Protection Policy)
- SMS OTP template ghi "dang ky tai khoan tai sieu thi GO!" (template dùng chung Central Retail)
- Note trong modal: web UA **không hỗ trợ đổi điểm** (redeem chỉ tại cửa hàng) = WAD, không report
- Điểm: 10,000 VND = 50 points/order; 1 point = 1 VND

## ❓ FAQ quan trọng (từ invitation)

- **Không nhận invitation sau Sign Up?** — Đã pass cycle này trước đó thì không join lại; còn lại → ticket tại https://support.utest.com/csp (category: Academy)
- **Không tìm ra bug?** — Test sâu như user thật, đừng vội nản; hết cơ hội thì sign up lại cycle
- **Lo duplicate?** — Issues của tester khác bị ẩn → cứ report bug valid
- **Bị Info Requested lâu không check?** — Mở report xem status: phải sửa lỗi + **bấm "Confirm all request is added"** để status về New; nếu đã New thì chờ (delay do lượng submit lớn)
- **Thêm video được không?** — Được, nhưng vẫn phải có screenshot có label (bắt buộc)
- **Area trong title ghi gì?** — Tên TRANG nơi lỗi xảy ra, không phải tên chức năng. VD đúng: `Windows 10 - Homepage - Store Locator link directs to a not found error page`; sai: `Windows 10 - Store Locator - ...`
- **Test case + issue approved rồi?** — Đợi Pass grade 12–24h → review course Computer Testing → pass quiz → sign up cycle 2
- Khác: hỏi trong **cycle chat** (Academy team theo dõi)
