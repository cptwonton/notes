#### Pre-requisites:
- must have a Linux box
- `sudo yum install bashdb` to db on red hat based distro
- `sudo apt-get install bashdb` to db on debian based distro
- vim, nano, emacs, or [VSCode](https://code.visualstudio.com/) (recommended)

#### History
- sh shell is original, followed by bash, then ksh. each are upgrades over the previous and support scripts written for older shells
- csh and tcsh are newest, based on C language since Linux is built using C

#### Intro
- every command is a binary, including if or else or while. all are linux executables
- shell is the "glue" that binds these commands together
- `type` command tells us exactly what a command is
  - alias
  - function
  - shell built-in
  - keyword
  - file
```Shell
$type ls
ls is alias to 'ls --color=auto'
```

```Shell
$type -a ls
ls is aliased to 'ls --color=auto'
ls is /bin/ls
```

```Shell
$type -t ls
alias
```
to easily add current directory (that scripts are in) to the PATH so they can be run from anywhere:
```Shell
$ export PATH=$PATH:.
```
but even better, move the scripts into the `$HOME/bin` folder so they're available anywhere. (assuming `$HOME/bin` is already on the `PATH`)

does bin exist? :
```Shell
$ test -d $HOME/bin || mkdir $HOME/bin
```

#### Configuring text editors
- vim: done by modifying the `$HOME/.vimrc` [file](./.vimrc)
- nano: done by modifying the `$HOME/.nanorc` [file](./.nanorc)

#### Scripting basics
- every script starts with `#!bin/bash`, this ensures script is interpreted using bash shell, no matter what shell we're on
- `chmod +x $HOME/bin/hello1.sh`, this ensures our script is executable
```Shell
$ command1 || command 2
```
This means command 2 will execute if command 1 fails, i.e. if command 1 `exit`s with a status other than `0`
```Shell
$ command1 && command 2
```
This means command 2 will execute if command 1 succeeds, i.e. if command 1 `exit`s with a `0` status
```Shell
$ hello1.sh
$ echo $?
```
viewing the `$?` variable allows us to see the exit status explicitly

```Shell
$0
``` 
is the name of the script itself
```Shell
$1
``` 
is the first argument passed in
```Shell
${10}
``` 
is the 10th argument, braces are necessary for more than 1 digit and also for evaluating variables
```Shell
$#
```
argument count, especially useful when we need to set the amount of arguments needed for correct script execution
```Shell
$*
```
refers to all arguments
