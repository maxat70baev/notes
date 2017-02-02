# Keeping a fork up to date
## Resources:
1. [Configuring a remote for a fork]("https://help.github.com/articles/configuring-a-remote-for-a-fork/")
2. [Syncing a fork]("https://help.github.com/articles/syncing-a-fork/")
3. [Keeping a fork up to date]("https://gist.github.com/CristinaSolana/1885435")

### 1. Clone your fork:

```
git clone git@github.com:YOUR-USERNAME/YOUR-FORK.git FOLDER/SUBFOLDER
```

### 2. List the current configured remote repository for your fork.

```
git remote -v
```
You should get something like this:
```
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```

### 3. Add remote upstream from original repository in your forked repository: 
To sync changes you make in a fork with the original repository, you must configure a remote that points to the upstream repository in Git.
```
cd into/cloned/fork-repo
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```

### 4. Fetch the branches and their respective commits from the upstream repository.
Commits to `master` will be stored in a local branch, `upstream/master`.
```
git fetch upstream
```

### 5. Updating your fork from original repo to keep up with their changes:

```
git pull upstream master
```