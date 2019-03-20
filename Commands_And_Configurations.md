# Commands and Configurations

## Syntax of a Git Command
~~~
git [command] [--flags|-f] [<argument>] [--] [<aguments>...] 
~~~
~~~
$ git pull                           ⭠ git command 

$ git pull  --set-upstream           ⭠ git command --flag. Flags are also known as options or switches. Flags change the command behaviour.

$ git pull  -u                       ⭠ git command -f. Many flags have shorthand notation i.e --set-upstream flag for the pull command is the equivalent of -u.

$ git pull origin master             ⭠ git command argument argument

$ git pull origin -- master          ⭠ git command argument -- argument. Standalone two dashes can be used to disambiguate a command. This command is the equivalent of `git pull origin master`.
~~~
Example documentation of a git command:
~~~
git push [--all | --mirror | --tags] [--follow-tags] [--atomic] [-n | --dry-run] [--receive-pack=<git-receive-pack>]
	   [--repo=<repository>] [-f | --force] [-d | --delete] [--prune] [-v | --verbose]
	   [-u | --set-upstream] [-o <string> | --push-option=<string>]
	   [--[no-]signed|--signed=(true|false|if-asked)]
	   [--force-with-lease[=<refname>[:<expect>]]]
	   [--no-verify] [<repository> [<refspec>…]]
~~~
* Optional values are surronded by square brackets `[]`. e.g. [--atomic]
* Placeholders are surronded by angular brackets `<>`. e.g. \<repository> 
* [<optional_placeholder>] e.g. [\<repository>]
* Elipses `...` indicate multiple occurences are possible. e.g. [\<refspec>…]
* The pipe symbol `|` represents or e.g. [--all | --mirror | --tags]  

## Git Help
~~~
$ git --version                ⭠ Returns the version of git installed.

$ git help                     ⭠ Provides generic help about common git commands in various scenarios.

$ git help <command>           ⭠ Opens online docummentation of the specified command.

$ git <command> -h|--help      ⭠ Returns concise offline help.
~~~

## Configuring User Information

* Username and email information is included in all commits you make.
* GitHub provides a default no-reply email address.
* The system flag applies a configuration change to every repo, for all users on the computer.
* The global flag applies the changes to every repo for the active user on the computer.
* The local flag or no flag applies the change to the current repository (highest precedence).
* If local value is set it takes precedence, if not global value takes precedence, otherwise the system value takes precedence.
~~~
  git config [--local|--global|--system] <key> [<value>]
~~~

~~~
$ git config --list|-l 				  ⭠ Lists the current global configuations (system and local configuations can be viewed by using the appropriate flag). 	

$ git config --global user.name "RyanLPrince"     ⭠ Configures the (global) username associated with repository. Note RyanLPrince is also a valid argument without the speech marks.                                                     

$ git config --get user.name                      ⭠ Returns the (gloabl) user name associated with the repository.
RyanLPrince
  
$ git config user.name                            ⭠ Also returns the (gloabl) user name associated with the repository.
RyanLPrince
  
$ git config --get --system user.name             ⭠ Returns the system user name.
                                               	  ⭠ Here no system user name is set so the response is empty.
  
$ git config --local user.email email@email.com   ⭠ Configures the (local) email address associated with the repository.
  
$ git config --local --unset user.email           ⭠ Removes the (local) email address associated with the repository. 
  
$ git config --global core.editor nano            ⭠ Configures the editor (used to write messages).
~~~ 
