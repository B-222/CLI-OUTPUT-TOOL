# GitHub Setup Guide

## Step 1: Create a New Repository on GitHub

1. Go to [GitHub](https://github.com) and sign in
2. Click the **"+"** icon in the top-right corner
3. Select **"New repository"**
4. Fill in the details:
   - **Repository name:** `log-filter-tool` (or your preferred name)
   - **Description:** "A CLI tool for filtering and analyzing cloud service logs"
   - **Public** or **Private:** Your choice
   - ❌ **DO NOT** initialize with README (we already have one)
5. Click **"Create repository"**

## Step 2: Set Up Git on Your Local Machine

Open your terminal and navigate to the project folder:

```bash
cd /path/to/your/project
```

## Step 3: Initialize Git and Push to GitHub

Run these commands one by one:

```bash
# Initialize git repository
git init

# Add all files to staging
git add .

# Create your first commit
git commit -m "Initial commit: Log Filter CLI Tool"

# Add your GitHub repository as remote
# Replace YOUR_USERNAME and YOUR_REPO_NAME with your actual values
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 4: Verify Your Repository

1. Go to your GitHub repository URL: `https://github.com/YOUR_USERNAME/YOUR_REPO_NAME`
2. You should see all your files:
   - log_tool.py
   - logs.txt
   - README.md
   - run_proof.txt
   - .gitignore

## Common Git Commands for Future Updates

```bash
# Check status of your files
git status

# Add specific file
git add filename.py

# Add all changed files
git add .

# Commit changes
git commit -m "Description of changes"

# Push to GitHub
git push

# Pull latest changes from GitHub
git pull
```

## Troubleshooting

### Authentication Issues

If you encounter authentication errors, you'll need to set up a Personal Access Token:

1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token
3. Select scopes: `repo` (all)
4. Copy the token
5. Use it as your password when pushing

### Alternative: Use SSH

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Add SSH key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy SSH key to clipboard (macOS)
pbcopy < ~/.ssh/id_ed25519.pub

# Or display it (Linux/Windows)
cat ~/.ssh/id_ed25519.pub
```

Then add the key to GitHub:
1. GitHub Settings → SSH and GPG keys
2. New SSH key
3. Paste your key

Change remote URL to SSH:
```bash
git remote set-url origin git@github.com:YOUR_USERNAME/YOUR_REPO_NAME.git
```

## Adding a Badge to Your README

Add this to the top of your README.md:

```markdown
![Python Version](https://img.shields.io/badge/python-3.6+-blue.svg)
![License](https://img.shields.io/badge/license-Educational-green.svg)
```

## Project Is Now Live! 🎉

Your repository is now available at:
`https://github.com/YOUR_USERNAME/YOUR_REPO_NAME`

Share this link with others to showcase your work!
