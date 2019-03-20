# Version Control

* Version control is a system that manages changes to a file or set of files over time. 
* The complete history of files is tracked and available at any time.

## Centalised Version Control Systems (CVCS)
* Centralised version control systems were developed to enable developers on different systems to collaborate. 
* CVCSs consist of a single copy of the versioned files (usually on a server), and a number of clients that *check out* files from that central place.
  - Here check out simply means switching to a version of the files held in the central place.
  <br>
  
![CVCS.png](https://github.com/RyanLPrince/Git-Reference-Guide/blob/master/Resources/Images/CVCS.png)

* Commits are made directly to the central copy. 
* A commit is simply a snapshot of the entire versioned project, containing all the directories and files at the time the snapshot was taken. While committing is the process of recording changes made in the version control system. 
* **(Disadvantage)** Single point of failure. If the server goes down, then committing is not possible.
* **(Disadvantage)** If the hard disk that is managing the changes becomes corrupted and proper backups aren't kept, the entire project can be lost, except for whatever single snapshots users happen to have on their local machines. 
* The single copy of the versioned files kept on a server is an example of a *remote repository*, as it is a copy of the complete history of the project and it is located remotely from the clients. 
* Subversion and Perforce are examples of CVCS.

## Distributed Version Control Systems (DVCS)
* Distributed version control systems address the single point of failure problem.
* Similarly to CVCS, there is a remote repository which is the official state of the project.
* DVCS differ in that each user has a copy of the complete history of the project known as a *local repository*. 
*  If any server dies, and systems were collaborating via that server, any of the clients local repositories can be copied to the server to restore it. However, any data not on the local repositories that happened to be on the remote repositories will still be lost.
* **(Advantage)** Smaller changes can be committed locally offline and then pushed to a remote repository. 
  - Pushing can be thought of updating the files in the remote repository with commits that have been made locally.
* **(Advantage)** Can perform many commands such as committing faster while offline.
* Git and Mercurial are examples of DVCS.

## Advantages of Using a Version Control System
1) Manage a history of changes
    - Metadata of files are maintained. 
    - Compare changes made to files. 
    - Revert to previous versions of a file.
2) Make use of Branches
    - Maintain independent streams of change.
    - Merge branches to combine work.
3) Traceability
    - Trace changes and authors for root cause analysis. 
    - Integration with other tools e.g. IDEs.
4) Facilitates Team work
    - People working independently on the same file/folder can combine their changes, often with minimal distruption.
