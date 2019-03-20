# Cheat Sheet
## Git Help
~~~
$ git --version                ⭠ Returns the version of git installed.

$ git help                     ⭠ Provides generic help about common git commands in various scenarios.

$ git help <command>           ⭠ Opens online docummentation of the specified command.

$ git <command> -h|--help      ⭠ Returns concise offline help.
~~~

## Configuring User Information

~~~
$ git config --list|-l 				  ⭠ Lists the current global configuations (system and local configuations can be viewed by using the appropriate flag). 	

$ git config --global user.name "RyanLPrince"     ⭠ Configures the (global) username associated with repository. Note RyanLPrince is also a valid argument without the speech marks.                                                     

$ git config --get user.name                      ⭠ Returns the (gloabl) user name associated with the repository.
RyanLPrince
  
$ git config user.name                            ⭠ Also returns the (gloabl) user name associated with the repository.
RyanLPrince
  
$ git config --get --system user.name             ⭠ Returns the system user name.
                                               	  ⭠ Here no system user name is set so the response is empty.
  
$ git config --local user.email email@email.com   ⭠ Configures the (local) email address associated with the repository.
  
$ git config --local --unset user.email           ⭠ Removes the (local) email address associated with the repository. 
  
$ git config --global core.editor nano            ⭠ Configures the editor (used to write messages).
~~~ 

## Editors and Messages 
###### How do I open Vim?
`vim` `enter`
###### How do I insert text in Vim?
`i` You should then see *-- INSERT --* at the bottom of the editor.
###### How do I bring up the menu in Vim?
`esc` `:`
###### How do I save in Vim?
`esc` `:w <file_name>` `enter`  ⭠ Save as <br>
`esc` `:w` `enter`              ⭠ Save 

###### How do I exit Vim?
`esc` `:q`  `enter` <br>
`esc` `:q!` `enter` ⭠ Exit override (exit with unsaved changes). 
###### How do I search and replace in Vim?
`esc` `:%s/<search_word>/<replace_word>/g` `enter`   ⭠ e.g. :%s/pick/fixup/g

###### How do I save in nano?
`ctrl`+`o` `<file_name>` `enter` ⭠ Save as <br>
`ctrl`+`o` `enter`  ⭠ Save

###### How do I exit nano?
`ctrl`+`x` `enter`<br>
`ctrl`+`x` `n` `enter` ⭠ Exit override (exit with unsaved changes). 

## Creating a Repository 
~~~
$ git init                                                              ⭠ Initialises a local repository (hidden .git file viewable with dir -a | ls -a).

$ git init --bare                                                       ⭠ Creates a repo without a working tree, we can treat this as a remote repository.

$ rm -rf .git                                                           ⭠ Delete .git directory.

$ git clone <url> [<local_project_name>]                                ⭠ Creates local copy of remote repo. If no local project name is provided, the project name in the url will be used.

$ git remote                                                            ⭠ After cloning the repository we can use this command to view the remotes. The remote maps the local repo to the remote repo. 'origin' is the default remote alias when cloning a repo. Aliases can be used in place of the full url that maps the local and remote repos. 
origin 

$ git remote -v|--verbose                                               ⭠ The verbose flag lists the url after the name of the remote. The remote url is the location of the remote repo.
origin  https://github.com/RyanLPrince/Git-Reference-Guide.git (fetch)
origin  https://github.com/RyanLPrince/Git-Reference-Guide.git (push)

$ git remote add <remote_name> <url>                                    ⭠ Adds remote with a given name to local repo.

$ git remote rename <old_name> <new_name>                               ⭠ Renames a remote. origin is the standard name given to a remote. 

$ git remote set-url <remote_name> <new_url>                            ⭠ Change the url of an existing remote.

$ git remote rm <remote_name>                                           ⭠ Remove a remote.               
~~~

### Already have an Unrelated Local and Remote Repo Each Containing Files?

**Unrecommended** This is not allowed by default but can be achieved with the --allow-unrelated-histories flag.
~~~
$ git remote add <remote_name> <url> 
$ git pull <remote_name> <branch_name> --allow-unrelated-histories  ⭠ Must pull in files from the remote repository to local before commiting. 
~~~
Note if unrelated local and remote repo have files with the same name, it will result in a merge conflict. 

