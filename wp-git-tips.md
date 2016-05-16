# WordPress & GitHub

### Only push your wp theme to GitHub
* change directories into your wp root folder and type 
```
$ git init
```
* check your untracked files by typing
```
$ git status
```
* create a .gitignore file in your wp root folder
```
$ touch .gitignore
```
* open your wp root folder in Sublime Text
```
$ sop
```
* copy the following code into your .gitignore file to ignore everything except your theme
```
# Thanks to: https://gist.github.com/jdbartlett/444295

# Ignore everything in the root except the "wp-content" directory.
/*
!.gitignore
!README.md
!wp-content/

# Ignore everything in the "wp-content" directory, except the "plugins" and "themes" directories.
wp-content/*
!wp-content/plugins/
!wp-content/themes/

# Ignore everything in the "plugins" directory, except the plugins you specify
wp-content/plugins/*
# !wp-content/plugins/my-single-file-plugin.php
# !wp-content/plugins/my-directory-plugin/

# Ignore everything in the "themes" directory, except the themes you specify
wp-content/themes/*
!wp-content/themes/my-wp-theme/

node_modules
.sass-cache
.DS_Store
bower_components
*maps*
*.min*
*vendors.js
```
* create a new repository in GitHub
* add a license (MIT) and a Readme.md file
* do a git status and you should only see .gitignore and wp-content listed
```
$ git status
```
* add your changes to GitHub
```
$ git add -A
```
* commit your changes to GitHub
```
$ git commit -m 'initialize repo'
```
* check your remote connections
```
$ git remote -v
```
* add your origin from the GitHub repo you created
```
git remote add origin git@github.com:JayJohnson1/my-wp-theme.git
```
* check your remote connections
```
$ git remote -v
```
* you should see 2 origin files now
* type the following to pull down any changes
```
$ git pull origin master
```
* an editor may open up, type the following to close it
```
$ :q
```
* push your local repo changes up to GitHub
```
$ git push origin master
```
