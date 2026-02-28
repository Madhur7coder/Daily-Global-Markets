# 🌐 Global Markets Dashboard

**Auto-updating daily financial dashboard** — indices, commodities, sectors, top/bottom stocks, and global markets. Refreshes every weekday at **8:00 AM Dubai time**.

---

## 🚀 One-Click Deploy to Vercel

### Step 1: Get a FREE API Key (2 minutes)

1. Go to **[https://site.financialmodelingprep.com/register](https://site.financialmodelingprep.com/register)**
2. Sign up for a **free account**
3. Go to your dashboard and copy your **API key**

### Step 2: Deploy to Vercel (3 minutes)

1. Go to **[https://vercel.com](https://vercel.com)** and sign up with your GitHub account (free)
2. Push this project to a new GitHub repository:
   - Go to **[https://github.com/new](https://github.com/new)** and create a new repo (e.g., `markets-dashboard`)
   - Upload all the files from this folder to that repo
3. Back in Vercel, click **"Add New Project"** → **Import** your GitHub repo
4. Before clicking Deploy, expand **"Environment Variables"** and add:

   | Name           | Value                        |
   |----------------|------------------------------|
   | `FMP_API_KEY`  | *(your API key from Step 1)* |
   | `CRON_SECRET`  | *(any random string, e.g. `mySecret123`)* |

5. Click **Deploy** ✅

That's it! Your dashboard will be live at `https://your-project.vercel.app`

---

## ⏰ Automatic Daily Updates

The dashboard auto-refreshes every **weekday at 8:00 AM Dubai time (4:00 AM UTC)** via a Vercel Cron Job configured in `vercel.json`.

> **Note:** Vercel Cron Jobs require the **Hobby plan** (free) or above. The cron is already configured — no additional setup needed.

---

## 📁 Project Structure

```
markets-dashboard/
├── app/
│   ├── api/
│   │   └── revalidate/
│   │       └── route.js        ← Cron endpoint (triggers data refresh)
│   ├── components/
│   │   └── Dashboard.js        ← Full dashboard UI (client component)
│   ├── layout.js               ← Root HTML layout
│   └── page.js                 ← Server component (fetches data)
├── lib/
│   └── fetchMarketData.js      ← All API calls to Financial Modeling Prep
├── public/
├── .env.example                ← Template for environment variables
├── next.config.js
├── package.json
├── vercel.json                 ← Cron schedule config
└── README.md
```

---

## 📊 Dashboard Tabs

| Tab | Contents |
|-----|----------|
| **Overview** | US 10Y Treasury yield + change, S&P 500 / Nasdaq / MSCI ACWI levels & performance, S&P 500 sector breakdown sorted by YTD |
| **Commodities** | Gold, Silver, Bitcoin, Crude Oil, Copper — prices and 1D/1W/1M/YTD changes |
| **Top & Bottom Stocks** | Best/worst 10 performers (>$10B market cap) by recent performance |
| **Global Markets** | Top/bottom 5 global equity markets by YTD return |

---

## 🔧 Local Development

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/markets-dashboard.git
cd markets-dashboard

# 2. Install dependencies
npm install

# 3. Create .env.local with your API key
cp .env.example .env.local
# Edit .env.local and add your FMP_API_KEY

# 4. Run locally
npm run dev
# Open http://localhost:3000
```

---

## 📌 Notes

- **Data source:** [Financial Modeling Prep](https://financialmodelingprep.com) (free tier: 250 requests/day)
- **Sectors** use SPDR ETF proxies (XLK, XLF, XLE, etc.)
- **Global markets** use iShares country ETF proxies (EWG, EWJ, EWZ, etc.)
- **Fallback:** Even without the cron, the page revalidates every 4 hours automatically
- **No database needed** — data is fetched fresh and cached by Next.js

---

## 📱 Share with Your Team

Just send your colleagues the Vercel URL — no login or account needed. Works on desktop and mobile.
