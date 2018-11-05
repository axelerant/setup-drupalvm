# DrupalVM configuration script

**IMPORTANT**: This is now *deprecated* in favour of Lando and other tools. DrupalVM is now only used along with BLT which makes this script unnecessary and not maintained.

This simple bash script lets you get started with [DrupalVM](https://www.drupalvm.com/) quickly for new projects. It downloads DrupalVM in the current directory and sets up a config.yml based on quick questions. The target is to have an opinionated way to run DrupalVM quickly and efficiently.

## Usage

Download the script to your working directory or you may place it in your bin directory to run it from anywhere.

    $ wget https://raw.githubusercontent.com/axelerant/setup-drupalvm/master/setup-drupalvm.sh
    $ chmod +x setup-drupalvm.sh

Run the script directly. You may symlink it to one of the directories in your PATH to run it from anywhere. It always works in the current directory.

**WARNING: This script immediately clears specific DrupalVM related files in your current directory WITHOUT any confirmations. It only checks for filenames like master.zip, Vagrantfile, etc... Please be careful before running the script.**

    $ ./setup-drupalvm.sh

You should see an output like this:

    Downloading DrupalVM...
    Extracting DrupalVM and preparing the directory...
    Enter the box: geerlingguy/ubuntu1604
    Enter the machine name: drupalvm
    Enter the domain name for the host: drupalvm.dev
    Enter the domain name to access the root: drupalvmroot.dev
    Enter the IP: 0.0.0.0
    Enter the relative path to the Drupal installation: drupalvm/docroot
    Enter the PHP version (5.6 or 7.0): 7.0

You may specify any valid values for the above questions. If you want to run PHP 5.6 for any reason, make sure you select `geerlingguy/ubuntu1404` for the box.

If you are using the [`vagrant-auto_network`](https://github.com/oscar-stack/vagrant-auto_network) plugin, you may use the IP `0.0.0.0` as shown above to let the plugin allocate an IP. When used along with [`vagrant-hostmanager`](https://github.com/devopsgroup-io/vagrant-hostmanager) plugin, it will add entries to your host's /etc/hosts (or equivalent) file. Another highly useful plugin is [`vagrant-cachier`](https://github.com/fgrehm/vagrant-cachier) to cache OS and composer packages across boxes.

After running the script, you may edit the `default.config.yml` or `config.yml` as you see fit to further customize DrupalVM. Refer to [DrupalVM's documentation](http://docs.drupalvm.com/en/latest/) for more details.

This script was tested with DrupalVM 4.1.0 and should work with DrupalVM 4.x.
