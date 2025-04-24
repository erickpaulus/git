# git-commit-folder-diff

This document demonstrates how to compare folders across two different Git commits — even when the folder paths or structures have changed — using tools like Git Worktree, Visual Studio Code, Windows Command Prompt, and meld.

## Use Case

You want to:
- Compare a specific folder (e.g., `src/components`) between two commits or branches
- Handle scenarios where folders were **renamed**, **moved**, or **restructured**
- View a full **side-by-side diff of all files**, even if they exist at different paths or commit histories


## Tools Used
- Git Worktree — for checking out multiple commits
- Visual Studio Code — for side-by-side diffing with code --diff
- Windows Command Prompt (cmd)
- Meld

## Folder Structure
```bash
/
├── v1/                  ← Checked-out commit A
│   └── src/
│       └── legacy components/
├── v2/                  ← Checked-out commit B
│   └── src/
│       └── modern ui/
├── README.md
```

## How It Works

1. Use `git worktree` to checkout two commits into temporary folders (`v1` and `v2`)
2. Locate the folders you want to compare from each commit
3. Use VSCode or another diff tool (meld) to compare the folders visually
4. Clean up the temporary folders when finished



## 🛠 Example: Compare Folder Across Commits

```cmd
:: Step 1: Add worktrees from two commits
git worktree add ..\v1 abc1234
git worktree add ..\v2 def5678

:: Step 2: Compare specific folders using VSCode
code --diff "..\v1\src\legacy components" "..\v2\src\modern ui"

:: Step 3: Clean up
git worktree remove ..\v1
git worktree remove ..\v2
```

in my case, step 2 did not work, because it looks like no difference. Therefore, I use another tool: meld (if needed, download this https://gnome.pages.gitlab.gnome.org/meld/).
After installing meld, remember to re-open the cmd
```cmd
:: Step 2: Compare specific folders using meld
meld "..\v1\src\legacy components" "..\v2\src\modern ui"
```
