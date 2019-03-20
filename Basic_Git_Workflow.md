# Basic Git Workflow
* The first step in a basic Git workflow is to create a remote and local repository. 
* Remote repositories can be created simply online on a number of Git hosting services such as, GitHub and VSTS. 
* Local repositories can be created via a Git command.

## Local Repositories 

There are two options for creating a new local repository:

1) Clone an already existing remote repository.
2) Create a new empty local repository.

Usually we clone a remote repository if one already exists for the project. If a remote repository does not exist, we can first create a new empty local repository, then create a remote repository, before finally syncrhonising the remote and local repositories. 

### Creating a New Empty Local Repository 
~~~
$ git init      ⭠ Initialises a local repository (hidden .git file viewable with dir -a | ls -a).

$ rm -rf .git   ⭠ Delete .git directory.
~~~

### Cloning a Remote Repository
~~~
$ git clone <url> [<local_project_name>]                                ⭠ Creates local copy of remote repo. If no local project name is provided, the project name in the url will be used.

$ git remote                                                            ⭠ After cloning the repository we can use this command to view the remotes. The remote maps the local repo to the remote repo. 'origin' is the default remote alias when cloning a repo. Aliases can be used in place of the full url that maps the local and remote repos. 
origin 

$ git remote -v|--verbose                                               ⭠ The verbose flag lists the url after the name of the remote. The remote url is the location of the remote repo.
origin  https://github.com/RyanLPrince/Git-Reference-Guide.git (fetch)
origin  https://github.com/RyanLPrince/Git-Reference-Guide.git (push)
~~~
###### Example of Using an Alias
The two commands below achieve the same outcome.
~~~
$ git pull https://github.com/RyanLPrince/Git-Reference-Guide.git
$ git pull origin 
~~~
* A repo can have multiple uniquley named remotes but each remote can only have one associated location (for fetch and push). 

## Synchronising a Local and Remote Repository 
~~~
$ git remote add <remote_name> <url>          ⭠ Adds remote with a given name to local repo.

$ git remote -v|--verbose                     ⭠ Provides information about remotes and their locations.
<alias> <host_url> (fetch)                
<alias> <host_url> (push)

$ git remote rename <old_name> <new_name>     ⭠ Renames a remote. origin is the standard name given to a remote. 

$ git remote set-url <remote_name> <new_url>  ⭠ Change the url of an existing remote.

$ git remote rm <remote_name>                 ⭠ Remove a remote.               
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

## Pushing Commits

* At this stage you should have:
  - A local and remote repository, with a remote that maps them together. 
  - File(s) that have been sucessfully commited locally.
* Pushing synchronises the remote branch with the local branch.
* Commits made locally will be added to the remote repo.
~~~
$ git push [-u|--set-upstream] [<remote>] [<branch>]      ⭠ The -u flag is used to set up a tracking relationship between the local and remote branches. 
$ git push -u origin master
~~~
* If a file is deleted locally and then the local repo changes are pushed, the file will be deleted in the remote repo. 
* Pushing may fail if commits exist in the remote repository that do not exist in the local repository. In this scenario, it is necessary to first carry out the git-pull command. 

## Pulling Commits
* If changes have been made to the remote repository, you will need to retrieve these changes before you can push any commits you have made. 
* Pulling retrieves and integrates changes from another repository or branch.
~~~
$ git pull [<remote>] [<branch>] 
$ git pull origin master
~~~

### Creating a Shared (Remote) Repository
* Usually a remote repository will be created on a remote hosting service such as GitHub, Bitbucket or VSTS, but it is possible to create one using a Git command. 
* We can treat this remote repo as any other and use its path instead of an url. We can also clone this remote repo by using its path in place of an url.
* Shared repositories should always be created with the --bare flag. 
* Conventionally, repositories initialized with the --bare flag end in .git. For example, the bare version of a repository called my-project should be stored in a directory called my-project.git.

> The --bare flag creates a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository. You would create a bare repository to git push and git pull from, but never directly commit to it. Central repositories should always be created as bare repositories because pushing branches to a non-bare repository has the potential to overwrite changes. Think of --bare as a way to mark a repository as a storage facility, as opposed to a development environment. This means that for virtually all Git workflows, the central repository is bare, and developers local repositories are non-bare.
~~~
$ git init --bare           ⭠ Creates a repo without a working tree, we can treat this as a remote repository.
~~~
