# 🚀 Deployment Guide for Håndtverkeren

Your app is now ready to deploy! Choose one of the following platforms:

---

## ✅ **Option 1: Netlify (Recommended - Easiest)**

### Method A: Drag & Drop (No Git Required)

1. **Build your app locally:**
   ```bash
   npm run build
   ```
   This creates a `dist` folder with your production files.

2. **Go to Netlify:**
   - Visit [netlify.com](https://www.netlify.com/)
   - Sign up or log in (free account)

3. **Deploy:**
   - Drag the `dist` folder into the Netlify drop zone
   - Wait 30 seconds
   - Get your live URL! 🎉

### Method B: Connect via Git (Automatic Updates)

1. **Push your code to GitHub/GitLab/Bitbucket**

2. **Import to Netlify:**
   - Click "New site from Git"
   - Connect your repository
   - Build settings:
     - **Build command:** `npm run build`
     - **Publish directory:** `dist`
   - Click "Deploy site"

3. **Auto-deploys:** Every push to your repo will auto-deploy!

---

## ✅ **Option 2: Vercel (Great for React)**

1. **Install Vercel CLI (optional):**
   ```bash
   npm i -g vercel
   ```

2. **Deploy:**
   ```bash
   vercel
   ```
   Follow the prompts - it auto-detects Vite settings!

**Or use the web interface:**
- Visit [vercel.com](https://vercel.com/)
- Import your Git repository
- Click Deploy (auto-detects everything!)

---

## ✅ **Option 3: GitHub Pages (Free)**

1. **Install gh-pages:**
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Add to package.json scripts:**
   ```json
   "scripts": {
     "build": "vite build",
     "predeploy": "npm run build",
     "deploy": "gh-pages -d dist"
   }
   ```

3. **Add base path to vite.config.ts:**
   ```ts
   export default defineConfig({
     base: '/your-repo-name/',
     // ... rest of config
   })
   ```

4. **Deploy:**
   ```bash
   npm run deploy
   ```

5. **Enable GitHub Pages:**
   - Go to repo Settings → Pages
   - Source: `gh-pages` branch
   - Your site: `https://username.github.io/repo-name/`

---

## 🎨 **Custom Domain (Optional)**

### Netlify:
1. Go to Site Settings → Domain Management
2. Add custom domain
3. Follow DNS instructions

### Vercel:
1. Go to Project Settings → Domains
2. Add your domain
3. Update DNS records

---

## 🔧 **Environment Variables**

If you add backend/API features later:

**Netlify:**
- Site Settings → Environment Variables

**Vercel:**
- Project Settings → Environment Variables

Prefix with `VITE_` for client-side access:
```bash
VITE_API_URL=https://api.example.com
```

Access in code:
```ts
const apiUrl = import.meta.env.VITE_API_URL;
```

---

## 📊 **Build Output**

Your build creates:
- `dist/` folder with optimized HTML, CSS, JS
- Minified and compressed assets
- Ready for production!

---

## ⚡ **Quick Deploy Commands**

```bash
# Build locally
npm run build

# Preview build locally
npm run preview

# Deploy to Vercel
vercel

# Deploy to Netlify (with CLI)
netlify deploy --prod
```

---

## 🐛 **Troubleshooting**

**Routes not working?**
- ✅ The `_redirects` file (Netlify) and `vercel.json` are already configured
- These handle React Router client-side routing

**Build fails?**
- Check Node version (use 18+ or 20+)
- Run `npm install` first
- Clear cache: `rm -rf node_modules dist && npm install`

**Images not loading?**
- Make sure images are in `public/` or imported in components
- Check image paths are correct

---

## 🎉 **You're All Set!**

Your app is production-ready. Choose your platform and deploy in minutes!

**Need help?**
- Netlify Docs: https://docs.netlify.com
- Vercel Docs: https://vercel.com/docs
- Vite Docs: https://vitejs.dev/guide/build.html
