# Tracking Branches
* A local branch that represents a remote branch.
* Locally, a tracking branch name starts with the remote name then a forward slash and then the branch name. <br>
* They are local branches that you can’t move; tracking branches move automatically, whenever you carry out any network communication. 
* Remote branches act as bookmarks to remind you where the branches on your remote repositories were the last time you connected to them.

**Naming Convention**
~~~
<remote>/<branch>
origin/master               ⭠ Tracking branch that represents the remote master branch in the local repo. 
~~~

* If you clone a repository, you'll have a default local tracking branch (origin/master).
* Tracking branches update separately from both the remote branch and the local branch. This is because tracking branches are only updated with network commands like clone, fetch, pull, and push. 

~~~
$ git branch                                ⭠ By default git branch shows all the local branches.
* master

$ git branch --all                          ⭠ Use the --all flag to display local and tracking branches names.
* master
remotes/origin/HEAD -> origin/master        ⭠ Symbolic reference to existing branch. Remote HEAD lable that points to origin/master branch lable.
remotes/origin/master                       ⭠ Shows that we have a tracking branch that tracks the master branch on the remote repository.
~~~

## Why set-up a tracking branch?
* Let's say your current local HEAD branch is named "dev". And let's also say that you have set it up to track the "dev" branch on the remote named "origin". This relationship is invaluable for two reasons:

* Pushing and pulling becomes a lot easier. You can simply use the shorthand commands "git pull" and "git push" - instead of having to think about the exact parameters like in "git push origin dev". Even more importantly than being "easier", this also prevents you from making mistakes!

* Git can now inform you about "unpushed" and "unpulled" commits. e.g.:

  - if you have 2 commits only locally that you haven't pushed to the remote yet, your local branch is "2 commits ahead" of its remote counterpart branch.
  - if, on the other hand, there are 4 commits on the remote branch that you haven't downloaded yet, then your local branch is "4 commits behind" its remote counterpart branch.

## Why change the default tracking branch?

* git pull commands will commands will automatically pull from this server e.g can state git pull instead of git pull origin dev. 

~~~
$ git remote --set-head <remote> <branch>                   ⭠ Change default remote tracking branch.

$ git branch -u <remote>/<branch> [<branch>]                ⭠ Set Tracking information with a branch. 

$ git branch -u|--set-upstream [remote] [<branch_name>]     ⭠ Set up tracking branch. 

$ git branch --unset-upstream [<branch_name>]               ⭠ Remove tracking branch (git push will no longer work without a remote and branch arguments).
~~~
