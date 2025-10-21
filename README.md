# 🧾 Accounting Panel

> A modern accounting panel built with Next.js, React, TypeScript, React Hook Form, Axios, Tailwind CSS and SQL Server.

![stack-badge](https://img.shields.io/badge/stack-Next.js%20|%20React%20|%20TypeScript-blue) 

![license-badge](https://img.shields.io/badge/license-MIT-green)

---

## 🔖 Project Overview

This project is a responsive, secure accounting panel (dashboard) that helps businesses manage invoices, transactions, customers, and reports. The frontend is built with **Next.js (React + TypeScript)** and styled with **Tailwind CSS**. Forms use **React Hook Form** and HTTP requests use **Axios**. The backend (API) uses a server-side approach and persists data to **SQL Server**.

> Designed for maintainability and developer experience: typed code, modular components, and a clear folder structure.

---

## 🚀 Key Features

* Authentication & authorization (JWT / session-based — adapt to your security flow)
* CRUD for Customers, Invoices, Payments, Accounts, and Transactions
* Form validation and user-friendly error handling with **React Hook Form**
* API communication with **Axios** (interceptors for auth and error handling)
* Responsive UI with **Tailwind CSS** and utility classes
* Reports and charts (placeholder for charting library e.g., Recharts or Chart.js)
* Database: Microsoft SQL Server with migrations and seeding scripts
* Type-safe code with TypeScript and typed API responses

---

## 🧱 Tech Stack

* Frontend: **Next.js** (App Router or Pages Router depending on your setup)
* UI: **React** + **Tailwind CSS**
* Forms: **React Hook Form**
* HTTP: **Axios**
* Language: **TypeScript**
* Database: **Microsoft SQL Server**
* Others: ESLint, Prettier, Husky (optional)

---

## 📁 Recommended Folder Structure

```
├─ /app or /pages         # Next.js app or pages
│  ├─ /api                # Edge / serverless API routes (if used)
│  ├─ /components
│  ├─ /features           # domain folders (customers, invoices, auth...)
│  └─ /styles
├─ /lib                   # axios, helpers, auth utilities
├─ /server                # (optional) backend API if colocated
│  ├─ /migrations
│  └─ /db
├─ /scripts               # db seed/migrate scripts
├─ /prisma or /orm        # prisma schema or other ORM configs (optional)
├─ README.md
└─ package.json
```

---

## 💡 Setup & Local Development

### Prerequisites

* Node.js (>= 18)
* pnpm or npm or yarn
* SQL Server running locally or accessible remotely
* (Optional) `dotnet`/ORM tooling if backend uses .NET

### Install

``
        # from project root
        pnpm install
        # or
        npm install
        # or
        yarn
```

### Run the development server (frontend)

```
        # Frontend
        pnpm dev
        # or
        npm run dev
        # or
        yarn dev
```

### Run API / backend

If your API is colocated, start it (example):

```
        cd server
        pnpm dev
```

### Database

* Apply migrations (depends on your ORM/tooling). Example with Prisma:

```
    npx prisma migrate dev --name init
    npx prisma db seed
```

* Or run your SQL migration scripts in `./server/migrations` against your SQL Server instance.

---

## 🔐 Authentication (Suggested)

* Use JWT or NextAuth.js depending on project needs.
* Secure cookies with `HttpOnly`, `SameSite=Strict`, and `Secure` flags on production.
* Refresh tokens flow or short-lived access tokens recommended.

---

## 🧩 Axios: Recommended Setup

Create a single axios instance (`/lib/axios.ts`) with interceptors for attaching tokens and handling errors:

```ts
import axios from 'axios';

const api = axios.create({
  baseURL: process.env.NEXT_PUBLIC_API_BASE_URL,
  withCredentials: true,
});

api.interceptors.request.use(config => {
  // attach token if present
  // config.headers.Authorization = `Bearer ${token}`;
  return config;
});

api.interceptors.response.use(
  r => r,
  err => {
    // central error handling
    return Promise.reject(err);
  }
);

export default api;
```

---

## 🧪 Forms & Validation (React Hook Form)

* Use `useForm<T>()` with TypeScript generics for typed form values.
* Combine `zod` or `yup` for schema validation and use `@hookform/resolvers`.

Example:

```
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';

// define zod schema and type inference
```

---

## 📦 Example Scripts (package.json)

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint . --ext .ts,.tsx",
    "format": "prettier --write ."
  }
}
```

---

## 🔁 Recommended Conventions

* Keep components small and reusable.
* Organize by feature/domain (e.g., `/features/invoices`).
* Use TypeScript interfaces/types for all API payloads.
* Centralize API calls in `lib/api` or `features/*/api`.

---

## 📌 Deployment Tips

* Frontend: Vercel (easy for Next.js) or any static host + serverless API.
* Backend: Azure App Service / Azure SQL, AWS Elastic Beanstalk, DigitalOcean App Platform, or Docker container.
* Use CI/CD pipelines to run tests, lint, and deploy.
* Store secrets in environment variables or a secrets manager.

---

## ✅ Checklist Before Production

* [ ] HTTPS enforced
* [ ] Secure cookies & proper CORS
* [ ] Input validation & sanitization
* [ ] Rate limiting on APIs
* [ ] Backups for SQL Server
* [ ] Proper logging and monitoring

---

## 🤝 Contributing

🌻 Azadeh Sharifi Soltani

Feel free to contribute to this project by submitting a pull request or opening an issue! Made with 💻, ☕, and 🌻 by Azadeh Sharifi Soltani




