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
