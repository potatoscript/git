# GIT Cheat Sheets:
| Title    | Remark/code  |
| -------------| -----|
| [Installation](https://github.com/potatoscript/git/wiki/Installation) | Setup and Configuration GIT `config`|
| [Alias Setup](https://github.com/potatoscript/git/wiki/Alias-Setup)|shortcut for those long long commands|
| [Basic Operation](https://github.com/potatoscript/git/wiki/Basic)|`init` `status` `commit` `cat` list `ls` `echo` `touch` `rm` |
| [Create Repository](#Create-Repository)|https://stackoverflow.com/questions/20325089/hosting-a-git-server-on-localhost|
| [.bashrc file](https://github.com/potatoscript/git/wiki/bashrc)|Create .bashrc file to store your own alias|
| [.gitignore file](https://github.com/potatoscript/git/wiki/gitignore)|https://www.codegrepper.com/code-examples/csharp/aspnet+core+gitignore|
| [Editing File](https://github.com/potatoscript/git/wiki/Editing-File)| read file `cat` and edit file `vim` or `code`|
| [Move your project to Remote](https://github.com/potatoscript/git/wiki/Move-Project-to-Remote) | `remote` `push` |
| [Restoring a File to an Earlier Version](https://github.com/potatoscript/git/wiki/Restore-File-Version)|`restore` |
| [Trouble Shooting Conflict](https://github.com/potatoscript/git/wiki/Trouble-Shooting-Conflict)|`stash`|
| [Unstaging Files](https://github.com/potatoscript/git/wiki/Unstaging-Files)|`restore` `clean` |
| [Viewing Staged & Unstaged Changes](https://github.com/potatoscript/git/wiki/View-Unstaged)|`diff --staged` `difftool` |
| [Viewing the History](https://github.com/potatoscript/git/wiki/View-History)|`log` |
| [Viewing a Commit](https://github.com/potatoscript/git/wiki/View-Commit)|`show` `ls-tree`|
| [Workflow basic](https://github.com/potatoscript/git/wiki/Workflow)|Clone Pull Push from Remote and create branch `branch` `merge`|
| [Workflow with feature branch](https://github.com/potatoscript/git/wiki/Workflow-feature)|using `tag`|
| [Wiki Repository](https://github.com/potatoscript/git/wiki/Wiki-Repository)||
| [Clone Repository](https://github.com/potatoscript/git/wiki/Clone-Repository)|clone all your GitHub repositories and their corresponding wiki repositories at once|
---

# **Comprehensive Git Tutorial: A Professional Guide**

## **Introduction**
Git is a powerful distributed version control system used by developers worldwide to manage source code efficiently. This tutorial provides a detailed guide on using Git effectively, covering fundamental and advanced commands for everyday workflows.

---
## **1. Configuring Git**
Before using Git, configure your global settings:

```bash
# Set your username
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"

# Verify your configuration
git config --global --list
```

If you work in multiple repositories, you can set repository-specific configurations using:

```bash
git config user.name "Repo-Specific Name"
git config user.email "repo-specific.email@example.com"
```

---
## **2. Initializing a Repository**

To create a new Git repository, navigate to your project folder and initialize Git:

```bash
git init
```

To clone an existing repository from a remote source:

```bash
git clone <repository-url>
```

Example:
```bash
git clone https://github.com/example/repo.git
```

---
## **3. Working with Branches**
### **Creating and Switching Branches**
```bash
git branch <new-branch-name>
git checkout <new-branch-name>
```
Alternatively, use:
```bash
git checkout -b <new-branch-name>
```

### **Merging Branches**
```bash
git checkout main
git merge <branch-name>
```

### **Deleting a Branch**
```bash
git branch -d <branch-name>
```
For remote branches:
```bash
git push origin --delete <branch-name>
```

---
## **4. Tracking and Committing Changes**

### **Checking Status**
```bash
git status
```

### **Adding Changes**
```bash
git add <file-name>
```
To add all changes:
```bash
git add .
```

### **Committing Changes**
```bash
git commit -m "Your commit message"
```

---
## **5. Undoing Changes**

### **Unstaging a File**
```bash
git reset HEAD <file-name>
```

### **Reverting a Commit**
```bash
git revert <commit-hash>
```

### **Resetting a Branch**
```bash
git reset --hard <commit-hash>
```

---
## **6. Working with Remote Repositories**

### **Viewing Remote Repositories**
```bash
git remote -v
```

### **Adding a Remote Repository**
```bash
git remote add origin <repository-url>
```

### **Fetching Remote Changes**
```bash
git fetch origin
```

### **Pulling Changes from Remote**
```bash
git pull origin main
```

### **Pushing Changes to Remote**
```bash
git push origin <branch-name>
```

---
## **7. Rebasing and Amending Commits**

### **Interactive Rebase**
```bash
git rebase -i HEAD~3
```

### **Amending the Last Commit**
```bash
git commit --amend -m "Updated commit message"
```

---
## **8. Cleaning Up a Repository**

### **Removing Untracked Files**
```bash
git clean -f
```

### **Optimizing the Repository**
```bash
git gc --prune=now
```

---
## **9. Resolving Merge Conflicts**

1. Open conflicted files and manually resolve issues.
2. Add resolved files:
   ```bash
   git add <resolved-file>
   ```
3. Continue the merge:
   ```bash
   git commit
   ```

---
## **10. Best Practices for Git**
- Commit frequently with meaningful messages.
- Use branches for new features.
- Pull before pushing to prevent conflicts.
- Clean up old branches regularly.
- Review changes with `git diff` before committing.

---
## **Conclusion**
By mastering these Git commands and best practices, you can manage source code efficiently and collaborate effectively in any development environment. Happy coding!



---

- Long-Running Branches (main, master, develop, staging, production branch )

  - exist through the complete lifetime of the project
  - often they mirror "stages" in your dev life cycle.

- Short-lived branches (feature branch)

  - for new features, bug fixes, refactorings, experiments...
  - will be deleted after integration (merge/rebase)

- Two Branching Strategies
  1. GitHub Flow - very simple, very lean: only one long-running branch(main or master) + feature branches.
  2. GitFlow - more structure, more rules...
     - long-running : main + develop
     - short-lived : features, releases, hotfixes.

### home

|                                       |                                                       |
| ------------------------------------- | ----------------------------------------------------- |
| ■ [Create Branch](#Branch)            |                                                       |
| ■ [Pull Requests](#Pull-Requests)     | Communicating about and reviewing code                |
| ■ [Merge](#Merge)                     |                                                       |
| ■ [Merge Conflicts](#Merge-Conflicts) | When Integrating commits from different Sources       |
| ■ [Rebase](#Rebase)                   | Integrating with rebase -> a straight line of commits |
| ■ [Cherry-Picking](#Cherry-Picking)   | Integrating Single, Specific Commits                  |

[home](#home)

### Branch

- Create branch

```git
git branch test
git checkout test
```

- set your remote origin repository

```git
git remote add origin /C/Apache24/htdocs/potatoscript.git
```

- make some change and commit and push it into the remote branch
- the `--set-upstream` allows you to set the default remote branch for your current local branch
- By default, every pull command sets the master as your default remote branch

```git
git push --set-upstream origin test
```

### Pull Requests

- without a `Pull Request` you would jump right to merging your code.
- Invites reviewers to provide feedback before merging
- Contributing code to other repositories that you don't have right access
- normally we will `Fork` the other people origin repository that you don't have the right to make changes<br>
  and clone it into your local repository to do editing.

[home](#home)

### Merge

- Merging Branches = Integrating one Branch into Another
- To merge branches locally, use git checkoutto switch to the branch you want to merge into.
- Next, use git mergeand specify the name of the other branch to bring into this branch.

```git
git checkout main
git merge feature/feature1
```

[home](#home)

### Merge Conflicts

- When contradictory changes happen
- To solve the conflicts use
  - `git rebase`, `git pull`, `git cherry-pick`, `git stash apply`
  - use the git mergetool like `www.git-tower.com`

[home](#home)

### Rebase

- Interactive Rebase

```git
- Change a commit's message
- delete commits
- reorder commits
- combine multiple commits into one
- edit/ssplit an existing commits into multiple new ones.
- Do NOT use Rebase on commits that you have already pushed/shared on a remote repository!!!
- Instead, use it for cleaning up your local commit history before merging it into a shared team branch.
```

- the mechanism of `git rebase branch-B`
- step 1 :
  - git rebase -i HEAD~3
  - removed all commits from branch A and temporary keep them somewhere
- step 2 : create a straight line of commits

  - use `git log --oneline` to check the commit status and id
  - use `git rebase -i HEAD~3` to set the range of commit to rebase
  - next determine the desired action (reword or squash) only and don't edit the comment
    - reword -> edit comment

  ```git
     reword 6bcf266 Optimize markup structure in inddpage
     pick 762317c Change the page structure
     pick del3564 Improve headline for improve
  ```

  - squash -> combine commit

  ```git
    pick 6bcf266 Optimize markup structure in inddpage
    squash 762317c Change the page structure
    pick del3564 Improve headline for improve
  ```

  this will combine `6bcf266` and `762317c` into new commit with new Id

- step 3 : return back the commits of branch A with the new Id

[home](#home)

### Cherry Picking

- allows you to select individual commits to be integrated
- therfore use it for moving a commit to a different branch
- when you commit to the wrong branch

for example: by using merge C2 and C4 from branch feature-X will all moved to branch master

by using cherry pick you can choice C2 or C4 only to move to branch master

```
   C1--------C3--------C5--------master
     \
      C2--------C4--------------feature-X

```

- Usage Example:
  - WHen you committed on the wrong branch
  - C3 should have been on feature-X

```
   C1--------C3-----------master
     \
      C2------------------feature-X
```

- first we shift to `feature-X` branch and apply cherry pick on the target commit

```git
  git checkout feature/neweletter
  git cherry-pick 26bf1648
```

- next clean up the commit from the master branch

```git
  git checkout master
  git reset --hard HEAD~1 #this will remove the C3 from master branch
```
