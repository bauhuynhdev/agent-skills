---
name: planning
description: Creates and manages implementation plans with four sections (overview, scope, how-to, steps). Use when user asks for planning, plan, kế hoạch, phạm vi, or to create/update/execute a plan. If only skill name is given, ask "Nội dung là gì?"
---

# Planning Skill

## Input

- **Format:** `{skill}` then newline or space, then `{content}`. First line = skill name (e.g. `planning`). Rest = content (task description, or `update` + text, or `execute`).
- **Only `{skill}`:** Reply **"Nội dung là gì?"** and wait. Do nothing until content is provided.
- **Save plan to file:** Use folder `plans/` at project root (create if missing). Filename: `{feature-name-english}-{YYYYMMDDHHmm}.md` (e.g. `add-login-api-202503131430.md`).

## When input is unclear

Show:

**Bạn có thể: (1) Ghi nội dung cần làm → tạo plan. (2) update + nội dung → cập nhật plan. (3) execute → thực hiện plan.**

## Plan structure (4 parts)

1. **Tổng quan** — Mục tiêu, bối cảnh, tóm tắt 1–2 câu.
2. **Phạm vi ảnh hưởng** — File, module, layer (frontend/backend), API/DB/UI bị ảnh hưởng.
3. **How to do** — Cách làm, kỹ thuật, thứ tự, lý do chọn approach.
4. **Các bước triển khai** — Bước đánh số hoặc checklist; rõ ràng, có thể thực thi. Khi `execute` thì chạy lần lượt phần này.

## Mẫu skeleton (plan)

Khi tạo plan mới, dùng cấu trúc sau (điền nội dung vào từng phần):

```markdown
# [Tên plan / feature]

## 1. Tổng quan

[Mục tiêu, bối cảnh, tóm tắt 1–2 câu.]

## 2. Phạm vi ảnh hưởng

- **Files:** 
- **Modules/layers:** 
- **API / DB / UI:** 

## 3. How to do

[Cách làm, kỹ thuật, thứ tự xử lý, lý do chọn approach.]

## 4. Các bước triển khai

1. 
2. 
3. 
```

## Keywords

- **update** — Dòng sau = nội dung cập nhật. Sửa plan hiện có, giữ đủ 4 phần.
- **execute** — Không thêm nội dung. Đọc plan (file hoặc context), thực thi **Các bước triển khai**.

## Ví dụ

| User | Agent |
|------|--------|
| `planning` | Nội dung là gì? |
| `planning` + xuống dòng + "Thêm API đăng nhập" | Tạo plan 4 phần; có thể lưu `plans/add-login-api-{YYYYMMDDHHmm}.md`. |
| `update` + xuống dòng + "Thêm bước 2.5: validate input" | Cập nhật plan (thêm bước vào Các bước triển khai). |
| `execute` | Thực hiện lần lượt Các bước triển khai trong plan. |
