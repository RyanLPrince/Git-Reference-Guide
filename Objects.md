# Git Objects

## Types of Objects:

1) **Commit Object:** Simple text file which stores:
    - Commit user information.
    - Commit message. 
    - Reference to parent(s).
    - Reference to the root tree of the project.<br><br>   
2) **Annotated Tag**: Reference to a specific commit.<br><br>
3) **Tree**: Contains a list of file names and directories.<br><br>
4) **Blob**: Contains the content of a file that is being managed by git. 

* Typically users will only interact with commit objects and annotated tags. 

## Git IDs
* A Git ID is the name of the git object.
    - 40 character hexadecimal string.
    - Also known as SHA-1, hash or checksum.
~~~
$ git log 
commit c95497e76de801035f80312b9d97ac8d06ebbd2c (origin/master)   ⭠ (Other log details omitted) 

$ git hash-object <file>                                          ⭠ Produces a SHA-1 value for a file
~~~

* Use git IDs to referene a commit 
* Git sometimes shortens the 40 character ID to the first 7 characters 

~~~
$ git  log --oneline
3bd90a7 (HEAD -> master, origin/master) "Initial commit"
~~~
* You can use the first 4 characters to reference a Git ID. As long as no other commit object shares the first 4 characters, git will know which object is being referenced. If not, you may need to enter more characters of the ID in order for git to unambiguosly differenciate the objects. 
~~~
$ git show 3bd9               ⭠ Shows the contents of the commit object 3bd9: author, date, commit message...
~~~

## Git References

* Commits can be associated with references.
* References are a user-friendly name that points to a commit's SHA-1 value or another reference.
    - References that point to another reference are known as a symbolic referene.
    - In the example below, HEAD is a symbolic reference.
~~~
$ git  log --oneline
3bd90a7 (HEAD -> master, origin/master) "Initial commit"     ⭠ This commit has two references associated with it.
~~~

* Can use references instead of SHA-1 values to refer to an object.
###### Note:
* Master is the default name of the main branch of the repository.
* Branch labels point to the most recent commit of a branch.

HEAD<br>
- Reference to the current commit.
- One HEAD reference per repo.
- Usually points to the branch label of the current branch. i.e (HEAD -> master)

* Possible to reference the parent of a commit by appending a `~` to the ID or reference.
~~~
$ git show HEAD~              ⭠ Shows parent of the HEAD. Same as HEAD~1.
$ git show HEAD~~             ⭠ Shows the HEADS's parent's parent. Same as HEAD~2.                           
~~~

* The `^` character can be appended to IDs and references in git commands, primarily to refer to a specific parent in a merge commit. 

~~~
$ git show 39jf^              ⭠ Shows first parent in a merge commit. Same as ~1 or ~.
$ git show 39jf^2             ⭠ Shows second parent in a merge commit. 
$ git show 39jf^^             ⭠ Shows first parent's first parent. Same as ~2 or ~~. 
~~~

## Tags
* A tag is a reference/label attached to a specific commit. e.g. master, HEAD, v1.0.
* 2 types of tags:
    - **Lightweight tags**: Simple reference to a commit, e.g branch lable or HEAD.
    - **Annotated tags**: Full git object that references a commit, (metadata) tag author, tag date, tag message, commit ID, optionally signed and verifies with GNU privacy guard (GPG).
* Tags can be used as an alternative to commit IDs and or branch labels for referencing.   

~~~
$ git tag                                                                       ⭠ View all tags in the repository.

$ git tag <tagname> [<commit>]                                                  ⭠ Create a lightweight, tag <commit> defaults to HEAD if not specified. 

$ git tag -a [-m <msg>|-F <file_containing_message>]  <tagname> [<commit>]      ⭠ Create an annotated tag. Use -f to force overwrite tag if you specify a name that already exists. If you do not write a message you will be prompted by the editor to write one.
~~~

* Git push does not automatically transfer tags. 

~~~
$ git push <remote> <tagname>                        ⭠ Pushes specified tag to remote repo.

$ git push <remote> --tags                           ⭠ Transfer all tags to remote repo.

$ git tag -d|--delete <tagname>                      ⭠ Delete specified tag in local repo.

$ git push -d|--delete <remote_name> <tagname>       ⭠ Delete specified tag in remote repo.
            OR
$ git push <remote_name> :refs/tags/<tagname>        ⭠ Pushes empty ref name to remote repo. Tag must be deleted locally first.
~~~
