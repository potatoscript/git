### home

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

|                                   |                                        |
| --------------------------------- | -------------------------------------- |
| ■ [Pull Requests](#Pull-Requests) | Communicating about and reviewing code |
| ■ [Merge](#Merge)                 |                                        |

[home](#home)

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
