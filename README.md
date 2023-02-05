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

- the mechanism of `git rebase branch-B`
- step 1 : removed all commits from branch A and temporary keep them somewhere
- step 2 : create a straight line of commits
- step 3 : return back the commits of branch A with the new Id
- Do NOT use Rebase on commits that you have already pushed/shared on a remote repository!!!
- Instead, use it for cleaning up your local commit history before merging it into a shared team branch.
- Interactive Rebase

```git
- Change a commit's message
- delete commits
- reorder commits
- combine multiple commits into one
- edit/ssplit an existing commits into multiple new ones.
```
