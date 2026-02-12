# NutriSync Backend

Backend API for NutriSync application with Gemini AI integration.

## Deploy to Vercel

1. Push this backend folder to a separate GitHub repository (or use a monorepo)
2. Go to [Vercel](https://vercel.com)
3. Click "New Project"
4. Import your backend repository
5. Configure:
   - **Root Directory**: `backend` (if monorepo) or `.` (if separate repo)
   - **Framework Preset**: Other
   - **Build Command**: Leave empty
   - **Output Directory**: Leave empty

6. Add Environment Variable:
   - Key: `GEMINI_API_KEY`
   - Value: Your Gemini API key

7. Deploy!

## After Deployment

Copy your backend URL (e.g., `https://your-backend.vercel.app`) and update the frontend environment variable:

```
VITE_API_BASE_URL=https://your-backend.vercel.app
```

Then redeploy your frontend.
