🏦 Financial Account & Transaction Management System

A full-stack banking platform for managing accounts, transactions, and secure authentication.
📌 Overview

A production-ready banking application with a Node.js/Express REST API backend, a React + Vite frontend, and a relational SQL database. Built to handle user registration, secure authentication, multi-account management, and real-time transaction processing.


✨ Features


🔐 Secure Authentication — JWT-based login & registration with bcrypt password hashing
🏦 Account Management — Create and manage multiple account types (savings, current, etc.)
💸 Transaction Processing — Debit/credit operations with balance tracking and history
🛡️ Middleware Layer — Request validation, auth guards, and centralized error handling
⚡ Fast Frontend — Vite-powered React SPA with hot module reload
🗄️ Structured Schema — Normalized SQL schema with stored procedures and constraints



🗂️ Project Structure

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


🛠️ Tech Stack

LayerTechnologyFrontendReact 18, Vite, ESLintBackendNode.js, Express.jsDatabaseMySQL / PostgreSQLAuthJWT, bcryptDev ToolsNodemon, dotenv, ESLint


🚀 Getting Started

Prerequisites


Node.js v18+
npm v9+
MySQL or PostgreSQL (local or cloud)



1️⃣ Database Setup

bash# Run the authentication schema first
mysql -u root -p < auth_schema.sql

# Then apply backend-specific schemas
mysql -u root -p < backend/sql/<schema_file>.sql


2️⃣ Backend Setup

bashcd backend
npm install

Create a .env file inside backend/:

envPORT=5000
DB_HOST=localhost
DB_PORT=3306
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=banking_db
JWT_SECRET=your_super_secret_key

Start the server:

bash# Development (hot reload)
npx nodemon server.js

# Production
node server.js


API runs at http://localhost:5000




3️⃣ Frontend Setup

bashcd banking-frontend
npm install

Create a .env file inside banking-frontend/:

envVITE_API_BASE_URL=http://localhost:5000/api

Start the dev server:

bashnpm run dev


App runs at http://localhost:5173



Build for production:

bashnpm run build    # Output → dist/


🔌 API Reference

Auth

MethodEndpointDescriptionPOST/api/auth/registerRegister a new userPOST/api/auth/loginLogin and receive JWT token

Accounts

MethodEndpointDescriptionGET/api/accountsGet all accounts for the logged-in userPOST/api/accountsCreate a new accountGET/api/accounts/:idGet a specific account's detailsDELETE/api/accounts/:idClose/delete an account

Transactions

MethodEndpointDescriptionGET/api/transactions/:accountIdGet transaction history for an accountPOST/api/transactionsCreate a debit or credit transactionGET/api/transactions/:idGet a single transaction by ID


🔒 All /accounts and /transactions endpoints require a valid Authorization: Bearer <token> header.




🗄️ Database Schema

Core Tables

users           → id, name, email, password_hash, created_at
accounts        → id, user_id (FK), account_type, balance, created_at
transactions    → id, account_id (FK), type (DEBIT/CREDIT), amount, balance_after, timestamp


auth_schema.sql — handles users and session/token management
backend/sql/ — contains accounts, transactions, and any stored procedures



🔒 Security Highlights


✅ Passwords hashed with bcrypt before storage
✅ Routes protected with JWT middleware
✅ All SQL queries use parameterized statements (no SQL injection risk)
✅ CORS configured to restrict cross-origin access
✅ .env files excluded from version control via .gitignore



📦 Deployment

Backend

Deploy to Railway, Render, or any Node.js host.

Set all .env variables as environment secrets in the dashboard.

Frontend

bashcd banking-frontend && npm run build

Deploy the dist/ folder to Vercel, Netlify, or Nginx.

Database

Use a managed SQL service like PlanetScale, Supabase, or AWS RDS.

Update DB_* env vars accordingly.


🤝 Contributing

Contributions are welcome!

bash# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feat/your-feature-name

# 3. Commit your changes
git commit -m "feat: describe your change"

# 4. Push and open a Pull Request
git push origin feat/your-feature-name

Please follow the existing code style and keep commits clean.
