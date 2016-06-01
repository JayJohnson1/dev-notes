# Bootstrap 4 & WordPress

### Install WordPress
* Using [Variable VVV](https://github.com/bradp/vv)
    * in iTerm, change directories into ~/Sites/vvv/vagrant-local/www and type the following:
    ```
    $ vv create
    ```
    * the local VVV install directory is: ~/Sites/vvv/vagrant-local
    * name your site "bhs"
    * the directory will be: /Users/Jay/Sites/vvv/vagrant-local/www/bhs
    * the URL will be: bhs.dev
    * username: admin
    * password: password

* Or by using [WP-CLI](http://wp-cli.org/)
    * in iTerm, change directories into ~/Sites and create a new folder for your WordPress installation:
    ```
    $ take bhs
    ```
    * download the WordPress core with:
    ```
    $ wp core download
    ```
    * wait til you see the success message
    * create a database in Tools > phpMyAdmin using Mamp Open WebStart page called 'bhs'
    * setup your wp-config file with:
    ```
    $ wp core config --dbuser=root --dbpass=root --dbname=bhs
    ```
    * finish the core install:
    ```
    $ wp core install --url=http://localhost/bhs --title=BHS --admin_user=admin --admin_password=password --admin_email=jayevanjohnson@gmail.com
    ```
    * the directory will be: /Users/Jay/Sites/bhs
    * the URL will be: localhost/bhs/
    * username: admin
    * password: password

* Or with a manual [WordPress](https://wordpress.org/download/) installation
    * download the wordpress.zip file
    * expand the .zip file
    * copy the unzipped wordpress folder into your Sites folder
    * rename it “bhs"
    * create a database called 'bhs' in Tools > phpMyAdmin using Mamp Open Webstart page 
    * navigate to bhs site in localhost using Mamp Open WebStart page
    * configure WordPress
    * the directory will be: /Users/Jay/Sites/bhs
    * the URL will be: localhost/bhs/
    * username: admin
    * password: password
    * title: BHS
    * admin email: jayevanjohnson@gmail.com
    
### Create a custom theme using Bootstrap 4
* in iTerm, change directories into the wp-content/themes folder
* create a new folder for your theme:
```
$ take bhs-theme
```
* create a css folder and a js folder:
```
$ mkdir css js
```
* copy a thumbnail image from [Google Images](https://images.google.com/) into your bhs-theme folder:
```
$ curl -O http://url-for-your-thumbnail-image.jpg
```
* open your thumbnail image in Photoshop and resize/resave it at 880 x 660 pixels as a .png file
* open your theme in Sublime from iTerm:
```
$ sop .
```
* create and edit a [Sublime project](https://github.com/JayJohnson1/dev-notes/blob/master/sublime-tips.md#setup-a-project-in-sublime) for your convenience 
* in your bhs-theme folder create the following files:
```
$ touch style.css header.php index.php footer.php functions.php
```
* add the following comment code to your style.css file in your bhs-theme folder:
```
/*
Theme Name: BHS Theme
Author: Firstname Lastname
Author URI: http://jayevanjohnson.com/
Description: A simple WordPress theme based on Bootstrap 4
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
*/
```
* log in as an admin to your site by appending /wp-admin to your WordPress url in your browser
* once logged in as an admin, navigate to Dashboard > Appearance > Themes
* you should see a thumbnail image for your site
* go to http://v4-alpha.getbootstrap.com/examples/jumbotron/ and right click to view source
* copy the html file into your index.php file in bhs-theme
* in index.html select everything between the doctype to the closing nav tag 
* copy and cut the code and paste it into header.php
* replace the cut code in index.php with:
```
<?php get_header(); ?>
```
* add the following code right before the closing head tag in header.php
```
<?php wp_head(); ?>
```
* in index.html select the hr tag to the end of the html
* copy and cut the code and paste it into footer.php
* replace the cut code in index.php with:
```
<?php get_footer(); ?>
```
* add the following code right before the closing body tag in footer.php:
```
<?php wp_footer(); ?>
```
* create a package.json file in your bhs-theme folder:
```
$ npm init
```
* install Bootstrap 4 with npm:
```
$ npm install bootstrap@4.0.0-alpha.2 --save
```
* install jQuery with npm:
```
$ npm install jquery --save
```
* install Tether with npm:
```
$ npm install tether --save
```
* in iTerm, change directories into the css folder and create a jumbotron.css file:
```
$ touch jumbotron.css
```
* add the following code to jumbotron.css:
```
/* Move down content because we have a fixed navbar that is 50px tall */
body {
  padding-bottom: 2rem;
}
```
* in iTerm, change directories into the js folder and create this file:
```
$ touch ie10-viewport-bug-workaround.js

```
* add the following code to ie10-viewport-bug-workaround.js:
```
/*!
 * IE10 viewport hack for Surface/desktop Windows 8 bug
 * Copyright 2014-2015 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */

// See the Getting Started docs for more information:
// http://getbootstrap.com/getting-started/#support-ie10-width

(function () {
  'use strict';

  if (navigator.userAgent.match(/IEMobile\/10\.0/)) {
    var msViewportStyle = document.createElement('style')
    msViewportStyle.appendChild(
      document.createTextNode(
        '@-ms-viewport{width:auto!important}'
      )
    )
    document.head.appendChild(msViewportStyle)
  }

})();
```
* add the following code to functions.php:
```
<?php
function theme_styles() {
    wp_enqueue_style( 'bootstrap_css', get_template_directory_uri() . '/node_modules/bootstrap/dist/css/bootstrap.min.css' );
    wp_enqueue_style( 'jumbotron_css', get_template_directory_uri() . '/css/jumbotron.css' );
}
add_action( 'wp_enqueue_scripts', 'theme_styles' );

function theme_js() {
    global $wp_scripts;

    wp_register_script( 'html5_shiv', 'http://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js', '', '', false);
    wp_register_script( 'respond_js', 'http://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js', '', '', false);

    $wp_scripts->add_data( 'html5_shiv', 'conditional', 'lt IE 9' );
    $wp_scripts->add_data( 'respond_js', 'conditional', 'lt IE 9' );

    wp_enqueue_script( 'tether_js', get_template_directory_uri() . '/node_modules/tether/dist/js/tether.js', array('jquery'), '', true );
    wp_enqueue_script( 'jquery_js', get_template_directory_uri() . '/node_modules/jquery/dist/jquery.min.js', array('jquery'), '', true );
    wp_enqueue_script( 'bootstrap_js', get_template_directory_uri() . '/node_modules/bootstrap/dist/js/bootstrap.min.js', array('jquery'), '', true );
    wp_enqueue_script( 'ie10_js', get_template_directory_uri() . '/js/ie10-viewport-bug-workaround.js', array('jquery'), '', true );
}
add_action( 'wp_enqueue_scripts', 'theme_js' );

?>
```
* in your header.php file, comment out the style links for bootstrap.min.css and jumbotron.css
* in your footer.php file, comment out the scripts for bootstrap.min.js and ie10-viewport-bug-workaround.js

### Activate the BHS theme
* if you're using Variable VVV:
    * bring up the vagrant box:
    ```
    $ vagrant up
    ```
    * ssh into vagrant:
    ```
    $ vagrant ssh
    ```
    * change directories into htdocs
    ```
    $ cd /srv/www/bhs/htdocs
    ```
    * see your installed themes with:
    ```
    $ wp theme list
    ```
    * activate your bhs theme:
    ```
    $ wp theme activate bhs-theme
    ```
    * refresh bhs.dev/wp-admin/themes.php page to see your custom theme

* if you're using WP-CLI:
    * change directories into ~Sites/bhs
    * see your installed themes with:
    ```
    $ wp theme list
    ```
    * activate your bhs theme:
    ```
    $ wp theme activate bhs-theme
    ```
    * refresh localhost/bhs/wp-admin/themes.php page to see your custom theme

* if you installed WordPress manually:
    * go to localhost/bhs/wp-admin in your browser
    * log into WordPress with username: admin, password: password
    * in the Dashboard, go to Appearance > Themes
    * click the activate button for the bhs-theme
    * refresh localhost/bhs/wp-admin/themes.php page to see your custom theme

### Add your theme to Git
* Install Git locally in your WordPress root folder (which contains wp-admin, wp-content, etc.):
```
$ git init
```
* Create a .gitignore file in this same WordPress root folder:
```
$ touch .gitignore
```
* Add the following code to your .gitignore file:
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
!wp-content/themes/bhs-theme/

node_modules
.sass-cache
.DS_Store
bower_components
*maps*
*.min*
*vendors.js
```
* Check to see that most of your files are ignored:
```
$ git status
```
* Add your files to Git with:
```
$ git add -A
```
* Create an initial commit in Git:
```
$ git commit -m 'Initialize repo'
```
* Use [Hub](https://github.com/JayJohnson1/dev-notes/blob/master/hub-tips.md) to create a remote repository on Github.com:
```
$ git create -d "my-new-remote-repo"
```
* Push your local repository up to the remote repo and set the remote as upstream:
```
$ git push --set-upstream origin master
```

