# Reset

## git-reset vs git-checkout 

* Resetting moves what the HEAD 'points' to. 
  - Used for undoing changes. 
* Checking out changes the HEAD itself.

* Resetting moves the the branch that the HEAD is pointing to (branch label is moved as well as HEAD). 

~~~
$ git reset                  ⭠ Unstages all files that have been added. Same as git reset --mixed HEAD.

$ git reset --soft HEAD~     ⭠ Moves the HEAD and branch label to point to the previous commit. --soft flag does not touch the index or working tree (essentially undoes the latest commit but changes remain in staging area). 

$ git reset --mixed HEAD~    ⭠ Moves the HEAD and branch label to point to the previous commit. --mixed flag unstages all the changes so the index and and HEAD commit are the same but the working tree still retains all the changes made (essentially undoes the latest commit and unstages the changes). This is the default behavious when no flag is specified.

$ git reset --hard HEAD~     ⭠ Resets the index and working tree. Any changes to tracked files in the working tree since the last commit are discarded (Essentially undoes the latest commit, unstages all the changes and discards the changes made to the working tree). The HEAD, working tree and index will all be the same.  

~~~

## Resetting with Paths

* If a path is provided git will limit its actions to a file or set of files and the HEAD and branch label won't be moved. 
  - *Why?* HEAD is just a pointer and it cannot point to part of a commit. However the index and working tree can be partially updated.
  
~~~
$ git reset file.txt HEAD     ⭠ Opposite opperation of git add file.txt (Same as git reset --mixed HEAD file.txt). Unstages changes for specified file. 
~~~

###### Why does git prevent the command git reset --hard|--soft <path> ?

* Because other commands provide this functionality already and it reduces the potential for mistakenly carrying out an action you did not mean to do. 

* git reset --hard <path> would essentially be the same as git checkout HEAD <path>
* Therefore git checkout <commit> <path> would be the correct command to use. 

* git reset --soft <path> does not make sense. 
  
---
## Squashing Commits with Reset

* Scenario there is are number of commits that you wish to squash into a single meaningful commit:

1. git reset --soft <sha1_of_commit_you_wish_to_keep>  
2. Commit with git-commit command. 





