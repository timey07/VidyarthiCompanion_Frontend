<![CDATA[<div align="center">

# 🖥 VidyarthiCompanion — Frontend

### Next.js 16 Web Application for the Campus OS

[![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Zustand](https://img.shields.io/badge/Zustand-5-000000)](https://zustand-demo.pmnd.rs/)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [Pages & Routes](#-pages--routes)
- [Feature Modules](#-feature-modules)
- [Components](#-components)
- [State Management](#-state-management)
- [Scripts](#-scripts)

---

## 📖 Overview

The VidyarthiCompanion frontend is a modern, responsive web application built with **Next.js 16 (App Router)** and **React 19**. It serves as the student-facing interface for the Campus OS, presenting AI-generated insights, community interactions, and financial tracking through an intuitive **Zero-UI Action Card** paradigm — minimizing cognitive load while maximizing actionable information.

---

## 🛠 Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **Next.js** | 16.2.9 | App Router, SSR/CSR hybrid rendering |
| **React** | 19.2.4 | Component-based UI with latest concurrent features |
| **Tailwind CSS** | v4 | Utility-first styling with PostCSS integration |
| **Zustand** | 5.x | Lightweight, hook-based global state management |
| **Axios** | 1.x | HTTP client for backend API communication |
| **Lucide React** | 1.x | Beautiful, consistent icon library |

---

## 📁 Project Structure

```
VidyarthiCompanion-frontend/
├── public/                          # Static assets (icons, images)
├── src/
│   ├── app/                         # Next.js App Router pages
│   │   ├── layout.js                # Root layout with global providers
│   │   ├── page.jsx                 # Landing page (marketing / hero)
│   │   ├── globals.css              # Global styles & design tokens
│   │   ├── login/                   # Authentication — login page
│   │   ├── register/                # Authentication — registration page
│   │   ├── dashboard/               # Main dashboard — Today's Plan, Action Cards
│   │   ├── features/                # Feature detail pages (Override, Wellness, etc.)
│   │   ├── community/               # Community Graph — join/create nodes, consensus
│   │   ├── wallet/                  # PocketBuddy — transactions, budget tracking
│   │   ├── profile/                 # User profile & settings
│   │   └── settings/                # App settings & preferences
│   ├── components/                  # Shared, reusable UI components
│   │   ├── AppShell.jsx             # Authenticated layout shell (sidebar + header)
│   │   ├── AuroraBackground.jsx     # Animated aurora gradient background
│   │   ├── BrandLogo.jsx            # App logo component
│   │   ├── DailyTimeline.jsx        # Chronological daily event timeline
│   │   ├── MasterCalendar.jsx       # Full interactive calendar view
│   │   ├── Navigation.jsx           # Sidebar navigation component
│   │   ├── PageHeader.jsx           # Standard page header
│   │   ├── ScrollReveal.jsx         # Scroll-triggered animation wrapper
│   │   ├── ZeroUiActionCard.jsx     # Core Zero-UI Action Card component
│   │   ├── marketing/               # Landing page marketing sections
│   │   ├── overlays/                # Modal & overlay components
│   │   └── ui/                      # Atomic UI primitives (buttons, inputs, etc.)
│   ├── features/                    # Feature-sliced business logic modules
│   │   ├── authEngine/              # Auth API calls & hooks
│   │   ├── communityEngine/         # Community graph interactions
│   │   ├── empathyMesh/             # Empathy Mesh & Safe-Skip logic
│   │   ├── overrideEngine/          # AI Override Engine (image upload, voting)
│   │   ├── pocketBuddy/             # PocketBuddy financial tracking
│   │   ├── presenceEngine/          # Geo-presence & campus location
│   │   ├── profileEngine/           # User profile management
│   │   ├── retrievalEngine/         # Ground-truth retrieval queries
│   │   ├── routineEngine/           # Dynamic Baseline Routine
│   │   ├── transitEngine/           # Transit departure alerts
│   │   └── wellnessTracker/         # Wellness & lifestyle tracking
│   ├── lib/                         # Utility functions & shared helpers
│   └── routineState/                # Zustand stores for routine state
├── .env.example                     # Environment variable template
├── eslint.config.mjs                # ESLint configuration
├── jsconfig.json                    # JS path aliasing
├── next.config.mjs                  # Next.js configuration
├── postcss.config.mjs               # PostCSS + Tailwind setup
├── package.json                     # Dependencies & scripts
└── README.md                        # ← You are here
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** ≥ 18
- **npm** (comes with Node.js)
- Backend server running (see [backend README](../VidyarthiCompanion-backend/README.md))

### Installation

```bash
# Navigate to the frontend directory
cd VidyarthiCompanion-frontend

# Install dependencies
npm install

# Create your environment file
cp .env.example .env.local

# Start the development server
npm run dev
```

The app will be available at **http://localhost:3000**.

---

## 🔐 Environment Variables

Create a `.env.local` file by copying `.env.example`:

```env
# Base URL for the VidyarthiCompanion backend API
NEXT_PUBLIC_API_BASE_URL=http://localhost:5000/api/v1
```

| Variable | Required | Description |
|----------|----------|-------------|
| `NEXT_PUBLIC_API_BASE_URL` | ✅ | The base URL of the backend REST API. All Axios calls are prefixed with this. |

---

## 🗺 Pages & Routes

| Route | Page | Description |
|-------|------|-------------|
| `/` | Landing Page | Marketing hero page with feature showcase & scroll animations |
| `/login` | Login | Email/password authentication |
| `/register` | Register | New user registration with college details |
| `/dashboard` | Dashboard | Today's Plan, Zero-UI Action Cards, daily timeline, calendar |
| `/features` | Features | Detailed feature exploration (Override Engine, Wellness, etc.) |
| `/community` | Community | Join/create community nodes, consensus ticker, alerts |
| `/wallet` | Wallet | PocketBuddy — add transactions (image/text), history, budget insights |
| `/profile` | Profile | User profile, attendance ledger, empathy circle management |
| `/settings` | Settings | App preferences and notification settings |

---

## 🧩 Feature Modules

Each feature module under `src/features/` follows a consistent pattern:

```
featureName/
├── featureApi.js      # Axios API calls to backend endpoints
├── featureStore.js    # Zustand store (if needed)
└── featureHooks.js    # Custom React hooks (if needed)
```

| Module | Backend Endpoint | Description |
|--------|------------------|-------------|
| `authEngine` | `/api/v1/auth` | Login, register, token refresh, get current user |
| `communityEngine` | `/api/v1/community` | CRUD community nodes, join by code, manage memberships |
| `empathyMesh` | `/api/v1/empathy` | Safe-Skip calculation, empathy circle nudges |
| `overrideEngine` | `/api/v1/overrides` | Upload images for AI extraction, consensus voting |
| `pocketBuddy` | `/api/v1/pocket` | Add/list transactions, budget recommendations |
| `presenceEngine` | `/api/v1/presence` | Campus geo-presence, check-in |
| `profileEngine` | `/api/v1/profile` | Profile CRUD, attendance buffer |
| `retrievalEngine` | `/api/v1/retrieval` | Ground-truth Q&A retrieval |
| `routineEngine` | `/api/v1/routine` | Baseline routine CRUD, recalculation |
| `transitEngine` | `/api/v1/transit` | Departure ETA alerts |
| `wellnessTracker` | `/api/v1/wellness` | Lifestyle logs, burnout score |

---

## 🧱 Components

### Core Components

| Component | Description |
|-----------|-------------|
| `AppShell` | Authenticated page wrapper with sidebar navigation and header |
| `ZeroUiActionCard` | The flagship card UI — renders AI-generated, single-tap action items |
| `MasterCalendar` | Full interactive calendar with event dots, day view, and filtering |
| `DailyTimeline` | Chronological vertical timeline of today's events and tasks |
| `Navigation` | Sidebar with route links, user info, and logout |

### UI Primitives

Located in `src/components/ui/` — reusable atomic elements like buttons, inputs, modals, and badges.

### Marketing Components

Located in `src/components/marketing/` — hero sections, feature showcases, and testimonial blocks for the landing page.

---

## 🗃 State Management

**Zustand** is used for lightweight, hook-based global state:

- **Auth State** — Current user, JWT token, login status
- **Routine State** — Located in `src/routineState/`, manages the dynamic baseline routine and action card queue

```jsx
// Example usage
import { useAuthStore } from '@/features/authEngine/authStore';

function Dashboard() {
  const user = useAuthStore((state) => state.user);
  // ...
}
```

---

## 📜 Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build optimized production bundle |
| `npm start` | Serve the production build |
| `npm run lint` | Run ESLint checks |

---

<div align="center">

**Part of the [VidyarthiCompanion](../README.md) Campus OS**

*Built by Team QuantYap for HackOn with Amazon 2026*

</div>
]]>
