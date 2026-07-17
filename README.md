<div align="center">
  <br>
  <h1>Bondarnh ERP</h1>
  <p>
    <strong>Khmer-first, multi-business ERP with a social platform overlay</strong>
  </p>
  <p>
    POS · Inventory · Purchasing · Accounting · HR · Tax · Customer Self-Ordering
  </p>
  <br>
</div>

---

## Overview

Bondarnh is a full-stack ERP built for small and growing businesses in Cambodia. It combines back-office modules (POS, inventory, accounting, HR, tax, purchasing) with a customer-facing QR self-ordering system and a social feed layer.

| Stack | |
|---|---|
| **Frontend** | React 19, Vite 8, Ant Design 6, Tailwind CSS 4, Redux Toolkit |
| **Backend** | Node.js 18+ (ESM), Express 4, MongoDB 8 (Mongoose) |
| **Auth** | JWT (access + refresh tokens), bcrypt (12 rounds) |
| **Payments** | Bakong KHQR, ABA PayWay |
| **i18n** | Khmer + English |

---

## Quick Start

```bash
# 1. Backend
cd backend
cp .env.example .env          # Edit with your MongoDB URI + secrets
npm install
npm run serve                 # http://localhost:5000

# 2. Frontend (separate terminal)
cd frontend
cp .env.example .env
npm install
npm run dev                   # http://localhost:3000
```

The Vite dev server proxies `/api` and `/private` to the backend — no CORS issues locally.

---

## Project Structure

```
backend/                          frontend/
├── src/                          ├── src/
│   ├── config/                   │   ├── api/           # Axios modules
│   ├── controllers/              │   ├── store/         # Redux slices
│   ├── middleware/                │   ├── views/
│   │   ├── auth.js               │   │   ├── auth/      # Login, Register
│   │   ├── businessScope.js      │   │   ├── erp/       # All ERP modules
│   │   ├── roleCheck.js          │   │   ├── social/    # Feed, Videos, etc.
│   │   ├── validator.js          │   │   └── layout/    # ErpLayout, Sidebar
│   │   └── errorHandler.js       │   ├── routes/        # Router + guards
│   ├── models/                   │   ├── components/    # Shared UI
│   ├── routes/                   │   ├── constants/     # Enums, permissions
│   ├── services/                 │   └── utils/         # Helpers
│   │   ├── khqr.service.js       ├── vite.config.js
│   │   ├── abaPayway.service.js  └── package.json
│   │   ├── invoicePdf.service.js
│   │   └── email.service.js
│   ├── seeds/
│   └── utils/
├── private/          # Uploads
├── jest.config.js
└── package.json
```

---

## Environment Variables

### Backend (`backend/.env`)

| Variable | Required | Default | Description |
|---|---|---|---|
| `MONGODB_URI` | Yes | — | MongoDB connection string |
| `JWT_SECRET` | Yes | — | Access token signing key |
| `JWT_REFRESH_SECRET` | Yes | — | Refresh token signing key |
| `CLIENT_URL` | No | `http://localhost:3000` | CORS origin |
| `SMTP_HOST` | No | — | SMTP server |
| `SMTP_USER` | No | — | SMTP username |
| `SMTP_PASS` | No | — | SMTP password |
| `PORT` | No | `5000` | Server port |
| `NODE_ENV` | No | `development` | Environment |

Full list: see `backend/.env.example`.

### Frontend (`frontend/.env`)

| Variable | Description |
|---|---|
| `VITE_API_URL` | Backend URL (blank in dev — uses Vite proxy) |

---

## API

Swagger docs available at `http://localhost:5000/api-docs` when running.

- **Auth**: `POST /api/v1/auth/register`, `POST /api/v1/auth/login`, `POST /api/v1/auth/refresh`
- **Headers**: `Authorization: Bearer <token>`, `X-Business-Id: <shortId or code>`
- **Public**: `GET /api/v1/public/menu/:businessId`, `POST /api/v1/public/order`

---

## Key Features

- **Multi-business** — One account manages multiple businesses, each with its own staff, roles, and permissions
- **POS Terminal** — 80mm thermal receipt printing, multiple payment methods, order management
- **Customer QR Ordering** — Menu QR code → customer self-orders via phone → pays with Bakong KHQR
- **Inventory** — Multi-warehouse, stock transfers, adjustments, cycle counts, reorder alerts
- **Accounting** — Chart of accounts, journal entries, general ledger, trial balance, period closing
- **HR** — Employees, departments, attendance, leave, payroll
- **Tax** — VAT input/output, withholding tax, monthly filing reports
- **Invoicing** — PDF invoice generation, recurring invoices, credit notes, payment tracking
- **Finance** — Budgeting, cash flow management, bank reconciliation
- **Social** — Feed, videos, marketplace (social platform layer)
- **i18n** — Full Khmer (KM) and English (EN) support

---

## Testing

```bash
cd backend
npm test                 # Jest + Supertest (uses mongodb-memory-server)
npm run test:coverage
```

---

## Scripts

### Backend

| Command | Description |
|---|---|
| `npm run serve` | Dev with nodemon |
| `npm start` | Production start |
| `npm test` | Run tests |
| `npm run lint` | ESLint |
| `npm run format` | Prettier |

### Frontend

| Command | Description |
|---|---|
| `npm run dev` | Vite dev server |
| `npm run build` | Production build |
| `npm run lint` | ESLint |
| `npm run format` | Prettier |

---

## Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b feat/my-feature`
3. Run `npm run format && npm run lint` before committing (both backend and frontend)
4. Open a PR

Conventional commits preferred: `feat:`, `fix:`, `chore:`, `refactor:`, `docs:`.

---

## Design System

See [`DESIGN.md`](./DESIGN.md) for the full design language — colors, typography, spacing, and component tokens.

---

## Collaborators

- [phanphoun](https://github.com/phanphoun)
- [bondarnh26](https://github.com/bondarnh26)

---

## License

Private — all rights reserved.
