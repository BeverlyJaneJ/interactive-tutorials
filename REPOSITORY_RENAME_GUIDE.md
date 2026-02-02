# Repository Rename Guide: interactive-tutorials → docs-ai-bev

This guide outlines the steps needed to rename the GitHub repository from `BeverlyJaneJ/interactive-tutorials` to `BeverlyJaneJ/docs-ai-bev`.

**Note**: Only the repository name changes; the owner namespace (`BeverlyJaneJ`) remains the same.

## Important Note

**Renaming a GitHub repository can only be done through the GitHub web interface by someone with admin/owner permissions.** This cannot be automated through git commands or GitHub Actions.

## Step 1: Rename the Repository on GitHub

1. Go to the repository on GitHub: https://github.com/BeverlyJaneJ/interactive-tutorials
2. Click on **Settings** (you must be the repository owner or have admin access)
3. Scroll down to the **Repository name** section
4. Enter the new repository name: `docs-ai-bev` (just the repository name, not the full path)
5. Click **Rename**

The new repository URL will be: `https://github.com/BeverlyJaneJ/docs-ai-bev`

⚠️ **Note**: GitHub will automatically set up redirects from the old repository name to the new one, so existing links will continue to work.

## Step 2: Update Local Repository

**⚠️ IMPORTANT**: You must run these commands from inside your local repository directory.

After renaming on GitHub, anyone with a local clone needs to update their git remote URL:

### If you're not already in the repository directory:

```bash
# Navigate to your local repository directory
# Replace the path below with wherever you cloned the repository
cd /path/to/interactive-tutorials

# OR if you cloned it to your home directory:
cd ~/interactive-tutorials
```

### Then run these commands:

```bash
# 1. Check current remote URL (should show the old repository name)
git remote -v

# 2. Update the remote URL to the new repository name
git remote set-url origin https://github.com/BeverlyJaneJ/docs-ai-bev.git

# 3. Verify the change (should now show the new repository name)
git remote -v
```

**Expected output after step 3:**
```
origin  https://github.com/BeverlyJaneJ/docs-ai-bev.git (fetch)
origin  https://github.com/BeverlyJaneJ/docs-ai-bev.git (push)
```

## Step 3: Things That Will Automatically Work

GitHub provides automatic redirects, so these will continue to work without changes:
- Existing clones will continue to push/pull (but should update their remote URL as shown above)
- Old URLs in documentation will redirect to the new repository
- Issues, pull requests, and other repository content remain intact

## Step 4: Optional Updates After Rename

### Repository Description
You may want to update the repository description on GitHub to reflect its new name/purpose.

### README Updates (Optional)
The current README.md doesn't reference the repository name directly, so no updates are strictly necessary. However, you could add a note about the rename if desired.

### CI/CD Workflows
The GitHub Actions workflows in `.github/workflows/` don't reference the repository name explicitly, so they will continue to work after the rename.

## What This Codebase Already Does Well

✅ **No hardcoded repository references**: The codebase doesn't have hardcoded references to the repository name in:
- Configuration files (index.json, etc.)
- GitHub Actions workflows
- Documentation files

✅ **External hosting is independent**: The guides are hosted at `interactive-learning.grafana.net`, which is independent of the GitHub repository name.

✅ **Relative paths**: All internal references use relative paths rather than absolute GitHub URLs.

## Troubleshooting

### If you get "fatal: not a git repository"
This means you're not in a git repository directory. You need to navigate to your local clone of the repository first using `cd /path/to/interactive-tutorials` before running git commands.

### If you get "remote: Repository not found"
This means your local git remote still points to the old URL. Follow Step 2 above to update it.

### If you have open pull requests
Open pull requests will automatically be associated with the new repository name. No action needed.

### If you have the repository forked
Forks do not automatically rename. If you have forks, you'll need to update their remotes to point to the renamed upstream repository.

## Frequently Asked Questions

### Q: Do I have to be in the local repo directory to run the git remote command?
**A: Yes!** All git commands must be run from within your local repository directory. Use `cd /path/to/interactive-tutorials` to navigate there first.

### Q: How do I know if I'm in the right directory?
**A:** Run `pwd` (on Mac/Linux) or `cd` (on Windows) to see your current directory. You should see the repository name in the path. You can also run `git status` - if you're in a git repository, it will show the branch and status; if not, you'll get an error.

### Q: What if I don't know where I cloned the repository?
**A:** Try these common locations:
- `~/interactive-tutorials` (your home directory)
- `~/Documents/interactive-tutorials`
- `~/Documents/GitHub/interactive-tutorials`
- Or search for it: `find ~ -name "interactive-tutorials" -type d 2>/dev/null`

### Q: Can I run the git remote command before the repository is renamed on GitHub?
**A:** No, wait until the repository is renamed on GitHub first. Otherwise, pushing/pulling will fail because the new URL doesn't exist yet.

## Summary

The actual repository rename is a simple process that takes just a few clicks in the GitHub web interface. The main thing to remember is to update local clones' remote URLs afterward. This repository is well-structured and doesn't require any code changes to support the rename.
