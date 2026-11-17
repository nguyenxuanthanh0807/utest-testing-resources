---
name: utest-bug-reporting
description: Help with uTest bug reporting for mobile testing cycles. Includes title format, form fields, attachments, and pre-submit checklist.
---

# Skill: uTest Bug Reporting Checklist

**Kích hoạt:** Mỗi khi người dùng log bug trong test cycle của uTest (form "Report Issue" trên uTest.com).

---

## 1. Title — BẮT BUỘC đúng format VÀ ≤ 50 KÝ TỰ

**Format:** `Device Name - Area - Issue Description`

**Giới hạn cứng:** 50 ký tự. ĐẾM KÝ TỰ trước khi paste vào form.

### Công thức phân bổ ký tự

```
len(Issue) ≤ 44 − len(Device) − len(Area)
```

| Area | Prefix (Device + Area + " - ") | Còn cho Issue |
|------|-------------------------------|---------------|
| PDP (3) | 18 | 32 |
| Shop (4) | 19 | 31 |
| Cart (4) | 19 | 31 |
| Search (6) | 21 | 29 |
| Coupons (7) | 22 | 28 |
| Checkout (8) | 23 | 27 |

**Lưu ý:** Nếu device name dài hơn (ví dụ `Samsung Galaxy S23` = 18 ký tự), Issue bị trừ thêm 9 ký tự nữa.

### Thứ tự rút gọn (khi quá 50 ký tự)

1. **Dùng Area ngắn nhất vẫn đúng**: `Shop` / `Cart` / `PDP` / `Coupons` / `Login` / `Search`
   - Tránh: `Navigation Flow`, `Registration Flow`, `Product Details Page`
2. **Bỏ mạo từ** "The / a / an" và tính từ thừa
3. **Giữ: DANH TỪ CHÍNH + KHUYẾT ĐIỂM**
   - Ví dụ: `Back button` + `stays, not working`
4. **Chi tiết đầy đủ ĐỔ VÀO BODY** — title chỉ cần nhận diện được bug
5. **KHÔNG** viết tắt khó hiểu: `BB stays on Shop pg`, `PDP→Shop btn stuck`

### Ví dụ đạt (≤50 ký tự)

```
✓ iPhone 15 - Shop - Back button stays, not working                 (49)
✓ iPhone 15 - Coupons - Categories do not respond                   (47)
✓ iPhone 15 - Cart - Total not updated after quantity change        (49)
✓ iPhone 15 - PDP - Price differs from search results               (48)
✓ iPhone 15 - Search - Infinite loading after searching "sneakers"  (50)
```

### Ví dụ sai

```
✗ iPhone 15 - Navigation - The back button remains on the Shop page after
  returning from the product details page                            (108, quá dài)

✗ Back button stays on Shop page                                     (thiếu Device + Area)

✗ iPhone 15 - Shop - The back button remains displayed in the header
  next to the menu icon after returning from PDP                     (quá dài)
```

---

## 2. Điền ĐẦY ĐỦ các ô form

| Ô | Cách chọn |
|---|---|
| **Issue Title** | Đúng format + ≤ 50 ký tự (mục 1) |
| **Type** | `Crash` (đơ/tự đóng) · `Functional` (nút/tính năng không hoạt động) · `Performance` (chậm, loading vô hạn) · `Visual` (sai hình/layout/chữ bị cắt) · `Content` (sai chính tả/nội dung/giá niêm yết) |
| **Frequency** | `Every Time` (3/3) · `Occasionally` (2/3 hoặc trung gian) · `Hardly Ever` · `Once` — **KHÔNG** khai `Every Time` khi chưa repro 3/3 |
| **Priority** | `Critical` (crash / chặn mua hàng / mất dữ liệu) · `High` (toàn bộ tính năng chết) · `Medium` (hỏng một phần, có workaround) · `Low` (thẩm mỹ) |
| **Source** | `Structured` (tìm ra khi chạy test case có kịch bản) · `Exploratory` (tìm ra khi tự do khám phá trong scope) |
| **My Environments** | Chỉ chọn đúng environment được phân công. **Không** thêm thiết bị khác. |

### Cách chọn Type

| Mức | Khi nào |
|-----|---------|
| **Crash** | App tự đóng / đơ cứng / không phản hồi |
| **Functional** | Nút/tính năng **không làm được việc nó phải làm** ← phổ biến nhất |
| **Performance** | Chậm, loading vô hạn, treo |
| **Visual** | Sai hình ảnh, layout lệch, chữ bị cắt, màu sai |
| **Content** | Sai chính tả, sai nội dung văn bản, sai giá niêm yết |

### Cách chọn Priority

| Mức | Khi nào |
|-----|---------|
| **Critical** | App crash/đơ, **chặn không cho mua hàng**, mất dữ liệu người dùng |
| **High** | **Toàn bộ tính năng** không dùng được (ví dụ: toàn bộ danh sách category chết) |
| **Medium** | Tính năng hỏng một phần, **có cách đi vòng** (workaround) |
| **Low** | Chỉ sai thẩm mỹ, không ảnh hưởng thao tác |

