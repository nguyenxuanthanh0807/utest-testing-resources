# Bug Report #1: Back Button Stays on Shop Page

## Issue Title
```
iPhone 15 - Shop - Back button stays, not working
```

## Form Fields

| Field | Value |
|-------|-------|
| **Issue Title** | `iPhone 15 - Shop - Back button stays, not working` (49 chars) |
| **Type** | Functional |
| **Frequency** | Every Time |
| **Priority** | Medium |
| **Source** | Exploratory |
| **My Environments** | Apple iPhone 15 - iOS 26.5, MobiFone - Native (No mobile browser) |

## Body

```
Environment: Apple iPhone 15 - iOS 26.5 - Shoe Carnival (native app) - MobiFone
App version: [ĐIỀN VERSION]

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

Attachments:
- Screenshot (.png) - back button highlighted with a red rectangle
- Screen recording (.mp4) - full repro, no background noise
- iOS device log (.txt/.log)
```

## Attachments

| File | Status | Notes |
|------|--------|-------|
| Screenshot | ✅ | Ảnh 2: grid 4 sản phẩm, không có breadcrumb, nút back khoanh đỏ |
| Screen recording | ⬜ | Cần quay lại |
| Device log | ✅ | `16112026_204935_810_iPhone.log` (3uTools, sạch PII) |

## Pre-submit Checklist

- [x] Title đúng format `Device - Area - Issue` (49 ký tự ≤ 50)
- [x] Đã đếm ký tự của title
- [x] Type: Functional
- [x] Frequency: Every Time (3/3)
- [x] Priority: Medium (có workaround: dùng tab bar)
- [x] Source: Exploratory
- [x] My Environments: đúng environment phân công
- [ ] Đủ 3 file đính kèm (cần video)
- [x] PII đã blur trong log
- [ ] Không lộ từ "tester"/"test"/"qa"
- [x] Reproduce được trên 2 lần (3/3)
- [x] Không phải field validation / accessibility / usability / security

---

**Status:** Chờ video + App version → Submit

**Created:** 2026-11-17
**Cycle:** Shoe Carnival Mobile Testing - uTest Academy