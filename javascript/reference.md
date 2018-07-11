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

`npm install <package_name>` will install packages locally AND add the appropriate entry into package.json | --save-dev

`npm install -g <package_name>` will install packages globally so u can run it from command line

if permissions issues: https://docs.npmjs.com/getting-started/fixing-npm-permissions

`npm update` will update all the packages listed in package.json | `npm update -g <package>` | `npm update -g` | `npm oudated -g --depth=0`

`npm outdated` will list all the outdated packages listed in package.json

`npm uninstall <package_name>` will remove a package from node_modules

`npm uninstall --save <package_name>` will also remove it from package.json | --save-dev

