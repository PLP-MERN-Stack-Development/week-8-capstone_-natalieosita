# ⚖️ LawBridge

**Kenya’s Legal Case Access Platform** — LawBridge is a secure, full-stack MERN application designed to help users create, view, and manage legal cases, built for clarity, accessibility, and deployment readiness. It features authentication, theming, routing, responsive UI, and is hosted with CI/CD workflows on Vercel and Render.

---

## 🚀 Tech Stack Overview

| Layer       | Technology                          |
|-------------|--------------------------------------|
| Frontend    | React (JSX), React Query, Axios      |
| Styling     | Styled-Components, ThemeProvider     |
| Backend     | Express.js, Node.js                  |
| Database    | MongoDB Atlas                        |
| Auth        | JWT                                  |
| Deployment  | Vercel (client) + Render (server)    |
| DevOps      | GitHub Actions (CI/CD)               |
| Monitoring  | Render Healthchecks, Sentry-ready    |
| Testing     | Jest, Supertest, Testing Library     |

---

## 🗂️ Folder Structure

```
lawbridge/
├── client/
│   ├── src/
│   │   ├── api/          # Axios client & React Query hooks
│   │   ├── components/   # UI components & Theme toggle
│   │   ├── pages/        # Routed views
│   │   ├── styles/       # global.js, theme.js
│   │   ├── utils/        # token/auth helpers
│   │   └── __tests__/    # Frontend unit tests
│   ├── public/           # Static assets
│   └── vercel.json       # Vercel config
│
├── server/
│   ├── controllers/      # Logic per route
│   ├── models/           # MongoDB schemas
│   ├── routes/           # Express endpoints
│   ├── middleware/       # Auth, validation
│   ├── tests/            # Backend test suite
│   └── render.yaml       # Render deployment config
│
└── .github/
    └── workflows/        # CI/CD pipelines
```

---

## 📚 Features

- 🔐 JWT Authentication & Protected Routes
- 🎨 Light/Dark Mode Toggle (Header)
- 💾 Theme Persistence via `localStorage`
- 🧠 System Theme Detection (`matchMedia`)
- 🚦 Health Check Endpoint (`/health`)
- ⚡ React Query + Axios Data Fetching
- 🧪 Test Scaffolding (frontend/backend)
- 🛠 CI/CD: GitHub Actions → Vercel & Render
- 📑 Deployment-Ready Environment Handling
- 🌍 Responsive Design

---

## 🧠 Technical Architecture

```text
                      ┌──────────────┐
                      │ MongoDB Atlas│
                      └─────┬────────┘
                            │
                     ┌──────▼───────┐
                     │ Express Server│
                     │ /auth /cases  │
                     └──────┬────────┘
                            │ JWT
                            ▼
┌────────────────────────────────────────────────────────┐
│ React Frontend (Vercel)                                │
│ - Protected Routes: /dashboard, /cases                 │
│ - Theme Toggle + System Detection                      │
│ - Axios + React Query integration                      │
│ - Styled Components w/ ThemeProvider                   │
└────────────────────────────────────────────────────────┘
```

---

## 🧰 Setup Instructions

### 🖥 Local Dev

```bash
git clone https://github.com/your-org/lawbridge.git

# Backend
cd server
cp .env.example .env
npm install
npm run dev

# Frontend
cd ../client
cp .env.local.example .env.local
npm install
npm start
```

### 🔐 `.env` Files

#### `client/.env.local`

```env
REACT_APP_API_URL=https://lawbridge-api.onrender.com
```

#### `server/.env`

```env
MONGO_URI=your-mongodb-uri
JWT_SECRET=your-secret
PORT=5000
NODE_ENV=production
```

---

## 🧪 Testing

### ✅ Frontend: `__tests__/`

- `Header.test.js`: checks navigation rendering
- Use Jest + @testing-library/react

### ✅ Backend: `tests/`

- `auth.test.js`: register/login flow
- Use Jest + Supertest

Run with:

```bash
npm test
```

---

## 🌐 API Reference

| Method | Endpoint           | Description              | Auth |
|--------|--------------------|--------------------------|------|
| POST   | `/auth/register`   | Create new user          | ❌   |
| POST   | `/auth/login`      | Login existing user      | ❌   |
| GET    | `/cases`           | Retrieve user cases      | ✅   |
| POST   | `/cases`           | Submit new case          | ✅   |
| GET    | `/health`          | Check server status      | ❌   |

---

## 🧭 Deployment Strategy

### ✅ Vercel (Frontend)

- Root: `client/`
- `vercel.json`:

```json
{
  "buildCommand": "npm run build",
  "outputDirectory": "build",
  "framework": "create-react-app"
}
```

### ✅ Render (Backend)

- Uses `render.yaml`
- Health check: `/health`

### 🤖 GitHub Actions

- On push to `client/` → Trigger Vercel
- On push to `server/` → Trigger Render

```yaml
# frontend.yml
run: curl -X POST ${{ secrets.VERCEL_DEPLOY_HOOK }}

# backend.yml
run: curl -X POST ${{ secrets.RENDER_DEPLOY_HOOK }}
```

---

## 📜 User Guide

1. Visit `https://lawbridge.vercel.app`
2. Register and login
3. Access dashboard and submit cases
4. Use theme toggle to switch UI appearance
5. All data persists and is securely transmitted via JWT

---

## 🎓 Presentation Overview

| Slide | Content                                  |
|-------|-------------------------------------------|
| 🚀    | Title + Capstone Context                 |
| 🧩    | Problem Statement + Target Users         |
| 🛠️    | Stack: MERN + CI/CD + Axios + Theming    |
| 🎥    | Demo: case creation, login, theme toggle |
| ⚙️    | Challenges Overcome                      |
| 🧠    | Learnings & Next Steps                   |

---

## 📄 License & Attribution

This project is open-source for educational and portfolio purposes.  
Please credit LawBridge in any redistributed work.

---
