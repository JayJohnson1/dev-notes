# Hub for Git

### Install Hub
* install Hub with
```
$ brew install hub
```
* create an alias in your .zshrc file
```
$ alias git=hub
```

### Clone a WordPress theme & Install a local Git repository
* copy a url from a repository on Github.com (git@github.com:JayJohnson1/wurtlepress.git)
* change directories into your Sites folder
```
$ cd Sites
```
* clone the custom WordPress theme into a folder called tmnt
```
$ git clone git@github.com:JayJohnson1/wurtlepress.git tmnt
```
* change directories into your local repo folder (tmnt)
```
$ cd tmnt
```
* trash your .git file
```
$ trash .git
```
* change directories into wp-content/themes/my-theme
```
$ cd tmnt/wp-content/themes/wp-ninja-turtles
```
* install node modules
```
$ npm install
```
* change directories into your local repo folder (tmnt) 
```
$ cd tmnt
```
* initialize a local repo, add the files, and do an initial commit
```
$ git init
$ git add .
$ git commit -m 'Initialize repo'
```

### Use Hub to create a remote repository on Github
* use Hub to create a remote repo
```
$ git create -d "my-new-repo"
```
* enter your github.com username and password
* push your local repo to the remote repo on github.com
```
$ git push origin master
```
* go to your Github.com repositories to see your new repository
