#Useful Git Tips

### Create a New Repository
* login to [GitHub](https://github.com/)
* Click the **'+'** on the upper-right corner of any page
* Select **New repository**
* Type in a name for your repository
* Select **Public**
* Click on **Create repository**
* Open iTerm2
* To change current working directory
```
$ cd Desktop/
$ cd [name_of_repo]
```
* Initialize the local directory at a Git repository
```
$ git init
```
* Copy files to your new repository, then track them with
```
$ git add .
```
* Commit your files and add a commit message
```
$ git commit -m "your commit message goes here, always use present tense"
```
* Copy the URL of your repository in GitHub to the clipboard then paste into the line below
```
$ git remote add origin [url_of_remote_repository_copied_from_GitHub]
```
* To check the url of the remote
```
$ git remote -v
```
* Push your local changes to the master (best to work on branch copy not master)
```
$ git push -u origin master
```

### Clone a Repository
* In GitHub, go to the main page of the repository you want to clone
* Under your repository name, click on the "clipboard with arrow" icon
* Open iTerm2
* Change to current working directory
```
$ cd Desktop/
```
* Clone repository to desktop
```
$ git clone [url_of_remote_repository_copied_from_GitHub]
```

### Add File to Repository
* Copy file you want to upload into the local clone folder
* Open iTerm2
* Change to current working directory
```
$ cd Desktop/
$ cd [name_of_repo] 
```
* Stage the files for the first commit to your repository
```
$ git add .
```
* Add a commit message to track your changes
```
$ git commit -m "your commit message goes here"
```
* push the changes to the master branch on GitHub
```
$ git push origin master
```

### Create a New Branch
* Create a new branch
```
$ git branch [name_of_new_branch]
```
* List branches including current branch
```
$ git branch
```
* Switch to new branch
```
git checkout [name_of_new_branch]
```

### Merge New Branch with Master Branch
* Push changes in new branch to remote branch in GitHub
```
$ git push origin [name_of_new_branch]
```
* Switch to master branch
```
$ git checkout master
```
* Merge the new branch
```
$ git merge [name_of_new_branch]
$ git push origin master
```

### Delete a Branch
* List all of the branches
```
$ git branch -a
```
* Switch to master branch
```
$ git checkout master
```
* Delete local copy of branch
```
$ git branch -D [branch_to_delete]
```
* Delete remote copy of branch in GitHub
```
$ git push origin --delete [branch_to_delete]
```

### Go back to earlier commit in Git

```
$ git reset --hard <last good SHA>
$ git push -f origin <branch>
```

### Change your origin url in git

```
$ git remote set-url origin git@github.com:JayJohnson1/final-project.git
```

### Push an exisiting git repo to github
* go to github.com and create a repo
* copy the SSH url to the clipboard
* in iTerm cd into your project directory that you created with “git init"
* create a .gitignore file with (.DS_Store in it)
```
$ touch .gitignore
```
* type:
```
$ git remote add origin git@github.com:JayJohnson1/example.git
$ git push -u origin master
```

### Sync a Fork with an existing repo
* type:
```
$ git fetch upstream
$ git merge upstream/master
$ git push
```







































