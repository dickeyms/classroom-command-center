# Next Steps - Deploy Your App

## Your GitHub: dickeyms

Everything is ready! Follow these steps to deploy:

## Step 1: Create GitHub Repository

1. Go to: https://github.com/new
2. Repository name: `west-valley-command-center`
3. **IMPORTANT**: Set to **Private** (protects your workflow)
4. Do NOT check any initialization options (README, .gitignore, license)
5. Click "Create repository"

## Step 2: Push Your Code

Run these commands in your terminal:

```bash
cd /Users/mdickey/Documents/Scripts

# Add the GitHub remote
git remote add origin https://github.com/dickeyms/west-valley-command-center.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 3: Deploy on Streamlit Community Cloud

1. Go to: https://share.streamlit.io
2. Click "Sign in with GitHub"
3. Click "New app"
4. Fill in:
   - **Repository**: dickeyms/west-valley-command-center
   - **Branch**: main
   - **Main file path**: class_monitor.py
5. Click "Deploy!"

## Step 4: Add Your Secrets (CRITICAL!)

While the app is deploying:

1. Click the Settings (⚙️) icon
2. Click "Secrets" in the sidebar
3. Copy and paste this into the secrets editor:

```toml
[passwords]
auth = "password"

[tokens]
DavidS = "4943~HAVHHLr9J4TmT7YQCQ8yEcCnCPtCZMuRW8UEauFfNuyNtkDMM6URwLaNKatx3BHD"
Jonathan = "4943~TvENvyHyGKD4fmmx3PTx8zPPC6zREAAPEf2Y8LhHhREuVWRYMfYQHBJEuHYZMm7x"
DavidM = "4943~G8MTZGa7VTVyUkWeUWHMzU8DFBUtKEEXVPKFBRCz8cGaZKNx6rr4rf3aVUczUHkT"
Anirudh = "4943~rGwyLF24BvBGZMLnGHmzayUHxRkkTPNXCEtcYNDWG8c9K7n24FWu6BxaBN9XcHJ9"
Alex = "4943~v2zxTwckKuyhXNLvzB3MDAkCYavvkWJREfn6893k4nVnGQ4HCrFH64B4fUzAVKeU"
Jesus = "4943~xGMXnCQXrhmPHEkA39JvGHCMwHh77z2HzzaLkZYVFJcnXLK9CnVLNyTULFYARBL7"
Olivia = "4943~rF6wMAeTXvUQhaCQBKT2e6TBUztLZKLXYzBFaEtQ9zXGJzD8v7B2vcrm3NLLa8tx"
Angel = "4943~BvfJAmwG4kXKJhXt4UnWnWzz89PK6M2vk6yfn2YPW9aZazRhQxmCLZ7LM2A83TTM"
Tava = "4943~fJY4HvKLZztHVU8PAnwR2Zfy6ZryzBUY6yFmxLYttXQ6QTXQNLR9WCexYZ2t8xhn"
Heidy = "4943~nFfQPQTkwY8nDELGyU4hCCcJZNv2XHXvY93Bcu9BNEEVk3f9a4MmRhzRYmGVVraK"
Melody = "4943~QckXF9X4QKWnQVuZuxJhPnrf4CDN3HZk3t4PfAuekGuxwPPvnGXPQDhF3w9C3YT6"
```

4. Click "Save"
5. The app will restart automatically

## Step 5: Access Your Live App

Your app will be available at:
**https://dickeyms-west-valley-command-center.streamlit.app**

(Or a custom URL if Streamlit suggests one)

## Step 6: Share with Teacher Aides

1. Send them the URL
2. Give them the password: `password`
3. They can bookmark it for daily use!

## Quick Reference

### Your App URL (after deployment)
https://dickeyms-west-valley-command-center.streamlit.app

### Login Password
`password`

### Change Password Later
Update in Streamlit Cloud: Settings → Secrets → Edit `auth` value

### Update Code
```bash
git add .
git commit -m "Description of changes"
git push
```
Streamlit will auto-deploy!

## Security Verified ✓

- ✅ secrets.toml is NOT in git (confirmed via .gitignore)
- ✅ No tokens in source code
- ✅ Password protection enabled
- ✅ Repository will be private

## Cost

**FREE** - Streamlit Community Cloud is free for private apps!

---

Need help? See DEPLOY.md for detailed troubleshooting.
