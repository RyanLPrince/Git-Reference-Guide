# Glossary

**Branch** - A branch is an independent line of development, consisting of a continuous set of commits, with the most recent commit in a branch tracing back to the project's first commit.<br><br>

**Commit**- A snapshot of a project, containing all the directories and files at the time the snapshot was taken. 
<br><br>

**Commiting**- Recording the changes made to the project.
<br><br>

**Detatched HEAD** - Branch labels usually point to most recent commit in a branch. Checking out a commit that a branch label does not point to leads to a detatched HEAD state.
This means that instead of the HEAD reference pointing to a branch label, HEAD points directly to the SHA-1 of a commit. Essentially, a detached HEAD means that the HEAD reference is detached from a branch label.<br><br>

**Fetch** - Downloads new objects and references from the remote repository. <br><br>

**FETCH_HEAD** - FETCH_HEAD is an alias for the tip of the tracking branch. <br><br>

**Fast-forward Merge** - Fast-forward merging moves the base branch label to the tip of the feature branch. After a fast-forward merge, both branches **contain exactly the same commits**. <br><br>

**Index** - See Staging Area. <br><br>

**Local Repository** - Contains all the commits of the project that have been made locally and that have been retrieved from the remote repository. Represents the version history of the project.
<br><br>

**Merge Commits** - A merge commit combines the work of the tips of the feature and base branches and places the result into a single merge commit.<br><br>

**Merge Conflicts** - Merge conflicts are when multiple branches make different changes to the same part of a file. Git cannot automatically decide on which branch contains the desired information so a human must resolve the situation.<br><br>

**Merging** - Merging combines the work of independent branches. More specifically git-merging combines sequences of commits into one unified history of commits.<br><br>

**(Git) Objects** -  
Commit Object - Simple text file which stores: <br>  
  * Commit user information.  
  * Commit message. 
  * Reference to parent(s).  
  * Reference to the root tree of the project.  
  
  Annotated Tag: Reference to a specific commit.<br><br>
Tree: Contains a list of filenames and directories.<br><br>
Blob: Contains the content of a file that is being managed by git. <br><br>
**Project Directory** - The working tree, staging area and local repository are stored in a single directory on the computer known as the project directory.

**Pulling** - Fetch from and integrate changes from another repository or a local branch. <br><br>

**Pushing** - Update remote references (refs) along with associated objects. Combines git-fetch and git-merge FETCH_Head. <br><br>
~~~
myProject/                ⭠ Project directory.
          file.txt        ⭠ Contents of working tree.
          .git            ⭠ Staging area + local repository.
~~~

**Rebasing** - Rebasing moves commits to a new parent (base). After rebasing you may find that you no longer need to merge commit. Merging is fast-forwardable because commits have moved. They are reapplied on top of the new commit. Rebasing creates a different ancestor chain and commit IDs change.<br><br>

**Remote** - The remote url is the location of remote repo. The remote maps the local repo to the remote repo.<br><br>

**Remote Repository** - Contains all the commits of the project that have been pushed to/made in the remote location. Usually located on a server or the cloud. Considered the official state of the project. 
<br><br>

**Repo** - Repository. 
<br><br>

**Repository** - A copy of the complete history of the project. 
<br><br>

**Staging Area** - List of changes that are planned to be included in the next commit you make (marks files that have changed as modified). Should be prepared so that the next commit is a meaningful snapshot of the project. <br><br>

**Stashing** - Stores changes made in a dirty working tree, so that the working tree status is clean (no modifications).<br><br>

**Symbolic Reference** - A reference that points to another reference. <br><br>

**Tag** - A tag is a reference/label attached to a specific commit. e.g. master, HEAD, v1.0.<br><br>

**Tracking Branch** - A local branch that represents a remote branch. <br><br>

**Version Control**- Version control is a system that manages changes to a file or set of files over time. The complete history of files is tracked and available at any time.
<br><br>

**Working Tree** - Location on the computer that contains all the directories and files of a single commit. On the working tree you can view and edit files preparing them for the next commit. When you checkout a commit, you place the commit in the working tree and the working tree is updated with its contents. You commit changes made to the working tree. <br><br>
