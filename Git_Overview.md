# Git Overview

* Git is a distributed version control system, that manages changes made to a set of files.
* A Git repository contains a series of snapshots of a project over time, known as commits.
* It is possible to revert to previous versions of the project by viewing previous commits.

## Why use Git?
* Free, opensource.
* IDE support.

## Git Locations

### Working Tree
* Location on the computer that contains all the directories and files of a **single commit**. 
* Where you view and edit files preparing them for the next commit. 
* When you checkout a commit, you place the commit in the working tree and the working tree is updated with its contents.
* You commit changes made in the working tree.

### Staging Area/Index
* List of changes that are planned to be included in the next commit you make. 
* Should be prepared so that the next commit is a meaningful snapshot of the project.  

### Local Repository
* Contains all the commits of the project that were made locally and pulled from the remote repo. Represents the version history of the project. 

### Project Directory
* The working tree, staging area and local repository are stored in a single directory on the computer known as the project directory. 
~~~
myProject/                ⭠ Project directory.
          file.txt        ⭠ Contents of working tree.
          .git            ⭠ Staging area + local repository.
~~~

### Remote Repository
* Contains all the commits of the project.
* Located usually on a server/cloud.
* Considered the official state of the project.
* When the local repository and remote repository are synchronised they contain exactly the same commits.
* The local repository and remote repository become out of sync and differ when: you commit locally and do not *push* these changes to the remote reposiory or someone else changes the remote reposiotry and you do not *pull* these changes to your local repository. 
