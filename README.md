# Exam Boilerplate Project

A comprehensive, generic boilerplate covering all required experiments for your practical exams. This project is designed to be easily customizable within one hour for any topic.

## 📋 Covered Experiments

✅ **1. Responsive and Interactive UIs using Tailwind CSS**
- Fully responsive design with Tailwind CSS
- Dark/Light mode toggle
- Mobile-first approach

✅ **2. React Hooks (useEffect, useContext, custom hooks)**
- `useEffect` - Used in App.jsx, useItems.js, Dashboard.jsx
- `useContext` - Redux Context (via react-redux)
- Custom Hook - `useItems.js` for reusable item management logic

✅ **3. Manage complex state with Redux or Context API**
- Redux Toolkit for global state management
- Auth slice, Items slice, Theme slice
- Persistent state with localStorage

✅ **4. Create secure, production-ready RESTful APIs**
- Express.js backend with RESTful endpoints
- Proper HTTP methods (GET, POST, PUT, DELETE)
- Error handling and validation

✅ **5. Implement authentication and user roles with JWT**
- JWT token-based authentication
- Role-based access control (admin/user)
- Secure password hashing with bcrypt

✅ **6. Validating RESTful APIs using VSCode REST Client**
- All endpoints ready for testing in VSCode
- `.vscode/http.http` file included
- Test credentials provided

✅ **7. CI/CD Deployment with GitHub Actions + Render/Vercel**
- GitHub Actions workflow configured
- Ready for deployment to Render/Vercel
- Separate frontend/backend deployment support

## 🚀 Quick Start

### 1. Install Dependencies

**Option 1: Use the shortcut command**
```bash
npm run install-all
```

**Option 2: Manual installation (if npm scripts are disabled)**
```bash
npm install
cd backend && npm install && cd ..
cd frontend && npm install && cd ..
```

**PowerShell Issue?** Use Option 2, or see troubleshooting section below.

### 2. Start Development Servers

**IMPORTANT: Run frontend and backend in separate terminals!**

**Terminal 1 - Start Backend:**
```bash
cd backend
npm run dev
```
Backend runs on https://fsd-backend-gymv.onrender.com

**Terminal 2 - Start Frontend:**
```bash
cd frontend
npm run dev
```
Frontend runs on https://fsdeploy-khaki.vercel.app/

**Why separate terminals?** This allows independent deployment and avoids dependency on `concurrently`.

### 3. Access the Application

- **Frontend:** Open https://fsdeploy-khaki.vercel.app/ in your browser
- **Backend API:** https://fsd-backend-gymv.onrender.com

### 4. Test Login

**Default Test Accounts:**
- **Admin:** `admin@example.com` / `admin123`
- **User:** `user@example.com` / `user123`

## 📁 Project Structure

```
exam-boilerplate/
├── backend/              # Express.js API server
│   ├── server.js        # Main server file with all routes
│   ├── package.json     # Backend dependencies
│   └── env.example      # Environment variables template
├── frontend/            # React application
│   ├── src/
│   │   ├── components/  # Reusable components
│   │   ├── pages/       # Page components
│   │   ├── store/       # Redux store
│   │   ├── hooks/       # Custom hooks
│   │   └── utils/       # Utilities
│   ├── package.json     # Frontend dependencies
│   └── env.example      # Environment variables template
├── .vscode/
│   └── http.http        # VSCode REST Client test file
├── .github/workflows/    # CI/CD configuration
├── README.md            # This file
├── QUICK_START.md       # Quick customization guide
├── EXPERIMENTS_CHECKLIST.md  # Exam checklist
├── SETUP_INSTRUCTIONS.md     # Detailed setup guide
├── DEPLOYMENT_ENV_SETUP.md   # Environment variables guide
└── POSTMAN_COLLECTION.json   # Postman collection (backup)
```

## 🎯 Quick Customization Guide (1 Hour Plan)

See `QUICK_START.md` for detailed 1-hour customization steps.

**Quick Overview:**
1. Update data structure in `backend/server.js`
2. Update form fields in `frontend/src/pages/Dashboard.jsx`
3. Update content in `frontend/src/pages/Home.jsx`
4. Update API routes if needed
5. Test everything

## 📝 API Testing with VSCode REST Client

### Setup (Recommended Method)
1. Install **REST Client** extension in VSCode (by Huachao Mao)
2. Open `.vscode/http.http` file
3. Click "Send Request" above each request to test endpoints

