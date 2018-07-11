#### installing NPM

if 

`npm -v` 

doesn't give latest version, run

`npm install npm@latest -g`

`npm login` if misspell username, will create new account

`npm whoami` to test successful login

#### Installing Modules

local install if wanna `require` within my own module

global install if wanna run from command line

if no package.json, npm will install latest

if package.json, npm will install latest that satisfies semver rules in package.json
