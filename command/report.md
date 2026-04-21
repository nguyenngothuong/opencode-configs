---
description: "Báo cáo toàn diện trạng thái project — git status, commits, diff, plan/tasks, docs"
---

<command-instruction>
Tạo BÁO CÁO trạng thái project. Chạy các lệnh dưới đây, thu thập kết quả, rồi output báo cáo.

## BƯỚC 1: Chạy các lệnh thu thập data (TẤT CẢ parallel)

### 1.1 Git status
!`git status --short`

### 1.2 Branch info
!`git branch -vv`

### 1.3 Commits local chưa push
!`git log origin/$(git rev-parse --abbrev-ref HEAD)..HEAD --oneline 2>/dev/null || echo "NONE"`

### 1.4 Commits remote chưa pull
!`git log HEAD..origin/$(git rev-parse --abbrev-ref HEAD) --oneline 2>/dev/null || echo "NONE"`

### 1.5 Diff unstaged (đã sửa chưa add)
!`git diff --stat HEAD 2>/dev/null || echo "NONE"`

### 1.6 Diff staged (đã git add)
!`git diff --cached --stat 2>/dev/null || echo "NONE"`

### 1.7 Tags chưa push
!`git tag --no-merged origin/$(git rev-parse --abbrev-ref HEAD) 2>/dev/null || echo "NONE"`

### 1.8 Plan/Task files
!`Get-ChildItem -Recurse -Depth 3 -File -Include "*plan*.md","*task*.md","*todo*.md","TASKS*","TODO*" -ErrorAction SilentlyContinue | Select-Object -First 20 FullName | ForEach-Object { $_.FullName } 2>$null; if (-not $?) { echo "NONE" }`

### 1.9 README / AGENTS.md changes
!`git diff --stat HEAD -- README.md AGENTS.md readme.md agents.md 2>/dev/null || echo "NONE"`

### 1.10 AGENTS.md nội dung (để check agents/skills hiện tại)
!`Get-Content AGENTS.md -ErrorAction SilentlyContinue 2>$null || echo "NOT_FOUND"`

## BƯỚC 2: Tạo báo cáo

Dựa trên kết quả từ Bước 1, tạo báo cáo theo format sau:

<output-format>
## 📊 Báo Cáo Trạng Thái Project

### 🟢 Tổng quan nhanh
> 1-2 dòng tóm tắt: branch gì, ahead/behind bao nhiêu, có gì urgent không

---

### 1. Git Status
| Metric | Giá trị |
|--------|---------|
| Branch | `<branch>` |
| Ahead origin | X commits |
| Behind origin | Y commits |
| Modified (unstaged) | N files |
| Staged | N files |
| Untracked | N files |

### 2. Commits Chưa Push
*Nếu có: liệt kê từng commit với hash + message*
*Nếu không: ✅ Đồng bộ*

### 3. Commits Remote Chưa Pull
*Nếu có: liệt kê — cảnh báo user cần pull trước*
*Nếu không: ✅ Không có gì mới*

### 4. Thay Đổi Chưa Commit
**Staged** (sẵn sàng commit):
- file1 (+N dòng)
- ...

**Unstaged** (đã sửa chưa add):
- file2 (-N dòng)
- ...

### 5. Plan & Task Files
| File | Cập nhật cuối | Ghi chú |
|------|--------------|---------|
| ... | ... | ... |

### 6. Documentation
| File | Trạng thái |
|------|-----------|
| README.md | ✅/❌/⚠️ Đã sửa/Chưa sửa/Có warning |
| AGENTS.md | ✅/❌/⚠️ Đã sửa/Chưa sửa/Có warning |

### 7. ⚠️ Cảnh báo & Đề xuất
- **Cần làm ngay**: (nếu có conflict risk, file quan trọng chưa commit)
- **Nên làm**: (nếu có thể cleanup, commit pending files)
- **An toàn để push**: ✅/❌ (giải thích nếu ❌)
</output-format>

## Nguyên tắc
- KHÔNG hỏi user, output ngay sau khi chạy xong lệnh
- Dùng tiếng Việt
- Nếu có dữ liệu → SHOW RA, đừng nói chung chung
- Nếu không có dữ liệu → ghi "Không có" hoặc "—", đừng bỏ trống
- Ưu tiên cảnh báo rủi ro lên đầu (conflict, untracked files quan trọng)
</command-instruction>
