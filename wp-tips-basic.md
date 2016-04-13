# Authoring for Interaction (notes)

* wordpress.com is where anyone can go to sign up and install wp
* by going to [wordpress.org](http://www.wordpress.org) we have more power
* largest community in the world, joomla and drupal are alternatives
* wp user experience is great
* we will work in wp-content
* ip for localhost is 127.0.0.1
* no program can run on the same port

### Helpful tools to use
* Alfred app
* Package Control for Sublime Text
 * hit control + ~ to paste in Package Control code
 * use command + shift + p to open Command Palette
 * type “packin” to install packages
 * type "packr" to uninstall packages
* Packages to install: 
 * Markdown Preview
 * Mardown Editor
 * Emmet
 * Bootstrap 3 Snippets
 * Material theme
 * Seti Ui
 * Sidebar Enhancements

### WordPress Installation Process
* go to [wordpress.org](http://www.wordpress.org)
* download WordPress 4.4.2 zip to your desktop
* unzip the wp folder
* copy the wp folder into your Sites folder
* rename the wp folder to my-first-wordpress
* start up Mamp
* open Webstart page in Mamp
* go to tools > phpMyAdmin
* create a new database called wp_test
* open the localhost page in your browser (or click on Open Webstart page)
* click on the my-first-wordpress link on your localhost page
* at the prompt click on “lets go"
* database name: wp_test
* user: root
* pass: root
* hit submit
* click run the install
* add information in the fields
* check Discourage search engines from indexing this site
* click install
* click login
* click on Test Site to bring up your new wp site
* go to Appearance > Themes to change themes
* Update your plugins
* Add a new post
* click on the text tab
* add info or an image and click on publish

### Add a Contact Form
* add a new page
* add “Contact Me” for title
* click publish
* view page
* click on edit
* goto Dashboard plugins to add new plugin
* look for Contact Form 7
* click on install now
* click on activate plugin
* click on contact forms under Contact
* click on Contact Form 7 and edit
* copy short code
* click on pages
* delete sample page
* edit contact me page and paste in short code
* click update and view page

### Setup a Project in Sublime
* type $ sublime . inside of your project directory to open it up in Sublime
* command + shift + p
* type save
* save your project in a folder inside the projects folder
* save the file as my-first-wp-site.sublime-project
* command + shift + p
* edit project
* add this to your project
* 
 ```
 {
     "folders":
     [
         {
             // CORE
             "path": "/Users/Jay/Sites/my-first-wordpress-site",
             "name": "CORE"
         },
         {
             // Evolve Theme
             "path": "/Users/Jay/Sites/my-first-wordpress-site/wp-content/themes/evolve/",
             "name": "evolve theme"
         }
     ]
 }
 ```

* HW: Install wp at home manually through browser, install iTerm, check out Wes Bos videos

-------------------------------------------------------------------------------
