

To move uncommitted changes from `main` to a new branch using a stash, use the following sequence of Git commands. 

Option 1: Standard Multi-Step Process

This is the most common manual approach to ensure your changes are safely stashed before switching branches. [GitHub Gist](https://gist.github.com/8378720). 

1. **Stash your changes:** Save your current progress to the stash stack.

    
    ```bash
    git stash push -m "description of changes"
    ```
    
    Use code with caution.
    
    _(Note: Using `git stash push` is the modern replacement for the deprecated `git stash save`.)_
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
    
    _(Use `git stash pop` instead of `apply` if you want to automatically delete the stash after applying it.)_ ![Stack Overflow]

Option 2: The Direct "Branch from Stash" One-Liner

If you have already stashed your work, you can create a new branch and apply those changes in a single command. [Scaler Topics](https://www.scaler.com/topics/git/git-stash-branch/). 


```bash
git stash branch <new-branch-name>
```

Use code with caution.

- **What it does:** Creates a new branch starting from the exact commit where you originally ran `git stash`, checks it out, and then "pops" (applies and deletes) the latest stash onto it.
- **Best for:** Avoiding potential merge conflicts that might occur if the `main` branch has changed significantly since you stashed your work.

Key Command Comparison ![Refine](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAABAlBMVEUJCQv///9a24tJ2J461rB7e3xv3nJ84GNq3XhV2pE91qxB16jU1NRZWVojIySL4lGB4V1232ll3X5i3IFP2Zc21bSW5ESQ40t54Gds3nVe24VS2ZNN2ZpD16Uz1bmOjo8uLjA4ODkXFxlHZyKGzT+d5TyO404rQBxDbzASGxNqymIjPyRDllwvrpEaY1pNTU7Hx8dkZGVxpC2T0jQ6XCd8x0YzVCdywU0tTShou1MnRyhftlmC0UoUIhhRpVlQgzRZkTpXuGgyakEaKBdeqk5OsGpTmEk/cjhMl1E+lWFCtoEfZFMVLiU4pXwOIR8toocxlHIXRT08xZoqgmcdUkIvvaJaytFbAAACQ0lEQVRIiZ3WaVPiQBCA4V4TE0KCSbgDYRFPUKO7Xoj3sYvxwAPh//+V7R5mDFUzItmu0oLhfWYCXxL4QeM0c0swc5ZyTYelQP8WZ8diFjlwlufrAVoOA3P3AMsE5rwecVXwK00PmOfSgd/QSgdasKJaXt0/ONhfVX2iztfK6zjlNSWR5vCoUi6X1/GvUjk6/DY/7rruBgnqN1y3ezwzP+l5nkuCDfae5/VOvsxPz3zTZOK8vbnZPncJmGb17FSZX1wahl9F4LlXHVroXONrz6z6vnF5oQA3mcDwUZjelVi65n2QuZH72zyCicD9291uG+DOZD2C/K18QEGIP/jl6WLwynuiL/yVQK2Q56IP0Ddx8Mr6vM8XFmQghIHgvopzj8Dgfa0mgQUuAiPGH2jL97fwq8RGwHv5BIuLTBDTT7q9TT9tHGR4bykACSJxshhTTr0C1D/FNMCc7W/VJVCsW4zUCjvJ4g7WtL1VL0ognAgk04By1ocS0MIiJ9OA58VQk4EW4iFIrIdk8QFz2j7UZNBoCDINrDrbXtMaErBJEClOA6xp+0ZjKIEIxYQ8JouPVFNvRxJ4ytqTQzTtWaw9azy3s08SgCjLCKKBWBrQWxvzrHwAwMurrnPzxhY6A17r+uuLAgC8RyjI2MOP0ehjyGrMo3dlzomuMzUZejcjpxmNSyU9mdJ4di6ImPHo25xmd/yTzXhX9anydkvkq3xvrkM/Zw9S3RPxrghOOuCkvO02U97YW+xJIMWd2vm/h5N0jz//AADWR7LG2QyQAAAAAElFTkSuQmCC)Refine 

|Command|Action|Recommended Use|
|---|---|---|
|`git stash apply`|Restores changes but **keeps** them in the stash stack.|Use if you might need to apply these same changes elsewhere.|
|`git stash pop`|Restores changes and **deletes** them from the stash stack.|Standard for moving work to a single new destination.|
|`git stash list`|Shows all saved stashes and their indexes (e.g., `stash@{0}`).|Use to identify a specific stash if you have multiple.|