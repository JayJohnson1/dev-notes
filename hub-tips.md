# Hub for Git

* install Hub with
```
$ brew install hub
```
* create an alias in your .zshrc file
```
$ alias git=hub
```
* copy a url from a repo on github (git@github.com:JayJohnson1/my-repo.git)
* change directories into your Sites folder
```
$ cd Sites
```
* clone your remote repo
```
$ git clone git@github.com:JayJohnson1/my-repo.git
```
* change directories into your local repo folder
```
$ cd my-repo
```
* trash your .git file
```
$ trash .git
```
* change directories into wp-content/themes/my-theme
```
$ cd wp-content/themes/my-theme
```
* install node modules
```
$ npm install
```
* change directories into your local repo folder
```
$ cd my-repo
```
* initialize a local repo, add the files, and do an initial commit
```
$ git init
$ git add .
$ git commit -m 'Initialize repo'
```
* use Hub to create a remote repo
```
$ git create -d "my-new-repo"
```
* enter your github.com username and password
* push your local repo to the remote repo on github.com
```
$ git push origin master
```
* go to your github repositories to see your new repo
