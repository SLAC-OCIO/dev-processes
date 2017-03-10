# Miscelleneous Drupal Fixes

  ## Current issues

  ### Missing Module blues

You may find that a site will show the error:

```
User warning: The following module is missing from the file system: MODULE NAME. In order to fix this, put the module back in its original location. For more information, see the the documentation page. in _drupal_trigger_error_with_delayed_logging()
```
I've attempted to use a module to fix this, but it does not work on every site we have

You can use a mysql query to solve this issue.

`drush sql-query "DELETE from system where name = 'modulename' AND type = 'module';"`

Invoking this is fairly easy:

1. Open a terminal. Login to `drupal-admin01.slac.stanford.edu`

2. Become the aegir user: `sudo su -i aegir`

3. Change to the platform of the site you're working on: `cd platforms/platforname`

4. Change to the site folder of the site you're fixing: `cd sites/www.sitename.com`

5. Run the sql-query command using drush, replacing moduelname with the module string in the error:  `drush sql-query "DELETE from system where name = 'modulename' AND type = 'module';"`

6. Flush all caches: `drush cc all`

7. Log out: [cntrl]+d


## Missing administration menu

If you discover the problem of a missing administration menu, the solution is to add the following line at the bottom of the settings.php file.

`$conf['admin_menu_cache_client'] = FALSE;`

1. Use your authorized SLAC Unix account and log into aegir.slac.stanford.edu via SSH  `ssh xalg@aegir.slac.stanford.edu`

2. Change user to aegir: `sudo su - aegir`

3. Change to the location of the platform->site that needs the fix applied: `cd /var/aegir/platforms/cm-prod-2/sites/yoursitename`

4. Invoke your command line editing utility and add the line above:
  - `vi settings.php`
  - Move to the bottom of the file: `G$`
  - paste the following: `$conf['admin_menu_cache_client'] = FALSE;`
  - Write and quit: `:wq`
