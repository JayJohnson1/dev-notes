# WP-CLI & WordPress

* change directory into your Sites folder
* create a new folder for your custom theme
```
$ mkdir ninja-turtles
$ cd ninja-turtles
```
* download the WordPress core with
```
$ wp core download
```
* wait til you see the success message
* create a database in phpMyAdmin (ours will be donatello_wp)
* after you have created a database, set up the wp-config file with
```
$ wp core config --dbuser=root --dbpass=root --dbname=donatello_wp
```
* now do the WordPress core install with
```
$ wp core install --url=http://localhost/ninja-turtles --title=NinjaTurtles --admin_user=jay --admin_password=password --admin_email=jayevanjohnson@gmail.com
```

* HW: Create a wp theme called Leonardo, create all files for your theme, activate your theme, use Phil's Bootstrap Jumbotron code, make the site TMNT themed, use wp enqueue styles in your functions.php, make sure to add hooks for the header and footer

-------------------------------------------------------------------------------
