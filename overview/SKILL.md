---
name: overview
description: Run when user invokes /overview. Analyze the current project then output summary, tech stack, and directory structure with comments.
---

# Overview Skill

## Trigger

- User gọi **/overview** (hoặc "overview", "tổng quan dự án", "cấu trúc dự án") → chạy skill này.

## Cách làm

1. **Phân tích dự án hiện tại**
   - Đọc cấu trúc thư mục: `src/`, config, docs; bỏ qua `node_modules`, `.git`, `.next`, `__pycache__`, build.
   - Đọc dependencies: frontend (`package.json`), backend (`requirements*.txt`, `pyproject.toml`).
   - Xác định: framework, UI lib, DB/ORM, auth, testing, deploy/dev tooling.
   - Xác định luồng: entry, API routes, services, repositories, models.

2. **Output theo thứ tự**

   **a) Tổng quan** — 1–2 câu: tên dự án, mục đích, tính năng chính, stack (vd: Next.js + FastAPI, Docker).

   **b) Tech stack** — Bảng (Frontend, UI, Form, i18n, Backend, ORM/DB, Auth, Deploy/Dev, Testing) từ dependencies và config.

   **c) Cấu trúc thư mục** — Cây thư mục quan trọng, **mỗi nhánh kèm comment** giải thích.

   **d) (Tùy chọn)** Architecture map (Lớp → Vị trí) và Luồng dữ liệu (1 dòng).

## Mẫu skeleton (output)

Dùng cấu trúc dưới đây, điền nội dung sau khi phân tích. Chỉ thay placeholder bằng dữ liệu thật.

```markdown
## 1. Tổng quan

**[Tên dự án]**: [1–2 câu mô tả mục đích, tính năng chính]. [Stack tổng quát, VD: Frontend X, Backend Y, Docker].

---

## 2. Tech stack

| Phần | Công nghệ |
|------|-----------|
| Frontend | … |
| UI | … |
| Form / validation | … |
| i18n | … |
| Backend | … |
| ORM / DB | … |
| Auth | … |
| Deploy / Dev | … |
| Testing | … |

---

## 3. Cấu trúc thư mục

    [repo-root]/
    ├── [thư_mục_1]/     # [comment giải thích]
    │   ├── [nhánh]/     # [comment]
    │   └── …
    ├── src/
    │   ├── backend/     # [comment]
    │   │   └── src/
    │   │       ├── apis/      # [comment]
    │   │       └── …
    │   ├── frontend/    # [comment]
    │   └── …
    └── …

---

## 4. Architecture map (ngắn)

| Lớp | Vị trí |
|-----|--------|
| Trang / Layout | … |
| Features / UI | … |
| Client services | … |
| REST API | … |
| Services (backend) | … |
| Repositories | … |
| Models | … |

**Luồng dữ liệu:** [1 dòng, VD: UI → services → API → services → repos → DB]
```

## Nguyên tắc

- Phân tích dựa trên repo hiện tại, không dùng nội dung cố định.
- Viết ngắn gọn, rõ ràng, đúng trọng tâm.
- Comment trong cây thư mục phải giải thích rõ vai trò từng phần.
