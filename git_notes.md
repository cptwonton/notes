## quicknotes
update local repo:

``git remote add upstream https://github.com/testingresearchillinois/starts.git``

``git fetch upstream``

``git checkout master``

``git merge upstream/master``

push merged local repo back up to remote

``git push origin master``

``git checkout STARTS-LOGGING``

``git rebase master``

``git pull``

``git push origin STARTS-LOGGING``

rebasing:
``git checkout <branch you're rebasing>``
``git rebase <branch you're rebasing to>``
resolve conflicts, ``git add .`` and ``git rebase --continue`` after each conflict resolution
``git push origin <branch> -f`` after rebase is done

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

[sample .gitignore](./.gitignore-sample)

[more .gitignore samples on github](https://github.com/github/gitignore)

`git diff` is a more specific version of `git status`. will answer two questions:
- what changed but not staged? `git diff`
- what staged but not committed? `git diff --staged`

`git rm --cached <pattern/filename>` will remove a file from the staging area but not from disk/workspace. useful for large log files, etc... things that I forgot to add to gitignore
seems like `git reset HEAD <filename>` does the same thing as `git rm --cached <file/pattern>`

`git mv <old file> <new file>` is shorthand for renaming a file and making sure git knows about it. otherwise, need to mv, rm, and add manually.

#### Viewing Commit History
`git log`, can call with a bunch of options

`git checkout -- <filename>` to discard changes to filename

#### Working with Remotes
`git remote` to show shortnames for each remote handle defined
`origin` is default name Git gives to server I cloned from
`-v` to show URLs

`git remote add <shortname> <url>`
`git fetch <remote>` grabs all the stuff you don't have but is on the remote
`git fetch origin`
`git push <remote> <branch>`

`git remote rename <oldname> <newname>`

#### Tagging
`git tag` lists all tags for repo
`git tag -a v1.4 -m "my version 1.4"` creates a new (annotated) tag called v1.4 with message "my version 1.4"
`git tag v1.4-lw` makes a lightweight tag without some of the info from the annotated tag
`git tag -a v1.2 9fceb02` adds tag to old commit by providing commit's checksum
`git push` does not automatically push tags up to remote. to do this individually, `git push origin <tagname>`. 
if pushing multiple tags, `git push origin --tags`
make sure to branch if making changes to tagged commits!!!

#### Aliases
`git config --global alias.co checkout`
`git config --global alias.br branch`
`git config --global alias.ci commit`
`git config --global alias.st status`
instead of typing `git commit`, can just type `git ci`
prefix with ! to run external command. i.e., `git config --global alias.visual '!gitk'`


## Chapter 3
git branching is super lightweight, which is what makes git the best compared to other VCS.

#### Branches

blobs stores each file and its checksum
tree stores collection of blobs
commits point to a tree, includes previous commit sha
branches point to a commit
head points to a branch
master is just like any other branch, nothing special except that its created by default

`git branch testing` to create a new branch called testing. This makes a new branch, points it to the latest commit, but does not switch to it - HEAD will still point to the current branch, not testing.
Confirm with `git log --oneline --decorate`
switch branches with `git checkout <branchname>`, like `git checkout testing`

branching is super cheap, only costs 41 bytes

#### Basic Branching and Merging

`git checkout -b iss53` to create a new branch called iss53 and swap to it
equivalent to `git branch iss53` + `git checkout iss53`
git will not let you switch branches if you have unstaged/uncommited files in workspace that conflict with branch to be switched to.
after making changes to hotfix branch, `git checkout master` + `git merge hotfix` will bring master up to date with hotfix branch

to delete a branch, git branch -d hotfix

sometimes, merge conflicts happen. will pause merge process to let you resolve. `git status` to see which files need to be manually merged
once you manually merge, running `git add` on each file that you manually merged will be all git needs to continue the merge
once you are completely done and `git status` shows that things are good, `git commit` to finalize the merge commit.

#### Branch Management

`git branch` shows you all the branches. * means that a branch is the HEAD
`git branch -v` shows the last commit on each branch
--merged and --no-merged options for `git branch` show you which branches you have or have not merged yet into the branch you're currently on

#### Branching Workflows

since its super easy to merge branches, alot of projects have long running branches. 
master will only hold code that is entirely stable.
develop/next branch holds work they're working on or used to test stability. whenever it's stable, it's merged into master. pulls in topic branches (small short lived branches to address certain issues) before merging into master.
topic branches are short lived branches that you make for a single piece of work. unique to git because of how easy it is to branch - other VCS, topic branches are too expensive to be useful.

#### Remote Branches

get full list of remote references with `git ls-remote [remote]` or `git remote show [remote]`



//bookmark
https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository




