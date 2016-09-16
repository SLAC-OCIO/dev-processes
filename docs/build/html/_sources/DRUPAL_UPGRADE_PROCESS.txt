Setting up Local Environment
----------------------------

- Enable PHP in Apache
   `sudo vi /etc/apache2/httpd.conf -> ‘/php’ ->remove ‘#’ from in front of "LoadModule php5_module libexec/apache2/libphp5.so" `

- Restart Apache
   `sudo apachectl restart`

- Download MySQL for OS-X 64bit 10.9
http://dev.mysql.com/downloads/mysql/

- Install MySQL

- Open Preferences App and Open MySQL
click start

- Download the VirtualHost script
https://github.com/virtualhost/virtualhost.sh

- Place it in /User/yourusername/

- Make it an executable file
`chmod +x virtualhost.sh`

- Run it to create a local virtual website
`virtualhost.sh yoursitename`
Answer ‘y’ to the questions.

- Go to GitHub and copy your repo URL

- Clone that repo into your new site folder
`git clone yourrepourl.git`

- Move those cloned files innto your site root.
In the root of your local site: `mv gitreponame/* ./`
and `mv gitreponame/.* ./`

- If you don’t have it already, install Navicat:
http://navicat.com/download/navicat-for-mysql

- Create a connection
http://navicat.com/manual/online_manual/en/navicat/mac_manual/index.html
If you’ve never used MySQL on your laptop before, the root user/pass is root and a blank password.
Please change that as soon as possible.
Name the connection to your local connection ‘local'

- Create a Database:
Right click on the ‘local’ connection you created earlier.
Choose 'create database'
name your database something relevant, choose UTF8 as the default character set and UTF8_unicode_ci as the encoding

- Create a User and attach it to that database
- Double click the databasease you created in the step above.
- In the tool menu, locate the silhouette of a person.
- Click that once
- Click the ‘+’ to add a userer.
- For our local purposes, add a user that has the same name as the database you created earlier.
> host:127.0.0.1
password:abc123
- Click Save
- Click on Object Privileges
- Click on the ‘+’ to add an object
  Select the databasebase you created earlier
- in the right pane, right click and ‘grant all'
- Click ‘Ok'
- Save.
###Run the drush site install command
```drush si profilename --db-url=mysql://youruser:abc123@127.0.0.1/yourdatabase --account-name=admin --account-pass=618hWVCDmY1n3uf --account-mail=admin@example.com --site-name=yoursitename -y```
Ensure Settingthat you adjust ‘yourprofilename' ‘yoursitename', 'youruser' and ‘yourdatabase' to something relevant to the task you’re carrying out.

- Now you should be able to visit your site in a browser. Use the name you utilized with the virtualhost.sh step earlier with a trailing ‘/'

###Upgrading a Drupal Codebase
- Clone the repository you’re going to upgrade.
`git clone git@github.com:SLACNationalAcceleratorLaboratory/slac-Settingfeatures.git`

- Create a branch:
`git checkout -b ‘drupal-7-xx'`

-Setting Download the newest drupal codebase.
http://ftp.drupal.org/files/projects/drupal-7.xx.tar.gz

- Extract that archive
`tar -xvzf drupal-7.xx.tar.gz`

- Copy the updated code to your drupal codebase
`cd your/drupal/codebase/`
`cp -R your/download/folder/drupal-7.xx/* ./1`

- Run database updates
in your local siteroot: `drush updb`
*Somethings may give warnings - if the whole process does not return the words ‘Upgrade Successful’, abandon and consult with the team.*

- Test to see if anything is broken.
Open the site locally on your dev Settingmachine. Visit each path in the main menu, looking for broken things/links.

- Add the changed files:
```git add CHANGELOG.txt INSTALL.mysql.txt MAINTAINERS.txt README.txt includes misc modules profiles scripts themes COPYRIGHT.txt INSTALL.txt robots.txt update.php web.config```

- Commit your changes:
`git commit -m ‘Upgrade to Drupal 7.xx'`

- Push your branch to github:
`git push origin ‘drupal-7-xx'`

###Deploying an Upgraded Drupal Codebase

- Login to github with your credentials.

- Locate the repository you are going to deploy.
- Copy the github URL.

- Clone it locally and build it

 -Test it locally.

- If all is ok, then go back to github.
- Locate the proper repository.
 - Choose the branch you’re going to deploy
 -  click the ‘pull request’ link
 - Create a meaningful and descriptive pull request descriptiveption and title
 - Click the very large ‘Create Pull Request” button

- Authorize the Merge
Click the merge branches button

- log into drupal-admin01 and sudo as aegir
`sudo -iu aegir`

- Change to the platform you will deployy on.
`cd platforms/platformyouaredeploying`

- Pull the merged code theo this directory
`git pull origin master`
- Logout of drupal admin 01
Setting
- Log into aegir front end
- Locate the platform you just updated.
- Click Verify

- Locate any sites attached to that platform
verify all of them.

You’remove Done
**Test the sites to ensure they are functioning properly**
