# Free Backend Hosting Options (No Credit Card Required)

**Last Updated:** May 8, 2026  
**Your Requirements:**
- ✅ NO credit card required
- ✅ Must support SMTP for Gmail email sending
- ✅ Must be free
- ✅ Must support Node.js backend

---

## ⚠️ IMPORTANT: Current Situation

Your backend is currently deployed on **Render** (https://ntourismsystem.onrender.com), but **Render blocks Gmail SMTP on the free tier**. This is why your email OTP system is not working in production.

**Your Frontend:** https://tourism-system-two.vercel.app ✅ (Working fine on Vercel)

---

## 🎯 RECOMMENDED OPTIONS (No Credit Card)

### 1. ⭐ **Leapcell.io** (BEST OPTION)
- **Website:** https://leapcell.io
- **Credit Card:** ❌ NOT required
- **Free Tier:**
  - 20 free projects
  - Free PostgreSQL database
  - Supports Node.js, Python, Go, Rust
  - Serverless deployment
  - **SMTP Support:** ✅ YES - No restrictions on outbound SMTP
- **Limitations:**
  - Scales to zero when idle (may have cold starts)
  - Limited resources per project
- **Why Choose This:**
  - Recently recommended by multiple developers (2025-2026)
  - No credit card required for signup
  - Supports SMTP without restrictions
  - Free PostgreSQL included
  - Easy deployment from GitHub

**Deployment Steps:**
1. Sign up at https://leapcell.io/signup
2. Connect your GitHub repository
3. Configure environment variables (same as Render)
4. Deploy automatically

---

### 2. **Vercel** (Backend + Frontend Together)
- **Website:** https://vercel.com
- **Credit Card:** ❌ NOT required
- **Free Tier:**
  - 100 GB bandwidth/month
  - Serverless functions
  - 100 builds per day
  - 10 seconds per function
- **SMTP Support:** ✅ YES - Vercel does NOT block SMTP (only port 25 is blocked)
- **Limitations:**
  - Serverless only (no persistent background jobs)
  - 10-second function timeout
  - Cannot run long-running processes
- **Why Choose This:**
  - You're already using Vercel for frontend
  - Can deploy both frontend and backend together
  - Gmail SMTP works fine (ports 465/587 are open)
  - Very reliable and fast

**Note:** Your backend needs to be adapted for serverless functions (API routes), but this is straightforward with Express.

---

### 3. **Netlify**
- **Website:** https://netlify.com
- **Credit Card:** ❌ NOT required
- **Free Tier:**
  - 100 GB bandwidth/month
  - 300 build minutes/month
  - Serverless functions (125k requests/month)
  - 10 seconds per function
- **SMTP Support:** ✅ YES - No SMTP restrictions
- **Limitations:**
  - Serverless only
  - 10-second function timeout
  - Best for JAMstack apps
- **Why Choose This:**
  - Similar to Vercel
  - Good for Node.js backends
  - No SMTP restrictions

---

### 4. **Back4app Container as a Service**
- **Website:** https://www.back4app.com/web-deployment-platform
- **Credit Card:** ❌ NOT required
- **Free Tier:**
  - 256 MB RAM
  - 0.25 shared CPU
  - 100 GB transfer/month
  - Deploy from GitHub
  - Custom Docker containers
- **SMTP Support:** ✅ YES - Should work
- **Limitations:**
  - Limited resources
  - May shut down after inactivity
- **Why Choose This:**
  - Supports Docker containers
  - No credit card required
  - Decent free tier

---

## ❌ PLATFORMS TO AVOID (Based on Your Requirements)

### Already Tried - Don't Work:
1. **Render** - Blocks Gmail SMTP on free tier ❌
2. **Railway** - Blocks email sending ❌
3. **Koyeb** - Requires credit card ❌
4. **Cyclic** - Shut down (May 2024) ❌
5. **Adaptable** - Shutting down ❌
6. **Deta Space** - Not working/404 ❌
7. **Glitch** - Not suitable for production ❌

### Require Credit Card:
1. **Fly.io** - Requires credit card (even for free tier) ❌
2. **Northflank** - Requires credit card for signup ❌
3. **Oracle Cloud** - Requires payment method ❌
4. **Heroku** - Discontinued free tier (2022) ❌

### Time-Limited Free Trials:
1. **AWS EC2** - Only free for 1 year ❌
2. **Azure** - Only free for 1 year ❌
3. **Microsoft Azure** - $200 credit for first month only ❌

---

## 🚀 RECOMMENDED DEPLOYMENT STRATEGY

### Option A: Deploy Backend to Leapcell.io (EASIEST)
1. Keep frontend on Vercel (already working)
2. Deploy backend to Leapcell.io
3. Update frontend API URL to point to Leapcell backend
4. Gmail SMTP will work without issues

**Pros:**
- No code changes needed
- No credit card required
- SMTP works out of the box
- Free PostgreSQL included

**Cons:**
- Cold starts (first request may be slow)
- Need to migrate from Render to Leapcell

---

### Option B: Move Backend to Vercel Serverless Functions (BEST LONG-TERM)
1. Convert Express backend to Vercel serverless functions
2. Keep database on Supabase (already working)
3. Deploy both frontend and backend on Vercel
4. Gmail SMTP will work without issues

**Pros:**
- Everything in one place (Vercel)
- Very fast and reliable
- No cold starts (Vercel is optimized)
- Already familiar with Vercel

**Cons:**
- Requires code refactoring (Express → Serverless functions)
- 10-second function timeout (should be fine for your app)

---

## 📋 MIGRATION CHECKLIST

### Before Migration:
- [ ] Backup current database (Supabase - already done)
- [ ] Test Gmail SMTP locally
- [ ] Document all environment variables
- [ ] Test all API endpoints

### During Migration:
- [ ] Sign up for chosen platform (Leapcell or Vercel)
- [ ] Configure environment variables
- [ ] Deploy backend
- [ ] Test email sending in production
- [ ] Update frontend API URL

### After Migration:
- [ ] Test all features (registration, login, booking, etc.)
- [ ] Verify email OTP is working
- [ ] Monitor for errors
- [ ] Update documentation

---

## 🔧 ENVIRONMENT VARIABLES (Updated)

```env
# Database (Supabase - Keep as is)
DATABASE_URL=postgresql://postgres.gclzstgdcguzocxxgkdv:53816705Aa%40@aws-0-eu-west-1.pooler.supabase.com:5432/postgres
DIRECT_URL=postgresql://postgres.gclzstgdcguzocxxgkdv:53816705Aa%40@aws-0-eu-west-1.pooler.supabase.com:5432/postgres

# Frontend URL (UPDATED)
FRONTEND_URL=https://tourism-system-two.vercel.app

# Gmail SMTP (Keep as is)
GMAIL_USER=abebemarye5381@gmail.com
GMAIL_APP_PASSWORD=odprlcravjovfhpj

# JWT & Security (Keep as is)
JWT_SECRET=north-wollo-tourism-jwt-secret-key-2025-very-secure-strong-key-0123456789-extra-padding-for-512-bits
JWT_EXPIRATION=15m
JWT_REFRESH_EXPIRATION=7d

# Server Config
NODE_ENV=production
PORT=3001

# Security
MAX_FAILED_ATTEMPTS=5
LOCKOUT_DURATION_MINUTES=15
MAX_IP_ATTEMPTS_PER_HOUR=100

# File Upload
UPLOAD_DIR=uploads
MAX_FILE_SIZE=10485760

# Audit
AUDIT_ENABLED=true
AUDIT_RETENTION_DAYS=90
```

---

## 📞 NEXT STEPS

1. **Choose a platform:**
   - **Leapcell.io** (easiest, no code changes)
   - **Vercel** (best long-term, requires refactoring)

2. **Test locally first:**
   - Ensure Gmail SMTP works in development
   - Test all email features

3. **Deploy to chosen platform:**
   - Follow platform-specific deployment guide
   - Configure environment variables
   - Test email sending

4. **Update frontend:**
   - Change API URL to new backend URL
   - Test all features

5. **Monitor:**
   - Check logs for errors
   - Verify email delivery
   - Test user registration and login

---

## 📚 ADDITIONAL RESOURCES

- **Leapcell Documentation:** https://docs.leapcell.io/
- **Vercel Serverless Functions:** https://vercel.com/docs/functions
- **Gmail SMTP Setup:** https://support.google.com/mail/answer/7126229
- **Nodemailer Documentation:** https://nodemailer.com/

---

## ⚠️ IMPORTANT NOTES

1. **Gmail SMTP Limits:**
   - Free Gmail accounts: 500 emails/day
   - Google Workspace: 2,000 emails/day
   - Your current usage should be well within limits

2. **Cold Starts:**
   - Serverless platforms may have cold starts (1-3 seconds delay on first request)
   - Use a cron job to ping your backend every 5-10 minutes to keep it warm
   - Service: https://cron-job.org (free)

3. **Database:**
   - Keep using Supabase (already working well)
   - No need to migrate database

4. **File Uploads:**
   - Serverless platforms don't support persistent file storage
   - Consider using cloud storage (Cloudinary, AWS S3, etc.) for receipts
   - Or keep using Render only for file storage

---

## 🎯 MY RECOMMENDATION

**Deploy to Leapcell.io** because:
1. ✅ No credit card required
2. ✅ No code changes needed
3. ✅ SMTP works without restrictions
4. ✅ Free PostgreSQL included (backup option)
5. ✅ Easy GitHub deployment
6. ✅ Recently recommended by developers (2025-2026)
7. ✅ Supports Node.js natively

**Alternative:** If Leapcell doesn't work, use **Vercel** (requires converting Express to serverless functions, but very reliable).

---

**Status:** Ready to deploy to Leapcell.io or Vercel
**Action Required:** Choose platform and start deployment