### Cách chọn Source

| Giá trị | Áp dụng khi |
|---------|-------------|
| **Structured** | Bạn tìm ra bug **trong khi đang thực thi test case** (có các bước được định nghĩa sẵn, tick pass/fail) |
| **Exploratory** | Bạn tìm ra **trong lúc tự do bấm khám phá** quanh các focus area, ngoài kịch bản test case |

---

## 3. Body — theo cấu trúc chuẩn

```
Environment: [Device] - [OS] - [App name] (native app) - [Network]
App version: [ĐIỀN VERSION]

Steps to Reproduce:
1. [Bước 1]
2. [Bước 2]
3. [Bước 3 - chi tiết, tên nút chính xác như trên màn hình]

Expected Result:
[Mô tả hành vi đúng - 1-2 câu]

Actual Result:
[Mô tả lỗi - 2-4 câu, factual, không suy đoán]

Reproducibility: Reproduced X/X attempts.

Attachments:
- Screenshot (.png) - defect highlighted with a red rectangle
- Screen recording (.mp4) - full repro, no background noise
- [Device] device log (.txt/.log)
```

### Lưu ý khi viết Body

- **Steps to Reproduce:** dùng tên nút chính xác như trên màn hình (ví dụ: `"CATEGORIES"` thay vì "button categories")
- **Expected Result:** mô tả hành vi **đúng** — không mô tả "nên có" mà mô tả "phải có"
- **Actual Result:** mô tả **sự thật** — không suy đoán nguyên nhân, không đề xuất fix
- **Reproducibility:** phải khớp với Frequency đã chọn (Every Time = 3/3)

---

## 4. Attachments — theo yêu cầu của từng cycle

### Bắt buộc (3 file)

| File | Định dạng | Yêu cầu đặc biệt |
|------|-----------|------------------|
| **Screenshot** | `.jpg` / `.png` | Khung đỏ quanh defect (highlight) |
| **Screen recording** | `.mp4` | **Mic TẮT** (không tạp âm), Do Not Disturb BẬT |
| **Device log** | `.txt` / `.log` | PII đã blur |

### PII cần blur ở CẢ 3 file

- Email
- Tên (first name, last name, full name)
- Số điện thoại
- Địa chỉ
- Ảnh đại diện / ảnh cá nhân
- Tên thiết bị (ví dụ: "Nguyen's iPhone")
- WiFi SSID (nếu có trong log)

### Không blur

- Tên app
- Tên sản phẩm
- Giá sản phẩm
- URL (nếu không chứa thông tin cá nhân)

### Công cụ thu thập log iOS trên Windows

| Công cụ | Ưu điểm | Nhược điểm |
|---------|---------|------------|
| **3uTools** (Realtime Log) | Miễn phí, phổ biến, xuất `.txt` | Có thể treo với log dày |
| **iMazing** (Console) | Giao diện đẹp, được dạy trong course | Trả phí, có thể treo |
| **idevicesyslog** (libimobiledevice) | Dòng lệnh, không giao diện, không thể treo | Cần cài libimobiledevice |

**Lưu ý quan trọng:**
- **KHÔNG** dùng simulator — cycle yêu cầu thiết bị thật
- **KHÔNG** dùng app Android (CatLog, aLogcat) — đó là cho Android
- **KHÔNG** cài app thứ 3 lên iPhone để lấy log
- **HỎI TTL** trước nếu không chắc công cụ được chấp nhận

---

## 5. Pre-submit gate — kiểm tra trước khi bấm Report Issue

### Checklist bắt buộc

- [ ] **Title** đúng format `Device - Area - Issue` VÀ ≤ 50 ký tự
- [ ] Đã **đếm ký tự** của title
- [ ] **Type** đã chọn đúng (Crash / Functional / Performance / Visual / Content)
- [ ] **Frequency** khớp với tỉ lệ repro thật (Every Time = 3/3)
- [ ] **Priority** phù hợp mức độ nghiêm trọng
- [ ] **Source** đúng (Structured khi chạy test case, Exploratory khi tự khám phá)
- [ ] **My Environments** chỉ chọn đúng environment được phân công
- [ ] **Đủ 3 file** đính kèm đúng định dạng
- [ ] **PII đã blur** ở cả 3 file (email, tên, SĐT, địa chỉ, ảnh)
- [ ] **Không lộ** từ "tester"/"test"/"qa" trong app, tên file, hay nội dung report
- [ ] **Reproduce được** trên 2 lần (cycle yêu cầu > 2 lần)
- [ ] **Không phải** field validation / accessibility / usability / security
- [ ] **Chưa vượt quá** số report cho phép trong cycle (thường 3-5 reports)

### Kiểm tra trùng lặp

Nếu có nhiều bug cùng loại (ví dụ: 2 bug "control không phản hồi"), chuẩn bị câu giải thích:

