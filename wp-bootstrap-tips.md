# Bootstrap & WordPress

* download [wordpress.zip](https://wordpress.org/download/)
* expand the .zip file
* copy the unzipped wordpress folder into your Sites folder
* rename it “wordstrap"
* change directory into wp-content/themes
* create a new folder for your custom theme:
```
$ mkdir wp-wordstrap
```
* inside of your wp-wordstrap folder create a Sublime Project for convenience
* in your wp-wordstrap theme directory, create the following files: 
```
$ touch style.css header.php index.php footer.php functions.php
```
* add a screenshot.png (880 x 660 pixels) to your wp-wordstrap folder
* create a folder for your css
```
$ mkdir css
```
* create a folder for your js
```
$ mkdir js
```
* add the following to your style.css file
```
/*
Theme Name: Kingluddite Magazine Theme
Author: Kingluddite
Author URI: http://kingluddite.com/
Description: A simple theme to showcase how to build a theme from Twitter Bootstrap
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Code and take over the world line-by-line
*/
```
* create a database using phpMyAdmin from a Webstart page in Mamp
* go to localhost/wordstrap/wp-admin/
* add your database name, root, root, localhost in the setup wizard
* create a name for your site, add an admin name and password
* log into your site
* go to wp Dashboard
* select your new custom theme
* visit your page and your site should be blank
* go to this page http://getbootstrap.com/examples/jumbotron/ and view source
* copy the html into your index.php file
* the css links won’t work yet
* in index.php, select the doctype to the closing nav tag
* copy and cut the code
* paste it into header.php
* replace the cut code in index.php with
```
<?php get_header(); ?>
```
* refresh your page in the browser to see if the header include is working
* in index.html, select the "hr" tag to the end of the html
* copy and cut the code
* paste it into footer.php
* replace the cut code in index.php with
```
<?php get_footer(); ?>
```
* refresh your page in the browser to see if the footer include is working
* place a copy bootstrap.min.css inside of your css folder
* place a copy of the ie10-viewport-bug-workaround.css into your css folder
* add the following code to your functions.php
```
<?php
function theme_styles() {
    wp_enqueue_style( 'bootstrap_css', get_template_directory_uri() . '/css/bootstrap.min.css' );
}
add_action( 'wp_enqueue_scripts', 'theme_styles' );
?>
```
* add the following code right before the closing head tag in header.php
```
<?php wp_head(); ?>
```
* add the following code right before the closing body tag in footer.php
```
<?php wp_footer(); ?>
```
* delete the old bootstrap.min.css link in header.php
* in the source page of http://getbootstrap.com/examples/jumbotron/ click on the link to jumbotron.css
* add that css to your style.css file under the comments
* change the class name and values to: .jumbotron { padding-top: 66px; padding-bottom: 48px; }
* delete the old jumbotron.css link in header.php
* copy the fonts folder from the bootstrap-3.3.6-dist folder into wp-wordstrap folder (it should be a sibling of the css and js folders)
* delete the debugging comment in your header.php file
* copy bootstrap.min.js to the js folder
* copy ie10-viewport-bug-workaround.js to the js folder
* your final functions.php file should look like this
```
<?php
function theme_styles() {
    wp_enqueue_style( 'ie10_css', get_template_directory_uri() . '/css/ie10-viewport-bug-workaround.css' );
    wp_enqueue_style( 'bootstrap_css', get_template_directory_uri() . '/css/bootstrap.min.css' );
    wp_enqueue_style( 'main_css', get_template_directory_uri() . '/style.css' );
}
add_action( 'wp_enqueue_scripts', 'theme_styles' );

function theme_js() {
    global $wp_scripts;

    wp_register_script( 'html5_shiv', 'http://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js', '', '', false);
    wp_register_script( 'respond_js', 'http://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js', '', '', false);

    $wp_scripts->add_data( 'html5_shiv', 'conditional', 'lt IE 9' );
    $wp_scripts->add_data( 'respond_js', 'conditional', 'lt IE 9' );

    wp_enqueue_script( 'bootstrap_js', get_template_directory_uri() . '/js/bootstrap.min.js', array('jquery'), '', true );
    wp_enqueue_script( 'ie10_js', get_template_directory_uri() . '/js/ie10-viewport-bug-workaround.js', array('jquery'), '', true );
}
add_action( 'wp_enqueue_scripts', 'theme_js' );
?>
```
* refresh your page in the browser and refresh your wp dashboard > themes page to see the updates