## Committing 

~~~
$ git status                      ⭠ Show working tree status.

$ git status -s|--short           ⭠ Show working tree status, in a concise format.

$ git add file1.txt               ⭠ Adds file1.txt to the staging area. 

$ git add file2.txt file3.txt     ⭠ Adds file2.txt and file3.txt to the staging area.

$ git add .                       ⭠ Adds all modified files to the staging area.

$ git rm --cached file1.txt       ⭠ Removes file1.txt from the staging area but keeps the file in the working tree.

$ git rm --cached -r              ⭠ Recurrsively removes all files from the staging area but keeps the files in the working tree.

$ git rm [-f|--force] file1.txt   ⭠ Removes file1.txt from the staging area and deletes it from the working tree. Use --force|-f flag to remove file if it has staged content different from the HEAD. 

$ git commit                      ⭠ Adds previously staged content to local repo as a commit. Without the -m|--message flag an editor is opened and the user is prompted to enter a commit message.
$ git commit -m|--message "commit message" 

$ git log                         ⭠ View local repo commit history. Type 'q' to exit scrollable program view which may be automatically implemented for logs with long commit histories.  

$ git log --oneline               ⭠ View condensened local repo commit history.

$ git log -2                      ⭠ View last 2 commits.

$ git log --graph                 ⭠ Draw a text-based graphical representation of the commit history on the left hand side of the output. 
~~~

~~~
$ git show 3bd9               ⭠ Shows the contents of the commit object 3bd9: author, date, commit message...

$ git show HEAD~              ⭠ Shows parent of the HEAD. Same as HEAD~1.
$ git show HEAD~~             ⭠ Shows the HEADS's parent's parent. Same as HEAD~2. 

$ git show 39jf^              ⭠ Shows first parent in a merge commit. Same as ~1 or ~
$ git show 39jf^2             ⭠ Shows second parent in a merge commit. 
$ git show 39jf^^             ⭠ Shows first parent's first parent. Same as ~2 or ~~
~~~

## Stashing

~~~
$ git stash                                             ⭠ Stores local modifcations and the index. Equivalent to git stash push.

$ git stash list                                        ⭠ List stashed modifications.
stash@{0}: WIP on master: 48aefe7 fileA.txt             ⭠ A stash is by default listed as "WIP on <branch_name>  <HEAD_SHA-1>  <HEAD_SHA-1_commit_message>" 

$ git stash push -m "Modified fileA.txt"
stash@{0}: On master: Modified fileA.txt 

$ git stash show                                        ⭠ Inspect modifcations in stash.

$ git stash apply                                       ⭠ Restore modifications made in stash. (Can be applied on top of a new commit). 

$ git stash apply stash@{2}                             ⭠ Apply modifications at index 2 of the stash.
$ git stash apply 2                                     ⭠ Also applies modifications at index 2 of the stash.

$ git stash clear                                       ⭠ Empty the stash.

$ git stash drop                                        ⭠ Removes latest stash (stash@{0}) from stash list. 

$ git stash drop stash@{<revision>}                     ⭠ Removes stash@{<revision>} from stash list

$ git stash pop                                         ⭠ Applies most recent stash then removes it from the stash. Equivalent of git stash apply stash@{0} folowed by git stash drop stash@{0}.

$ git stash --include-untracked|-u                      ⭠ Stash untracked files.
~~~

## Reset
~~~
$ git reset                  ⭠ Unstages all files that have been added. Same as git reset --mixed HEAD.

$ git reset --soft HEAD~     ⭠ Moves the HEAD and branch label to point to the previous commit. --soft flag does not touch the index or working tree (essentially undoes the latest commit but changes remain in staging area). 

git reset --mixed HEAD~     ⭠ Moves the HEAD and branch label to point to the previous commit. --mixed flag unstages all the changes so the index and and HEAD commit are the same but the working tree still retains all the changes made (essentially undoes the latest commit and unstages the changes). This is the default behavious when no flag is specified.

git reset --hard HEAD~      ⭠ Resets the index and working tree. Any changes to tracked files in the working tree since the last commit are discarded (Essentially undoes the latest commit, unstages all the changes and discards the changes made to the working tree). The HEAD, working tree and index will all be the same.  

