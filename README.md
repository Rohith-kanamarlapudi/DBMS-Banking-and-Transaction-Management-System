<div align="center">

# 🏦 Financial Account & Transaction Management System

**A full-stack banking platform for managing accounts, transactions, and secure authentication.**

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)

</div>


## 📌 Overview

A production-ready banking application with a **Node.js/Express REST API** backend, a **React + Vite** frontend, and a **relational SQL** database. Built to handle user registration, secure authentication, multi-account management, and real-time transaction processing.

---

## ✨ Features

- 🔐 **Secure Authentication** — JWT-based login & registration with bcrypt password hashing
- 🏦 **Account Management** — Create and manage multiple account types (savings, current, etc.)
- 💸 **Transaction Processing** — Debit/credit operations with balance tracking and history
- 🛡️ **Middleware Layer** — Request validation, auth guards, and centralized error handling
- ⚡ **Fast Frontend** — Vite-powered React SPA with hot module reload
- 🗄️ **Structured Schema** — Normalized SQL schema with stored procedures and constraints

---

## 🗂️ Project Structure

```
financial-account-and-transaction-management/
│
├── 📂 backend/
│   ├── config/          # DB connection, env config
│   ├── middleware/       # Auth guards, validators, error handlers
│   ├── routes/           # Express route definitions
│   ├── sql/              # Schema & seed SQL files
│   ├── utils/            # Helper functions
│   ├── .env              # Environment variables
│   ├── package.json
│   └── server.js         # App entry point
│
├── 📂 banking-frontend/
│   ├── src/              # React components, pages, hooks
│   ├── public/           # Static assets
│   ├── dist/             # Production build (auto-generated)
│   ├── .env              # Frontend environment variables
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
│
└── auth_schema.sql       # Auth tables (users, sessions)
```

---

## 🛠️ Tech Stack

| Layer       | Technology                          |
|-------------|-------------------------------------|
| **Frontend**  | React 18, Vite, ESLint             |
| **Backend**   | Node.js, Express.js                |
| **Database**  | MySQL / PostgreSQL                 |
| **Auth**      | JWT, bcrypt                        |
| **Dev Tools** | Nodemon, dotenv, ESLint            |

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [npm](https://www.npmjs.com/) v9+
- MySQL or PostgreSQL (local or cloud)

---

### 1️⃣ Database Setup

```bash
# Run the authentication schema first
mysql -u root -p < auth_schema.sql

# Then apply backend-specific schemas
mysql -u root -p < backend/sql/<schema_file>.sql
```

---

### 2️⃣ Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file inside `backend/`:

```env
PORT=5000
DB_HOST=localhost
DB_PORT=3306
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=banking_db
JWT_SECRET=your_super_secret_key
```

Start the server:

```bash
# Development (hot reload)
npx nodemon server.js

# Production
node server.js
```

> API runs at `http://localhost:5000`

---

### 3️⃣ Frontend Setup

```bash
cd banking-frontend
npm install
```

Create a `.env` file inside `banking-frontend/`:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

Start the dev server:

```bash
npm run dev
```

> App runs at `http://localhost:5173`

Build for production:

```bash
npm run build    # Output → dist/
```

---

## 🔌 API Reference

### Auth

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Login and receive JWT token |

### Accounts

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/accounts` | Get all accounts for the logged-in user |
| `POST` | `/api/accounts` | Create a new account |
| `GET` | `/api/accounts/:id` | Get a specific account's details |
| `DELETE` | `/api/accounts/:id` | Close/delete an account |

### Transactions

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/transactions/:accountId` | Get transaction history for an account |
| `POST` | `/api/transactions` | Create a debit or credit transaction |
| `GET` | `/api/transactions/:id` | Get a single transaction by ID |

> 🔒 All `/accounts` and `/transactions` endpoints require a valid `Authorization: Bearer <token>` header.

---

## 🗄️ Database Schema

### Core Tables

```
users           → id, name, email, password_hash, created_at
accounts        → id, user_id (FK), account_type, balance, created_at
transactions    → id, account_id (FK), type (DEBIT/CREDIT), amount, balance_after, timestamp
```

- **`auth_schema.sql`** — handles users and session/token management
- **`backend/sql/`** — contains accounts, transactions, and any stored procedures

---

## 🔒 Security Highlights

- ✅ Passwords hashed with **bcrypt** before storage
- ✅ Routes protected with **JWT middleware**
- ✅ All SQL queries use **parameterized statements** (no SQL injection risk)
- ✅ **CORS** configured to restrict cross-origin access
- ✅ `.env` files excluded from version control via `.gitignore`

---

## 📦 Deployment

### Backend
Deploy to [Railway](https://railway.app), [Render](https://render.com), or any Node.js host.  
Set all `.env` variables as environment secrets in the dashboard.

### Frontend
```bash
cd banking-frontend && npm run build
```
Deploy the `dist/` folder to [Vercel](https://vercel.com), [Netlify](https://netlify.com), or Nginx.

### Database
Use a managed SQL service like [PlanetScale](https://planetscale.com), [Supabase](https://supabase.com), or AWS RDS.  
Update `DB_*` env vars accordingly.

🗂️ Project Structure

## 🤝 Contributing

Contributions are welcome!

```bash
# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feat/your-feature-name

# 3. Commit your changes
git commit -m "feat: describe your change"

# 4. Push and open a Pull Request
git push origin feat/your-feature-name
```

Please follow the existing code style and keep commits clean.




<div align="center">

Made with ❤️ by [Rohith Kanamarlapudi](https://github.com/rohithkanamarlapudi)

</div>
