# 🚀 Azure App Service — Auto Deploy & Build Timestamp Demo

This project demonstrates a simple static website automatically deployed to **Azure App Service** using **GitHub Actions**.  
It also writes the latest build timestamp (`build.txt`) on every deployment.

---

## ✨ Features
- **Auto Deploy on Every Push** — commits to `main` or `master` trigger an automatic deployment.  
- **Daily Scheduled Redeploy** — workflow runs daily at **00:00 UTC (08:00 Taipei)**.  
- **Build Timestamp Display** — front-end reads `build.txt` and shows the last build time.  

---

## 🧭 Project Structure
├── site/
│ ├── index.html
│ └── build.txt ← auto-generated each deploy
└── .github/
└── workflows/
└── deploy-aps.yml