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
