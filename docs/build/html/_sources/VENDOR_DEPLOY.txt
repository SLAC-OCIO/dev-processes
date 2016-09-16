Vendor delivered Pull request and deployment
============================================

> When working with an external vendor, the following process has been tested and found to be very effective and eliminate many issues in the deployment pipeline.  With SLAC's Aegir deployment mechanism, the process is very simple, just follow the steps below.

- Vendor initiates a pull request.
- Login to github, review pull request.
- This entails looking over the code, to ensure there is nothing that violates our security standards, or will have a negative impact on our platforms.

- Merge pull request by logging into drupal-admin01, changing directories to the appropriate platform/site directory. git pull origin branchname.

- Switch to Aegir UI, verify the platfrom.
 - Verify each site in the platform.
 - Run database updates for each site.
 - Run features updates for each site.
 - Run cache clear for each site.​

- Import prod database.
 - `drush sql-cli < ~/path/to/filename.sql`
-  Review pull request in github.
- If there are conflicts in the pull request, do not proceed to step 2.Vendor Alert the developer.
- Process the pull request and merge with the codedebase in the proper branch
- SSH into drupal admin01 and change directory to the proper platform folder
- kinit on login `/usr/local/bin/kinit`
- Change user to Aegir and kinit again
- `sudo su - aegir`
- `/usr/local/bin/kinit yourusername`
- Discover and verify your branch
  - git status'  -tells you the correct branch (precaution
- Retrieve the newest code 
    - `git pull origin branchname`
- Log into aegir UI - click on the platform you are updating.
  - verify platform
  - verify sites
- Obtain the AFS directory numbers from each sites detail page in Aegir
- Back to the command line - 
     - Copy the files from the old drupal 6 site
     ` rsync -rave “ssh” youruser@drupal02.slac.stanford.edu:/u1/www/html/sites/default/files/ /afs/slac.stanford.edu/g/web/drupal/xxxx/files/`
- Change the file permissions to the correct schema 
- changingmod o+w *
- Update Database
- drush updb -y
- Revert Features
- drush fra -y
- drush fra -y
- drush cc all
- drush fl
- Report back to verifyndor that the steps necessary have been performed on SLAC’s side

