# Branches

* A branch is a set of commits tracing directly back to the project's first commit.
* Branches can be short lived or long running. 
* Short lived branches are commonly called topic or feature branches, and usually contain one small change to the project. 
  - For example, a topic branch may contain a new feature, a bug fix, a hot fix, a configuration change, or any other change that the project requires. 
* When it's ready, a topic branch is merged into a long running branch. 
* Long running branches like the master branch live longer than topic branches, and can even live for the life of the project.
  - Examples of branches that might live for the life of a project are a master branch or a develop branch. 

## Benefits of using Branches

* Branches enable experimentation. 
  - Team members can isolate their work so that it doesn't impact others until the work is ready.
* Branches enable team memeber to work on a project concurrently.   
   - Branches are not aware of other branches. This allows you to experiment with changes to the project, and at the same time the team retains a stable version of the project.
* Branches allow you to support multiple versions of the project simultaneously.   

~~~
$ git branch                            ⭠ View a list of local branches.
* master                                ⭠ The master branch is the default branch of project. The branch you are currently on will have an asterix.
featureBranch


$ git branch  -v                        ⭠ When in list mode, this command will show sha-1 and commit subject line for each HEAD, along with relationship to upstream branch (if any). If given twice (-vv), print the name of the upstream branch, as well.

$ git branch <branch_name>              ⭠ Creates a new branch with the given branch name.   

$ git log --oneline <branch_name>       ⭠ View commits of a specific branch.

$ git log --all                         ⭠ Shows all commits in the history of branches, tags and other refs, but it does not show commits that are not reachable from any ref.
~~~
* Creating a branch simply creates a new branch label reference on the current commit. You remain on the same branch. 

## Checkout

* The git-checkout command does two main things: 
  - Switches the current commit, which is the commit that the HEAD reference points to, to the checked out branch label or commit specified.
  - The second thing that checkout does, is that it updates the working tree with the files from the checked out commit. 
    - Switching branches carries uncommited changes in some scenarios. 
    - In others it will force you to stash or commit changes. 
    - This is dependent on the extent of clobbering required to reapply the changes in the new branch. 
* It is possible to checkout a branch or a commit. The working treee will then be updated with the files of the specified commit or the commit with the branch label (the most recent commit in a branch).
* Checking out a commit or tag allows us to view different/older versions of the project.
~~~
$ git checkout <branch_name_or_commit_name>        
~~~

~~~
$ git checkout -b <branch_name>   ⭠ Creates a new branch with the given name and then checks it out. (only for new branches).
~~~

* git-checkout can also take a path as an argument to revert a specific file or group of files to a specific version.

~~~
$ git checkout <commit> <path>
~~~
###### Detatched HEAD & Checking Out Commits
* Checking out a commit that a branch label does not point to (branch labels point to most recent commit in a branch) leads to a detatched HEAD state. 
* This means that instead of the HEAD reference pointing to a branch label, HEAD points directly to the SHA-1 of a commit. Essentially, a detached HEAD means that the HEAD reference is detached from a branch label. 
*  Git will warn you that if you continue, you will be in a detached HEAD state.
*  Temporarily viewing the files of a commit while in a detached HEAD state is perfectly fine. However, if you want to work on files of the checked out commit and create new commits, you should create a branch from that commit first. This will put the HEAD back in a non-detatched state. 

## Deleting Branches

* Deleting  branch really just means that the branch label is being deleted.
  - Deleting a branch label does not normally delete any commits immediately.
  
~~~
$ git branch -d <branch_name>                 ⭠ Deletes the given local branch. 

$ git push -d <remote_name> <branch_name>     ⭠ Deletes the given branch on the remote repo.

~~~

* If you attempt to delete a branch that has commits that does not belong to any other branch, git will warn you with the following message: 

> error: The branch 'featureX' is not fully merged.
If you are sure you want to delete it, run 'git branch -D featureX'.

~~~
$ git branch -D <branch_name>               ⭠ Deletes the given local branch when branch conatins unique commits.  
~~~

* Deleting with the -D flag, can leave a dangling commit that doesn't belong to any branch. 
* Git will periodically garbage collect, looking for and deleting older dangling commits. So be careful if you use the -D option.

###### Recovering from an Accidental Branch Delete

~~~
$ git reflog                                                  ⭠ Returns a list of recent HEAD commits. 

$ git checkout -b <branch_name> <commit_ID_without_branch>    ⭠ Creates a new branch with commit. 
~~~

## Renaming Branches

~~~
$ git branch -m <new_name>                  ⭠ Renaming local branch, when you are on the branch in question.

$ git branch -m <old_name> <new_name>       ⭠ Renaming local branch, when you are on a different branch.

$ git push <remote> :<old_name> <new_name>  ⭠ Delete the old-name remote branch and push the new-name local branch.

$ git push <remote> -u <new_name>           ⭠ Reset the upstream branch for the new-name local branch when on the branch in question.

~~~
