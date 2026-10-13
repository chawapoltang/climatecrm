# Climate CRM

Climate CRM is a CRM built for sustainability and climate consulting firms. It brings your sales pipeline, cost sheets, project delivery, timesheets, and KPI dashboards into one place, so your team doesn't have to juggle spreadsheets and disconnected tools.

There's nothing to install and no server to run. Open `index.html` and you're in.

---

## What's inside

| Module | What it does |
|---|---|
| **Dashboard / KPI** | See revenue, pipeline, and won value (as a donut chart), plus monthly KPI splits |
| **Customers** | Keep company profiles, manage multiple contacts, log activity with @mentions, and organize with tags |
| **Opportunities** | Track deals in a Kanban board or table, build quotations, export to PDF, and link cost sheets |
| **Cost Sheet** | Build service costs from COGS and OPEX tasks by staff level, and check your margins |
| **Delivery** | Follow project delivery, plan installment schedules, and keep a work log |
| **Time Sheet** | Record staff hours and compare planned cost against actual cost |
| **Team & Rates** | Manage users, set role-based access, and configure man-hour rates |
| **Setup** | Connect your own Google Sheets backend by pasting a single URL |

---

## Getting started

### Option A: Run it locally

1. Download or clone this repository.
2. Open `index.html` in any browser.
3. Log in with one of the demo accounts below.

That's all. Your data is saved in your browser's localStorage.

### Option B: Host it on GitHub Pages

Push the project to a GitHub repo, enable Pages from the root of the `main` branch, and share the link with your team.

---

## Demo logins

| Email | Password | Role |
|---|---|---|
| `admin@demo.com` | `demo1234` | Admin (full access) |
| `alice@demo.com` | `demo1234` | Sales |
| `bob@demo.com` | `demo1234` | Manager |
| `carol@demo.com` | `demo1234` | Operation |

In offline demo mode the password isn't actually checked. Enter any email from the list and type whatever you like in the password field.

---

## Connecting your own Google Sheets (optional)

If you want your team to share live data, you can hook the app up to your own Google Apps Script backend. Here's how.

### Step 1: Create the Google Sheet

Make a new Google Sheet with these tabs, named exactly as shown:

```
customers   opportunities   deliveries   costsheets   costsheet_quotes
kpi         users           timesheet    notifications   settings
```

### Step 2: Add the Apps Script backend

1. In your sheet, go to **Extensions > Apps Script**.
2. Paste in your GAS backend code. It needs to handle reading, writing, and deleting data.
3. Open **Project Settings > Script Properties** and add a property:
   - Key: `AUTH_SECRET`
   - Value: any secret string you choose (for example, `my-secret-token-2025`)

### Step 3: Deploy it as a Web App

1. Click **Deploy > New Deployment**.
2. Choose **Web App** as the type.
3. Set "Execute as" to **Me**.
4. Set "Who has access" to **Anyone**.
5. Copy the deployment URL.

### Step 4: Connect the app

1. Open the app and click the plug icon in the top-right corner of the header.
2. Paste in your **Deployment URL** and **Auth Token**.
3. Click **Test Connection** to make sure everything works.
4. Click **Save & Activate**, then refresh the page.

Once connected, the app syncs all your data to your Google Sheets in real time.

---

## Tech stack

| | |
|---|---|
| **Frontend** | React 18, loaded from a CDN with no bundler |
| **JSX transform** | Babel Standalone, running in the browser |
| **Styling** | Plain CSS (inline styles and injected stylesheets) |
| **Storage** | localStorage for offline use, with optional Google Apps Script sync |
| **Charts** | Hand-built SVG, no charting library |
| **Backend** | Google Apps Script (bring your own) |

There's no `npm install` and no build step. Open the HTML file and go.

---

## Language and localization

The app is made with Thai users in mind, and includes:

- Thai UI labels and company names
- Buddhist Era (BE) dates, so you'll see 2569 instead of 2026
- Thai month abbreviations (ม.ค., ก.พ., and so on)
- Thai baht (฿) currency formatting

---

## Project structure

```
Climate_crm-main/
├── index.html        <- Entry point: loads React and Babel from CDN, mounts the app
└── src/
    └── App.jsx       <- The whole application (about 7,500 lines in one file)
```

---

## How your data is handled

```
Open index.html
      │
      ▼
  Is a Google Sheets URL configured?
  (saved in your browser's localStorage)
      │
   ┌──┴─────────────────────────┐
  NO (demo mode)              YES (live mode)
   │                            │
   ▼                            ▼
localStorage only          Syncs with your
Demo data preloaded        Google Sheets
Any login works            Real team credentials required
```

---

## Supported services

The CRM comes pre-configured with these climate and sustainability service codes:

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

## Who can see what

| Role | Dashboard | Customers | Opportunities | Delivery | Cost Sheet | Timesheet | Team & Rates |
|---|---|---|---|---|---|---|---|
| Admin | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| Manager | Yes | Yes | Yes | Yes | Yes | Yes | No |
| Sales | Yes | Yes | Yes | Yes | Yes | Yes | No |
| Operation | Yes | No | No | No | No | Yes | No |

---

## License

MIT. You're free to use, modify, and deploy it however you like.

---

Built with React 18, Babel Standalone, and Google Apps Script.
