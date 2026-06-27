
To move uncommitted changes from `main` to a new branch using a stash, use the following sequence of Git commands. 

### Option 1: Standard Multi-Step Process

This is the most common manual approach to ensure your changes are safely stashed before switching branches. [GitHub Gist](https://gist.github.com/8378720). 


1. **Stash your changes:** Save your current progress to the stash stack.

```bash
git stash push -m "description of changes"
```


Use code with caution.

_(Note: Using `git stash push` is the modern replacement for the deprecated 
`git stash save`.)_

2. **Create and switch to the new branch:** Base it off your current `main` branch.

```bash
git checkout -b <new-branch-name>
```

Use code with caution.

3. **Apply the stashed changes:** Bring the stashed work into your new branch.

```bash
git stash apply
```


Use code with caution.

_(Use `git stash pop` instead of `apply` if you want to automatically delete the stash after applying it.)_ 

### Option 2: The Direct "Branch from Stash" One-Liner

If you have already stashed your work, you can create a new branch and apply those changes in a single command. [Scaler Topics](https://www.scaler.com/topics/git/git-stash-branch/). 

```bash
git stash branch <new-branch-name>
```

Use code with caution.

- **What it does:** Creates a new branch starting from the exact commit where you originally ran `git stash`, checks it out, and then "pops" (applies and deletes) the latest stash onto it.
- **Best for:** Avoiding potential merge conflicts that might occur if the `main` branch has changed significantly since you stashed your work.

Key Command Comparison  

|Command|Action|Recommended Use|
|---|---|---|
|`git stash apply`|Restores changes but **keeps** them in the stash stack.|Use if you might need to apply these same changes elsewhere.|
|`git stash pop`|Restores changes and **deletes** them from the stash stack.|Standard for moving work to a single new destination.|
|`git stash list`|Shows all saved stashes and their indexes (e.g., `stash@{0}`).|Use to identify a specific stash if you have multiple.|

## The 4-Step "Clean Slate" Reset (If Git breaks or corrupts)

If you ever see a `fatal: loose object is corrupt` error, or if the repository tracking metadata gets completely tangled, use this sequence to rebuild Git without touching your markdown files:


```bash
# 1. Nuke the hidden Git tracking folder (Your actual notes remain 100% safe)
rm -rf .git

# 2. Re-initialize Git and link your remote repository back up
git init
git remote add origin https://github.com


# 3. Fetch a clean, uncorrupted history from GitHub 

git fetch origin 

# 4. Point Git to match GitHub while keeping all your current local text edits 

git reset --mixed origin/main
```





## Git Rebase

When Your working directory is completely clean, which makes this very straightforward. You can now pull the remote changes and push your work without worrying about uncommitted file conflicts. [[1](https://medium.com/@mohammadatifhossain/git-branch-merging-made-simple-a-step-by-step-guide-to-combining-code-changes-3544632dafcb), [2](https://komodor.com/learn/how-to-fix-fatal-refusing-to-merge-unrelated-histories-error/), [3](https://stackoverflow.com/questions/62176095/how-do-i-resolve-a-branch-and-orgin-branch-that-have-diverged)]

Run these two commands in your terminal to complete the sync:

## Step 1: Rebase Local Commits

Pull the 5 remote commits and place your 17 local commits cleanly on top of them.



```bash
git pull --rebase origin main
```



## Step 2: Push to Remote

Once the rebase finishes successfully, push your combined history up to your remote repository.


```bash
git push origin main
```

