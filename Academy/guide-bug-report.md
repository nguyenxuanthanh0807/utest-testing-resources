# 🐛 GUIDE — Viết Bug Report trên uTest

> ⭐ File tra cứu MỖI KHI viết bug report (mọi cycle). EN = luật gốc · VN = ghi chú thực chiến
> Nguồn: uTest Academy courses "Understanding Issue Report", "How to Write/Edit an Issue Report", "Issue report information fields", "Severity vs Value", "Bug Rejections", "Confirm Issue", "Issue Quality Review", "Known Issues", "Best Practices" + Quiz Issue Reports (10/10 — 02/11/2026)

---

## 1. Quy trình submit issue (6 bước)

1. Tìm bug trên sản phẩm đang test → xác nhận **valid** (reproduce được, in scope)
2. Bấm nút xanh **Report Issue** ở header của test cycle (KHÔNG phải trong test case)
3. Điền đầy đủ các field (xem mục 2)
4. Attach đầy đủ attachment yêu cầu
5. Recheck tất cả field + attachment
6. **Submit Issue** → sau đó **mở lại từng attachment kiểm tra mở được, không hỏng**

**VN:** Cycle Academy Introduction to Testing chỉ được report ĐÚNG 1 issue → chuẩn bị đủ attachment rồi mới bấm Submit (placeholder = vi phạm ToS).

## 2. Các field và luật từng field

### 2.1 Issue Title
- Theo ĐÚNG format trong overview của từng cycle (VD Academy PC: `Operating System - Area - Issue Description`)
- Area = **tên trang/nơi lỗi xảy ra**: Homepage, Cart, Checkout, PLP, Search Results Page...
- Mô tả lỗi chính xác, rõ ràng
- ❌ Không viết IN HOA toàn bộ (ALL CAPS)
- ❌ KHÔNG ghi tên browser vào title (trừ khi overview yêu cầu) — browser khai ở field Environment
- ✅ Viết hoa chữ cái đầu mỗi câu (áp dụng cho mọi field)
- Test sản phẩm ngoại ngữ → kèm dịch tiếng Anh trong ngoặc: `"Quần Áo" (Clothing)`

### 2.2 Issue Classifications
| Field | Luật |
|-------|------|
| **Issue Type** | Functional / Visual / Content / Performance / Crash — chọn đúng loại |
| **Frequency** | Every time / Hardly ever / Occasionally / Once — theo thực tế reproduce |
| **Priority/Severity** | Low / Medium / High / Critical (xem mục 6) |
| **Source** | **Exploratory** = tìm ngoài test case; **Structured** = từ bước test case. Lưu ý: "Fail & Report Issue" tự chọn Structured, không đổi được |
| **Environment** | Đúng device + browser + OS đã test, **khớp với title**. Web → chọn browser, KHÔNG chọn "Native (No mobile browser)". Native app → chọn Native |

### 2.3 Actions Performed (bị soi kỹ nhất)
- Đánh số, **mỗi bước đúng 1 hành động**, theo thứ tự
- Bước 1: mở URL homepage của site (hoặc tên app) — **URL chỉ ghi ở bước 1**
- ❌ KHÔNG kết thúc bằng: Observe / Check / View results / Find / See / Pay attention
- ❌ Không viết expected/actual result vào steps
- Điều kiện trước khi test → viết `Precondition: ...` trước bước 1
- PC dùng từ **Click**, mobile dùng từ **Tap**

### 2.4 Expected Result / Actual Result
- Expected: điều user **mong đợi** xảy ra sau các steps
- Actual: điều **thực sự** xảy ra
- Viết rõ ràng, tách bạch 2 field

### 2.5 Error Message
- Chỉ điền khi màn hình CÓ hiển thị lỗi → copy NGUYÊN VĂN
- **Không có → để TRỐNG** — tuyệt đối không ghi "None", "N/A", "-" ⭐ (câu quiz 4/10)

