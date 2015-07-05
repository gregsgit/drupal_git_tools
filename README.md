# drupal_git_tools
Tools to maintain a drupal install managed by git

Suppose this repo is checked out in ~/drupal\_git\_tools ...
Suppose top level site folder is ~/public\_html ...

# Updating core

* backup drupal database (e.g. via web using 'Backup and Migrate' module).

* mkdir ~/drupal-core-updates ; cd ~/drupal-core-updates
* wget ... ; tar xzf *.tar.gz   -- leaves drupal-x.nn folder
* cd ~/drupal\_git\_tools
* ./update-core ~/drupal-core-updates/drupal-x.nn ~/public_html
* git status -- sanity check
* git commit -a -m 'updated core to x.nn'
* git merge
* cd ~/public_html
*   chmod -R 755 .


# Updating modules