$ git reset file.txt HEAD   ⭠ Opposite opperation of git add file.txt (Same as git reset --mixed HEAD file.txt). Unstages changes for specified file. 
~~~

## Squashing Commits with Reset

* Scenario there is are number of commits that you wish to squash into a single meaningful commit:

1. git reset --soft <sha1_of_commit_you_wish_to_keep>  
2. Commit with git-commit command. 


## Pushing 
~~~
$ git push [-u|--set-upstream] [<remote>] [<branch>]      ⭠ The -u flag is used to set up a tracking relationship between the local and remote branches. 
$ git push -u origin master

$ git push -f                                             ⭠ Force push, delete previous commits and pushes current commits. 
~~~
* If a file is deleted locally and then the local repo changes are pushed, the file will be deleted in the remote repo. 

## Branches

~~~
$ git branch                                  ⭠ View a list of local branches.
* master                                      ⭠ The master branch is the default branch of project. The branch you are currently on will have an asterix.
featureBranch


$ git branch  -v                              ⭠ When in list mode, this command will show sha-1 and commit subject line for each HEAD, along with relationship to upstream branch (if any). If given twice (-vv), print the name of the upstream branch, as well.

$ git branch <branch_name>                    ⭠ Creates a new branch with the given branch name.   

$ git log --oneline <branch_name>             ⭠ View commits of a specific branch.

$ git log --all                               ⭠ Shows all commits in the history of branches, tags and other refs, but it does not show commits that are not reachable from any ref.

$ git checkout <branch_name_or_commit_name>   

$ git checkout <commit> <path>

$ git checkout -b <branch_name>               ⭠ Creates a new branch with the given name and then checks it out. (only for new branches).

$ git branch -d <branch_name>                 ⭠ Deletes the given local branch. 

$ git push -d <remote_name> <branch_name>     ⭠ Deletes the given branch on the remote repo.

$ git branch -m <new_name>                    ⭠ Renaming local branch, when you are on the branch in question.

$ git branch -m <old_name> <new_name>         ⭠ Renaming local branch, when you are on a different branch.

$ git push <remote> :<old_name> <new_name>    ⭠ Delete the old-name remote branch and push the new-name local branch.

$ git push <remote> -u <new_name>             ⭠ Reset the upstream branch for the new-name local branch when on the branch in question.
~~~
###### Recovering from an Accidental Branch Delete
~~~
$ git reflog                                                  ⭠ Returns a list of recent HEAD commits. 

$ git checkout -b <branch_name> <commit_ID_without_branch>    ⭠ Creates a new branch with commit.
~~~

## Tracking Branches

**Naming Convention**
~~~
<remote>/<branch>
origin/master                                               ⭠ Tarcking branch that represents the remote master branch in the local repo. 
~~~

~~~
$ git branch                                                ⭠ By default git branch shows all the local branches.
* master

$ git branch --all                                          ⭠ Use the --all flag to display local and tracking branches names.
* master
remotes/origin/HEAD -> origin/master                        ⭠ Symbolic reference to existing branch. Remote HEAD lable that points to origin/master branch lable.
remotes/origin/master                                       ⭠ Shows that we have a tracking branch that tracks the master branch on the remote repository.

$ git remote --set-head <remote> <branch>                   ⭠ Change default remote tracking branch.

$ git branch -u <remote>/<branch> [<branch>]                ⭠ Set Tracking information with a branch. 

$ git branch -u|--set-upstream [remote] [<branch_name>]     ⭠ Set up tracking branch 

$ git branch --unset-upstream [<branch_name>]               ⭠ Remove tracking branch (git push will no longer work without a remote and branch arguments).
~~~


## Tags
~~~
$ git tag                                                                       ⭠ View all tags in the repository.

$ git tag <tagname> [<commit>]                                                  ⭠ Create a lightweight, tag <commit> defaults to HEAD if not specified. 

$ git tag -a [-m <msg>|-F <file_containing_message>]  <tagname> [<commit>]      ⭠ Create an annotated tag. Use -f to force overwrite tag if you specify a name that already exists. If you do not write a message you will be prompted by the editor to write one.
~~~
* git-push does not automatically transfer tags. 
~~~
$ git push <remote> <tagname>                        ⭠ Pushes specified tag to remote repo.

