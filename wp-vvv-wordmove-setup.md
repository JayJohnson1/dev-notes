# VVV and Wordmove Install Notes

### Install VirtualBox
* Download [VirtualBox 5.0.x](https://www.virtualbox.org/wiki/Downloads)

### Install Vagrant
* Download [Vagrant](https://www.vagrantup.com/downloads.html)
* vagrant will now be available in your terminal, check the version
```
$ vagrant -v
```
* Install the vagrant-hostsupdater plugin
```
$ vagrant plugin install vagrant-hostsupdater
```
* Install the vagrant-triggers plugin
```
$ vagrant plugin install vagrant-triggers
```
* In your Sites/vvv folder type
```
$ git clone git://github.com/Varying-Vagrant-Vagrants/VVV.git vagrant-local
```
* cd into the vagrant-local/provision folder and create a file called provision-pre.sh:
```
$ touch provision-pre.sh
```
* Add the following code to this provision-pre.sh file
```
# Rubygems update

if [ $(gem -v|grep '^2.') ]; then
    echo "gem installed"
else
    apt-get install -y ruby-dev
    echo "ruby-dev installed"
    echo "gem not installed"
    gem install rubygems-update
    update_rubygems
fi

# wordmove install
wordmove_install="$(gem list wordmove -i)"
if [ "$wordmove_install" = true ]; then
  echo "wordmove installed"
else
  echo "wordmove not installed"
  gem install wordmove

  wordmove_path="$(gem which wordmove | sed -s 's/.rb/\/deployer\/base.rb/')"
  if [  "$(grep yaml $wordmove_path)" ]; then


    echo "can require yaml"
  else
    echo "can't require yaml"
    echo "set require yaml"

    sed -i "7i require\ \'yaml\'" $wordmove_path

    echo "can require yaml"

  fi
fi
```
* Bring up your vagrant box with
```
$ vagrant up
```
* Run vagrant provision
```
$ vagrant reload --provision
```
* When nginx is done restarting type
```
$ vagrant ssh
```
* Check to make sure wordmove is installed by typing the following
```
$ wordmove
```
* You should see a list of options for using Wordmove

### Variable VVV - The Best VVV Site Wizard
* [Variable VVV](https://github.com/bradp/vv)
```
$ brew install bradp/vv/vv
```
* create a new WP site by typing:
```
$ vv create
```

### VVV-Dashboard
* [VVV-Dashboard](https://github.com/leogopal/VVV-Dashboard)
* Change into your vagrant-local/www/default directory
```
$ cd ~/Sites/vvv/vagrant-local/www/default
```
* Clone the repository
```
$ git clone git@github.com:leogopal/VVV-Dashboard.git VVV-Dash-Files-tmp
```
* Move the dashboard files into the default folder with the following
```
$ sudo ditto VVV-Dash-Files-tmp/dashboard dashboard/
$ sudo ditto VVV-Dash-Files-tmp/dashboard-custom.php dashboard-custom.php
```
* Carefully delete the tmp folder
```
sudo rm -rf VVV-Dash-Files-tmp
```
* Go to <http://vvv.dev> to see the dashboard in use

