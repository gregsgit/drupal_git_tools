# drupal_git_tools
Tools to maintain a drupal install managed by git

# Updating core

* backup database (e.g. using 'Backup and Migrate' module).
* git checkout -b core-update
* mkdir ~/drupal-core-updates
* wget ... ; tar xzf *.tar.gz - leaves druplal.x.nn
* cd drupal\_git\_tools
* ./update-core ~/drupal-core-updates/x.nn ~/public_html
* git status
* git commit -a -m 'updated core to x.nn'


