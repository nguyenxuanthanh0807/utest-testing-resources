# Shoe Carnival Mobile Testing - uTest Academy Cycle

## Overview

| Field | Value |
|-------|-------|
| **Cycle Name** | Shoe Carnival Mobile Testing |
| **Platform** | uTest Academy |
| **Date** | November 2026 |
| **Device** | Apple iPhone 15 - iOS 26.5 |
| **Network** | MobiFone - Native (No mobile browser) |
| **App** | Shoe Carnival (iOS) |

## Cycle Requirements

To pass this cycle:
- ✅ 1 approved bug report
- ✅ 1 approved test case

## Focus Areas

1. **Account & Authentication** - Registration, Profile, Login/Logout, Forgot Password
2. **App Navigation & UI** - Menu items, submenus, links
3. **Search & Filter** - Search queries, filters, sorting
4. **Category Pages** - Categories, links, filters
5. **Product Details (PDP)** - Images, sizes, details, size chart, cart, favorites
6. **Cart & Checkout** - Quantity, prices, checkout flow
7. **Bug Hunting** - Price mismatches, freezes, device-specific bugs

## Bugs Found

### Bug #1: Back Button Stays on Shop Page
- **Title:** `iPhone 15 - Shop - Back button stays, not working`
- **Type:** Functional | **Priority:** Medium | **Status:** Draft
- **Location:** `bug-01-back-button/report.md`

### Bug #2: Categories List Not Responding
- **Title:** `iPhone 15 - Coupons - Categories do not respond`
- **Type:** Functional | **Priority:** High | **Status:** Draft
- **Location:** `bug-02-coupons/report.md`

## Test Case

- **Status:** In Progress
- **Location:** `test-case.md`

## Important Rules

### Do NOT
- ❌ Complete any orders or make purchases
- ❌ Report field validation issues
- ❌ Add payment methods to account
- ❌ Use third-party apps (Google Translate, etc.)
- ❌ Change country on App Store
- ❌ Report Accessibility/Usability/Security issues
- ❌ Report issues not reproducible > 2 times
- ❌ Submit more than 3 bug reports

### Do
- ✅ Use 3uTools for iOS device logs (approved by TTL)
- ✅ Blur PII in all attachments (email, name, phone, address, photo)
- ✅ Follow title format: `Device Name - Area - Issue Description` (≤50 chars)
- ✅ Attach 3 files: screenshot + screen recording + device log
- ✅ Respond to TTL within 48 hours

## Attachments Checklist

For each bug report:
- [ ] Screenshot (.jpg/.png) - highlighted with red rectangle
- [ ] Screen recording (.mp4) - no background noise, mic off
- [ ] Device log (.txt/.log) - PII blurred

## Timeline

| Date | Activity |
|------|----------|
| 2026-11-16 | Started cycle, found Bug #1 (back button) |
| 2026-11-17 | Found Bug #2 (Coupons categories), created workspace |
| TBD | Complete test case |
| TBD | Submit bug reports |
| TBD | Receive TTL feedback |

---

## Resources

- **Skill:** `../skills/utest-bug-reporting/SKILL.md`
- **Academy:** `../Academy/`
- **uTest Academy Courses:** https://www.utest.com/academy/

---

**Created:** 2026-11-17
**Last Updated:** 2026-11-17