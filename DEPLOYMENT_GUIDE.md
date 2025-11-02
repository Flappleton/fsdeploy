# 🚀 Deployment Guide

Complete guide for deploying frontend and backend separately.

## 📌 Important: Separate Deployment

This project uses **independent frontend and backend** for easier deployment:
- ✅ No `concurrently` dependency needed
- ✅ Deploy frontend and backend separately
- ✅ Each can be on different hosting services
- ✅ Easier to scale independently

## 🎯 Quick Deployment Options

### Option 1: Render.com (Recommended for Beginners)

#### Backend Deployment
1. Go to [render.com](https://render.com) and sign up
2. Click "New +" → "Web Service"
3. Connect your GitHub repository
4. **Settings:**
   - **Name:** `yourapp-backend`
   - **Root Directory:** `backend`
   - **Environment:** `Node`
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
5. **Environment Variables:**
   - `JWT_SECRET` - Generate with: `openssl rand -base64 32`
   - `PORT` - `3001` (or leave default)
   - `CORS_ORIGIN` - Your frontend URL (will set after frontend deployment)
   - `NODE_ENV` - `production`
6. Click "Create Web Service"
7. Copy the backend URL (e.g., `https://yourapp-backend.onrender.com`)

#### Frontend Deployment
1. In Render dashboard, click "New +" → "Static Site"
2. Connect your GitHub repository
3. **Settings:**
   - **Name:** `yourapp-frontend`
   - **Root Directory:** `frontend`
   - **Build Command:** `npm install && npm run build`
   - **Publish Directory:** `dist`
4. **Environment Variables:**
   - `VITE_API_URL` - Your backend URL (from step above)
   - `VITE_APP_NAME` - Your app name
   - `VITE_NODE_ENV` - `production`
5. Click "Create Static Site"
6. Copy the frontend URL (e.g., `https://yourapp-frontend.onrender.com`)
7. **Go back to backend** and update `CORS_ORIGIN` to your frontend URL

### Option 2: Vercel (Frontend) + Render (Backend)

#### Backend on Render
Follow "Backend Deployment" from Option 1 above.

#### Frontend on Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. In your project:
   ```bash
   cd frontend
   vercel
   ```
3. Follow prompts:
   - Link to existing project or create new
   - Set environment variables:
     - `VITE_API_URL` - Your Render backend URL
4. Vercel will automatically build and deploy

**Or use Vercel Dashboard:**
1. Go to [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. **Settings:**
   - **Root Directory:** `frontend`
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
4. Add environment variables (same as above)

### Option 3: Both on Vercel

#### Backend
1. Use Vercel Serverless Functions (requires code changes)
2. Or deploy as separate Node.js service on Render/Heroku

#### Frontend
Follow "Frontend on Vercel" from Option 2 above.

## 📋 Deployment Checklist

Before deploying, ensure:

- [ ] **Backend:**
  - [ ] All dependencies installed (`cd backend && npm install`)
  - [ ] `.env` file configured (or set in hosting platform)
  - [ ] `JWT_SECRET` is set and strong
  - [ ] `CORS_ORIGIN` matches frontend URL
  - [ ] `PORT` is configured (if needed)

- [ ] **Frontend:**
  - [ ] All dependencies installed (`cd frontend && npm install`)
  - [ ] `.env` file configured (or set in hosting platform)
  - [ ] `VITE_API_URL` points to backend URL
  - [ ] Build succeeds locally (`npm run build`)
  - [ ] `dist` folder is generated

- [ ] **After Deployment:**
  - [ ] Backend URL is accessible
  - [ ] Frontend can connect to backend (check browser console)
  - [ ] Login/Register works
  - [ ] API calls work (check Network tab)
  - [ ] CORS errors are resolved

## 🔧 Environment Variables Setup

See `DEPLOYMENT_ENV_SETUP.md` for detailed environment variable configuration.

## 🆘 Common Deployment Issues

### Build Fails

**Backend:**
- Check Node.js version (should be 18+)
- Verify all dependencies in `package.json`
- Check build logs for specific errors

**Frontend:**
- Ensure `VITE_API_URL` is set
- Check for TypeScript errors
- Verify Tailwind CSS configuration

### CORS Errors

**Symptom:** Frontend can't connect to backend

**Fix:**
1. Update `CORS_ORIGIN` in backend to match exact frontend URL
2. Include protocol: `https://yourapp.onrender.com` (not `yourapp.onrender.com`)
3. No trailing slash

### API Connection Failed

**Check:**
1. Backend is running and accessible
2. `VITE_API_URL` in frontend matches backend URL
3. Backend URL includes protocol: `https://...`
4. No firewall blocking requests

### Environment Variables Not Working

**VSCode/Vite:**
- Frontend env vars must start with `VITE_`
- Rebuild after changing env vars: `npm run build`
- Check `.env` file is in `frontend/` folder

**Backend:**
- Ensure `.env` file exists in `backend/` folder
- Or set directly in hosting platform
- Restart backend after changing env vars

## 📝 Post-Deployment Testing

1. ✅ Visit frontend URL
2. ✅ Try login with test credentials
3. ✅ Test CRUD operations
4. ✅ Check browser console for errors
5. ✅ Test on mobile device (responsive design)
6. ✅ Verify dark mode toggle works
7. ✅ Test API with VSCode REST Client (use production URLs)

## 🎓 Exam Tips

- Deploy both frontend and backend before exam
- Have production URLs ready to show
- Test all features work in production
- Be prepared to explain the deployment process
- Keep backup of working local version

---

**Your app is ready for deployment!** 🚀

