# 🧬 YCARE 2025 – Hệ thống TMĐT Plugin hóa (AI-first)

YCare là hệ thống thương mại điện tử plugin-first, tối ưu cho ngành TPCN với các nghiệp vụ chuyên biệt:

- 🛍️ Đặt hàng, voucher, loyalty, xếp hạng
- 💼 Hệ thống KPI đa tầng cho CTV ẩn danh
- 🔁 Plugin manager bật/tắt runtime
- 🔐 RBAC theo 10 role chuẩn (Admin, CTV, CMS...)
- 📦 CMS động, export, audit log, retry queue
- ✅ Sinh UID/code tự động, không nhập tay

---

## ⚙️ Kiến trúc kỹ thuật

| Thành phần  | Công nghệ |
|-------------|-----------|
| Backend     | [NestJS](https://nestjs.com/), [PostgreSQL](https://www.postgresql.org/), Prisma ORM |
| Frontend    | [Next.js](https://nextjs.org/), Tailwind, Shadcn |
| Auth        | JWT, RBAC chuẩn |
| Plugin      | Dynamic Module NestJS |
| CI/CD       | GitHub Actions → Railway (BE), Vercel (FE) |
| Deploy      | Railway (backend), Vercel (frontend) |
| Repo        | Monorepo (`apps/backend`, `apps/frontend`) |

---

## 📁 Cấu trúc thư mục

```bash
Duanycare2025/
├── apps/
│   ├── backend/        # NestJS backend
│   │   └── src/modules/<module-name>/
│   └── frontend/       # Next.js frontend + CMS
├── prisma/             # Schema chung nếu dùng
├── .github/workflows/  # GitHub Actions CI/CD
├── .env.example        # Biến môi trường mẫu
├── README.md           # Tài liệu dự án
└── package.json        # Nếu dùng workspace
---
## clone & cài thư viện
```bash
git clone https://github.com/duanycare/Duanycare2025.git
cd Duanycare2025
pnpm install
