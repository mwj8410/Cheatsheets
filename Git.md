# Git Cheat-Sheet

## Setup

## Repository Configuration

Spin up a local repository to track an existing project
```
```

Initialize a new repository
```
```

Set or change the upstream for a repository. This is useful when providing the initial push to a new empty upstream repository.
```
```


## Every-Day Actions

Hold onto changes without committing, and pull changes
```
git stash
git pull
git stash pop
```

Undo changes to working copy (this sets the state of the working copy to the latest local repository version.)
```
git reset --hard
```

Undo all local changes and reset to local repository to the state of the remote repository (applies only to current branch).
```
```

## Branch Operations

Show or list branches that are remote, then list all branches that are local or remote.
```
git branch -r
git branch -a
```

Merge one branch into another.
In the branch being merged to, run:
```
git merge feature/branch-name
```

Reset local branch to match remote branch

```
git fetch origin
git reset --hard origin/master
```

Merge a branch into the current active branch
```
```

Merge a branch into the current active branch as 1 commit. This is useful for feature branches, where the individual commits only make sense while working on that feature and will loose meaning and add complication to the historic log. The following sequence ensures that 'feature' is fully up-to-date with 'develop' before attempting to make changes to develop.
```
git checkout feature
git merge develop
git checkout develop
git merge --squash feature
```

Squash a series of commits within a branch into a single commit.
```
git rest --soft HEAD~<number of commits>
git commit -m "action(area) message"
git push --force
```
