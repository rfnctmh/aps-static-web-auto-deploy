# Azure App Service Demo (Auto Deploy + Last Build Time)

This project demonstrates:
- Auto deploy to **Azure App Service** on every push
- Daily **scheduled redeploy** (via GitHub Actions)
- Frontend shows the latest build time from `build.txt` (Taiwan time, GMT+8)

## Usage
1. Push this repo to your GitHub account.
2. Create an **Azure App Service (Linux)** Web App and link to this repo (app location = `site`).
3. Secrets (GitHub → Settings → Secrets → Actions):
   - `AZURE_WEBAPP_NAME` — your App Service name
   - `AZURE_WEBAPP_PUBLISH_PROFILE` — content of your publish profile XML (from Azure Portal → *Get publish profile*)
4. On each push (and on your daily trigger), GitHub Actions will:
   - write `site/build.txt` with **Taiwan time**:
     ```
     Last build: YYYY-MM-DD HH:MM:SS GMT+8
     ```
   - deploy to Azure App Service
5. The page fetches `build.txt` and **displays its full content** (no parsing needed).

## Trigger options
- **GitHub Actions schedule (simple)**
  - `on.schedule: "0 0 * * *"` (runs near 08:00 TW; may delay)
- **Manual trigger**
  - Run manually in GitHub → *Actions → Run workflow*

## Notes
- Azure App Service **Free (F1)** tier does not support custom domains; upgrade to **Basic (B1)** or higher if needed.
- The workflow uses `azure/webapps-deploy@v3` to upload static content from the `site` folder.
- The build time display is auto-updated on every deployment.