# [GIT Cheat Sheets](https://github.com/potatoscript/git/wiki)

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