### Quick Test Flow
1. Run "Login" request first
2. Copy token from response
3. Update `@token = Bearer YOUR_TOKEN_HERE` at top of file
4. Run other requests (they'll use the token automatically)

### Alternative: Postman
You can also use Postman - import `POSTMAN_COLLECTION.json` if needed.

## 🔐 Authentication Flow

1. User registers/logs in → Backend generates JWT token
2. Token stored in Redux state and localStorage
3. Token sent in `Authorization: Bearer TOKEN` header for protected routes
4. Backend validates token on each request
5. Role-based access control checks user role

## 🎨 Theme (Dark/Light Mode)

- Toggle button in Navbar
- Preference saved in localStorage
- Managed by Redux `themeSlice`

## 📦 Deployment

### Separate Frontend/Backend Deployment

**Backend (Render/Heroku/Any Node.js host):**
```bash
cd backend
npm install
npm start
```

**Frontend (Vercel/Netlify/Render Static):**
```bash
cd frontend
npm install
npm run build
# Deploy the 'dist' folder
```

### Environment Variables

**Before deploying, set up environment variables:**
- Backend: See `backend/env.example`
- Frontend: See `frontend/env.example`
- Full guide: See `DEPLOYMENT_ENV_SETUP.md`

### Render.com Setup

**Backend:**
1. Create new Web Service
2. Connect GitHub repository
3. Root directory: `backend`
4. Build command: `npm install`
5. Start command: `npm start`
6. Add environment variables from `backend/env.example`

**Frontend:**
1. Create new Static Site
2. Connect GitHub repository
3. Root directory: `frontend`
4. Build command: `npm install && npm run build`
5. Publish directory: `dist`
6. Add environment variables from `frontend/env.example`

### Vercel Setup

**Frontend:**
1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in `frontend` folder
3. Follow prompts
4. Configure environment variables

## ⚠️ Important Notes

- **Mock Backend**: No real database - all data stored in arrays (resets on server restart)
- **JWT Secret**: Configure `JWT_SECRET` in `.env` file (see `DEPLOYMENT_ENV_SETUP.md`)
- **Password Hashing**: Uses bcryptjs (salted hashes)
- **CORS**: Configured via `CORS_ORIGIN` in `.env` file
- **Environment Variables**: See `backend/env.example` and `frontend/env.example`
- **Separate Terminals**: Frontend and backend must run in separate terminals for development

## 🆘 Troubleshooting

### PowerShell Execution Policy Error?

**Error:** `cannot be loaded because running scripts is disabled`

**Quick Fix - Use Command Prompt:**
1. Open Command Prompt (CMD) instead of PowerShell
2. Navigate to project folder
3. Run `npm run install-all`

**Or Fix PowerShell (One-time):**
```powershell
# Run PowerShell as Administrator, then:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Or Use Manual Installation:**
Just follow Option 2 in the installation section - no scripts needed!

### Backend/Frontend Won't Start?

**Check:**
1. Are you in the correct directory? (`backend` or `frontend`)
2. Did you install dependencies? (`npm install`)
3. Check if ports 3000/3001 are already in use
4. Check terminal output for error messages

**Port already in use?**
- Change ports in `backend/server.js` (PORT) and `frontend/vite.config.js` (server.port)

**Cannot connect to API?**
- Ensure backend is running on port 3001
- Check CORS settings in `backend/server.js`
- Verify `VITE_API_URL` in frontend `.env` matches backend URL

**Token errors?**
- Clear localStorage and login again
- Check JWT_SECRET matches in backend `.env`

## 📚 Key Files to Modify During Exam

1. **`backend/server.js`** - Data structure, API endpoints
2. **`frontend/src/pages/Dashboard.jsx`** - Main content page
3. **`frontend/src/pages/Home.jsx`** - Landing page
4. **`frontend/src/store/slices/itemSlice.js`** - State management for items
5. **`frontend/src/components/Navbar.jsx`** - Navigation and branding

## 🎓 Exam Tips

1. **Read all comments** - Every file has detailed comments explaining what to change
2. **Search for "TO CUSTOMIZE"** - These comments mark areas you need to modify
3. **Test locally first** - Ensure everything works before deploying
4. **Keep VSCode REST Client ready** - Test API endpoints to demonstrate RESTful APIs
5. **Document your changes** - Mention what you customized during the exam
6. **Separate terminals** - Remember to run frontend and backend separately

---

**Good luck with your exams!** 🚀

