  `# 🧬 YCARE 2025 – Hệ thống TMĐT Plugin hóa (AI-first)  YCare là hệ thống thương mại điện tử plugin-first, tối ưu cho ngành TPCN với các nghiệp vụ chuyên biệt:  - 🛍️ Đặt hàng, voucher, loyalty, xếp hạng - 💼 Hệ thống KPI đa tầng cho CTV ẩn danh - 🔁 Plugin manager bật/tắt runtime - 🔐 RBAC theo 10 role chuẩn (Admin, CTV, CMS...) - 📦 CMS động, export, audit log, retry queue - ✅ Sinh UID/code tự động, không nhập tay  ---  ## ⚙️ Kiến trúc kỹ thuật  | Thành phần  | Công nghệ | |-------------|-----------| | Backend     | [NestJS](https://nestjs.com/), [PostgreSQL](https://www.postgresql.org/), Prisma ORM | | Frontend    | [Next.js](https://nextjs.org/), Tailwind, Shadcn | | Auth        | JWT, RBAC chuẩn | | Plugin      | Dynamic Module NestJS | | CI/CD       | GitHub Actions → Railway (BE), Vercel (FE) | | Deploy      | Railway (backend), Vercel (frontend) | | Repo        | Monorepo (`apps/backend`, `apps/frontend`) |  ---  ## 📁 Cấu trúc thư mục  ```bash Duanycare2025/ ├── apps/ │   ├── backend/        # NestJS backend │   │   └── src/modules/<module-name>/ │   └── frontend/       # Next.js frontend + CMS ├── prisma/             # Schema chung nếu dùng ├── .github/workflows/  # GitHub Actions CI/CD ├── .env.example        # Biến môi trường mẫu ├── README.md           # Tài liệu dự án └── package.json        # Nếu dùng workspace `  
## 🚀 Cài đặt local
 
### Yêu cầu:
 
 
- Node.js >= 18
 
- pnpm hoặc npm/yarn
 
- PostgreSQL local hoặc Railway
 

 
### Bước 1: Clone và cài thư viện
 `git clone https://github.com/duanycare/Duanycare2025.git cd Duanycare2025 pnpm install ` 
### Bước 2: Chạy Backend (NestJS)
 `cd apps/backend cp .env.example .env pnpm run dev ` 
### Bước 3: Chạy Frontend (Next.js)
 `cd apps/frontend cp .env.example .env pnpm run dev `  
## 🔁 CI/CD
 
  
 
Thành phần
 
Triển khai
 
Công cụ
 
   
 
Backend
 
Railway
 
`backend.yml`
 
 
 
Frontend
 
Vercel
 
`frontend.yml`
 
 
 
Tự động
 
GitHub Actions
 
`.github/workflows/`
 
  
  
## 🔐 Chuẩn RBAC & Plugin
 
 
- Có 10 role: Superadmin, Admin, CTV, User, CSKH, Warehouse, Accountant, Marketing, CMS Editor, Reviewer
 
- Mỗi module đều check role + plugin bật/tắt
 
- Plugin tắt → API không load, frontend ẩn toàn bộ route/field liên quan
 

  
## 🧩 Các module/plugin
 
  
 
Nhóm
 
Module/plugin
 
   
 
Core
 
user, product, order, auth, address
 
 
 
Voucher
 
voucher-ref, voucher-birthday, manual
 
 
 
KPI
 
kpi-core, kpi-1, kpi-2, kpi-3, settlement
 
 
 
Loyalty
 
loyalty-core, loyalty-rank, redeem-core
 
 
 
CMS
 
cms-article, cms-policy, cms-kpi...
 
 
 
Hệ thống
 
plugin-manager, export-log, rollback, queue
 
  
  
## 🆔 UID & CODE
 
  
 
Entity
 
UID field
 
Code hiển thị
 
   
 
Order
 
`order_uid`
 
`ORD-YYYYMMDD-XXXX`
 
 
 
Voucher-ref
 
`voucher_uid`
 
`VREF-<sessionUID>-<UUID>`
 
 
 
Export log
 
`export_uid`
 
UUID v7
 
 
 
KPI Log
 
`kpi_log_uid`
 
UUID v7 hoặc Snowflake
 
  
 
 
- Không nhập tay mã ngoài `voucher-manual`
 
- Mọi hành động đều log qua bảng `event_log`
 

  
## 🧪 Dev flow khuyến nghị
 
 
1. ✅ Bắt đầu module → trả lời checklist nghiệp vụ
 
2. 🧱 Viết backend: schema → service → controller → test
 
3. 🌐 Viết frontend: gọi API, render UI theo role/plugin
 
4. 🧪 Test case plugin off/on, RBAC, sinh UID/code
 
5. 🔁 Ghi log (audit), export, retry queue nếu cần
 

  
## 📚 License
 
MIT – Free for commercial & academic use.
