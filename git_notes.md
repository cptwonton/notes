## Chapter 1
came out of Linux/Bitkeeper fallout
snapshots instead of diffs, means *super* efficient


#### First-Time Git Setup
only need to do once. stick around thru upgrades.
can change by running again.

`C:\ProgramData\Git\config` (system level) can only be changed by `git config -f <file>` as admin
`C:\Users\$USER\.gitconfig` (user level)
in etc on linux

###### set profile
`git config --global user.name "Jeffrey Hong"`
`git config --global user.email hong66@illinois.edu`

###### set default editor 
`git config --global core.editor "'D:/Program Files/Notepad PP/notepad++.exe' -multiInst -nosession"`

###### set USPS proxy
`git config http.proxy=http://proxy.usps.gov:8080`
`git config https.proxy=https://proxy.usps.gov:8080`

git will use the LAST entry of `git config --list` command as the effective config

pull up git man pages with `git help <verb>` //i.e git help config

## Chapter 2
#### Getting a Git Repo
can either init a pre-existing folder OR clone a repo elsewhere

`git init`
`git add *.c`
`git add LICENSE`
`git commit -m 'initial project version'`

OR

`git clone <remote repo name>`

**untracked** files are unknown by git until you add them, untracked -> staged
**unmodified** files are known by git but are unchanged since last snapshot, can either edit -> modified or remove -> untracked
**modified** files are known by git and are changed since last snapshot, modified -> staged
**staged** files are known by git and are ready to commit -> unmodified

`git status` will tell me which files are in what state (**untracked**, **unmodified**, **modified**, **staged**)

`cat .gitignore`

`*.[oa]` _.o and .a files, these are object and archive files, products of building code_

`*~` _files ending in ~, these are temp files made by most text editors_

!negate-these-patterns
#ignore these lines
/avoid recursivity
directory/



//bookmark
https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository




