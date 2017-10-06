# NPM
This is specifically for working with NPM in a git repo


## Version Publishing
(This assumes that the master branch is the release branch.)
```
git checkout master
git pull
npm version patch
git push origin master
git push origin <tag name>
npm publish
```
*<tag name>* will correspond to the version reported by NPM after `npm version patch`

## NVM ##
Althought not actually part of npm, I find this to be commonly useful while also working with NPM.

Install and use a specific version by default (fairly common to need to do when working with new versions)
```
nvm install v8.5.0
nvm alias default v8.5.0
```
