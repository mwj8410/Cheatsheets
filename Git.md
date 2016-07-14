# Git Cheat-Sheet

## Setup

## Repository Configuration

Spin up a local repository to track an existing project, or  reset an existing repository to track a different remote location
```
git remote set-url origin <new uri>
```

Initialize a new repository
```
git init
```

Git clone
```
git clone <repo uri>
```

If using a local repository to initialize a remote repository,
```
git remote add origin <repo url>
git push -u origin master
```

Set or change the upstream for a repository. This is useful when providing the initial push to a new empty upstream repository.
```
git remote rm origin
git remote add origin <new uri>
```

## Every-Day Actions

Commit changes
```
git commit -m "<message>"
```

```
git commit -m "<message>" -m "<second message"
```

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
git reset --hard origin/<branch>
```

## Branch Operations

Create a new local branch and switch to it
```
git checkout -b <branch name>
```

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

Merge a branch1 into branch2
```
git checkout <branch 1>
git pull
git checkout <branch 2>
git merge <branch 1>
```

View how a branch relates to the remote
```
git remote show origin
```

To change the upstream for a local branch
```
git branch --set-upstream-to=origin/<remote branch>
```

Merge a remote branch
```
git push origin --delete <branchName>
```

## Advanced Branch Operation

Merge a branch into the current active branch as 1 commit. This is useful for feature branches, where the individual commits only make sense while working on that feature and will loose meaning and add complication to the historic log. The following sequence ensures that 'feature' is fully up-to-date with 'develop' before attempting to make changes to develop.
```
git checkout feature
git merge development
git checkout development
git merge --squash feature
```

Squash a series of commits within a branch into a single commit.
```
git rest --soft HEAD~<number of commits>
git commit -m "action(area) message"
git push --force
```

Delete all merged local branches
```
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```


Increment the version number of a node application with NPM and commit as new version
```
npm version patch
git push origin master --tags
```
