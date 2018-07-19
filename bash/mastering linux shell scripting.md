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
