# Classroom Command Center - Setup Guide

## Overview
The Classroom Command Center is a secure Streamlit application that allows Teacher Aides to monitor student assignments from Canvas LMS.

## Security Features
- **Password Protection**: The app requires a password before any data is displayed
- **No Hardcoded Tokens**: All sensitive API tokens are stored in a secure secrets file
- **Protected Secrets**: The `.streamlit/secrets.toml` file is automatically gitignored by Streamlit

## Setup Instructions

### 1. Install Dependencies
```bash
pip install streamlit pandas requests
```

### 2. Configure Secrets
1. Navigate to `/Users/mdickey/Documents/Scripts/.streamlit/`
2. Edit the `secrets.toml` file
3. **IMPORTANT**: Change the default password:
   ```toml
   [passwords]
   auth = "YourSecurePasswordHere"
   ```
4. The student tokens have been pre-populated from your original file
5. If you need to update any tokens, edit the `[tokens]` section

### 3. Run the Application
```bash
cd /Users/mdickey/Documents/Scripts
streamlit run class_monitor.py
```

### 4. Using the App

1. **Login**: Enter the password you set in `secrets.toml`
2. **Select Timeframe**: Choose how far ahead to view assignments:
   - End of This Week
   - End of Next Week (2 Weeks)
   - 3 Weeks Out
   - All Tasks
3. **Sync Data**: Click the "🔄 Sync All Students" button
4. **View Results**:
   - **Master List**: See all tasks from all students in one table
   - **Student Breakdown**: View tasks organized by individual student

## File Structure
```
/Users/mdickey/Documents/Scripts/
├── class_monitor.py                    # Main application
├── .streamlit/
│   ├── secrets.toml                    # Your actual secrets (DO NOT SHARE)
│   └── secrets.toml.template           # Template for reference
└── CLASSROOM_SETUP.md                  # This file
```

## Students Monitored
The app monitors these 11 students:
- DavidS
- Jonathan
- DavidM
- Anirudh
- Alex
- Jesus
- Olivia
- Angel
- Tava
- Heidy
- Melody

## Troubleshooting

### "Password incorrect" Error
- Check that you've updated the password in `.streamlit/secrets.toml`
- Make sure you're entering it exactly as stored (passwords are case-sensitive)

### "Token not found" Warning
- Verify that all student names in the `STUDENTS` list match the keys in `secrets.toml`
- Check for typos in student names

### "Access Denied (Check Token)" Error
- The Canvas API token for that student may be expired or invalid
- Generate a new token from Canvas: Account > Settings > New Access Token
- Update the token in `secrets.toml`

## Security Best Practices
1. **Never commit** `secrets.toml` to version control
2. **Change the default password** immediately
3. **Rotate tokens** periodically for security
4. **Limit access** to the machine running this application
5. **Use strong passwords** for the app authentication

## API Details
- **Endpoint**: `https://wvm.instructure.com/api/v1/planner/items`
- **Method**: Direct REST API calls using `requests.get()`
- **Authentication**: Bearer token in Authorization header

## Deployment to Streamlit Community Cloud

### Quick Deployment Steps

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Classroom Command Center"
   git remote add origin https://github.com/YOUR_USERNAME/classroom-command-center.git
   git branch -M main
   git push -u origin main
   ```

2. **Deploy on Streamlit**:
   - Go to [share.streamlit.io](https://share.streamlit.io)
   - Sign in with GitHub
   - Click "New app"
   - Select your repository and `class_monitor.py`
   - Click "Deploy"

3. **Add Secrets**:
   - In Streamlit Cloud, go to Settings → Secrets
   - Copy contents from your local `.streamlit/secrets.toml`
   - Paste and save

4. **Share the URL**:
   - Your app will be live at: `https://YOUR_USERNAME-classroom-command-center.streamlit.app`
   - Share with Teacher Aides!

### Important Notes for Deployment

- The `.gitignore` file ensures `secrets.toml` is never committed to GitHub
- Secrets are managed securely through Streamlit Cloud's encrypted secrets manager
- The app will automatically restart when you update secrets in the cloud dashboard
- Free tier includes sufficient resources for this use case

## Support
If you encounter issues, check:
1. Network connectivity to `wvm.instructure.com`
2. Token validity in Canvas
3. Streamlit logs in the terminal (local) or Streamlit Cloud logs (deployed)
