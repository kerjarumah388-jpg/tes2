# 🚀 Deployment Guide

This guide will help you deploy the Kalkulator Sederhana application to production.

## 📋 Prerequisites

Before deploying, make sure you have:
- ✅ A Git account (GitHub, GitLab, or Bitbucket)
- ✅ This project pushed to a Git repository
- ✅ Node.js and npm/bun installed locally

## 🌐 Deploy to Vercel (Recommended)

Vercel is the easiest way to deploy Next.js applications. Here's how to do it:

### Option 1: Deploy via Vercel Dashboard (Easiest)

1. **Push your code to Git**
   ```bash
   git init
   git add .
   git commit -m "Initial commit - Calculator app"
   git branch -M main
   git remote add origin https://github.com/your-username/calculator-app.git
   git push -u origin main
   ```

2. **Create a Vercel Account**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub, GitLab, or email

3. **Import Your Project**
   - Click **"Add New Project"** in the dashboard
   - Find and import your repository
   - Vercel will automatically detect Next.js

4. **Configure Settings**
   - Project name: `calculator-app` (or your preferred name)
   - Framework Preset: Next.js
   - Build Command: `npm run build`
   - Output Directory: `.next`
   - Install Command: `npm install`

5. **Deploy**
   - Click **"Deploy"**
   - Wait for the build to complete (typically 1-2 minutes)
   - Your app will be live at `https://calculator-app.vercel.app`

### Option 2: Deploy via Vercel CLI

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy Your App**
   ```bash
   # Preview deployment
   vercel

   # Production deployment
   vercel --prod
   ```

### Option 3: Automatic Deployments (Git Integration)

1. **Connect Your Git Repository**
   - In Vercel dashboard, connect your Git account
   - Import the repository

2. **Set Up Automatic Deployments**
   - Every push to `main` branch triggers a production deployment
   - Every push to other branches triggers a preview deployment

3. **Push Changes**
   ```bash
   git add .
   git commit -m "Update calculator features"
   git push origin main
   ```

## 📝 Environment Variables

For this simple calculator app, no environment variables are required. However, if you add features later:

1. **Create `.env` file locally**
   ```bash
   cp .env.example .env
   ```

2. **Add to Vercel**
   - Go to Project Settings → Environment Variables
   - Add each variable name and value
   - Select the appropriate environments (Production, Preview, Development)
   - Redeploy your application

## 🔄 Update Your Deployed App

### Method 1: Git Push (Recommended)
```bash
# Make your changes
git add .
git commit -m "Add new feature"
git push origin main
# Vercel automatically deploys the changes
```

### Method 2: Vercel CLI
```bash
vercel --prod
```

## 🎯 Post-Deployment Checklist

After deployment, verify:
- ✅ Application loads at your Vercel URL
- ✅ All calculator operations work correctly
- ✅ Responsive design works on mobile devices
- ✅ Dark/light mode switches properly
- ✅ No console errors in browser
- ✅ All buttons are functional

## 🌍 Custom Domain Setup (Optional)

### Using a Custom Domain on Vercel

1. **Purchase a Domain**
   - Buy from any domain registrar (Namecheap, GoDaddy, etc.)

2. **Add Domain in Vercel**
   - Go to Project Settings → Domains
   - Enter your domain (e.g., `calculator.com` or `app.calculator.com`)

3. **Update DNS Records**
   - Follow Vercel's instructions for your registrar
   - Typically add a CNAME record pointing to `cname.vercel-dns.com`

4. **SSL Certificate**
   - Vercel automatically provisions SSL for free
   - Your site will be accessible over HTTPS

## 🐳 Docker Deployment (Alternative)

For self-hosted deployment or other platforms:

### Build and Run Locally
```bash
# Build the Docker image
docker build -t calculator-app .

# Run the container
docker run -p 3000:3000 calculator-app
```

### Deploy to Docker Hub
```bash
# Login to Docker Hub
docker login

# Tag your image
docker tag calculator-app your-username/calculator-app:latest

# Push to Docker Hub
docker push your-username/calculator-app:latest
```

### Deploy to Cloud Platforms

**Heroku**
```bash
# Install Heroku CLI
npm install -g heroku

# Login
heroku login

# Create app
heroku create calculator-app

# Set buildpack
heroku buildpacks:set https://github.com/heroku/heroku-buildpack-nodejs

# Deploy
git push heroku main
```

**Railway, Render, or similar**
- Most platforms support Next.js directly
- Import from Git repository
- Configure build command: `npm run build`
- Set start command: `npm start`

## 📊 Performance Optimization

### Enable Vercel Analytics (Optional)
1. Install Vercel Analytics package
   ```bash
   npm install @vercel/analytics
   ```

2. Add to your app
   ```bash
   # src/app/layout.tsx
   import { Analytics } from '@vercel/analytics/react'

   // Add <Analytics /> component
   ```

### Optimize Images
- Use Next.js Image component for all images
- Enable automatic optimization in next.config.ts

### Enable Caching
- Static assets are cached by Vercel's CDN
- API responses can be cached using Next.js revalidate

## 🔒 Security Best Practices

1. **Keep Dependencies Updated**
   ```bash
   npm audit
   npm audit fix
   ```

2. **Enable HTTPS** (Automatic on Vercel)
   - Vercel provides free SSL certificates

3. **Environment Variables**
   - Never commit `.env` files
   - Use Vercel's environment variables feature

4. **Rate Limiting** (If adding API routes)
   - Implement rate limiting for API endpoints

## 📈 Monitoring and Logging

### Vercel Dashboard
- View deployment logs
- Monitor performance metrics
- Track error rates
- Analytics for user behavior

### Custom Logging
```typescript
// src/app/api/example/route.ts
export async function GET() {
  console.log('API request received')
  // ... your logic
}
```

## 🆘 Troubleshooting

### Build Failures
- Check the build logs in Vercel dashboard
- Ensure all dependencies are in package.json
- Verify TypeScript and ESLint configurations

### Runtime Errors
- Check browser console for errors
- Review Vercel deployment logs
- Test locally with `npm run build && npm start`

### Performance Issues
- Use Vercel Analytics to identify bottlenecks
- Optimize images and static assets
- Consider using Edge Functions for API routes

## 📚 Additional Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Next.js Deployment](https://nextjs.org/docs/deployment)
- [Docker Best Practices](https://docs.docker.com/develop/dev-best-practices/)
- [Environment Variables Guide](https://vercel.com/docs/projects/environment-variables)

---

For questions or issues, check the [main README.md](README.md) or open an issue on GitHub.
