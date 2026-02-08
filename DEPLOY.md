# Deployment Guide

## GitHub Repository
**URL:** https://github.com/karthvp/agentops-landing

Repository is live and public.

## Cloudflare Pages Deployment

### Option 1: Manual Deployment (Recommended for now)

1. **Login to Cloudflare Dashboard**
   - Go to: https://dash.cloudflare.com
   - Navigate to: Workers & Pages → Create application → Pages → Connect to Git

2. **Connect GitHub Repository**
   - Select repository: `karthvp/agentops-landing`
   - Branch: `main`

3. **Configure Build Settings**
   - Framework preset: `None` (static HTML)
   - Build command: (leave blank)
   - Build output directory: `/`
   - Root directory: `/`

4. **Deploy**
   - Click "Save and Deploy"
   - Wait for build to complete (~30 seconds)

5. **Custom Domain (Optional)**
   - After deployment, go to Custom Domains
   - Add: `agentops.dev` or similar
   - Configure DNS (Cloudflare will provide CNAME records)

### Option 2: CLI Deployment (If wrangler is configured)

```bash
cd /Users/athena/.openclaw/workspace/vault/100-Business-Ideas/sprints/KAR-34-agentops/tier2-sprint-7

# Install wrangler if needed
npm install -g wrangler

# Login to Cloudflare
wrangler login

# Deploy
wrangler pages deploy . --project-name=agentops-landing
```

## Post-Deployment Checklist

- [ ] Verify landing page loads correctly
- [ ] Test form submission (use real email)
- [ ] Confirm Formspree integration works
- [ ] Check mobile responsiveness
- [ ] Set up custom domain (if available)
- [ ] Configure Plausible analytics (update domain in script tag)
- [ ] Add DNS records if using custom domain

## Expected Deployment URL

After Cloudflare Pages deployment, you'll get:
- **Cloudflare URL:** `agentops-landing.pages.dev` (or similar)
- **Custom domain:** Configure after deployment

## Form Integration

**Formspree Endpoint:** https://formspree.io/f/mvggabpw

All form submissions will be sent here. You can:
- View submissions at: https://formspree.io/forms/mvggabpw/submissions
- Export to CSV
- Set up email notifications

## Analytics

**Plausible Analytics** is configured in the HTML. Once deployed:
1. Sign up at https://plausible.io (or self-host)
2. Add your deployed domain
3. Verify tracking is working

## Monitoring

Check these metrics daily:
- Cloudflare Analytics (traffic, geography)
- Formspree submissions (conversion rate)
- Plausible events (if configured)

## Updates

To update the site:
```bash
cd /Users/athena/.openclaw/workspace/vault/100-Business-Ideas/sprints/KAR-34-agentops/tier2-sprint-7
git add .
git commit -m "Update landing page"
git push origin main
```

Cloudflare Pages will auto-deploy on push to main.
