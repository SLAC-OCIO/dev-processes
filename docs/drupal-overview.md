#Drupal at SLAC
[SLAC](https://slac.stanford.edu) employs [Drupal](https://drupal.org) as the informational website content management system
Obtaining Drupal Websites is simple, log in to [Service Now](https://slacprod.service-now.com/navpage.do) and create a ticket from the catalog.

This documentation system provides several groups within SLAC information about Drupal
###SLAC's Drupal Stack

 - Drupal 7.xx
 - PHP 5.4
 - Apache 2.4
 - Redhat EL 6.5

####Drupal Customizations

 - Custom modules written for SLAC are prefixed with `slac_`
 - SLAC's Themes:
	 - www6 - slac-www
	 - intranet - slac-igp
	 - group sites - slac
		 - Subthemes
			 - ext-org
			 - int-org
			 - projects
			 - people

		 - Front End markup
		- Sass
		- Compass
		- susyone


####Development Tools
 
 OS-X
 
 - SLAC-OCIO has created a tool that enables a user to rapidly build the
   necessary infrastructure to develop Drupal locally, that tool is
   called [Grail](https://github.com/SLAC-OCIO/grail) 
 - Acquia also has a   tool to manage Drupal sites on OS-X, it is called [Acquia Dev Desktop](https://www.acquia.com/products-services/dev-desktop)
 - The MAMP stack can be manually configured on OS-X.  Configuration is
   dependent largely on your operating system version. The Help Desk won't have the depth of knowledge to assist with custom MAMP stack configurations.
	 - OS-X 10.9
	 [Guide:](https://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-9-mavericks/) Get Apache, MySQL, PHP and phpMyAdmin working on OSX 10.9 Mavericks
	 - OS-X 10.10
	 [Guide:](Get%20Apache,%20MySQL,%20PHP%20and%20phpMyAdmin%20working%20on%20OSX%2010.10%20Yosemite) Get Apache, MySQL, PHP and phpMyAdmin working on OSX 10.10 Yosemite
	 - OS-X 10.11
	 [Guide:](https://coolestguidesontheplanet.com/get-apache-mysql-php-and-phpmyadmin-working-on-osx-10-11-el-capitan/) Get Apache, MySQL, PHP and phpMyAdmin working on OSX 10.11 El Capitan

	   

	*MAMP stack: Mac, Apache web server, MySQL database server, PHP text interpreter*
	
Linux 
	- See Mamp Linux

 Windows
 
	 Generally, it is possible to configure windows to develop an *AMP CMS.  However, it is beyond the scope to reliably re-produce the steps necessary. 