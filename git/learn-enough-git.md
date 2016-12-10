<a href="http://www.learnenough.com/git-tutorial"><img style="height:250px" src="https://softcover.s3.amazonaws.com/636/learn_enough_git/images/cover-web.png" /></a>

## Starting up
`git help <command>` - git help on a *command*
`git config` - configure git
`git config --global user.name "Your Name"` - set your name
`git config --global user.email your.email@example.com` - set your email address
`git config --global alias.co checkout` - set alias for *checkout* (example)
`git config --global core.editor "atom --wait"` - set default editor in Git to Atom

## Initializing
`git init` - initialize empty Git repository (.git) in the current directory
`git status` - show the status of the repository
> *The main Git status sequence for a changing file:*
<img src="https://softcover.s3.amazonaws.com/636/learn_enough_git/images/figures/git_status_sequence.png" />

## Adding
`git add -A` - add *all* files or directories to staging area
`git add .` - add current directory
`git add <name>` - add given file or directory to staging area

## Commiting
`git diff` - show diffs between commits, branches, etc.
`git commit -am "<Commit message>"` - stage and commit *all* changes with a *message*
`git commit --amend` - amend the last commit
`git log -p` - view full log of commits (shows full diffs)
`git show <SHA>` - show diff vs. the SHA

## Pushing to GitHub or Bitbucket
`git remote add <location> <URL>` - add remote repo, e.g. `git remote add origin git@github.com:username/reponame.git`
`git push -u <location> <branch>` - push with "set upstream" option, the destination *location* and the branch name *branch*, e.g. `git push -u origin bugfix`
`git push <location> <local branch>:<remote branch>` - push local branch to remote branch
`git push` - push to default remote

## Branching and merging
`git checkout <branch>` - switch to *branch*
`git checkout -b <branch>` - create new *branch*
`git branch <branch>` - create new *branch* but does not check out
`git branch` - list local branches
`git branch -a` - list *all* (incl. remote) branches
`git diff <master>` - compare *branch* with *master*
`git merge <branch>` - merge *branch* with *master*

## Deleting branches
`git branch -d <branch>` - delete the *branch*
`git branch -D <branch>` - delete the *branch* even if its changes are unmerged
`git push origin :<branch>` - delete remote branch
`git push origin --delete <branch>` - delete remote branch

## Recovering
`git checkout -f` - force check out HEAD (i.e. most recent commit)
`git checkout <SHA>` - switch to earlier version of repository

## Clone and pull
`git clone <clone URL> <dir/name of repo>` - clone repo (name if name is different than the original repo)
`git clone --recursive <clone URL> <dir/name of repo>` - clone repo including submodules
`git pull` - pull changes from the remote origin

## GitHub Pages
`gh-pages` - branch name for production website
`git checkout -b gh-pages` - switch to GitHub Pages branch
`git push -u origin gh-pages` - push to GitHub Pages branch
`http://<username>.github.io/<reponame>/` - URL of static html from GitHub Pages branch

## Submodules
`git submodule add <submodule URL> <name of repo>` - add repo as submodule
`git submodule update --init --remote` - upgrade submodules to the latest published version

## Rollback to previous commits
```
git reset --hard <old-commit-id>
git push -f <remote-name> <branch-name>
```
> NOTE: As written in comments below, Using this is dangerous in a collaborative environment: you're rewriting history