> These are two separate defects on two different screens. Bug #1 is [mô tả bug 1]. Bug #2 is [mô tả bug 2]. Different area, different behaviour, different repro steps.

---

## 6. Quy tắc liêm chính (LIÊM CHÍNH > 1 BUG)

### KHÔNG BAO GIỜ

- Khai sai công cụ thu thập log (ví dụ: ghi iMazing nhưng thực tế dùng 3uTools)
- Dùng AI tạo/điều chỉnh nội dung log hoặc video
- Đổ lỗi cho mạng khi bug tái hiện ổn định
- Khai Frequency "Every Time" khi chưa repro 3/3
- Thêm thiết bị khác vào My Environments

### NÊN LÀM

- Khai đúng sự thật ngay từ đầu
- Chủ động hỏi TTL nếu không chắc
- Nếu TTL yêu cầu làm lại → **làm lại thật**, không đổi tên file
- Giữ log/video/screenshot nguyên bản, không chỉnh sửa

---

## 7. Ví dụ thực tế từ cycle Shoe Carnival Mobile Testing

### Bug #1: Nút back chết trên trang Shop

```
Title: iPhone 15 - Shop - Back button stays, not working (49 ký tự)

Body:
Environment: Apple iPhone 15 - iOS 26.5 - Shoe Carnival (native app) - MobiFone
App version: [ĐIỀN]

Steps to Reproduce:
1. Launch the Shoe Carnival app. The app opens on the "Home" tab.
2. Tap the "Shop" tab in the bottom navigation bar.
3. Tap on the product "Women's Nike Air Max Exece Sneakers".
4. On the product details page, tap the back button ("<") in the top-left corner.
5. Observe that the app returns to the Shop page and the back button is still
   displayed in the header.
6. Tap the back button again.

Expected Result:
The Shop page is the top level of the Shop section, so there is no previous
screen to navigate back to. The header should show only the menu (hamburger)
icon on this page, and the back button should disappear immediately.

Actual Result:
After returning to the Shop page, the back button remains displayed in the
top-left corner of the header. Tapping it does not navigate to any screen and
the page content stays unchanged - the button simply disappears from the header.
The user has to tap the dead button once to clear the incorrect state.

Reproducibility: Reproduced 3/3 attempts.

Type: Functional
Frequency: Every Time
Priority: Medium (có workaround: dùng tab bar để điều hướng)
Source: Exploratory
```

### Bug #2: Danh sách Categories trong Coupons không phản hồi

```
Title: iPhone 15 - Coupons - Categories do not respond (47 ký tự)

Body:
Environment: Apple iPhone 15 - iOS 26.5 - Shoe Carnival (native app) - MobiFone
App version: [ĐIỀN]

Steps to Reproduce:
1. Launch the Shoe Carnival app.
2. Tap the "Coupons" tab in the bottom navigation bar.
3. Tap the "CATEGORIES" button.
4. In the Categories list, tap "Mens Shoes (15)".
5. Tap other items in the list as well, for example "All (32)", "Nike Hot Deals
   (7)" or "Boots (7)".

Expected Result:
Tapping a category should select it and filter the coupon list on the Coupons
page to show the coupons belonging to that category. The number displayed next
to each category name indicates how many coupons it contains - for example
"Mens Shoes (15)" should display 15 coupons, and "All (32)" should display 32
coupons in total.

Actual Result:
Nothing happens when any category item is tapped. The tapped item shows a
highlighted/pressed state, but no category is selected, the Categories panel
does not close, and no coupons are displayed - the screen stays unchanged.
Every item in the list is unresponsive, even though each of them shows a
non-zero coupon count. The only control in the panel that works is the close
(X) button in the top-right corner.

Reproducibility: Reproduced 3/3 attempts, including after fully closing and
relaunching the app.

Type: Functional
Frequency: Every Time
Priority: High (toàn bộ tính năng Categories chết)
Source: Exploratory
```

---

## 8. Lưu ý về cycle uTest Academy

### Payouts

- Cycle Academy **không có payout** (base payout = VND 0.00)
- Mục tiêu: **1 approved bug report + 1 approved test case** để pass cycle
- Pass grade được gán 12-24 giờ sau khi hoàn thành yêu cầu

### Quy tắc chung

- **Không** hoàn thành đơn hàng / không mua hàng (no reimbursement)
- **Không** thêm thẻ thanh toán / payment method
- **Không** dùng third-party apps (Google Translate, v.v.)
- **Không** thay đổi country trên App Store / Google Play
- **Không** báo Accessibility / Usability / Security issues
- **Không** báo issues không reproducible được trên 2 lần
- **Tối đa 3-5 reports** (tùy cycle) — chất lượng > số lượng

### Thời gian phản hồi TTL

- **48 giờ** để trả lời TTL — sau đó issues bị reject
- Nếu không trả lời sau 2 reminders từ TTL → reject ngay

---

**Tạo bởi:** OpenCode Agent  
**Ngày cập nhật:** 2026-11-17  
**Phiên bản:** 1.0