<div align="center">
  <br/>
  <h1>Bondarnh</h1>
  <h3>បណ្តាញ — Boundless Commerce</h3>
  <p>
    <strong>Khmer-first ERP for small and growing businesses in Cambodia</strong>
  </p>
  <br/>
  <p>
    <img src="https://img.shields.io/badge/React-19-61DAFB?logo=react" alt="React 19"/>
    <img src="https://img.shields.io/badge/Express-4-000000?logo=express" alt="Express 4"/>
    <img src="https://img.shields.io/badge/MongoDB-8-47A248?logo=mongodb" alt="MongoDB 8"/>
    <img src="https://img.shields.io/badge/Ant_Design-6-0170FE?logo=antdesign" alt="Ant Design 6"/>
    <img src="https://img.shields.io/badge/Tailwind-4-06B6D4?logo=tailwindcss" alt="Tailwind 4"/>
    <img src="https://img.shields.io/badge/i18n-KH%2FEN-FF6B6B" alt="Khmer + English"/>
  </p>
  <br/>
</div>

---

## What is Bondarnh?

Bondarnh is a **multi-business ERP platform** purpose-built for Cambodian small and medium enterprises. It replaces spreadsheets, paper receipts, and disconnected tools with one unified system — in Khmer and English.

A clothing retailer in Phnom Penh can run their POS, track inventory across two warehouses, manage staff, send invoices, handle Bakong KHQR payments, and let customers order via QR code — all from one account.

---

## Why Bondarnh?

| Problem | Solution |
|---|---|
| No Khmer-first ERP on the market | Full Khmer (KM) interface + English toggle |
| Running 5 separate tools for POS, inventory, accounting, HR, tax | One platform, one login |
| Paper receipts and manual bookkeeping | Digital POS with 80mm thermal printing + auto journal entries |
| Customers wait to order | QR code menu → customer self-orders from phone |
| No Bakong/ABA integration built-in | Native Bakong KHQR + ABA PayWay |
| Staff permissions are a nightmare | Granular role-based access per business |

---

## Who is it for?

- **Shop owners** — POS, inventory, customer management, sales reports
- **Restaurants & cafes** — QR menu ordering, table management, KHQR payment
- **Wholesalers** — Purchase orders, supplier management, multi-warehouse inventory
- **Accountants** — Chart of accounts, journal entries, trial balance, period closing
- **HR managers** — Employee records, attendance, leave, payroll
- **Business owners with multiple locations** — Each branch/business under one account with separate staff and permissions

---

## Modules

### POS Terminal
80mm thermal receipt printing · Cash / KHQR / ABA / credit payment · Order hold & recall · Refund & return · Daily sales report · Multi-currency (USD / KHR)

### Customer QR Self-Ordering
Generate menu QR code · Customer scans with phone · Browse menu, customize extras · Self check-out with Bakong KHQR · Order status tracking · Cancellation requests

### Inventory
Multi-warehouse · Stock transfers between locations · Stock adjustments · Cycle counts · Low-stock alerts · Reorder suggestions · Shipping management

### Accounting
Chart of accounts · Journal entries · General ledger · Trial balance · Account mapping · Period closing · Auto-posting from POS and invoices

### Invoicing
Professional PDF invoices · Recurring invoices (daily/weekly/monthly) · Credit notes · Payment tracking · Overdue invoice monitoring · Email invoices

### HR & Payroll
Employee database · Departments · Attendance tracking · Leave management · Payroll processing · KPI tracking

### Tax
VAT output (sales tax) · VAT input (purchase tax) · Withholding tax · Monthly filing reports

### Finance
Budgeting · Cash flow management · Bank reconciliation · Expense tracking

### Supplier & Purchasing
Supplier database · Purchase orders · Goods receipt · Expenses · Supplier returns & credits · Payment tracking

### Social Platform
Business feed · Video posts · Marketplace · Community engagement

---

## Tech Stack

```
Frontend            Backend             Database
─────────           ─────────           ─────────
React 19            Node.js 18+        MongoDB 8
Vite 8              Express 4          Mongoose 8
Ant Design 6        JWT (jsonwebtoken)
Tailwind CSS 4      bcrypt (12 rounds)
Redux Toolkit       Multer (uploads)
React Query         Nodemailer
React Router 7      PDFKit
React Hook Form     node-cron
Zustand             Pino (logging)
Leaflet / OSM       Swagger
                     Jest + Supertest
                     mongodb-memory-server
```

### Payment Gateways

| Gateway | Type | Integration |
|---|---|---|
| **Bakong KHQR** | QR scan & pay | NBC Cambodia — individual & merchant QR |
| **ABA PayWay** | Online KHQR | ABA Bank — merchant API |

---

## Getting Started

```bash
# Backend
cd backend
cp .env.example .env     # Set your MongoDB URI + JWT secrets
npm install
npm run serve            # http://localhost:5000

# Frontend
cd frontend
cp .env.example .env
npm install
npm run dev              # http://localhost:3000
```

API docs: http://localhost:5000/api-docs

---

## Screenshots (placeholder)

_Replace with actual screenshots of:_

| | |
|---|---|
| POS Terminal | Invoice PDF |
| Customer QR Menu | Inventory Dashboard |
| Accounting — Journal Entry | HR — Employee List |
| Social Feed | KHQR Payment |

---

## Design Philosophy

> **Trustworthy but warm**

Institutional blue (`#1a5fa8`) carries trust and drives every primary action. Warm amber (`#E8A020`) is the brand accent — focus states, highlights, logo energy. A calm slate/white neutral base keeps dense data screens legible.

The personality: dependable for back-office modules that hold a business's money and books, yet welcoming for shop owners and staff who aren't accountants.

See [`DESIGN.md`](./DESIGN.md) for the full design token system.

---

## Security

- Passwords hashed with bcrypt (12 salt rounds)
- JWT access tokens (7d) + refresh tokens (30d)
- Business-scoped data isolation — every query is scoped to `req.businessId`
- Role-based access control — feature-level permissions per user type
- Rate limiting in production (per-user buckets)
- Helmet HTTP headers
- CORS locked to configured origins in production
- File uploads stored outside web root

---

## The Name

**Bondarnh** (បណ្តាញ) means *network* in Khmer — reflecting the vision of connecting Cambodian businesses on one platform.

---

## Contributing

See [`CONTRIBUTE.md`](./backend/CONTRIBUTE.md) for branch naming, commit conventions, and PR workflow.

```text
feat(ERP-142): add product export to Excel
fix(ERP-148): resolve token refresh infinite loop
docs(ERP-155): update environment variable guide
```

---

<div align="center">
  <br/>
  <p>
    <strong>Bondarnh</strong> — បណ្តាញ Network Commerce<br/>
    <sub>Built for Cambodia. Built for connection.</sub>
  </p>
  <br/>
</div>
