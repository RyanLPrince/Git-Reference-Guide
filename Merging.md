# Merging 

* Merging combines the work of independent branches. 
  - More specifically git-merging combines sequences of commits into one unified history of commits.

## Four Main Types of Merging
1) Fast-forward merge
2) Merge commit
3) Squash merge
4) Rebase

### Fast-Forward Merge

* Fast-forward merges move the base branch label to the tip of the feature branch.
* After a fast-forward merge, both branches **contain exactly the same commits**.
* Fast-forward merge is possible when you create a feature branch off a base branch and the base branch has no new commits that are not in the feature branch.
* Fast-forward merge is not possible if commits have been made to the base branch after the feature branch was created.  

![Fast-forward merge](https://github.com/RyanLPrince/Git-Reference-Guide/blob/master/Resources/Images/Fast-Forward_Merge.PNG)

#### Steps for a Fast-Forward Merge

~~~
$ git checkout <base_branch_name>       ⭠ Checkout base branch.

$ git merge <feature_branch_name>       ⭠ Merge feature branch with base branch. (attempting to fast-forward merge is the default for this command). 

$ git branch -d <feature_branch_name>   ⭠ (Optional) Delete the feature branch.

$ git log --all                         ⭠ Shows the commit history for all branches. 
~~~
* When a branch is deleted the knowledge of which branch the work was done on is lost. To retain this knowledge, a note of where work was done should be left in a commit message or tag commits.
* After the merge, the commit history is linear. No commits have multiple parents. 

### Merge Commits
* A merge commit combines the work of the tips of the feature and base branches and places the result into a single merge commit.
* A merge commit always has multiple parents. 
* Because of this non-linear commit graph, it's easy to see the branch in the commit history.
* Combining the work of multiple commits may result in what's called a merge conflict, if both branches change the same thing in different ways. 

![Merge commit](https://github.com/RyanLPrince/Git-Reference-Guide/blob/master/Resources/Images/Merge_Commit.PNG)

##### Steps for a Merge Commit
* The steps for a merge commit are practically the same as those for a fast-forward commit.
~~~
$ git checkout <base_branch_name>                         ⭠ Checkout base branch.

$ git merge <feature_branch_name> [-m][<commit_message>]  ⭠ Merge commit will occur by deafult if a fast-forward commit cannot occur. Can add message or accept provided message 

$ git branch -d <feature_branch_name>                     ⭠ (Optional) Delete the feature branch.
~~~

* In some cases, you might have a situation where a merge is fast forwardable, but you would rather have a merge commit. For example, your team's policy might be to always merge feature branches using merge commits. This is so you can clearly see the branches in the commit graph. A no fast-forward merge means that a merge commit will always be created, even if the merge is fast-forwardable. 

~~~
$ git merge --no-ff <feature_branch_name>     ⭠ Merge commit will occur even if merge can be fast-forwarded. Feature branch history is easy to see. 
~~~
*  The difference between a fast-forward merge and a merge commit is only in the project history information, not in the project files.

---
## Merge Conflicts
* Merge conflict can occur when multiple branches make different changes to the same part of a file.
* Git will attempty to automatically merges changes to different parts (hunks) of a files.
* Resolving a merge commit involves 3 commits:
  - Tip of the current branch "ours".
  - Tip of the branch to be merged "theirs".
  - Common ancestor "merge base".

### Steps to Resolve a Merge Conflict
  
~~~
$ git checkout <base_branch_name>                                       ⭠ Checkout "their" branch.
  
$ git merge <feature_branch_name>                                       ⭠ Attempting to merge. 
Auto-merging <file_name>                                                        
CONFLICT (content): Merge conflict in <file_name>                       ⭠ Git informing user of merge conflict.
Automatic merge failed; fix conflicts and then commit the result.

$ git merge --abort                                                     ⭠ Can abort the merge at this stage with with the --abort flag.
~~~
* Git will modify the conflicting file(s) to show you exactly where the conflicts are, and then place the modified file(s) in your working tree. 
* The user can then open the conflicting file(s) and resolve the merge conflict(s).

**Example of how git modifies conflicted files:**
* Conflicted hunks are surrounded by less than and greater than signs that are called, conflict markers.
* Any text that isn't surrounded by conflict markers was cleanly resolved by Git.
* The equals sign separates where the version from the HEAD and the branch we are merging.
~~~
<<<<<<< HEAD
int x=1;
=======
Integer x=1;
>>>>>>> featureBranch
~~~
**Then modify conflicted file to look how it should look**
~~~
int x=1;
~~~

~~~
$ git add <file_name>                     ⭠ Add file to staging area after merge conflict is resolved. This file can then become part of the merge.
$ git commit [-m] ["commit message"]      ⭠ Commit the merge to complete the merging process.

OR (after git-add)

$ git merge --continue [-m]               ⭠ After a git merge stops due to conflicts you can conclude the merge by running the --continue flag.
~~~

