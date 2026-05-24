# 🚀 DEPLOYMENT GUIDE - Railway or Render (FREE)

## ✅ PREREQUISITE
Your code is already pushed to GitHub ✓

---

## **OPTION 1: RAILWAY (RECOMMENDED - 5 MINUTES)**

### **Step 1: Go to Railway**
1. Visit [railway.app](https://railway.app)
2. Click **"Start Project"**
3. Sign in with **GitHub**

### **Step 2: Deploy Your Project**
1. Click **"New Project"** → **"Deploy from GitHub repo"**
2. Search and select: **RFNbProject3**
3. Click **"Deploy Now"**

*Railway will automatically:*
- ✅ Build Docker image (using your Dockerfile)
- ✅ Deploy your app
- ✅ Generate a domain

### **Step 3: Add MySQL Database**
1. In Railway Dashboard, click **"Add"**
2. Select **"MySQL"** from the list
3. Click **"Add"** → Auto-configures connection

### **Step 4: Set Environment Variables**
1. Click on your **Web Service**
2. Go to **"Variables"** tab
3. Add these variables:

```
APP_ENV = production
APP_DEBUG = false
APP_KEY = (leave blank - auto-generated)
APP_NAME = RFN
APP_URL = (your railway domain)
LOG_CHANNEL = stack
```

*Database variables auto-populate from MySQL plugin:*
- `DATABASE_URL` (automatically set)
- `DB_HOST` (automatically set)
- `DB_USERNAME` (automatically set)
- `DB_PASSWORD` (automatically set)

### **Step 5: Run Migrations**
1. Go to **"Deploy"** tab
2. Click **"View Logs"**
3. In terminal, run:
```bash
railway run php artisan migrate --force
railway run php artisan db:seed
```

### **Step 6: Done!** 🎉
Your app is live at: `https://your-app-randomid.up.railway.app`

---

## **OPTION 2: RENDER**

### **Step 1: Go to Render**
1. Visit [render.com](https://render.com)
2. Sign in with **GitHub**

### **Step 2: Create New Service**
1. Click **"New"** → **"Web Service"**
2. Select your **RFNbProject3** repository
3. Click **"Connect"**

### **Step 3: Configure**
```
Name: rfnproject
Environment: Docker
Plan: Free
```

### **Step 4: Add MySQL Database**
1. Click **"New"** → **"MySQL"**
2. Name: `rfnproject-db`
3. Plan: **Free**
4. Click **"Create Database"**

### **Step 5: Connect Database to Web Service**
1. Go to Web Service
2. **Environment** → Add these:
```
DB_CONNECTION = mysql
DB_HOST = (copy from MySQL dashboard)
DB_PORT = 3306
DB_DATABASE = rfnproject
DB_USERNAME = (copy from MySQL dashboard)
DB_PASSWORD = (copy from MySQL dashboard)
```

### **Step 6: Deploy**
1. Click **"Deploy"**
2. Wait 5-10 minutes
3. View at: `https://rfnproject.onrender.com`

---

## **COMPARISON**

| Feature | Railway | Render |
|---------|---------|--------|
| **Free Tier** | $5/month credit | Truly free |
| **Uptime** | 24/7 | 24/7 |
| **Cold starts** | None | None |
| **Setup** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Database** | MySQL ✅ | MySQL ✅ |
| **Custom domain** | ✅ | ✅ (paid) |

---

## **COMMON ISSUES**

### **"App keeps crashing"**
- Check logs: Dashboard → **"Logs"** tab
- Run migrations: `railway run php artisan migrate --force`
- Check `.env` variables are set

### **"Database connection error"**
- Verify `DB_HOST`, `DB_USERNAME`, `DB_PASSWORD` in Environment Variables
- Wait 1-2 minutes for database to initialize

### **"App says 'Maintenance Mode'"**
- Run: `railway run php artisan up`

### **"404 Not Found"**
- Your app might be in a subdirectory
- Check the domain provided and make sure routes are accessible

---

## **AFTER DEPLOYMENT**

### **Access Admin Dashboard**
- Visit: `https://your-domain.com/admin-dashboard`
- Login: `admin@rfn.com` / password you set during seeding

### **Change Admin Password**
- Go to **Profile** → **Change Password**

### **Monitor Logs**
- Railway: Dashboard → **"Logs"** tab
- Render: Dashboard → **"Logs"** tab

---

## **NEXT STEPS**

1. ✅ Choose Railway or Render
2. ✅ Follow the steps above
3. ✅ Visit your live URL
4. ✅ Login and test features
5. ✅ Share with friends!

**Questions? Ask in the logs or check the error messages.**

Happy deploying! 🚀
