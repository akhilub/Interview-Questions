
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