### 2.6 Additional Environment Info
- Thông tin device/env bổ sung ảnh hưởng bởi bug
- Không cần thiết → để trống (xem overview có yêu cầu không)

## 3. Attachments

### Screenshots
- `.jpg` hoặc `.png`
- Highlight bằng **khung/tròn/mũi tên ĐỎ hoặc VÀNG** — ❌ KHÔNG vẽ nguệch bằng chuột (mouse drawing tool)
- Chụp **toàn màn hình, gồm URL bar** (khi test web)
- **Tối đa 2 screenshot/issue**
- **Blur/xóa PII** (email, SĐT, tên, ảnh đại diện, OTP...) trong attachment
- Không chụp bằng thiết bị ngoài (chụp màn hình máy tính bằng điện thoại) trừ khi DRM/được yêu cầu
- Submit xong phải mở lại kiểm tra file không hỏng

### Videos
- `.mp4`, tối đa **1 video/issue** (gộp hết steps vào 1 video)
- Video khớp với các steps trong Actions Performed, bug phải hiện rõ trong video
- Full màn hình có URL bar; tắt tiếng nền (trừ khi cần thuyết minh); nén video nếu quá lớn
- Không quay màn hình máy tính bằng điện thoại; không quay hình uTest platform/customer cycles

### Logs (nếu cycle yêu cầu)
- `.txt`/`.log`, thu trong lúc reproduce, URL test phải hiện trong log
- Bật "Preserve/Persist log" + "Show timestamps" trong DevTools
- ⚠️ **Cycle Academy Intro to Testing KHÔNG yêu cầu log** (chỉ 1 screenshot) — luôn theo overview từng cycle

### Attachment Visibility
- Nếu cycle bật tính năng này → attachment có chứa thông tin nhạy cảm thì tắt toggle **"Visible to testers"** (vẫn thấy được với TTL/TE/TSM/Customer)
- Chỉ ẩn khi thực sự chứa thông tin nhạy cảm

## 4. Giới hạn số issue

- Unrated/Rated tester: tối đa **5 issue chưa approved/cycle** — 1 issue approved thì mở thêm 1 slot
- Rating cao hơn (Gold/Silver/Bronze/Proven) → bỏ giới hạn
- Mỗi cycle có thể có limit riêng (do customer config) — hết limit nút Report Issue bị disable
- **Cycle Academy Intro: chỉ được ĐÚNG 1 issue!**

## 5. Sửa / Xóa issue report

### Trạng thái được EDIT
- **New** — mới report, chưa check
- **Info Requested** — TTL yêu cầu sửa → sửa xong **PHẢI bấm "Confirm all requested info is added"** (hoặc Actions > Send Requested Info) để status về `New`, TTL mới được thông báo recheck ⭐ (quên bấm = bug nằm chờ mãi!)
- **Rejected** — chỉ edit khi định **dispute** (sửa rõ hơn + thêm bằng chứng)

### Trạng thái KHÔNG edit được
- **Pending** — TTL đã review, đang chờ TE/Customer chốt
- **Approved** — đã duyệt

### Cách edit
1. Mở report → đọc message TTL ở tab Messages
2. **Actions → Edit Issue** → sửa → Submit Issue
3. ⚠️ Attachment KHÔNG sửa được trong Edit Issue — chỉ thêm/xóa ở section **Attachments** trên trang report (kéo xuống)
4. Bị yêu cầu attachment mới → upload cái mới, **xóa cái cũ không cần thiết**

### Discard (xóa report)
- **Chỉ được khi TTL chưa review** (chưa từng Pend/Info Request — kể cả status đang New)
- Mở report → Actions → **Discard** → Confirm
- Nên discard khi: bug không còn reproduce được, phát hiện bug thuộc OOS
- ⚠️ Đã bị TTL review rồi thì KHÔNG discard được nữa (báo lỗi)

