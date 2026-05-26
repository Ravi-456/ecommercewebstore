

#High-Performance Animated Full-Stack E-Commerce Platform

A production-grade, highly responsive, full-stack e-commerce experience built using **Next.js 14+ (App Router)**, **Framer Motion**, **Tailwind CSS**, and **Zustand**. This application features fluid, GPU-accelerated micro-interactions, an animated cart drawer, structural multi-step validation flows, and a hardened backend API pipeline integrated with automated transactional email alerts.

---

## 🚀 Key Architectural Features

### 1. Advanced Animation Architecture (Framer Motion)
* **GPU-Accelerated Micro-Interactions:** Smooth scale, translation, and opacity animations that offload workloads to the GPU, preventing layout thrashing and preserving excellent **Core Web Vitals**.
* **Staggered Orchestration:** Sequential layout reveals using stagger parameters across catalog entries, card components, and text items.
* **Layout Isolation:** Uses `AnimatePresence` for unmounting states (e.g., Cart Drawer panel sliding out, validation modal clean-ups).
* **Scroll-Triggered Reveals:** Viewport intersection observers triggering keyframes conditionally with configured offsets.

### 2. State Engineering & Local Persistence
* Managed using a lightweight, reactive state store via **Zustand**.
* Built-in atomic mutations for additions, quantities updates, and item removal.
* Out-of-the-box hydration sync via middleware utilizing internal storage channels (`localStorage`) for real-time session recovery.

### 3. Hardened Server Pipeline & Form Lifecycle
* Native Serverless API route handling within the Next.js runtime.
* Comprehensive structural request payload decoding and server-side syntax validation via specific regex engines.
* Abuse-mitigation structures through IP-based request logging mechanisms.
* **Dual Transactional Invoicing:** Concurrent asynchronous SMTP dispatch pipelines utilizing connection pooling models for instant user receipts and store notification triggers.

---

## 📂 Project Directory Structure

```text
├── src/
│   ├── app/
│   │   ├── layout.tsx             # Application core context & layout wrappers
│   │   ├── page.tsx               # Interactive multi-section landing page
│   │   ├── products/
│   │   │   └── [id]/              # High-performance SSR/ISR detail viewport
│   │   ├── checkout/              # Interactive validation entry page
│   │   ├── confirmation/          # Celebrate checkout landing UI view
│   │   └── api/
│   │       ├── products/          # GET - Catalog parsing & querying endpoints
│   │       └── orders/            # POST - Hardened processing & validation node
│   ├── components/
│   │   ├── ui/                    # Reusable primitive operational buttons/inputs
│   │   │   ├── Button.tsx
│   │   │   ├── Input.tsx
│   │   │   └── Badge.tsx
│   │   ├── cart/
│   │   │   ├── CartDrawer.tsx     # Sliding context side panel wrapper
│   │   │   └── CartItem.tsx       # Dynamic incremental adjustment element
│   │   └── checkout/
│   │       └── CheckoutForm.tsx   # Transaction form structure
│   ├── context/
│   │   └── store.ts               # Global state store slice
│   └── utils/
│       └── animations.ts          # Orchestrated configuration variants repository
├── public/                        # Optimized compressed asset inventory
├── .env.example                   # Environment variable template
├── package.json                   # Build dependency profile
└── tailwind.config.js             # Atomic UI utility configurations
```

---

## 🛠️ Setup & Local Configuration

### 1. Clone & Install Dependencies

```bash
git clone https://github.com/your-organization/animated-commerce.git
cd animated-commerce
npm install
```

### 2. Environment Variables

```bash
cp .env.example .env.local
```

Open `.env.local` and configure:

```env
# Database
MONGODB_URI=mongodb+srv://<db_user>:<db_password>@cluster0.mongodb.net/store_db?retryWrites=true&w=majority

# SMTP
SMTP_HOST=smtp.resend.com
SMTP_PORT=465
SMTP_USER=resend
SMTP_PASS=re_prod_secret_token_12345

# Notifications
STORE_OWNER_EMAIL=merchant-operations@yourdomain.com

# Base URL
NEXT_PUBLIC_BASE_URL=http://localhost:3000
```

### 3. Database Seeding

```bash
npm run db:seed
```

### 4. Run Development Server

```bash
npm run dev
```

Navigate to `http://localhost:3000`.

---

## 📦 Production Deployment

1. Push your code to GitHub, GitLab, or Bitbucket.
2. Import the project in **Vercel** or **Railway** and link your repository.
3. Add all variables from `.env.local` under the **Environment Variables** tab.
4. Trigger a deployment — the platform runs the build pipeline automatically:

```bash
npm run build
```

---

## 🔒 Security & Performance

* **Input Sanitization:** API handlers escape incoming strings before database operations, mitigating NoSQL/SQL injection vectors.
* **Component Lazy-Loading:** Images use `next/image`, serving `WebP`/`AVIF` formats with dynamic source sets and base64 blur placeholders.
* **Keyboard Accessibility / ARIA:** All interactive elements include `aria-expanded`, `role="dialog"`, and `aria-label`. Full keyboard tab-order support throughout.
```
