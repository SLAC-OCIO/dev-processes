## Upgrading the Drupal Codebase
1. Clone the repository you’re going to upgrade. `git clone git@github.com:slac/slac-features.git`
2. Create a branch:  `git checkout -b ‘drupal-7-xx'`
3. Download the newest drupal codebase from [drupal.org](http://ftp.drupal.org/files/projects/drupal-7.xx.tar.gz)
4. Extract that archive  `tar -xvzf drupal-7.xx.tar.gz`
5. Copy the updated code to your drupal codebase
    ```
    cd your/drupal/codebase/
    cp -R your/download/folder/drupal-7.xx/* ./
    ```
6. Run database updates In your local siteroot (/var/sites/slac-www/): `drush updb`

  Some things may give warnings - if the whole process does not return the words ‘Upgrade Successful’, abandon and consult with the team.

### Test Locally.

Open the site locally on your dev machine.
  - Visit each path in the main menu looking for broken links.
  - Try uploading images.
  - Changing some path aliases
  - Attempt to modify the 'Panels in Place front page'
  - review the logs at admin/reports/dblog - if there are any glaring errors, investigate.

### Prepare to send to Github

1. Add the changed files:

    ```
    git add CHANGELOG.txt INSTALL.mysql.txt MAINTAINERS.txt README.txt includes misc modules profiles scripts themes COPYRIGHT.txt INSTALL.txt robots.txt update.php web.config
    ```

2. Commit your changes: `git commit -m ‘Upgrade to Drupal 7.xx'`

3. Push your branch to github: `git push origin ‘drupal-7-xx'`

### Deploying an Upgraded Drupal Codebase
1. Login to github with your credentials
  - Locate the repository you are going to deploy.
  - Copy the github URL.

2. Clone it locally and build it `git clone git@github.com/slac/slac-www`

3. Test it locally. If all is ok, then go back to github.

4. Locate the proper repository.
  - Choose the branch you’re going to deploy
  - click the ‘pull request’ link

5. Create a meaningful and descriptive pull request description and title "I corrected for a missing bracket and added padding to footer links"

6. Click the very large, green ‘Create Pull Request” button

5. Authorize the Merge
  - Click the merge branches button

6. log into drupal-admin01 and sudo as aegir
  - `sudo su -i aegir`

7. Change to the platform you will deploy on.
  - `cd platforms/platformyouaredeploying`
  - Pull the merged code to this directory `git pull origin master`
8. Logout of drupal admin 01 (cntrl+d)

9. Log into aegir front end
  - Locate the platform you just updated.
  - Verify
  - Locate any sites attached to that platform
  - verify all of them.
**You’re Done**

Test the sites to ensure they are functioning properly. Request the relevant clients run tests.

### Change Order
If the site you are upgrading is www6 or intranet a change order is necessary.

1. Log into Service Now and click on the 'Change' menu.
2. Click Create new
3. Enter the appropriate values in the fields
  - impact -> medium
  - Security Control Modification -> no
  - Assignment Group -> Web team
  - Stakeholder -> Communications
  - Stakeholder Approved -> Yes
  - Short Description -> A brief statement of the reason for the changes
  - Change Plan -> Routine deployment of patches and security updates to xxxx website. Git, and automated Aegir deployment.
  - Backout plan -> Using the source control github system, backing out from the majority of changes is simple and quick.
  - Click 'Request Approval'

------------------------
## Upgrading the Drupal and associated modules

1. Clone the repository you’re going to upgrade.

  `git clone git@github.com:slac/slac-features.git`
2. Create a branch:

  `git checkout -b ‘drupal-7-xx'`

3. From within a terminal session on your local development system:
  - `cd /var/sites/slac-yourplatform`
  - `drush upc`
  - Note all of the modules that have updates. Security updates are a priority. Modules that have normal updates may solve issues. However, evaluate each module according to its drupal.org/projects/modulename webpage for the changes that it makes.  Modules that have patches (siteroot/sites/all/patches/) will not be updated automatically. These will require further evaluation.

4. Run database updates

In your local siteroot (/var/sites/slac-www/): `drush updb`

Some things may give warnings - if the whole process does not return the words ‘Upgrade Successful’, abandon and consult with the
team.

### Test Locally.

Open the site locally on your dev machine.
  - Visit each path in the main menu looking for broken links.
  - Try uploading images.
  - Changing some path aliases
  - Attempt to modify the 'Panels in Place front page'
  - review the logs at admin/reports/dblog - if there are any glaring errors, investigate.

### Prepare to send to Github

1. Add the changed files:

```
git add CHANGELOG.txt INSTALL.mysql.txt MAINTAINERS.txt README.txt includes misc modules profiles scripts themes
COPYRIGHT.txt INSTALL.txt robots.txt update.php web.config
```

2. Commit your changes:
`git commit -m ‘Upgrade to Drupal 7.xx'`

3. Push your branch to github:
`git push origin ‘drupal-7-xx'`

### Deploying an Upgraded Drupal Codebase and Modules
1. Login to github with your credentials
  - Locate the repository you are going to deploy.
  - Copy the github URL.

2. Clone it locally and build it `git clone git@github.com/slac/slac-www`

3. Test it locally. If all is ok, then go back to github.

4. Locate the proper repository.
  - Choose the branch you’re going to deploy
  - click the ‘pull request’ link

5. Create a meaningful and descriptive pull request description and title "I corrected for a missing bracket and added padding to footer links"

6. Click the very large, green ‘Create Pull Request” button

5. Authorize the Merge
  - Click the merge branches button

6. log into `drupal-admin01.slac.stanford.edu` and sudo as aegir
  - `sudo su -i aegir`

7. Change to the platform you will deploy on.
  - `cd platforms/platformyouaredeploying`
  - Pull the merged code to this directory `git pull origin master`
8. Logout of drupal admin 01 (cntrl+d)

9. Log into aegir front end
  - Locate the platform you just updated.
  - Verify
  - Locate any sites attached to that platform
  - verify all of them.

**You’re Done**

Test the sites to ensure they are functioning properly. Request the relevant clients run tests.

### Change Order
If the site you are upgrading is www6 or intranet a change order is necessary.

1. Log into Service Now and click on the 'Change' menu.
2. Click Create new
3. Enter the appropriate values in the fields
  - impact -> medium
  - Security Control Modification -> no
  - Assignment Group -> Web team
  - Stakeholder -> Communications
  - Stakeholder Approved -> Yes
  - Short Description -> A brief statement of the reason for the changes
  - Change Plan -> Routine deployment of patches and security updates to xxxx website. Git, and automated Aegir deployment.
  - Backout plan -> Using the source control github system, backing out from the majority of changes is simple and quick.
  - Click 'Request Approval'


### issues

If the sites will not verify correctly then database updates will need to be ran.

1. Wait for all of sites to fail verification
2. Select all of the sites in the appropriate platform
3. Select from the select menu for multiple sites: Update database
4. Wait for each sites database update to complete
5. Re-Verify each site.  Platform re-verification is not needed
