# uTest Testing Resources

> Comprehensive testing resources for uTest mobile and browser testing cycles.

## 📁 Repository Structure

```
testing-resources/
├── skills/
│   └── utest-bug-reporting/     # Skill: Hướng dẫn log bug uTest
│       └── SKILL.md
├── Academy/                     # Tài liệu uTest Academy (tiếng Việt)
│   ├── README.md
│   ├── 00-quy-dinh-chung.md
│   ├── guide-bug-report.md
│   ├── guide-utest-mobile-app.md
│   └── ...
├── cycles/                      # Theo từng test cycle
│   └── shoe-carnival-2026-11/   # Cycle hiện tại
│       ├── README.md            # Tổng quan cycle
│       ├── test-case.md         # Test case submission
│       ├── bug-01-back-button/  # Bug report #1
│       │   └── report.md
│       └── bug-02-coupons/      # Bug report #2
│           └── report.md
└── README.md                    # File này
```

## 🎯 Quick Start

### Khi có task uTest mới

1. **Mở workspace:** `F:\testing-resources`
2. **Đọc skill:** `skills/utest-bug-reporting/SKILL.md`
3. **Tạo cycle folder:** `cycles/<cycle-name>/`
4. **Test trên device thật** (iPhone/Android)
5. **Lưu bug report + evidence** vào cycle folder
6. **Submit lên uTest**
7. **Commit + push** lên GitHub

### Workflow chi tiết

| Bước | Hành động | Ở đâu |
|------|-----------|-------|
| 1 | Nhận task từ uTest | uTest.com |
| 2 | Mở OpenCode session | `F:\testing-resources` |
| 3 | Đọc skill + Academy | `skills/`, `Academy/` |
| 4 | Tạo cycle folder | `cycles/<cycle-name>/` |
| 5 | Test trên device | Device thật |
| 6 | Viết bug report | `cycles/<cycle-name>/bug-XX/` |
| 7 | Thu thập evidence | Screenshot + Video + Log |
| 8 | Submit lên uTest | uTest.com |
| 9 | Commit + push | GitHub |

## 📋 Bug Report Checklist

Trước khi submit, kiểm tra:

- [ ] Title đúng format `Device - Area - Issue` (≤50 ký tự)
- [ ] Đã đếm ký tự của title
- [ ] Type / Frequency / Priority / Source đã chọn đúng
- [ ] Frequency khớp tỉ lệ repro thật
- [ ] Đủ 3 file: screenshot + video + log
- [ ] PII đã blur ở cả 3 file
- [ ] Không lộ từ "tester"/"test"/"qa"
- [ ] Reproduce được trên 2 lần

## 📚 Learning Resources

### Skill uTest Bug Reporting
- **Location:** `skills/utest-bug-reporting/SKILL.md`
- **Contents:** Title format, form fields, body template, attachments, checklist

### uTest Academy Materials
- **Location:** `Academy/`
- **Contents:** Bug report guides, test cycle process, mobile testing, web debugging

### External Resources
- [uTest Academy](https://www.utest.com/academy/)
- [awesome-testing](https://github.com/TheJambo/awesome-testing)
- [howtheytest](https://github.com/abhivaikar/howtheytest)

## 🔧 Tools

### iOS Device Log Collection
| Tool | Platform | Status |
|------|----------|--------|
| **3uTools** | Windows | ✅ Approved by TTL |
| **iMazing** | Windows/Mac | Alternative |
| **idevicesyslog** | Windows/Mac/Linux | Command line |

### PII Blurring
- **StripPii** (iOS/Mac) - Blur, frosted glass, keyword redact
- **Photoshop/GIMP** - Manual blur

## 📊 Current Cycle Status

### Shoe Carnival Mobile Testing (Nov 2026)

| Item | Status |
|------|--------|
| Bug #1 (Back button) | Draft |
| Bug #2 (Coupons categories) | Draft |
| Test case | In Progress |
| **Cycle Status** | **In Progress** |

## 🔒 Security Notes

- **Never commit PII** (emails, names, phones, addresses)
- **Blur PII** in all screenshots, videos, and logs
- **Regenerate tokens** after sharing in conversations
- **Use SSH keys** for GitHub authentication

---

## 📝 Contributing

1. Fork this repository
2. Create a new cycle folder for each test cycle
3. Follow the bug report checklist
4. Submit a pull request

---

**Maintained by:** nguyenxuanthanh0807
**Last Updated:** 2026-11-17