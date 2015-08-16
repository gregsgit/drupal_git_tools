# drupal_git_tools
Tools to maintain a drupal install managed by git

Suppose this repo is checked out in ~/drupal\_git\_tools ...
Suppose top level site folder is ~/public\_html ...

## Updating core

* backup drupal database (e.g. via web using 'Backup and Migrate' module).

* mkdir ~/drupal-core-updates ; cd ~/drupal-core-updates
*   wget ... ; tar xzf *.tar.gz   -- leaves drupal-x.nn folder
* cd ~/public_html
*   git checkout -b core-updates
* cd ~/drupal\_git\_tools
*   ./update-core ~/drupal-core-updates/drupal-x.nn ~/public_html
* edit ~/public_html/sites/default, settings.php, set $update\_free\_access to TRUE.
*   visit http://website.html/update.php
* cd ~/public_html
*   git status -- sanity check
*   git commit -a -m 'updated core to x.nn'
*   git checkout master
*   git merge core-updates
*   git push
    * note that if your post-receive hook does a checkout, that may mess up
	  your permissions.
* chmod -R 755 ~/public_html

## Updating a module

* backup drupal database (e.g. via web using 'Backup and Migrate' module).

* mkdir ~/drupal-module-updates ; cd ~/drupal-module-updates
*   wget ... ; tar xzf *.tar.gz 
* cd ~/public_html
*   git checkout -b module-updates
* cd ~/drupal\_git\_tools
*   ./update-module ~/drupal-module-updates/*module-name* ~/public_html
* edit ~/public_html/sites/default, settings.php, set $update\_free\_access to TRUE.
*   visit http://website.html/update.php
* cd ~/public_html
*   git status -- sanity check
*   git commit -a -m 'updated <module name> module'
*   git checkout master
*   git merge module-updates
*   git push
    * note that if your post-receive hook does a checkout, that may mess up
	  your permissions.
* chmod -R 755 ~/public_html

## Adding untracked files

For a drupal site, it might be that files are uploaded via the drupal
file manager. Sometimes you want to collect all the untracked files
and add/stage them.

* cd ~/public_html
* ~/drupal\_git\_tools/gen-adds > ../adds.out
* *remove lines from adds.out for files you do not want to add*
* . ../adds.out
* git commit -m 'added new files'
* git pull ; git push ; etc.

