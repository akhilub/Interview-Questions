

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
    
    _(Use `git stash pop` instead of `apply` if you want to automatically delete the stash after applying it.)_ ![Stack Overflow](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAMAAAD04JH5AAAAflBMVEX/XgAgHB0dGx0AFx4tHxzMTwn1WwD/YQAaGx0OGR4YGh2IOhESGh0AGB0VGh4SGR7BSwudQBC6SQxFJxo1IhskHhwAEx+NOxIeHRyyRw3rWATkVgXZUwhVKxnSUQhuMhd6NhOBNxQ7JBqUPRGmQw9iLxhnMBZ1NBZbLBlKJxk8C7FfAAAELklEQVR4nO2Z67aiOBCFMcGEQECuXrgpiJfz/i84AfUIId3tmSlg9azsv7qsz6pNVSUYhpaWlpaWlpaWltZ/Ew12y8Y/uO6ZLhmfIcSb5eL7CVqt0L5ZKAfUN62VEOKHRQhEfHvVyUoOS8TPX/FbAn/+HPjv+ILAmj0H6358QWDO7YMjXg1kWeG8AOTCJYIknDcH6Z1JBGY5cxXucg5W/rwAoxzYcT5zFQqZoM5mBRAEUhU2UT4vQRl7QwIekVkBaCYTbKJ5q0DXtZyDIp00Yi6nuIxtiSCakiCLC6nlUmkqiCoUE1bhzLz9MRs+7b5MwKPJ4meuWIDY/pz2EWiZSARsMh+cus6D8H1QBzrOwWWap7FbQruWx479OgsfWHIOpiAgx3frZcmuVwcaJhIBr+AJaNhvvIgV/eE3IvBu4IOJSHm2t9fyTee7aEiAT8A5oI3U88QTH1fG63/SQCZAwMfGvLZkAFGHuCEvhIYPCZBbgQLs8Ci+kOUeX5vYKAeIg+Ygv3qjGnR1ML+LfZZzYFeQTqTh3UMKAsTq1wE5cKXP8A7UieTsMhWC5d6edXDkKlgBJIBB05vc95914NWj/QcSIdpCH5nCCCvrgKNDl+3dMAfDng0iEiClFWx+afsScXqrMnKhu1ErmlXuuCUIedhp/+77eUV7Z5qDAvFrZR1W7Cug1Di5r7KcJwnfqYmZisDCtRhR1aNhuMGEByWaO66yL9lJlfrd2MSn6cJ38guusoLoS3FbH3aD81++JopkUqOJuIJghdr4Xg0W3qBFcnd8g44gaH7aKusgzBCv4QAMjGyGcR2UqSFB0PxuKR9JG/K+ZI2fDudF1eQSA2kSxXxgkAsZ3X0/cTb3zK+qJAN7pVUi18GqQQ8Gl/7vI4th69b0bUn9y7AvIQR6ZZZHcpXRhpn3KiTftiQH3q/D5gIZ3whVRu9sGQVl9rAEJU6y+f6Mw07As7LpPm35dWryRyLWV/zMFIZ9h0EK5QryYmBeEjl+Srq+9HQgbAJSrhx8vWoIWybH1pZZ3X6VA89AX7mOyxCeaxYnx2zfoCDYmzJ6U49+RSI2m/abmyPwEF6fYow96zMKIbf882/+VHlwrRP2Oy++ZU9yM0BpFu4KjpXb6FBsqrd41Eizw7WdBsrp9xKKJ6jAG4Ia/vlaq49HzwrcJ4z/gCC57yRb/ItEsIkWcVlpc432zB5nAs91XS4sEZ7vlrDlcBDzmeI/GEgWXkzEN2+G6S0gQ1BjHdxixp6OYLCn8Q8hhC2r+HEcc2d+b/VCECrbmYVM8C6QrT9TGbRriwX+voTu9uZnSh4ehL4mpw5Dn6mzgHeEnkTU+eVCqOyDoNdy/wZgtzAAXxwA/E5EA/x1AEubEH4f+nEjAo5v0GqLf6DtFfxQQH4o6PhaWlpaWlpaWlpaWlr/f/0DViY+xu94gUsA

Option 2: The Direct "Branch from Stash" One-Liner

If you have already stashed your work, you can create a new branch and apply those changes in a single command. [Scaler Topics](https://www.scaler.com/topics/git/git-stash-branch/). 

bash

```
git stash branch <new-branch-name>
```

Use code with caution.

- **What it does:** Creates a new branch starting from the exact commit where you originally ran `git stash`, checks it out, and then "pops" (applies and deletes) the latest stash onto it.
- **Best for:** Avoiding potential merge conflicts that might occur if the `main` branch has changed significantly since you stashed your work. ![Stack Overflow](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAMAAAD04JH5AAAAflBMVEX/XgAgHB0dGx0AFx4tHxzMTwn1WwD/YQAaGx0OGR4YGh2IOhESGh0AGB0VGh4SGR7BSwudQBC6SQxFJxo1IhskHhwAEx+NOxIeHRyyRw3rWATkVgXZUwhVKxnSUQhuMhd6NhOBNxQ7JBqUPRGmQw9iLxhnMBZ1NBZbLBlKJxk8C7FfAAAELklEQVR4nO2Z67aiOBCFMcGEQECuXrgpiJfz/i84AfUIId3tmSlg9azsv7qsz6pNVSUYhpaWlpaWlpaWltZ/Ew12y8Y/uO6ZLhmfIcSb5eL7CVqt0L5ZKAfUN62VEOKHRQhEfHvVyUoOS8TPX/FbAn/+HPjv+ILAmj0H6358QWDO7YMjXg1kWeG8AOTCJYIknDcH6Z1JBGY5cxXucg5W/rwAoxzYcT5zFQqZoM5mBRAEUhU2UT4vQRl7QwIekVkBaCYTbKJ5q0DXtZyDIp00Yi6nuIxtiSCakiCLC6nlUmkqiCoUE1bhzLz9MRs+7b5MwKPJ4meuWIDY/pz2EWiZSARsMh+cus6D8H1QBzrOwWWap7FbQruWx479OgsfWHIOpiAgx3frZcmuVwcaJhIBr+AJaNhvvIgV/eE3IvBu4IOJSHm2t9fyTee7aEiAT8A5oI3U88QTH1fG63/SQCZAwMfGvLZkAFGHuCEvhIYPCZBbgQLs8Ci+kOUeX5vYKAeIg+Ygv3qjGnR1ML+LfZZzYFeQTqTh3UMKAsTq1wE5cKXP8A7UieTsMhWC5d6edXDkKlgBJIBB05vc95914NWj/QcSIdpCH5nCCCvrgKNDl+3dMAfDng0iEiClFWx+afsScXqrMnKhu1ErmlXuuCUIedhp/+77eUV7Z5qDAvFrZR1W7Cug1Di5r7KcJwnfqYmZisDCtRhR1aNhuMGEByWaO66yL9lJlfrd2MSn6cJ38guusoLoS3FbH3aD81++JopkUqOJuIJghdr4Xg0W3qBFcnd8g44gaH7aKusgzBCv4QAMjGyGcR2UqSFB0PxuKR9JG/K+ZI2fDudF1eQSA2kSxXxgkAsZ3X0/cTb3zK+qJAN7pVUi18GqQQ8Gl/7vI4th69b0bUn9y7AvIQR6ZZZHcpXRhpn3KiTftiQH3q/D5gIZ3whVRu9sGQVl9rAEJU6y+f6Mw07As7LpPm35dWryRyLWV/zMFIZ9h0EK5QryYmBeEjl+Srq+9HQgbAJSrhx8vWoIWybH1pZZ3X6VA89AX7mOyxCeaxYnx2zfoCDYmzJ6U49+RSI2m/abmyPwEF6fYow96zMKIbf882/+VHlwrRP2Oy++ZU9yM0BpFu4KjpXb6FBsqrd41Eizw7WdBsrp9xKKJ6jAG4Ia/vlaq49HzwrcJ4z/gCC57yRb/ItEsIkWcVlpc432zB5nAs91XS4sEZ7vlrDlcBDzmeI/GEgWXkzEN2+G6S0gQ1BjHdxixp6OYLCn8Q8hhC2r+HEcc2d+b/VCECrbmYVM8C6QrT9TGbRriwX+voTu9uZnSh4ehL4mpw5Dn6mzgHeEnkTU+eVCqOyDoNdy/wZgtzAAXxwA/E5EA/x1AEubEH4f+nEjAo5v0GqLf6DtFfxQQH4o6PhaWlpaWlpaWlpaWlr/f/0DViY+xu94gUsAAAAASUVORK5CYII=)Stack Overflow +1

Key Command Comparison ![Refine](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAABAlBMVEUJCQv///9a24tJ2J461rB7e3xv3nJ84GNq3XhV2pE91qxB16jU1NRZWVojIySL4lGB4V1232ll3X5i3IFP2Zc21bSW5ESQ40t54Gds3nVe24VS2ZNN2ZpD16Uz1bmOjo8uLjA4ODkXFxlHZyKGzT+d5TyO404rQBxDbzASGxNqymIjPyRDllwvrpEaY1pNTU7Hx8dkZGVxpC2T0jQ6XCd8x0YzVCdywU0tTShou1MnRyhftlmC0UoUIhhRpVlQgzRZkTpXuGgyakEaKBdeqk5OsGpTmEk/cjhMl1E+lWFCtoEfZFMVLiU4pXwOIR8toocxlHIXRT08xZoqgmcdUkIvvaJaytFbAAACQ0lEQVRIiZ3WaVPiQBCA4V4TE0KCSbgDYRFPUKO7Xoj3sYvxwAPh//+V7R5mDFUzItmu0oLhfWYCXxL4QeM0c0swc5ZyTYelQP8WZ8diFjlwlufrAVoOA3P3AMsE5rwecVXwK00PmOfSgd/QSgdasKJaXt0/ONhfVX2iztfK6zjlNSWR5vCoUi6X1/GvUjk6/DY/7rruBgnqN1y3ezwzP+l5nkuCDfae5/VOvsxPz3zTZOK8vbnZPncJmGb17FSZX1wahl9F4LlXHVroXONrz6z6vnF5oQA3mcDwUZjelVi65n2QuZH72zyCicD9291uG+DOZD2C/K18QEGIP/jl6WLwynuiL/yVQK2Q56IP0Ddx8Mr6vM8XFmQghIHgvopzj8Dgfa0mgQUuAiPGH2jL97fwq8RGwHv5BIuLTBDTT7q9TT9tHGR4bykACSJxshhTTr0C1D/FNMCc7W/VJVCsW4zUCjvJ4g7WtL1VL0ognAgk04By1ocS0MIiJ9OA58VQk4EW4iFIrIdk8QFz2j7UZNBoCDINrDrbXtMaErBJEClOA6xp+0ZjKIEIxYQ8JouPVFNvRxJ4ytqTQzTtWaw9azy3s08SgCjLCKKBWBrQWxvzrHwAwMurrnPzxhY6A17r+uuLAgC8RyjI2MOP0ehjyGrMo3dlzomuMzUZejcjpxmNSyU9mdJ4di6ImPHo25xmd/yTzXhX9anydkvkq3xvrkM/Zw9S3RPxrghOOuCkvO02U97YW+xJIMWd2vm/h5N0jz//AADWR7LG2QyQAAAAAElFTkSuQmCC)Refine +1

|Command|Action|Recommended Use|
|---|---|---|
|`git stash apply`|Restores changes but **keeps** them in the stash stack.|Use if you might need to apply these same changes elsewhere.|
|`git stash pop`|Restores changes and **deletes** them from the stash stack.|Standard for moving work to a single new destination.|
|`git stash list`|Shows all saved stashes and their indexes (e.g., `stash@{0}`).|Use to identify a specific stash if you have multiple.|