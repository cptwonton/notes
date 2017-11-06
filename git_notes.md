came out of Linux/Bitkeeper fallout
snapshots instead of diffs, means super efficient


First-Time Git Setup
only need to do once. stick around thru upgrades.
can change by running again.

C:\ProgramData\Git\config (system level) can only be changed by git config -f <file> as admin
C:\Users\$USER\.gitconfig (user level)
in etc on linux

//set profile
git config --global user.name "Jeffrey Hong"
git config --global user.email hong66@illinois.edu

//set default editor 
git config --global core.editor "'D:/Program Files/Notepad PP/notepad++.exe' -multiInst -nosession"

//set USPS proxy
git config http.proxy=http://proxy.usps.gov:8080
git config https.proxy=https://proxy.usps.gov:8080

git will use the LAST entry of 
git config --list 
command as the effective config

pull up git man pages with 
git help <verb> //i.e git help config

