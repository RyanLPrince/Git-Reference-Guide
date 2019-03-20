# Pull Requests
* Pull requests are a feature of Git hosting sites such as Bitbucket and GitHub. 
* The ultimate goal of a pull request is to merge a branch into the project. 
* Pull requests enable team communication related to the work of the branch. 
* Notifications, related to the pull request, can be sent to team members. 

* There are two basic repository configurations related to pull requests.
* The first one is a single remote repository.
    - A pull request in a single repository configuration is a request to merge a branch of the repository. 
* The second configuration involves two remote repositories.
    - in this configuration, a pull request is a request to merge a branch from a forked repository into the upstream repository. 
    - The fork approach is common if the submitter doesn't have write access to the upstream repository. 
* You can create a pull request, which is also called opening a pull request, anytime during the life of the branch.   
* You can open a pull request when you create the branch.
    - this enables the team to begin discussion on the work of the branch immediately. 
* You can also open a pull request when you want comments on the branch. 
    - For example, you may be stuck implementing something and want to ask the team for help.   
* You can open the pull request when you think the branch is ready for review and merging.   

## Single Repository Pull Requests

1) Checkout feature branch
2) Push feature branch
3) Open git hosting service and select pull request or follow url in response text of branch being pushed. 
4) You are presented with a pull request form to fill out. You title your pull request, 
add a description of work done on the branch, optionally specify specific reviewers of the pull request, 
and then click Create pull request. 

* Click Decline to reject or remove the pull request. 
        - Be careful if you do this because it cannot be undone for all hosting services.
* You can merge the pull request using an online Git host or by pushing the merge from your local client. 

## Forking

* Forking generally means copying a remote repository to your own online account. 
* Both repositories are remote repositories. 
* The upstream repository is usually considered the source of truth for the project. 

### Reasons for Forking

* It can be used to experiment with or learn from the upstream repository. 
    - You have a separate remote repository that can be synchronized with the upstream repository as the upstream repository changes. 
* A fork can also be used to create branches and issue pull requests to the upstream repository. 
* A fork can also be used to create a different source of truth. 
    - In other words, it can be used to start a new line of development of the project that remains independent from the upstream repository. 
*  You could use the upstream project as a starting point for a different type project or you could create a source of truth that competes with the upstream project. This may or may not be a desirable thing to do. It maybe better to just help improve the upstream project. 
* A fork is a feature of a Git hosting service.

### Synchronising a Fork

* This is done on the git hosting service 
*  This merge commit is not in the upstream repository. So even though the project files are synchronized, the commit histories of the two repositories differ. This behavior may be fine, depending on how you are using the fork. If you would like more control over the commit histories, you can manually sync the repositories using your local Git client. 

* A multi-repository pull request involves an upstream repository and a fork. To open a multi-repository pull request, you fork the upstream repository and create a branch on that fork. That branch will be the branch related to the pull request. When you are ready, you can open a pull request right from your fork. 

* To create the pull request, navigate to the forked repository and click Create a pull request. Because this is a forked repository, the git hosting service knows the information related to the upstream repository. Default pull request information is filled out for you. You can then add a title and description, change any other information, and then click Create pull request. 

* The upstream repository will then have an open pull request. You can navigate to the pull request's tab to view and act upon the pull request. 

* If the upstream owner decides to merge the pull request, they have two basic choices. The first is to use the interface to perform the merge. The second is to use a local client to add the forked repository as a remote and then perform and push the merge to the upstream repository. 

* Forking workflow is common in open source projects because the forked repository does not need to have right access to the upstream repository. 
