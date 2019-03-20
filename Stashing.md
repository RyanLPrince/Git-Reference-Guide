# Stashing 

* Stashing stores changes made in the dirty working tree, so that the working tree status is clean (no modifications).
* Use git-stash when you want to record the current state of the working directory and the index, 
but want to go back to a clean working directory. 
* Stashing saves your local modifications away and reverts the working directory to match the HEAD commit.
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
~~~
* stash@{0} is the latest stashed modifications. 

* The latest stash you created is stored in refs/stash; older stashes are found in the reflog of this reference and can be named using the usual reflog syntax (e.g. stash@{0} is the most recently created stash, stash@{1} is the one before it, stash@{2.hours.ago} is also possible). Stashes may also be referenced by specifying just the stash index (e.g. the integer n is equivalent to stash@{n}).


* git-stash does not stash untracked files by deafault. The --include-untracked flag can be used to achieve this.
~~~
$ git stash --include-untracked|-u                         ⭠ Stash untracked files.
~~~
* For quickly making a snapshot, you can omit "push". In this mode, non-option arguments are not allowed to prevent a misspelled subcommand from making an unwanted stash entry.
