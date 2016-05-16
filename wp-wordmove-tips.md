# Using Wordmove

### Create a database and subdomain on your host
* go to the cpanel in Hostmonster and navigate to the Subdomains icon
* create a subdomain (first.jayevanjohnson.com) and note the absolute path (/home6/jayevanj/public_html/first)
* go to the cpanel in Hostmonster and navigate to the MySQL Databases
* create a database called "jayevanj_first", user: "jayevanj_admin", password: "p@ssword" and enable privileges

### Create a Movefile
* change directories into your WordPress root folder
```
$ cd vvv/vagrant-local/www/first-wp-site
```
* start up Vagrant if it isn't already up
```
$ vagrant up
```
* once the box comes up, ssh into it
```
$ vagrant ssh
```
* change directories into your local wp htdocs folder
```
$ cd /srv/www/first-wp-site/htdocs
```
* create your Wordmove Movefile
```
$ wordmove init
```
* open your Movefile in Sublime (set file type to yaml) and configure it like this:
```
local:
  vhost: "http://first-wp-site.dev"
  wordpress_path: "/srv/www/first-wp-site/htdocs" # use an absolute path here

  database:
    name: "first-wp-site"
    user: "wp"
    password: "wp"
    host: "localhost"

staging:
  vhost: "http://first.jayevanjohnson.com"
  wordpress_path: "/home6/jayevanj/public_html/first" # use an absolute path here

  database:
    name: "jayevanj_first"
    user: "jayevanj_admin"
    password: "p@ssword"
    host: "localhost"
    # port: "3308" # Use just in case you have exotic server config
    # mysqldump_options: "--max_allowed_packet=1G" # Only available if using SSH

  exclude:
    - ".git/"
    - ".gitignore"
    - ".sass-cache/"
    - "node_modules/"
    - "bin/"
    - "tmp/*"
    - "Gemfile*"
    - "Movefile"
    - "wp-config.php"
    - "wp-content/*.sql"

  # paths: # you can customize wordpress internal paths
  #   wp_content: "wp-content"
  #   uploads: "wp-content/uploads"
  #   plugins: "wp-content/plugins"
  #   mu_plugins: "wp-content/mu-plugins"
  #   themes: "wp-content/themes"
  #   languages: "wp-content/languages"

  ssh:
    host: "jayevanjohnson.com"
    user: "jayevanj"
    password: "************" # password is optional, will use public keys if available.
  #   port: 22 # Port is optional
  #   rsync_options: "--verbose" # Additional rsync options, optional
  #   gateway: # Gateway is optional
  #     host: "host"
  #     user: "user"
  #     password: "password" # password is optional, will use public keys if available.

  # ftp:
  #   user: ""
  #   password: ""
  #   host: ""
  #   passive: true
  #   scheme: "ftps" # default "ftp"

# production: # multiple environments can be specified
#   [...]
```

### Install WordPress on your host
* in iTerm ssh into your host
```
$ ssh jayevanj@jayevanjohnson.com
```
* change directories into your subdomain folder
```
$ cd public_html/first
```
* install Wordpress core
```
$ wp core download
```
* open up your subdomain in Chrome, first.jayevanjohnson.com
* initialize WordPress with a username and password
* log into WordPress admin

### Push your local WordPress site to a staging server
* while still ssh'd into your Vagrant box, change into your local wp htdocs folder
```
cd /srv/www/first-wp-site/htdocs
```
* push your database, themes and plugins using Wordmove
```
$ wordmove push -e staging -dtp
```
* refresh the first.jayevanjohnson.com site to see the changes

