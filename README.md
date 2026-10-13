# 🌿 Climate CRM

A full-featured CRM built for **sustainability and climate consulting firms**. Manage your sales pipeline, cost sheets, project delivery, team timesheets, and KPI dashboards — all in one place.

> **No install. No server. Just open `index.html`.**

---

## ✨ Features

| Module | What it does |
|---|---|
| **Dashboard / KPI** | Revenue, pipeline, won-value donut chart, monthly KPI splits |
| **Customers** | Company profiles, multi-contact management, activity log with @mentions, tags |
| **Opportunities** | Pipeline (Kanban + Table), quotation builder, PDF export, cost sheet linking |
| **Cost Sheet** | Service cost builder — COGS + OPEX tasks by staff level, margin calculator |
| **Delivery** | Project delivery tracking, installment schedule, work log |
| **Time Sheet** | Staff timesheet with planned vs. actual cost |
| **Team & Rates** | User management, role-based access, man-hour rate configuration |
| **Setup** | Connect your own Google Sheets backend with one URL paste |

---

## 🚀 Getting Started

### Option A — Run Locally (no setup needed)

1. Download or clone this repository
2. Open `index.html` in any browser
3. Log in with the demo credentials below

That's it. All data is saved in your browser's localStorage.

### Option B — GitHub Pages

Push to any GitHub repo, enable **Pages** from the `main` branch root, and share the URL.

---

## 🔐 Demo Login Credentials

| Email | Password | Role |
|---|---|---|
| `admin@demo.com` | `demo1234` | Admin (full access) |
| `alice@demo.com` | `demo1234` | Sales |
| `bob@demo.com` | `demo1234` | Manager |
| `carol@demo.com` | `demo1234` | Operation |

> **Note:** In offline/demo mode, any password is accepted — just enter the email and type anything in the password field.

---

## ☁️ Connect Your Own Google Sheets (Optional)

To sync data across a real team, connect your own Google Apps Script backend:

### Step 1 — Create a Google Sheet

Create a new Google Sheet with the following tab names (exact):

```
customers   opportunities   deliveries   costsheets   costsheet_quotes
kpi         users           timesheet    notifications   settings
```

### Step 2 — Add the Apps Script Backend

1. In your Google Sheet, open **Extensions → Apps Script**
2. Paste your GAS backend code (the script handles all read/write/delete operations)
3. In **Project Settings → Script Properties**, add:
   - Key: `AUTH_SECRET`
   - Value: any secret string (e.g. `my-secret-token-2025`)

### Step 3 — Deploy as a Web App

1. Click **Deploy → New Deployment**
2. Type: **Web App**
3. Execute as: **Me**
4. Who has access: **Anyone**
5. Copy the deployment URL

### Step 4 — Connect in the App

1. Open the app → click the **plug icon** (⬆) in the top-right header
2. Paste your **Deployment URL** and **Auth Token**
3. Click **Test Connection** to verify
4. Click **Save & Activate**, then refresh the page

✅ The app will now sync all data to your Google Sheets in real time.

---

## 🛠 Tech Stack

| | |
|---|---|
| **Frontend** | React 18 (via CDN — no bundler) |
| **JSX Transform** | Babel Standalone (browser-side) |
| **Styling** | Vanilla CSS (inline + injected stylesheets) |
| **Storage** | `localStorage` (offline) + Google Apps Script (optional sync) |
| **Charts** | Hand-rolled SVG — no charting library |
| **Backend** | Google Apps Script (bring your own) |

No `npm install`. No build step. No framework. Just open the HTML file.

---

## 🌍 Internationalization

The app includes:
- **Thai language** UI labels and company names
- **Buddhist Era (BE)** date formatting (e.g. 2569 instead of 2026)
- **Thai month abbreviations** (ม.ค., ก.พ., …)
- **THB currency** formatting (฿)

---

## 📁 Project Structure

```
Climate_crm-main/
├── index.html        ← Entry point (load React + Babel from CDN, mount app)
└── src/
    └── App.jsx       ← Entire application (~7,500 lines, single file)
```

---

## 🔄 How Data Works

```
Open index.html
      │
      ▼
  GS URL configured?
  (saved in browser localStorage)
      │
   ┌──┴─────────────────────────┐
  NO (demo mode)              YES (live mode)
   │                            │
   ▼                            ▼
localStorage only          Sync with your
Demo data preloaded        Google Sheets
Any login works            Team credentials required
```

---

## 📋 Services Supported

The CRM is pre-configured for these climate/sustainability service codes:

| Code | Service |
|---|---|
| CFO | Carbon Footprint for Organization |
| CFP | Carbon Footprint of Product |
| ISO14064 | ISO 14064-1 Verification |
| ISO14067 | ISO 14067 Verification |
| CNE | Carbon Neutral Event |
| DR | Decarbonization Roadmap |
| TRN | Training / Workshop |
| GSTC | Global Sustainable Tourism Council |
| GH / GHP | Green Hotel / Green Hotel Plus |
| GC | Green Certificate |
| CSRDIW | CSR-DIW |
| CCAWD | Alternate Wetting & Drying |
| CCREF | Reforestation |
| LCR | Low-Carbon Rice |
| CC | Carbon Credit |
| REC | Renewable Energy Certificate |
| DRO&GIS | Drone + GIS Survey |
| OTH | Other Service |

---

## 🧑‍💻 Role-Based Access

| Role | Dashboard | Customers | Opportunities | Delivery | Cost Sheet | Timesheet | Team & Rates |
|---|---|---|---|---|---|---|---|
| Admin | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Manager | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Sales | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Operation | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |

---

## 📄 License

MIT — free to use, modify, and deploy.

---

*Built with React 18, Babel Standalone, and Google Apps Script.*
