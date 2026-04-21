---
description: "Báo cáo tiến độ plan hiện tại — tasks completed/pending/failed/blocked, files đã sửa, commit history"
---

Báo cáo tiến độ toàn diện của plan đang chạy.

## Bước 1: Thu thập thông tin — Chạy TẤT CẢ parallel

### 1.1 Tìm plan files
!`Get-ChildItem -Path "docs/plans" -Filter "plan.md" -Recurse -ErrorAction SilentlyContinue | Select-Object -ExpandProperty FullName 2>$null || echo "NO_PLANS"`

### 1.2 Git status
!`git status --short`

### 1.3 Commits gần đây
!`git log --oneline -10`

### 1.4 Files thay đổi (unstaged)
!`git diff --stat HEAD 2>/dev/null || echo "NONE"`

## Bước 2: Phân tích và báo cáo

Sau khi thu thập, output theo format:

<output-format>
## 📊 Trạng thái Plan

### Plan hiện tại
- **Plan**: [tên plan]
- **Status**: draft / ready / in-progress / completed
- **Created**: [ngày]

### Tasks Overview
| Status | Count | Details |
|--------|-------|---------|
| ✅ Completed | N | [task IDs] |
| ⏳ Pending | N | [task IDs] |
| 🔴 Failed | N | [task IDs] |
| ⏸️ Blocked | N | [task IDs] |

### Progress Bar
[██████░░░░] 60% (6/10 tasks)

### Tasks chi tiết
| ID | Title | Status | Duration | Notes |
|----|-------|--------|----------|-------|
| BE-001 | ... | ✅ | 15m | ... |

### Files đã sửa (chưa commit)
- file1 (+N/-N dòng)
- file2 (+N/-N dòng)

### Commits gần đây
| Hash | Message | Time |
|------|---------|------|
| abc123 | feat: ... | 2h ago |

### Next Steps
- Task tiếp theo có thể chạy: [task ID + title]
- Dependencies satisfied: YES/NO
- Có task blocked không? Nếu có → lý do

### Đề xuất
- Nếu có tasks pending → `/next` để chạy task tiếp theo
- Nếu có tasks failed → `/continue` để retry
- Nếu plan completed → `/wrap` để tạo walkthrough
</output-format>

## Nguyên tắc
- Output ngay, KHÔNG hỏi user
- Dùng tiếng Việt
- Nếu không tìm thấy plan → báo "Không có plan nào trong docs/plans/"
- Highlight tasks failed/blocked lên đầu
