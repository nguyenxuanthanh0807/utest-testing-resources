# Bug Report #2: Categories List Not Responding

## Issue Title
```
iPhone 15 - Coupons - Categories do not respond
```

## Form Fields

| Field | Value |
|-------|-------|
| **Issue Title** | `iPhone 15 - Coupons - Categories do not respond` (47 chars) |
| **Type** | Functional |
| **Frequency** | Every Time |
| **Priority** | High |
| **Source** | Exploratory |
| **My Environments** | Apple iPhone 15 - iOS 26.5, MobiFone - Native (No mobile browser) |

## Body

```
Environment: Apple iPhone 15 - iOS 26.5 - Shoe Carnival (native app) - MobiFone
App version: [ĐIỀN VERSION]

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

Attachments:
- Screenshot (.png) - unresponsive category items highlighted with a red rectangle
- Screen recording (.mp4) - taps on several categories with no response, no background noise
- iOS device log (.txt/.log)
```

## Attachments

| File | Status | Notes |
|------|--------|-------|
| Screenshot | ✅ | 2 ảnh: panel Categories với pressed state (Mens Shoes + Nike Hot Deals) |
| Screen recording | ⬜ | Cần quay: force quit → Coupons → CATEGORIES → bấm 4 item → bấm X |
| Device log | ⬜ | Cần thu thập bằng 3uTools (cùng phiên với video) |

## Pre-submit Checklist

- [x] Title đúng format `Device - Area - Issue` (47 ký tự ≤ 50)
- [x] Đã đếm ký tự của title
- [x] Type: Functional
- [x] Frequency: Every Time (3/3 + sau restart)
- [x] Priority: High (toàn bộ tính năng Categories chết)
- [x] Source: Exploratory
- [x] My Environments: đúng environment phân công
- [ ] Đủ 3 file đính kèm (cần video + log)
- [ ] PII đã blur trong video + log
- [ ] Không lộ từ "tester"/"test"/"qa"
- [x] Reproduce được trên 2 lần (3/3)
- [x] Không phải field validation / accessibility / usability / security

---

**Status:** Chờ video + log + App version → Submit

**Created:** 2026-11-17
**Cycle:** Shoe Carnival Mobile Testing - uTest Academy