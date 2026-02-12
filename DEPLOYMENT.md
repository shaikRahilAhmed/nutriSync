# NutriSync Deployment Guide

## Current Issue
Your frontend is deployed on Vercel but trying to connect to `localhost:5000`, which doesn't exist in production.

## Solution: Deploy Backend to Vercel

### Step 1: Deploy Backend

#### Option A: Separate Repository (Recommended)
1. Create a new GitHub repository called `nutrisync-backend`
2. Copy the `backend` folder contents to this new repo
3. Push to GitHub:
   ```bash
   cd backend
   git init
   git add .
   git commit -m "Initial backend commit"
   git remote add origin https://github.com/YOUR_USERNAME/nutrisync-backend.git
   git push -u origin main
   ```

#### Option B: Monorepo (Current Setup)
1. Your backend is already in the same repo
2. You'll deploy it as a separate Vercel project

### Step 2: Deploy Backend on Vercel

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click **"Add New Project"**
3. Import your repository
4. Configure the project:
   - **Project Name**: `nutrisync-backend`
   - **Root Directory**: `backend` (if monorepo) or `.` (if separate repo)
   - **Framework Preset**: Other
   - **Build Command**: Leave empty
   - **Output Directory**: Leave empty
   - **Install Command**: `npm install`

5. **Add Environment Variable**:
   - Go to **Settings** → **Environment Variables**
   - Add:
     - **Key**: `GEMINI_API_KEY`
     - **Value**: `YOUR_GEMINI_API_KEY` (from backend/.env)

6. Click **Deploy**

7. **Copy your backend URL** (e.g., `https://nutrisync-backend.vercel.app`)

### Step 3: Update Frontend Environment Variables

1. Go to your frontend project on Vercel
2. Go to **Settings** → **Environment Variables**
3. Add/Update these variables:
   - **VITE_SUPABASE_URL**: `YOUR_SUPABASE_URL`
   - **VITE_SUPABASE_PUBLISHABLE_KEY**: `YOUR_SUPABASE_KEY`
   - **VITE_API_BASE_URL**: `https://nutrisync-backend.vercel.app` (your backend URL)

4. **Redeploy** your frontend:
   - Go to **Deployments** tab
   - Click the three dots on the latest deployment
   - Click **Redeploy**

### Step 4: Verify

1. Visit your frontend: `https://nutri-sync-r.vercel.app`
2. Go to AI NutriScan
3. Upload a food image
4. It should now work! 🎉

---

## Alternative: Use a Different Backend Hosting

If Vercel doesn't work for your backend, you can use:

### Option 1: Railway.app
1. Go to [Railway.app](https://railway.app)
2. Create new project from GitHub
3. Select backend folder
4. Add `GEMINI_API_KEY` environment variable
5. Deploy
6. Copy the URL and update frontend `VITE_API_BASE_URL`

### Option 2: Render.com
1. Go to [Render.com](https://render.com)
2. Create new Web Service
3. Connect your GitHub repo
4. Root Directory: `backend`
5. Build Command: `npm install`
6. Start Command: `node server.js`
7. Add `GEMINI_API_KEY` environment variable
8. Deploy
9. Copy the URL and update frontend `VITE_API_BASE_URL`

### Option 3: Heroku
1. Install Heroku CLI
2. Create Heroku app
3. Deploy backend
4. Add `GEMINI_API_KEY` config var
5. Copy the URL and update frontend `VITE_API_BASE_URL`

---

## Quick Fix for Testing (Not Recommended for Production)

If you just want to test quickly, you can:

1. Keep your local backend running
2. Use a service like [ngrok](https://ngrok.com) to expose it:
   ```bash
   ngrok http 5000
   ```
3. Copy the ngrok URL (e.g., `https://abc123.ngrok.io`)
4. Update Vercel environment variable:
   - `VITE_API_BASE_URL=https://abc123.ngrok.io`
5. Redeploy frontend

**Note**: This only works while your computer is on and ngrok is running.

---

## Troubleshooting

### CORS Errors
Make sure your backend CORS configuration includes your frontend URL:
```javascript
const corsOptions = {
  origin: [
    "http://localhost:8080",
    "http://localhost:8081",
    "https://nutri-sync-r.vercel.app"
  ],
  // ...
};
```

### Environment Variables Not Working
- Make sure to redeploy after adding environment variables
- Check that variable names match exactly (case-sensitive)
- Verify variables are set in Vercel dashboard

### Backend Not Responding
- Check Vercel function logs
- Verify Gemini API key is correct
- Check if you've hit API rate limits

---

## Summary

**Current Setup:**
- ✅ Frontend: Deployed on Vercel
- ❌ Backend: Running locally only

**What You Need to Do:**
1. Deploy backend to Vercel (or Railway/Render)
2. Update frontend `VITE_API_BASE_URL` environment variable
3. Redeploy frontend

**Estimated Time:** 10-15 minutes

Good luck! 🚀
