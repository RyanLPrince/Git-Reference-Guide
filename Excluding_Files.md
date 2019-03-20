# Excluding Files

## .gitignore
* Specifies intentionally untracked files to ignore.
* Files already tracked by Git are not affected.
* Each line in a gitignore file specifies a pattern.
* Patterns which should be version-controlled and distributed to other repositories via clone 
(i.e., files that all developers will want to ignore) should go into a .gitignore file.

* You can still use some git commands with files that satisfy the .gitignore patterns by specifying the -f|--force flag.
e.g. git add -f fileA.txt.
--
## Pattern Format

* A blank line matches no files, so it can serve as a separator for readability.
* A line starting with # serves as a comment. Put a backslash ("\\") in front of the first hash for patterns that begin with a hash.
* Trailing spaces are ignored unless they are quoted with backslash ("\\").
* An optional prefix "!" which negates the pattern.
* foo/ will match a directory foo and paths underneath it, but will not match a regular file or a symbolic link foo.
*  "*" matches anything except "/", "?" matches any one character except "/" and "[]" matches one character in a selected range.
