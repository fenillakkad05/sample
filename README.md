# Git Practical: Local Repository to GitHub, Branching, Merge and Graph

## Step 1: Create local repository and index.html

```bash
mkdir gitSample
cd gitSample

git init
git branch -M main

echo "<h1>Welcome to Git Sample</h1>" > index.html

git status
git add index.html
git commit -m "Add index.html"
```

## Step 2: Create and switch to development branch

```bash
# Check existing branches
git branch

# Create development branch
git branch development

# Switch to development using checkout
git checkout development

# Check current branch
git branch
```

Alternative modern command to create and switch in one step (use this instead of the two commands above if preferred):

```bash
git switch -c development
```

**Important:** Use either method, not both, because the branch should only be created once.

## Step 3: Create about.html and commit it

```bash
echo "<h1>About Us</h1>" > about.html

git status
git add about.html
git commit -m "Add about.html"
```

## Step 4: Connect to GitHub

First, create a GitHub repository named `gitSample`. Do not initialize it with a README.

```bash
git remote add origin https://github.com/YOUR_USERNAME/gitSample.git

git remote -v
```

Replace `YOUR_USERNAME` with your actual GitHub username.

## Step 5: Push both branches to GitHub

```bash
# Switch to main
git checkout main
git branch
git push -u origin main

# Switch to development
git switch development
git branch
git push -u origin development
```

## Step 6: Add README.md on GitHub

On the GitHub website:

1. Open the `gitSample` repository.
2. Select the `main` branch.
3. Click **Add file → Create new file**.
4. Name the file `README.md`.
5. Add some text and click **Commit changes**.

## Step 7: Pull README.md into local main

```bash
git checkout main
git pull origin main
```

## Step 8: Merge development into main

```bash
# Confirm you are on main
git branch

# Merge development into main
git merge development
```

If Vim opens for the merge message, press `Esc`, type `:wq`, and press `Enter`.

Check the files:

```bash
ls
git status
```

Expected files:

```text
README.md
about.html
index.html
```

## Step 9: Push the merged main branch

```bash
git push origin main
```

## Step 10: Delete development branch

Delete the branch only after the merge and push succeed.

```bash
# Make sure you are on main
git switch main

# Delete local development branch
git branch -d development

# Delete remote development branch
git push origin --delete development

# Refresh remote branch references
git fetch --prune
```

## Step 11: Final verification

```bash
# Check local branches
git branch

# Check remote branches
git branch -r

# Check files in main
git ls-tree --name-only main

# Check working tree
git status

# Display commit graph
git log --oneline --graph --all --decorate
```

### Expected final result

- Only local branch: `main`
- Only remote branch: `origin/main`
- Files in `main`: `index.html`, `about.html`, `README.md`
- Working tree: clean
- GitHub: merged changes pushed successfully
