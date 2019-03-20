# Rebasing 

* Rebasing rewrites history.
* General rule: do not rewrite history that has been shared with others. If you're working locally or no one else uses your branch you can safely rebase. 

* Two types of rebase:
1) Regular rebase
2) Interactive rebase

* Rebasing moves commits to a new parent (base).
* Result is that you no longer need a merge commit.
* Merge can be fast-forwarded because commits have moved, they are reapplied on top of the new commit.
* Creates different ancestor chain, commit IDs change.

## Diff
* The difference between two commits is known as a **diff** or a **patch**.
* diff AB is the difference between commits A and B. 
* When rebasing, git applies the diffs to the new parent commit. This is called "reapplying commits".

![alt text](https://github.com/RyanLPrince/Git-Reference-Guide/blob/master/Resources/Images/Rebasing.png)

* Before rebasing the parent of B is A and the parent of C is B.
* The difference between A and B is diff AB and the difference between C and B is diff BC.
* When rebasing Git takes diff AB and applies it to the child of commit D. This creates a new commit ID B'. 
* Reapplying commits is a form of merge and is susceptible to merge conflicts. 
* If B and D change the same file in different ways, git will not know how to apply this change to commit B'. 

## Advantages of Rebasing

* You can incorporate changes from the parent branch. 
    * bug fixes, you will see them.
    * Tests will be on more current code.
    * It makes eventual merging fast-forwardable. 
* Avoids 'unnecessary' merge commits.
    * shape/define clean commit histories.

## Disadvantages of Rebasing

* Conflicts may need to be resolved.
* Problematic if commits have been shared.
* Not preserving commit history.

### Steps for rebasing
~~~
$ git checkout [feature_branch]                 ⭠ Switch to feature banch.

$ git rebase <upstream> [<feature branch>]      ⭠ Specifiy upstream argument as the base. This will become the parent of the currently checked out branch. Specify feature branch if it is different from the currently checked out branch. 

$ git add .                                     ⭠ Add any conflicted files after the conflict has been resolved. 

$ git rebase --continue                         ⭠ Continue rebase after merge conflict is resolved.

$ git checkout <base_branch/upstream> 

$ git merge <feature_branch>                    ⭠ Move master branch label to tip of the rebased branch.
~~~

## Rewriting History

* You can change the most recent commit. 
    - Change the commit message.
    - Change project files.
* This creates a new SHA-1 (rewrites history).

~~~
$ git commit --amend -m <amended commit message>          ⭠ Changing commit message for most recent commit.
~~~

###### Changing files in most recent commit 
1) Prep working tree how you want it for commit 
2) Add files to staging area 
3) Commit files with -amend flag 
~~~
$ git commit --amend --no-edit                            ⭠ Changes previous commit, --no-edit flag retains previous commit message.
~~~

## Interactive Rebase

* Interactive rebase lets you edit commits using commands.
    * The commits can belong to any branch 
    * The commit history is changed 
~~~
$ git rebase -i <after-this-commit>                       ⭠ Commits in the current branch after <after this commti> are listed in an editor and can be modified.

$ git rebase -i --root                                    ⭠ Rebase all commits reachable from <branch>, instead of limiting them with an <upstream>.
~~~

###### Uses of Interactive Rebase

\# Commands:  
\# p, pick = use commit  
\# r, reword = use commit, but edit the commit message (edit only commit message)    
\# e, edit = use commit, but stop for amending (edit commit files and message)    
\# s, squash = use commit, but meld into previous commit  
\# f, fixup = like "squash", but discard this commit's log message  
\# x, exec = run command (the rest of the line) using shell  
\# d, drop = remove commit  


## Squash Merge

* Squashes all commits of feature branch into a single commit then merges single commit with tip of base branch. 
* A squash merge merges the tip of the feature branch onto a the tip of the base branch with a single new commit. 
* It places the results of this merge into the staging area which then can be committed.

### Steps of Commiting a Sqash Merge
~~~
$ git checkout <base_branch>                               ⭠ Switch to base branch.

$ git merge --squash <feature_branch>                      ⭠ Adds merged content to staging area.

$ git commit -m <commit message>                           ⭠ Commit squash merge. 
~~~

## Cherry-picking

* Cherry picking allows us to apply the changes introduced by some existing commits to a branch.
* This is in contrast with other methods such as merging and rebasing which normally apply many commits onto another branch.

~~~
$ git checkout <branch>                                     ⭠ Switch to branch we want to introduce the commit to   

$ git cherry-pick <commit>                                  ⭠ Applies change introduced by the given commit to the given branch.

$ git cherry-pick <branch>                                  ⭠ Apply the change introduced by the commit at the tip of the given branch and create a new commit with this change at the tip of the checked out branch. 
~~~