### Placeholder — TUYỆT ĐỐI TRÁNH (vi phạm ToS = khóa account)
- Submit khi thiếu attachment / điền "1. 2. 3." / "..." / nội dung chờ sửa sau
- Dùng attachment không liên quan để report nhanh hơn người khác
- **Edit bug này thành bug KHÁC** (kể cả status New/Info Requested) → sai thì DISCARD, không sửa thành bug khác

## 6. Severity vs Value

### Severity (tester chọn) — 4 mức
| Mức | Định nghĩa | Ví dụ |
|-----|-----------|-------|
| **Low** | Ảnh hưởng nhỏ, không chạm tính năng cốt lõi | Lệch layout, lỗi chính tả |
| **Medium** | Ảnh hưởng vừa, còn workaround | Chậm đáng kể, bất tiện có cách khắc phục |
| **High** | Ảnh hưởng lớn tính năng cốt lõi, có thể delay release | Service unavailable với 1 nhóm user |
| **Critical** | Rất nghiêm trọng, dừng testing, phải fix trước release | **App crash/freeze**, lộ dữ liệu |

### Value (CUSTOMER quyết định) — 4 mức
- **Somewhat Valuable (Won't Fix)** — valid nhưng customer không định fix
- **Somewhat Valuable** — có tác động nhỏ
- **Very Valuable** — tác động đáng kể
- **Exceptionally Valuable** — tác động critical, phải fix

**⭐ Ghi nhớ:** Severity ≠ Value. Bug tester đánh Low vẫn có thể Very Valuable với customer. Bug Critical với tester có thể bị coi thường nếu: ngoài scope, user không bao giờ gặp, chỉ có ở dev/stage, kết quả stress test.

## 7. Bug Rejections (Lý do reject + ảnh hưởng rating)

| Lý do | Ý nghĩa | Rating |
|-------|---------|--------|
| **WAD** (Working as Designed) | Hành vi đúng thiết kế | ✅ KHÔNG ảnh hưởng |
| **DUP** (Duplicate) | Đã có người report / known issue | ❌ Trừ |
| **OOS** (Out of Scope) | Ngoài scope cycle | ❌ Trừ |
| **DNFI** (Did Not Follow Instructions) | Không theo instructions | ❌❌ Trừ **GẤP ĐÔI** |
| **INF** (Need more info) | Không trả lời info request | ❌ Trừ |
| **Other** | Không thuộc các loại trên (VD: không còn reproduce) | ❌ Trừ |

### Dispute (kháng cáo rejection)
- **Chỉ dispute khi:** chắc chắn mình đúng + đã theo đúng instructions + có thêm info/attachment chứng minh
- **KHÔNG dispute khi:** DUP / OOS / WAD / not reproducible / mình sai instructions
- Cách: mở report → Actions → **Dispute Rejection** → giải thích rõ ràng + upload evidence → gửi
- ⭐ **Mỗi bug chỉ 1 lần dispute**; số lượt dispute/tháng có hạn; double rejection (dispute lại bị reject) trừ rating thêm
- Chỉ dispute khi cycle đang **active hoặc locked**
- Ngôn ngữ chuyên nghiệp. Ví dụ TỐT: *"Hi TTL, Thank you for reviewing the report. However, I still believe the issue is valid and in scope because... I have edited the steps and provided new attachments. Could you please review the issue again? Thank you."*
- Ví dụ XẤU (cấm dùng): *"Are you kidding me?..."*, *"Are you blind?..."*
- ❌ Cấm negotiated/năn nỉ ngoài tính năng dispute — mọi dispute được giám sát

## 8. +1 Confirm Issue (Xác nhận bug người khác)

- Dùng khi: tự tay **reproduce được** bug của tester khác + chắc chắn bug đúng & in scope
- Steps: Issues tab → tìm bug → **+1** → chọn env + comment + **attachment** (visual bug = screenshot; bug khác = video)
- Lợi ích: bug được approve → rating được cộng nhẹ
- ❌ Không +1 nếu không reproduce được; không +1 thiếu attachment — TTL giám sát toàn bộ

## 9. Issue Quality Review (tự động check chất lượng)

- Bật ở 1 số cycle: tự đánh giá report theo (1) ngôn ngữ/lỗi chính tả, (2) best practices uTest, (3) instructions của cycle
- Không có lỗi → giữ nguyên. Vài lỗi nhỏ → **tự sửa**, status vẫn New, không thông báo
- Nhiều lỗi → gửi **Info Request**: mở report → **Edit Issue link** → xem so sánh 2 cột (trái: hiện tại, phải: đề xuất) →
  - Chấp nhận hết → **Submit New Version** (không sửa gì)
  - Sửa 1 phần → chỉnh rồi Submit New Version
  - Từ chối hết → **Re-Submit Original Version**
- Sau đó status về New, TTL được thông báo
- Đánh giá chỉ chạy 1 LẦN duy nhất. Có thể discard sau khi có Info Request từ feature này
- Không xử lý Info Request → report tự động bị reject khi cycle đóng
- ⚠️ Feature có thể làm report tệ hơn → xem kỹ đề xuất trước khi accept

## 10. Known Issues (KI)

- Bug customer ĐÃ BIẾT (report từ cycle trước / notice từ trước) → **KHÔNG report lại** (bị reject DUP)
- Check ở 3 nơi:
  1. Mục **Out of Scope** trong overview
  2. **File/link External Known Issue Sheet** đính kèm overview
  3. **Issues tab** — bug có **cờ xanh** 🔵 bên phải title
- Không hiểu KI nào → hỏi TTL trong chat

## 11. Bug Report Integrity (chất lượng report được chấm)

- **High Integrity** — bug rất valuable / report rất tốt, đủ info + attachment → **cộng rating**
- **Low Integrity** — không theo instructions, viết kém, bị đòi info nhiều lần, phản hồi thiếu chuyên nghiệp → **trừ rating**
- Mặc định: **Unrated** (không ảnh hưởng)

## 12. ✅ Checklist TRƯỚC KHI bấm Submit Issue

- [ ] Bug reproduce được **≥ 2 lần**? (cycle cấm report lỗi không reproduce được)
- [ ] In scope? Không thuộc OOS / Do Not Report? Không phải Known Issue?
- [ ] Title đúng format cycle + không ALL CAPS + không có tên browser?
- [ ] Type / Frequency / Priority / Source / Environment chọn đúng, env khớp title?
- [ ] Steps: đánh số, mỗi bước 1 hành động, bước 1 có URL, không có "Observe" cuối?
- [ ] Expected/Actual rõ ràng, tách bạch?
- [ ] Error Message: có lỗi → nguyên văn; không lỗi → **để trống**?
- [ ] Screenshot: full màn + URL bar, khung đỏ/vàng, đã blur PII, ≤ 2 ảnh?
- [ ] Video (nếu có): .mp4, khớp steps, ≤ 1 video?
- [ ] Trả lời đủ các câu tự-check trong form?
- [ ] Submit xong: mở lại attachment kiểm tra + vào Issues list kiểm tra trùng lặp?

## 13. Mẫu report hoàn chỉnh (tham khảo)

```
Title: Windows 11 - PLP - Sorting products by price, High to Low, gives incorrect results

Type: Functional    Frequency: Every Time    Priority: Medium
Source: Exploratory    Environment: Windows 11 Home - Chrome

Action Performed:
1. Go to https://<test-url>/<category-page>
2. Click the "Sort By" dropdown
3. Select the "Price: High to Low" option

Expected Result:
The products are displayed sorted from the highest price to the lowest price.

Actual Result:
The product priced at $45.00 is displayed above the product priced at $80.00.

Error Message: (để trống)

Attachment: screenshot full màn hình, khung đỏ quanh 2 sản phẩm sai thứ tự
```

**Ví dụ thực tế đã viết (cycle #563984):** xem `01-introduction-to-testing.md` mục Findings.
