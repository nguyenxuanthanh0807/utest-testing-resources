# AGENTS.md

## Project Overview

This is a **uTest testing workspace** for managing test cycles, bug reports, and learning materials for uTest Academy mobile and browser testing.

## Repository Structure

```
testing-resources/
├── .opencode/              # OpenCode configuration
│   ├── skills/             # Skills for OpenCode
│   │   └── utest-bug-reporting/
│   └── plan/               # Plan files
├── skills/                 # Source skills (git tracked)
│   └── utest-bug-reporting/
├── Academy/                # uTest Academy learning materials
├── cycles/                 # Test cycles
│   └── <cycle-name>/
│       ├── README.md       # Cycle overview
│       ├── test-case.md    # Test case submission
│       └── bug-XX-name/    # Bug reports
│           └── report.md
└── README.md               # Quick start guide
```

## Workflow for uTest Tasks

### When starting a new test cycle:

1. **Read the skill:** `skills/utest-bug-reporting/SKILL.md`
2. **Create cycle folder:** `cycles/<cycle-name>/`
3. **Create cycle README** with focus areas and requirements
4. **Create test-case.md** with checklist
5. **Test on real device** (iPhone/Android)
6. **Create bug reports** in `cycles/<cycle-name>/bug-XX-name/report.md`
7. **Collect evidence:** Screenshot + Video + Device Log
8. **Submit to uTest** and update status
9. **Commit and push** to GitHub

### When logging a bug:

1. **Use the skill:** `skills/utest-bug-reporting/SKILL.md`
2. **Follow title format:** `Device Name - Area - Issue Description` (≤50 chars)
3. **Fill all form fields:** Type, Frequency, Priority, Source, Environment
4. **Write body:** Environment, Steps, Expected, Actual, Reproducibility
5. **Attach 3 files:** Screenshot (highlighted) + Video (no noise) + Log (PII blurred)
6. **Pre-submit checklist** before clicking "Report Issue"

## Bug Report Format

### Title (≤50 characters)
```
Device Name - Area - Issue Description
```

### Body Template
```
Environment: [Device] - [OS] - [App] (native app) - [Network]
App version: [VERSION]

Steps to Reproduce:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Expected Result:
[What should happen]

Actual Result:
[What actually happens]

Reproducibility: Reproduced X/X attempts.

Attachments:
- Screenshot (.png) - defect highlighted with red rectangle
- Screen recording (.mp4) - full repro, no background noise
- Device log (.txt/.log) - PII blurred
```

## Form Fields

| Field | Options |
|-------|---------|
| **Type** | Crash, Functional, Performance, Visual, Content |
| **Frequency** | Every Time, Occasionally, Hardly Ever, Once |
| **Priority** | Critical, High, Medium, Low |
| **Source** | Structured, Exploratory |
| **My Environments** | Only assigned environment |

## Important Rules

### Do NOT:
- Complete orders or make purchases
- Report field validation issues
- Add payment methods
- Use third-party apps during testing
- Report Accessibility/Usability/Security issues
- Report issues not reproducible > 2 times
- Submit more than 3 bug reports per cycle
- Leak PII in attachments (email, name, phone, address, photo)

### Do:
- Use 3uTools for iOS device logs (approved by TTL)
- Blur PII in all attachments
- Follow title format (≤50 chars)
- Attach 3 files per bug report
- Respond to TTL within 48 hours
- Be honest about tools used

## Tools

### iOS Device Log Collection
- **3uTools** (Windows) - ✅ Approved by TTL
- **iMazing** (Windows/Mac) - Alternative
- **idevicesyslog** (Command line) - Advanced

### PII Blurring
- **StripPii** (iOS/Mac) - Blur, frosted glass
- **Photoshop/GIMP** - Manual blur

## Security Notes

- **Never commit PII** (emails, names, phones, addresses)
- **Blur PII** in all screenshots, videos, and logs
- **Regenerate tokens** after sharing in conversations
- **Use SSH keys** for GitHub authentication

## Cycle Status Tracking

Update `cycles/<cycle-name>/README.md` with:
- Bug status (Draft, Submitted, Approved, Rejected)
- Test case status
- Timeline
- TTL feedback

---

**Project Type:** uTest Testing Workspace
**Language:** Vietnamese + English (for bug reports)
**Platform:** uTest Academy