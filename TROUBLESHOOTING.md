# 🔧 Troubleshooting Contact Form Errors

## Error: "Something went wrong. Please try again or contact me directly."

This error appears when the contact form cannot connect to the backend. Here are common causes and solutions:

---

## ✅ Checklist to Fix

### 1. Check Backend is Running

**Test your backend:**
- Visit: `https://backendportfoliodeepak.onrender.com/api/health`
- Should see: `{"success":true,"message":"Backend server is running"}`

**If backend is down:**
- Go to Render dashboard
- Check if service is "Live" (not "Sleeping")
- If sleeping, wake it up or wait 30 seconds for first request

---

### 2. Check CORS Configuration

**On Render Dashboard:**
1. Go to your backend service
2. Click **Environment** tab
3. Verify `FRONTEND_URL` is set to your actual frontend URL:
   ```
   FRONTEND_URL=https://your-frontend.vercel.app
   ```
   (Replace with your actual Vercel URL)

4. After updating, Render will auto-redeploy

---

### 3. Check Frontend Environment Variable

**On Vercel Dashboard:**
1. Go to your frontend project
2. Settings → Environment Variables
3. Verify `VITE_BACKEND_URL` is set:
   ```
   VITE_BACKEND_URL=https://backendportfoliodeepak.onrender.com
   ```

4. Redeploy frontend after updating

---

### 4. Check MongoDB Connection

**On Render Dashboard:**
1. Go to Environment Variables
2. Verify `MONGODB_URI` is correct:
   ```
   MONGODB_URI=mongodb+srv://deepakkeshri263_db_user:P13LcQdkJFxGeQ0i@cluster0.cyrmscn.mongodb.net/?appName=Cluster0
   ```

3. Check Render logs for MongoDB connection errors

---

### 5. Check Browser Console

**Open browser DevTools (F12):**
- Go to **Console** tab
- Try submitting form
- Look for error messages:
  - `Failed to fetch` = Network/CORS issue
  - `CORS blocked` = Frontend URL not in allowed origins
  - `500 Internal Server Error` = Backend/MongoDB issue

---

## 🔍 Common Issues & Solutions

### Issue: "Failed to fetch"
**Cause:** Backend not accessible or CORS blocking

**Fix:**
1. Verify backend URL is correct
2. Check `FRONTEND_URL` in Render matches your frontend domain exactly
3. Ensure backend is "Live" on Render

---

### Issue: "CORS blocked"
**Cause:** Frontend URL not in allowed origins

**Fix:**
1. In Render, set `FRONTEND_URL` to your exact Vercel URL (include `https://`)
2. Example: `FRONTEND_URL=https://your-portfolio.vercel.app`
3. Redeploy backend

---

### Issue: "500 Internal Server Error"
**Cause:** MongoDB connection failed or validation error

**Fix:**
1. Check Render logs for error details
2. Verify `MONGODB_URI` is correct
3. Check MongoDB Atlas Network Access allows all IPs (0.0.0.0/0)

---

### Issue: Backend "Sleeping"
**Cause:** Free tier service inactive for 15+ minutes

**Fix:**
1. Wait 30 seconds for cold start
2. Or upgrade to paid tier to avoid sleep

---

## 📝 Testing Steps

### 1. Test Backend Health
```bash
curl https://backendportfoliodeepak.onrender.com/api/health
```

### 2. Test Contact Endpoint
```bash
curl -X POST https://backendportfoliodeepak.onrender.com/api/contact \
  -H "Content-Type: application/json" \
  -d '{"name":"Test","email":"test@example.com","message":"Test message"}'
```

### 3. Check Frontend Console
- Open DevTools → Console
- Submit form
- Look for backend URL in logs: `Submitting to: https://...`

---

## 🎯 Quick Fix Summary

1. **Backend URL**: `https://backendportfoliodeepak.onrender.com`
2. **Set in Vercel**: `VITE_BACKEND_URL`
3. **Set in Render**: `FRONTEND_URL` = Your Vercel URL
4. **MongoDB**: Verify connection string in Render
5. **Test**: Visit `/api/health` endpoint

---

## 💡 Still Not Working?

1. Check Render logs for detailed errors
2. Check browser console for client-side errors
3. Verify all environment variables are set correctly
4. Make sure both frontend and backend are redeployed after changes

**Your backend URL**: `https://backendportfoliodeepak.onrender.com`

