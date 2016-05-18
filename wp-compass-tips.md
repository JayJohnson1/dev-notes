# Compass & WordPress

### Install Sass and Compass
* in Term, type the following:
```
$ gem update --system
$ gem install sass
$ gem install compass
```

### Adding necessary files and folders
* in your custom theme folder, duplicate the previous style.css file in the css folder and rename it style.scss
* create an scss folder in your custom theme folder
```
$ mkdir scss
```
* move the style.scss file into the scss folder
* open up the style.css file in the root of your custom theme folder
* copy the top comment section and paste it into your style.scss file
* add an "!" at the beginning of the comment section in your style.scss file
```
/*!
Theme Name: Custom WordPress Theme
Author: Jay Johnson
Author URI: http://jayevanjohnson.com/
Description: 
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

*/
```

### The config.rb file
* create a config.rb file in your custom theme folder
```
$ touch config.rb
```
* add this to your config.rb file:
```
http_path = "/" #root level target path
css_dir = "." #targets our default style.css file at the root level of our theme
sass_dir = "scss" #targets our sass directory
images_dir = "img" #targets our pre existing image directory
javascripts_dir = "js" #targets our JavaScript directory

# You can select your preferred output style here (can be overridden via the command line):
# output_style = :expanded or :nested or :compact or :compressed
output_style = :compressed

# To enable relative paths to assets via compass helper functions.
# note: this is important in wordpress themes for sprites

relative_assets = true
```
* now you can rename or delete the previous style.css file in the root of your custom theme folder
* you can also delete the previous style.css file in the css folder of your custom theme 

### Make Sass watch for updates to your style.scss file
* start watching your files with compass. A new compressed style.css file will be generated in the root of your custom theme folder:
```
$ compass watch
```


