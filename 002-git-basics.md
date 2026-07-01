## 🔧 Git Basics

**11. What does `git init` do?**
Initializes a new, empty Git repository in the current folder (creates a `.git` folder to start tracking changes).
 
**12. Difference between `git add` and `git commit`?**
`git add` stages changes (prepares them to be saved). `git commit` actually **saves** the staged changes into the repository's history with a message.
 
**13. What does `git status` show?**
Shows the current state of the working directory: which files are modified, staged, or untracked.
 
**14. What does `git log` show, and `git log --oneline`?**
`git log` shows the full commit history (author, date, message, hash). `git log --oneline` shows a **compact** version — one line per commit (short hash + message).
 
**15. Difference between `git push` and `git pull`?**
`git push` sends your local commits to the remote repository (e.g. GitHub). `git pull` fetches and merges changes from the remote repository into your local branch.
 
**16. What does `git clone` do?**
Downloads/copies an entire existing remote repository (with full history) to your local machine.
 
**17. Purpose of `git branch`?**
Lists, creates, or deletes branches — allows you to work on separate lines of development without affecting the main code.
 
**18. Difference between `git checkout` and `git checkout -b`?**
`git checkout <branch>` switches to an **existing** branch. `git checkout -b <branch>` **creates a new branch** and switches to it immediately.
 
**19. What does `git merge` do?**
Combines the changes from one branch into another (usually merging a feature branch into `main`).
 
**20. Difference between `git reset` and `git revert`?**
`git reset` moves the branch pointer backward, **removing** commits from history (rewrites history — risky on shared branches). `git revert` creates a **new commit** that undoes the changes of a previous commit, **keeping history intact** (safe for shared branches).
 
**21. Purpose of `.gitignore`? Two examples?**
Tells Git which files/folders to **ignore** and not track. Examples: `node_modules/`, `.env`, `__pycache__/`, `*.log`.
 
**22. What is a Personal Access Token (PAT)? Why needed instead of a password?**
A PAT is a secure, generated token used to authenticate with GitHub (e.g. over HTTPS) instead of your account password. It's needed because GitHub no longer accepts plain passwords for Git operations — tokens are safer, can be scoped to specific permissions, and can be revoked individually.
 
**23. What is a Pull Request (PR)? Why used?**
A PR is a request to merge changes from one branch (or fork) into another. It's used for **code review**, discussion, and quality control before changes are merged into the main codebase.
 
**24. What is a merge conflict? Why does it happen?**
A merge conflict happens when Git can't automatically combine changes because **two branches modified the same lines** of a file (or one deleted a file the other edited). It requires manual resolution.
 
**25. Basic steps of GitHub Flow?**
1) Create a branch from `main`. 2) Make commits with changes. 3) Open a Pull Request. 4) Review and discuss. 5) Merge the PR into `main`. 6) Deploy/delete the branch.