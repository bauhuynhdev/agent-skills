---
name: planning
description: Creates and manages implementation plans with three sections (overview, scope, implementation steps). Use when user invokes /planning, planning, plan, kế hoạch, phạm vi, or create/update/execute a plan. If /planning has no content, MUST ask "Nội dung là gì?" and do not create a plan until content is provided. Do NOT run plan steps (edit code, run commands) unless user explicitly says execute. Steps: specific (what/where), not verbose within each step; use list format for sub-items. Code-related: describe by concept and location for cross-language understanding.
---

# Planning Skill

## Input

- **Cú pháp:** `/planning` rồi xuống dòng hoặc cách, sau đó `{nội dung}`. Ví dụ: `/planning Thêm API đăng nhập` hoặc `/planning` + xuống dòng + mô tả.
- **Chưa có nội dung:** Nếu user chỉ gõ `/planning` (hoặc `planning`) mà không kèm nội dung → **bắt buộc** trả lời **"Nội dung là gì?"** và chờ; **không** tạo plan, không đoán nội dung.
- **Có nội dung:** Chỉ khi đã có nội dung (mô tả task, feature, hoặc từ khóa `update`/`execute` kèm thông tin) mới tạo hoặc cập nhật plan.
- **Không tự ý chạy:** Chỉ **tạo** hoặc **cập nhật** plan (ghi file, mô tả bước). **Không** thực thi các bước triển khai (sửa code, chạy lệnh, v.v.) trừ khi user gửi rõ lệnh **execute**.
- **Lưu plan:** Thư mục `plans/` tại root dự án (tạo nếu chưa có). Tên file: `{feature-name-english}-{YYYYMMDDHHmm}.md` (vd: `add-login-api-202503131430.md`).

## Khi input không rõ

Hiển thị:

**Bạn có thể: (1) Ghi nội dung cần làm sau /planning → tạo plan. (2) update + nội dung → cập nhật plan. (3) execute → thực hiện plan.**

## Plan structure (3 parts)

1. **Tổng quan** — Mục tiêu, bối cảnh, tóm tắt 1–2 câu.
2. **Phạm vi ảnh hưởng** — File, module, layer (frontend/backend), API/DB/UI bị ảnh hưởng.
3. **Các bước triển khai** — Chỉ cần **cụ thể** từng bước (làm gì, ở đâu); **không** cần mô tả chi tiết bên trong từng bước. Nếu trong bước có liệt kê thì dùng **dạng list** (bullet hoặc sub-list). Đủ để khi `execute` thực thi từng bước. **Phần liên quan code:** diễn đạt theo **ý niệm** (validate dữ liệu, gọi API, lưu DB…) và **vị trí** (file, layer, tên hàm) để user quen ngôn ngữ khác vẫn hiểu.

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

## 3. Các bước triển khai

(Các bước cụ thể; không cần chi tiết trong từng bước. Nếu có liệt kê thì dùng dạng list.)

1. 
2. 
3. 
```

## Keywords

- **update** — Dòng sau = nội dung cập nhật. Sửa plan hiện có, giữ đủ 3 phần.
- **execute** — Chỉ khi user gửi lệnh này mới thực thi **Các bước triển khai** (sửa code, chạy lệnh). Không tự ý chạy khi chỉ tạo/cập nhật plan.

## Ví dụ

| User | Agent |
|------|--------|
| `/planning` hoặc `/planning` (chỉ vậy, không nội dung) | **Nội dung là gì?** (bắt buộc hỏi, không tạo plan). |
| `/planning Thêm API đăng nhập` hoặc `/planning` + xuống dòng + "Thêm API đăng nhập" | Tạo plan 3 phần (Tổng quan, Phạm vi, Các bước triển khai cụ thể, list nếu liệt kê); có thể lưu `plans/add-login-api-{YYYYMMDDHHmm}.md`. |
| `update` + xuống dòng + "Thêm bước 2.5: validate input" | Cập nhật plan (thêm bước vào Các bước triển khai). |
| `execute` | Thực hiện lần lượt Các bước triển khai trong plan. |
