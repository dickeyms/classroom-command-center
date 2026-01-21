# Quick Deployment Guide

## Deploy West Valley Command Center to Streamlit Community Cloud

### Prerequisites
- GitHub account
- Streamlit Community Cloud account (free - sign up with GitHub at [share.streamlit.io](https://share.streamlit.io))

### Step-by-Step Deployment

#### 1. Initialize Git Repository

```bash
cd /Users/mdickey/Documents/Scripts
git init
git add .
git commit -m "Initial commit: West Valley Command Center"
```

#### 2. Create GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `west-valley-command-center` (or your choice)
3. Set to **Private** (recommended for security)
4. Do NOT initialize with README, .gitignore, or license (you already have these)
5. Click "Create repository"

#### 3. Push to GitHub

```bash
git remote add origin https://github.com/YOUR_USERNAME/west-valley-command-center.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

#### 4. Deploy on Streamlit Community Cloud

1. Visit [share.streamlit.io](https://share.streamlit.io)
2. Click "Sign in with GitHub"
3. Authorize Streamlit to access your repositories
4. Click "New app" button
5. Fill in the form:
   - **Repository**: Select `YOUR_USERNAME/west-valley-command-center`
   - **Branch**: `main`
   - **Main file path**: `class_monitor.py`
   - **App URL**: Choose a custom URL (optional)
6. Click "Deploy!"

#### 5. Configure Secrets in Streamlit Cloud

**CRITICAL STEP - The app won't work without this!**

1. While your app is deploying, click on "Settings" (⚙️ icon)
2. Click on "Secrets" in the left sidebar
3. Copy the entire contents of your local `.streamlit/secrets.toml` file
4. Paste into the secrets editor
5. It should look like this:

```toml
[passwords]
auth = "password"

[tokens]
DavidS = "4943~HAVHHLr..."
Jonathan = "4943~TvENvyHy..."
# ... all other students
```

6. Click "Save"
7. The app will automatically restart with the secrets

#### 6. Access Your Live App

Your app will be available at:
```
https://YOUR_USERNAME-west-valley-command-center.streamlit.app
```

Or your custom URL if you chose one.

### Sharing with Teacher Aides

1. Copy the app URL
2. Share it with your Teacher Aides
3. Give them the password (set in secrets)
4. They can bookmark the URL for easy access

### Updating the App

When you make changes locally:

```bash
git add .
git commit -m "Description of changes"
git push
```

Streamlit Cloud will automatically detect the changes and redeploy your app.

### Updating Secrets

To change passwords or tokens:

1. Go to your app on [share.streamlit.io](https://share.streamlit.io)
2. Click Settings → Secrets
3. Edit the secrets
4. Click Save
5. App will restart with new secrets

### Monitoring

- **View logs**: Click "Manage app" → "Logs" to see real-time logs
- **Reboot app**: Click the three dots (⋮) → "Reboot app" if needed
- **Analytics**: See usage stats in the Streamlit Cloud dashboard

### Security Notes

✅ **Safe to commit** (already in repo):
- `class_monitor.py`
- `requirements.txt`
- `.gitignore`
- `README.md`
- `.streamlit/secrets.toml.template`

❌ **NEVER commit**:
- `.streamlit/secrets.toml` (already protected by .gitignore)
- Any file containing actual tokens or passwords

### Troubleshooting

**App shows "Please enter password" but won't accept it:**
- Check that secrets are properly formatted in Streamlit Cloud
- Ensure there are no extra spaces or quotes
- Verify you're using the exact password from the secrets

**"Token not found" errors:**
- Check all 11 student names are in the `[tokens]` section
- Names must match exactly (case-sensitive)

**App crashes on startup:**
- Check the logs in Streamlit Cloud dashboard
- Verify `requirements.txt` is present and correct
- Ensure secrets are saved properly

**API timeout or "Access Denied" errors:**
- Canvas tokens may be expired
- Generate new tokens in Canvas: Account → Settings → New Access Token
- Update the tokens in Streamlit Cloud secrets

### Cost

**Streamlit Community Cloud is FREE** and includes:
- 1 private app (or unlimited public apps)
- 1 GB of resources per app
- Community support

This is more than sufficient for your use case!

### Need Help?

- Streamlit Docs: [docs.streamlit.io](https://docs.streamlit.io)
- Community Forum: [discuss.streamlit.io](https://discuss.streamlit.io)
