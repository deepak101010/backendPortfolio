# ⚡ Quick Render Setup - TL;DR

## 1. Go to Render
👉 https://render.com → Sign in with GitHub

## 2. Create Web Service
- Click **"New +"** → **"Web Service"**
- Connect repo: `deepak101010/backendPortfolio`
- Branch: `main`

## 3. Configure
- **Name**: `deepak-portfolio-api`
- **Environment**: `Node`
- **Build Command**: `npm install`
- **Start Command**: `npm start`
- **Plan**: Free

## 4. Environment Variables (IMPORTANT!)
Add these in the **Environment** tab:

```
MONGODB_URI = mongodb+srv://deepakkeshri263_db_user:P13LcQdkJFxGeQ0i@cluster0.cyrmscn.mongodb.net/?appName=Cluster0
PORT = 10000
NODE_ENV = production
FRONTEND_URL = https://your-portfolio.vercel.app (update after frontend deploy)
```

## 5. Deploy
- Click **"Create Web Service"**
- Wait 2-5 minutes for deployment
- Your URL: `https://your-service-name.onrender.com`

## 6. Test
Visit: `https://your-service-name.onrender.com/api/health`

---

**For detailed instructions, see [RENDER_DEPLOYMENT.md](./RENDER_DEPLOYMENT.md)**

