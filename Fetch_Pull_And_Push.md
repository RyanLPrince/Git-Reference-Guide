# Fetch, Pull & Push

* Most commands only interact with a local repository. 
* Network commands, communicate with the remote repository.

## Network Commands

1) Clone- Copies a remote repo and creates a local repo.
2) Fetch- Retrives new objects and references form the remote repo.
3) Pull- Fetches and merges commits locally (combines a fetch and a merge).
4) Push- Downloads new objects and references from the remote repository. 

## Fetch

* The git-fetch command retrieves new objects and references from another repository. 
* It also updates all of your tracking branch information.

~~~
$ git branch -vv                                                  ⭠ When in list mode, shows sha1 and commit subject line for each head, along with relationship to upstream branch (if any). If given twice (vv), print the name of the upstream branch, as well
master        c5318b1 [origin/master] Add feature 1 

$ git log --oneline
c5318b1 (origin/master , HEAD->master) Add feature 1

$ git fetch [<repository>]  

$ git branch -vv 
master        c5318b1 [origin/master: behind 1] Add feature 1     ⭠ After fetch local repo has knowledge of changes to remote repo. 

$ git log --oneline --all
b0ac5ce (origin/master) add feature 2                             ⭠ Tracking branch has moved. 
c5318b1 (HEAD->master) add feature 1

$ git merge FETCH_HEAD                                            ⭠ Merges changes from commit that was fetched. FETCH_HEAD is a short-lived ref, to keep track of the last fetch from the remote repository.
~~~
* git-fetch allows you to download and view changes on the remote repository without having to immediately merge them into your current work. 
* You can also checkout commits that have been fetched and enter a detatched HEAD state (branch label does not point to this commit).
* After the fetch, the tracking branch has the same commits as the remote repository's branch. 

## Pull

* git-pull is the equivalent of git fetch followed by git merge FETCH_HEAD
* FETCH_HEAD is an alias for the tip of the tracking branch. 

### How git-pull works

1) First new objects and references from the remote repository are fetched.
2) If new objects are added to the tracking branch, the tracking branch is merged into the local branch.
    -  The current branch is assumed if branch is not specified. 

* When you execute the git-pull command you can specify merging options. 

~~~
$ git pull [<remote>] [<branch>] 

$ git pull [<remote>] [<branch>] --ff      ⭠ Same as default behaviour, fast-forward merge if possible otherwise will perform a merge commit.

$ git pull [<remote>] [<branch>] --no-ff   ⭠ Always perform merge commit.

$ git pull [<remote>] [<branch>] --ff-only ⭠ Abort if fast-forward merge is not possible.
~~~

* We have just seen that executing a pull can update files in your working tree. What if you have modified fileA.text before executing git pull? You wouldn't want git to replace your file. Git detects this situation and will abort the merge rather than letting you lose uncommitted changes. 
* Let's look at an example:
  - First, we modify fileA.text, causing it to have uncommitted changes in the working tree. 
  - Git suggests that you commit or stash your changes before the merge, then it aborts the merge. 
  - Stashing is a way to save files modified in the working tree for later access. 
  - git-pull only aborts the merge if you have uncommitted changes that would be overwritten by git. If you've modified a file that's not going to be replaced by git it lets the merge continue (even if auto-merging is possible). 

## Pushing
* Add commits to a remote repository.
*  You are pushing the commits of your current branch. 
* You optionally specify the repository you want to push to. This can be a name like origin or URL. You then optionally specify the branch name on the remote that you would like to push to. 
* You can use the -u option to set up the local tracking branch with this remote branch. Once you've done this, the repository and branch name no longer need to be specified in the command, because that information is known from the tracking branch.
*  A general rule is to fetch or pull before you do a push.
*  If you try to push when you don't have the latest remote changes, the push will fail. If you execute a fetch and no objects are retrieved, we can safely push. If you're worried about a pull creating an unwanted merge commit, you can use the --ff-only option.

~~~
$ git push -f                                             ⭠ Force push, delete previous commits and pushes current commits. 
$ git push [-u|--set-upstream] [<remote>] [<branch>]      ⭠ The -u flag is used to set up a tracking relationship between the local and                                                              remote branches. 
$ git push -u origin master
~~~
