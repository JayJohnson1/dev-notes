# Interactive Communication Dev & Delivery (notes)

### If you forget your admin/password
* cd into ~/Sites/vagrant-local/www/my-cool-wp-site/
* type $ sop .
* open vvv-init.sh file
* check line 16 for username and password information

### VVV & WP-CLI Setup & Workflow
* Install VirtualBox (if you haven’t already)
* Install Vagrant (if you haven’t already)
* Install the vagrant-hostsupdater plugin
* Install the vagrant-triggers plugin
* In your Sites folder type:
```
$ git clone git://github.com/Varying-Vagrant-Vagrants/VVV.git vagrant-local
```
* Install VV
```
$ brew install bradp/vv/vv
```
* cd into the vagrant-local folder and type:
```
$ vagrant up
```
* create a new WP site by typing:
```
$ vv create
```
* install a VVV Dashboard
* go to <http://vvv.dev> to confirm your site exists
* confirm vagrant box is still running:
```
$ vagrant status
```
* when the box comes up type:
```
$ vagrant ssh
```
* at the vagrant@vvv prompt type:
```
$ cd /srv/www/my-cool-wp-site/htdocs/
```
* confirm you're in the root WP directory by typing:
```
$ ls
```
* now you can use wp-cli commands like 'wp theme list' or 'wp plugin list'
* to exit vagrant ssh type:
```
$ exit
```

### Git in WordPress
* after you install wp, you can add your site to Github. Only push your site's htdocs folder.
```
$ cd ~/Sites/vagrant-local/www/my-cool-site/htdocs
$ git init
$ git status
```
* after doing a git status you'll see 21 files listed in red
* create a remote repo on Github and copy the ssh code to your clipboard
* add a remote origin to your local git
```
$ git remote add origin git@github.com:JayJohnson1/my-cool-site.git
```
* create a .gitignore file in your htdocs folder
```
$ touch .gitignore
```
* open your .gitignore file and add the following...
```
# Thanks to: https://gist.github.com/jdbartlett/444295

# Place this .gitignore file into ~/Sites/vagrant-local/www/my-wp-site/htdocs/

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
!wp-content/themes/my-awesome-theme/

node_modules

```
* save and close your .gitignore file. The next time you do a git status in htdocs you should only see the .gitignore file as untracked (in red).
```
$ git status
```
* now add your file and do a commit and push
```
$ git add -all
$ git commit -m "Add new wp site to repo"
$ git push -u origin master
```
* if you get stuck in Vim mode type esc, :wq and return to exit
```
$ esc:wq
```
