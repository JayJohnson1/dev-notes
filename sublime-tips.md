#Useful Sublime Tips

### ST3 Packages to install:
* Package Control
* Emmet
* Sidebar Enhancements
* Bootstrap 3 Snippets
* MarkdownEditing
* Markdown Preview
* Material theme
* Seti Ui


### Goto Anything in ST3
```
command + p
```

### Show/Hide Sidebar
```
command + k followed by command + b
```

### Command Palette
```
shift + command + p
```

### Install a Package
```
shift + command + p
packin
```

### Uninstall a Package
```
shift + command + p
packr
```

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
