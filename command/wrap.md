---
description: "Tạo Walkthrough + Learning Summary cho feature/task đã hoàn thành — giải thích what changed, why, how to test"
---

Tạo Walkthrough và Learning Summary cho plan đã hoàn thành.

## Bước 1: Thu thập thông tin — Chạy TẤT CẢ parallel

### 1.1 Tìm plan files
!`Get-ChildItem -Path "docs/plans" -Filter "plan.md" -Recurse -ErrorAction SilentlyContinue | Select-Object -ExpandProperty FullName 2>$null || echo "NO_PLANS"`

### 1.2 Đọc task files completed
!`Get-ChildItem -Path "docs/plans" -Filter "*.md" -Recurse -ErrorAction SilentlyContinue | Select-Object -ExpandProperty FullName 2>$null || echo "NO_TASKS"`

### 1.3 Git diff tổng quan
!`git diff --stat origin/$(git rev-parse --abbrev-ref HEAD)..HEAD 2>/dev/null || git diff --stat HEAD~10..HEAD 2>/dev/null || echo "NONE"`

### 1.4 Files mới
!`git ls-files --others --exclude-standard 2>/dev/null || echo "NONE"`

## Bước 2: Tạo Walkthrough + Learning Summary

Dựa trên thông tin thu thập, output theo format:

<output-format>
# 🚀 Walkthrough: [Feature/Task Name]

## Tóm tắt
[1-2 câu mô tả đơn giản những gì đã làm]

## Những gì đã thay đổi

### ✨ Files mới
| File | Làm gì |
|------|--------|
| `path/to/file.ts` | Mô tả chức năng |

### 📝 Files đã sửa
| File | Thay đổi |
|------|----------|
| `path/to/file.ts` | Mô tả thay đổi |

## Cách hoạt động (đơn giản)

```
User action
    ↓
Step 1
    ↓
Step 2
    ↓
Result ✅
```

## Cách test thử

```bash
# Commands để test
```

## Lưu ý quan trọng
- [Things to know]

---

## 💡 Học được gì từ task này?

### Concepts chính
| Concept | Giải thích đơn giản | Khi nào dùng |
|---------|---------------------|--------------|
| ... | ... | ... |

### Patterns đã dùng
| Pattern | Tại sao dùng | Alternative |
|---------|--------------|-------------|
| ... | ... | ... |

### Trade-offs đã chọn
| Quyết định | Ưu điểm | Nhược điểm | Tại sao vẫn chọn |
|------------|---------|------------|------------------|
| ... | ... | ... | ... |

### Nếu tự làm lần sau
1. **Bước 1**: ...
2. **Bước 2**: ...
3. ...

---
✅ **Done!** Bạn có thể test thử ngay.
</output-format>

## Nguyên tắc
- Output ngay, KHÔNG hỏi user
- Dùng tiếng Việt
- KHÔNG có code blocks dài — dùng diagram ASCII thay vì code
- Emoji để dễ scan (✅ ❌ 📝 ✨ 🔧 ♻️ 💡)
- Tối đa 40-50 dòng cho walkthrough
- Learning summary tập trung vào WHY, không phải WHAT
- Nếu plan chưa completed → cảnh báo user
