Drupal Production Process
====================

##Preparation

**Requirements**

- Notification from site owner that their site is ready for production
- Approved production URL
- pre-prod URL

**Test**
Go through the production site, generally looking for problems and errors.
An exhaustive test is not needed, but a quick sanity test is due diligence.

##Process

###Domain and URL
1. Open a browser to https://netdb.slac.stanford.edu
2. Log in.
3. In the search field, type `*drupal*` then enter.
4. Choose **drupal-prod** not drupal-prod1 - 4, you want the aliases for the load balancer.
5. Select the **add new** option
6. Fill in the subdomain only, omitting `slac.stanford.edu`  If your subdomain is `make-things.slac.stanford.edu` you would only enter `make-things`
7. Click **save** located near the bottom of the page.
It will generally take between 30 minutes up to 6 hours to propagate internally. It may take up to 24 hours for a URL that was previously in use to change world-wide.

###Aegir
Log into https://aegir.slac.stanford.edu with your **-a** account. An elevated set of privileges is needed to access the Aegir platform.  

####Outline
> - Create production site
> - Verify production site
> - Test for issues
> - Sync database from Pre-Prod
> - Sync Files and Active Directory from Pre-Prod site
> - Verify production site

####Steps

1. Select the platform that houses the site you are porting to production.  Usually, it is in the pre-prod-2 platform.
2. Select verify, read the verify logs to be sure everything is normal. Yellow warnings are normal, whereas red errors will need examined in depth.
3. Select the **cm-prod-2** platform, click **add site**
4. Enter the full domain name in the URL field. This includes `slac.stanford.edu` . If your subdomain is `make-things` the string you enter into the url field, in the site creation view would be `make-things.slac.stanford.edu`
5. Match the new site options with the pre-production options, ensuring that you're enabling backups, and the database resides on the production database server, rather than the development database server.
	6. Important fields are: Domain Name, Site Owner, Install Profile, Database Server.
6. Click **save** and occasionally keep an eye on the process checking for issues.
7. When installation is complete, choose the site in Aegir, and run the **verify** command.
8. If verification is successful, run the **Sync** command. Ensure you only sync the Database initially, files and Active Directory are synced separately.
9. If the database sync is successful, run the **Sync** command again, choosing to only sync **files** and **active directory**
10 If the files and AD sync is successful, run the **verify ** command.

###Production Site

####Outline
- Disable Errors
- Enable Caching
- Sanity Test

####Steps
1. Login to the new production site with your superuser credentials, typically **-a** account.
2. Select configuration from the administrator menu, then select **Logging and Errors**, in the **Development** group, then change the error display to **None**. 
3. Click Submit
4. Select **Performance** in the **Development** group. Select **Cache pages for anonymous users**
5. Use the select list labeled **Minimum cache lifetime** and set to 1 hour
6. Use the select list labeled **Maximum cache lifetime** and set to 3 hours
7. Under the **Bandwidth Optimization** group, select and enable:
	8. Compress cached pages.
	9. Aggregate and compress CSS files.
	10. Aggregate JavaScript files.
8. Click **Save Configuration**
9. Hover over the **Drupal Icon** in the top left of the administration menu, and select **Flush All Caches**
10. Open a different browser, without having a slac.stanford.edu session, go to the new production site and click around, ensuring everything loads correctly.

###Search and Indexing
The new site should be updated in IDOL. 

###Cleanup and Notification

Depending on the circumstances and group preferences you may archive the old site, delete the pre-prod site.
Update the requesting group, through Service Now that the process is complete.