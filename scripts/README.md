# 🤖 Auto-Commit Scripts

Automated commit generation scripts for maintaining an active GitHub contribution graph.

## 📋 Overview

This package includes:

- **GitHub Actions Workflow**: Automatically creates commits on a schedule
- **Shell Script**: Main script that runs in the GitHub Action (Linux/Ubuntu)
- **PowerShell Script**: Local testing version for Windows users

## 🚀 Quick Start

### Option 1: Automatic (GitHub Actions) - Recommended

The workflow runs automatically **every Monday at 00:00 UTC** and creates 7 commits.

**No setup needed!** Just commit these files and the workflow will run automatically.

To manually trigger the workflow:

1. Go to your GitHub repository
2. Click **Actions** tab
3. Select **🤖 Auto-Commit Generator** workflow
4. Click **Run workflow**
5. Commits will be created and automatically pushed

### Option 2: Manual Local Testing (Windows PowerShell)

```powershell
# Navigate to your repository root
cd c:\Users\kumar\OneDrive\readme\roshaniist

# Run in test mode (dry run, no actual commits)
.\scripts\auto-commit.ps1 -CommitCount 7 -TestMode

# Create actual commits
.\scripts\auto-commit.ps1 -CommitCount 7

# Then push manually
git push origin main
```

### Option 3: Manual Local Testing (Linux/macOS)

```bash
# Navigate to your repository root
cd /path/to/roshaniist

# Make script executable
chmod +x ./scripts/auto-commit.sh

# Run the script
./scripts/auto-commit.sh 7

# Then push manually
git push origin main
```

## 📊 What Gets Created

Each run creates:

- **7 commits** with different timestamps (spread over 2 days)
- **Updated ACTIVITY_LOG.md** with commit details and timestamps
- **Automatic push** to the main branch

**Example commit messages:**

```
📅 Auto-Commit #1 - Monday, April 21, 2026 at 08:00:00 UTC
📅 Auto-Commit #2 - Monday, April 21, 2026 at 12:00:00 UTC
📅 Auto-Commit #3 - Tuesday, April 22, 2026 at 04:00:00 UTC
... and so on
```

## ⚙️ Configuration

### Adjust Frequency (GitHub Actions)

Edit `.github/workflows/auto-commit.yml`:

```yaml
on:
  schedule:
    # Change this cron expression:
    # Format: minute hour day-of-month month day-of-week
    # Examples:
    # '0 0 * * 1'     = Every Monday at 00:00 UTC
    # '0 0 * * *'     = Every day at 00:00 UTC
    # '0 */6 * * *'   = Every 6 hours
    - cron: "0 0 * * 1"
```

**Cron Cheat Sheet:**

- `0 0 * * 1` = Weekly (Monday)
- `0 0 * * *` = Daily
- `0 */12 * * *` = Every 12 hours
- `30 2 * * 0` = Weekly (Sunday at 2:30 AM)

### Adjust Commit Count

**In GitHub Actions UI:**

- Click "Run workflow" dropdown
- Enter desired count (1-10)

**In Scripts (Manually):**

```powershell
.\scripts\auto-commit.ps1 -CommitCount 10  # 10 commits instead of 7
```

```bash
./scripts/auto-commit.sh 10  # 10 commits instead of 7
```

## 📝 Files Created/Modified

- `.github/workflows/auto-commit.yml` - GitHub Actions workflow
- `scripts/auto-commit.sh` - Main shell script
- `scripts/auto-commit.ps1` - PowerShell version for Windows
- `ACTIVITY_LOG.md` - Log file updated with each run

## 🔐 Security Notes

- The workflow uses GitHub's built-in `GITHUB_TOKEN` - no additional secrets needed
- Bot commits are identified by name "🤖 Auto-Commit Bot"
- All commits are visible in repository history

## ❌ Troubleshooting

### Workflow doesn't run

- Check that `.github/workflows/auto-commit.yml` is committed to main branch
- GitHub Actions must be enabled in repository settings
- Wait for the scheduled time (Mondays 00:00 UTC by default)

### Permission denied on shell script

```bash
chmod +x ./scripts/auto-commit.sh
```

### Git configuration errors

Ensure git is configured:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

## 📌 Use Cases

✅ **Maintain contribution streak**
✅ **Test repository workflows**
✅ **Generate activity history**
✅ **Portfolio demonstration**
✅ **Continuous integration testing**

## 🎯 Features

- ✅ Automatic weekly scheduling
- ✅ Manual trigger via GitHub Actions UI
- ✅ Customizable commit count (1-10)
- ✅ Realistic timestamp distribution
- ✅ Activity log tracking
- ✅ Cross-platform support (Windows/Linux/macOS)
- ✅ Proper git commit dating
- ✅ Auto-push to repository

## 📖 Example Workflow Run

```
✓ Commit #1 created at 2026-04-21 08:00:00
✓ Commit #2 created at 2026-04-21 12:00:00
✓ Commit #3 created at 2026-04-21 16:00:00
✓ Commit #4 created at 2026-04-22 00:00:00
✓ Commit #5 created at 2026-04-22 04:00:00
✓ Commit #6 created at 2026-04-22 08:00:00
✓ Commit #7 created at 2026-04-22 12:00:00

✓ Successfully created 7 commits
✓ Activity log updated
✓ Changes pushed to repository
🎉 Auto-Commit Generation Complete!
```

## 🤝 Contributing

Feel free to modify these scripts for your needs!

## 📄 License

Feel free to use and modify these scripts as needed.
