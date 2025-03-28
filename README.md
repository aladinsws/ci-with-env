# 🚀 CI/CD Pipeline


This repository includes a GitHub Actions workflow to automate **build**, **test**, and **deployment** processes for the application.

> ⚠️ **Note**: This is a simplified example to simulate and display the deployment URL. You should replace the deployment steps with real logic for your infrastructure (e.g., upload to a server, trigger a cloud deployment, etc).

---

## 📂 Workflow File

Located at: `.github/workflows/ci.yml`

---

## 🔁 Trigger Events

This pipeline runs automatically on the following events:

- **Push** to any branch
- **Pull request**
- **Manual trigger** via the GitHub Actions UI (`workflow_dispatch`)

---

## 🛠 Jobs Breakdown

### 1. 🔧 Build Job
**Runs on**: `ubuntu-latest`

**Steps:**
- ✅ Checkout repository  
- 🛠 Setup Node.js environment  
- 📦 Install dependencies  
- 🧪 Run tests  
- 🏗 Build the project  
- 📤 Upload the build artifact  

---

### 2. 🚀 Deploy Job
**Runs after** the build job completes successfully.

**Dynamic Environment Target:**
- Deploys to **production** if the branch is `main`
- Deploys to **dev** for all other branches  
- Deployment URL is sourced from the GitHub environment variable: `${{ vars.ENV_URL }}`

**Steps:**
- 📥 Download the build artifact  
- 🌐 Set deployment URL from environment variables  
- 🚀 Simulate deployment  
- 🔗 Output the deployment URL  

---

## 🌎 Deployment Environment Variables

Make sure the following environment variable is set in your **GitHub repository settings**:

- `ENV_URL` – Base URL where the app should be considered "deployed"

> You can set this in **Settings → Environments → (dev/production) → Environment Variables**

---

## 🧪 Example Deployment Output

```bash
Using deployment URL from Environment variables...
Application deployed at: https://your-env-url.com
Application is live at: https://your-env-url.com
```

## 💡 Notes
This is a template-style pipeline meant to be customized for your stack (e.g., Node version, real deploy commands).

You can extend it to include caching, linting, or advanced test/reporting steps.
