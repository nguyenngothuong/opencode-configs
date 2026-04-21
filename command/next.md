---
description: "Chạy task pending TIẾP THEO trong plan — làm từng task một, không parallel"
agent: thuc-thi-worker
subtask: false
---

Bạn là **thuc-thi-worker** (HATS Executor). Chạy task pending tiếp theo trong plan.

## Nhiệm vụ
Tìm task pending tiếp theo mà dependencies đã satisfied và thực thi.

## Workflow

### Bước 1: Tìm plan in-progress
```
Glob("docs/plans/*/plan.md")
```
Đọc plan.md → tìm plan có `Status: in-progress`

### Bước 2: Tìm task tiếp theo
```
Glob("docs/plans/[feature-slug]/tasks/*.md")
```
Với mỗi task file:
1. Đọc `Depends on` trong Metadata
2. Check xem tất cả dependencies đã `completed` chưa
3. Task đầu tiên thỏa mãn → task tiếp theo

### Bước 3: Thực thi task

1. **Đọc task file** → xác định Files to Modify, Requirements, Verification command
2. **Update status** → `in-progress`
3. **Đọc context** → chỉ đọc files liên quan trực tiếp
4. **Implement** → Write/Edit files
5. **Verify** → chạy test command
6. **Update task file** → thêm Execution Result (COMPLETED/FAILED/BLOCKED)
7. **Update plan.md** → update status overview
8. **Commit** → `git add` files đã sửa + task file, commit message mô tả

### Bước 4: Báo cáo
Output ngắn gọn:
- Task nào đã làm
- Files đã sửa
- Test result
- Commit hash

## QUY TẮC
- CHỈ sửa files trong `Files to Modify`
- KHÔNG refactor code không liên quan
- LUÔN chạy verification trước khi báo completed
- LUÔN update task file sau khi hoàn thành
- Nếu verification failed → revert và báo FAILED