$ git push <remote> --tags                           ⭠ Transfer all tags to remote repo.

$ git tag -d|--delete <tagname>                      ⭠ Delete specified tag in local repo.

$ git push -d|--delete <remote_name> <tagname>       ⭠ Delete specified tag in remote repo.
            OR
$ git push <remote_name> :refs/tags/<tagname>        ⭠ Pushes empty ref name to remote repo. Tag must be deleted locally first.
~~~

## Fetch

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

## Pulling
~~~
$ git pull [<remote>] [<branch>] 
$ git pull origin master
 
$ git pull [<remote>] [<branch>] --ff         ⭠ Same as default behaviour, fast-forward merge if possible otherwise will perform a merge commit.

$ git pull [<remote>] [<branch>] --no-ff      ⭠ Always perform merge commit.

$ git pull [<remote>] [<branch>] --ff-only    ⭠ Abort if fast-forward merge is not possible.
~~~

## Merging
~~~
$ git checkout <base_branch_name>             ⭠ Checkout base branch.

$ git merge <feature_branch_name>             ⭠ Merge feature branch with base branch. (attempting to fast-forward merge is the default for this command). 

$ git merge --no-ff <feature_branch_name>     ⭠ Merge commit will occur even if merge can be fast-forwarded. Feature branch history is easy to see. 

$ git log --all                               ⭠ Shows the commit history for all branches. 
~~~

###### Example Merge Conflict
~~~
<<<<<<< HEAD
int x=1;
=======
Integer x=1;
>>>>>>> featureBranch
~~~
**Conflicted file modified to how it should look**
~~~
int x=1;
~~~
~~~
$ git add <file_name>                     ⭠ Add file to staging area after merge conflict is resolved. This file can then become part of the merge.
$ git commit [-m] ["commit message"]      ⭠ Commit the merge to complete the merging process.

OR (after git-add)

$ git merge --continue [-m]               ⭠ After a git merge stops due to conflicts you can conclude the merge by running the --continue flag.
~~~

## Rebasing & Rewriting History

~~~
$ git checkout [feature_branch]                 ⭠ Switch to feature banch.

$ git rebase <upstream> [<feature branch>]      ⭠ Specifiy upstream argument as the base. This will become the parent of the currently checked out branch. Specify feature branch if it is different from the currently checked out branch. 

$ git add .                                     ⭠ Add any conflicted files after the conflict has been resolved. 

$ git rebase --continue                         ⭠ Continue rebase after merge conflict is resolved.

$ git checkout <base_branch/upstream> 

$ git merge <feature_branch>                    ⭠ Move master branch label to tip of the rebased branch.

$ git rebase -i <after-this-commit>             ⭠ Commits in the current branch after <after this commti> are listed in an editor and can be modified.

$ git rebase -i --root                          ⭠ Rebase all commits reachable from <branch>, instead of limiting them with an <upstream>.
~~~

\# Commands:  
\# p, pick = use commit  
\# r, reword = use commit, but edit the commit message (edit only commit message)    
\# e, edit = use commit, but stop for amending (edit commit files and message)    
\# s, squash = use commit, but meld into previous commit  
\# f, fixup = like "squash", but discard this commit's log message  
\# x, exec = run command (the rest of the line) using shell  
\# d, drop = remove commit  

~~~
$ git commit --amend -m <amended commit message>          ⭠ Changing commit message for most recent commit.

$ git commit --amend --no-edit                            ⭠ Changes previous commit, --no-edit flag retains previous commit message.
~~~

## Cherry-pick
~~~
$ git checkout <branch>                                    ⭠ Switch to branch we want to introduce the commit to   

$ git cherry-pick <commit>                                 ⭠ Applies change introduced by the given commit to the given branch.

$ git cherry-pick <branch>                                 ⭠ Apply the change introduced by the commit at the tip of the given branch and create a new commit with this change at the tip of the checked out branch. 
~~~
## Squash Merge

~~~
$ git checkout <base_branch>                               ⭠ Switch to base branch.

$ git merge --squash <feature_branch>                      ⭠ Adds merged content to staging area.

$ git commit -m <commit message>                           ⭠ Commit squash merge. 
~~~
