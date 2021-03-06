# Git Cheat-Sheet #

## Setup ##

```
git config --global user.name "John Doe"
git config --global user.email johndoe@email.com
git config --global credential.helper cache
```

View current global config
```
git config --list
```

## Repository Configuration ##

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

## Every-Day Actions ##

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

Working with a repo as a different user. This functionallyt unsets the configured user for the current repo only. All actious require manually providing the username and password.
```
git config --local credential.helper ""
git push origin master
```

## Advanced Repo Operations ##
Stop tracking changes to a file
```
git update-index --assume-unchanged <file>
```

List all tracked files
```
git ls-files -v
```

List all untracked files
```
git ls-files . --ignored --exclude-standard --others
```

Remove a file from tracking
```
git rm --cached filename
```

## Branch Operations ##

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

Merge a single frile from one branch into the current active branch.
(This is useful when both branches requre the same change but final merge order cannot be anticipated.)
```
git checkout --patch <branch name> <file path>
```

View how a branch relates to the remote
```
git remote show origin
```

To change the upstream for a local branch
```
git branch --set-upstream-to=origin/<remote branch>
```

Rename a local branch
```
git branch -m <oldname> <newname>
```

Remove a remote branch
```
git push origin --delete <branchName>
```

Remove a local branch
```
git branch -d <branchName>
```

Remove a local branch that has not been merged
```
git branch -D <branchName>
```

## Advanced Branch Operation ##

Merge a branch into the current active branch as 1 commit. This is useful for feature branches, where the individual commits only make sense while working on that feature and will loose meaning and add complication to the historic log. The following sequence ensures that 'feature' is fully up-to-date with 'develop' before attempting to make changes to develop.
```
git checkout feature
git merge development
git checkout development
git merge --squash feature
```

Squash a series of commits within a branch into a single commit. (This is not a git Squash)
```
git reset --soft HEAD~<number of commits>
git commit -m "action(area) message"
git push --force
```

Count the number of commits in a branch as compared to another branch. Example assumes comparing current working branch to development.
```
git rev-list --count HEAD ^development
```

Retrieve a single commit from a different branch into the current working copy. (Note that there is no need to specify which branch the commit is from)
```
git cherry-pick <commit hash id>
```

Delete all merged local branches
```
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```

Delete all local branches not in origin (verify)
```
git remote prune origin --dry-run
git remote prune origin
```

Wipe all branches except master and development branches
```
git branch | egrep -v "(master|\*)" | xargs git branch -D
```


Increment the version number of a node application with NPM and commit as new version
```
npm version patch
git push origin master --tags
```

Create a new project that uses another project as a seed
```
git clone -o seed <seed repo uri> <new project directory>
git rev-list --count HEAD
git reset --sfot HEAD~<rev list output minus 1>
git add .
git remote rm seed
git commit -m "chore(seed)"
```
This pulls the specified repo under the new name, then removes the development history for the seed repo from the newly created repo. Then removes the seed repo from the current repo so changes in the new project will not affect the seed project.

Alternative way
```
git clone -o seed <seed repo uri> <new project directory>
rm -rf .git
git init
git add .
git commit -m "chore(): seed project"
```
