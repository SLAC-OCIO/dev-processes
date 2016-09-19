Getting started with Development on SLAC Websites
===========================

## Loading Code as a Project ##
Open your preferred IDE (PHPStorm, Sublime Text or Atom)

**If using PHPStorm**, chose 'Open' once you load PHPStorm

>**Note:**
>If you're working on a SLAC site installed via this script, and you used default settings, your sites are located in `/var/sites/sitename`

- Use PHPStorm finder utility to descend directories to `/var/www/slac-features`

- Select 'Ok' This will load the project into the PHPStorm window. At this point, you're ready to start coding.

Your website should be reachable by loading a browser and entering `http://slac-features/` into the address field. Remember the trailing slash.

**If using Sublime Text** chose File > Open and browse to your directory `/var/sites/slac-features`

- Ensuring you have the directory selected, click 'Open'

- Reaching your website is the same for PHPstorm

## Adding a new site for local development ##

###Codebase###

Begin by cloning the repository that contains the repository you're working with. We'll be working with the [SLAC Features](https://github.com/SLAC-OCIO/slac-features.git) codebase

> **Note:**
>  Cloning to the `/var/sites/` directory is recommended.

I'm going to create a site named 'slac-ext' So, the command to clone slac-ext would be: 

`$ git clone https://github.com/SLAC-OCIO/slac-features.git /var/sites/slac-ext`

###Webserver Configuration###

Now we'll setup the necessary local webserver configuration.

Included in the Grail package is a script, named *virtualhost.sh* it is located in your bin directory `/Users/yourusername/bin`

Open a terminal (Command + Space, type 'terminal' hit enter)

You'll enter the path to the script and give it parameters.

For example, were I to setup my local machine to load a site called 'slac-ext', in the terminal I would enter:

`$ ~/bin/virtualhost.sh slac-ext`

You will receive output that resembles the following:

```
Enter your password to continue...
Password:
Create http://slac-ext:80/? [Y/n]: y
Creating a virtualhost for slac-ext...
+ Adding slac-ext to /etc/hosts... done
+ Looking in /var/sites for an existing document root to use...
  searching to a maximum directory depth of 2. This could take some time...
  - Use /var/sites/slac-ext as the virtualhost folder? [Y/n] /var/sites/slac-ext
  + Creating folder /var/sites/slac-ext... done
+ Creating 'index.html'... done
+ Creating virtualhost file... done
+ Flushing cache... done
+ Restarting Apache... done

http://slac-ext:80/ is set up and ready for use.
```

##Database and Site Initialization##

Thus far you have retrieved the codebase and configured the local webserver. Next,  we'll need to setup the database. 

###Local Sites Settings###

Every Drupal site needs a settings file. This file is called _settings.php_ for single websites it is located in /_sitename_/sites/default/settings.php. 

I've included a pre-configured copy for you to use, it is distributed with Grail, you can find it in:

_/usr/local/grail/roles/slac.grail-sites-build/files_

```
.../roles/slac.grail-sites-build/files]$ ☠ ls
Icon?                      slac-features.settings.php slac-gtw.settings.php      slac-www.settings.php
``` 

We'll use slac-features.settings.php. You'll copy this file to your website.

`$ cp /usr/local/grail/roles/slac.grail-slac-sites-build/files/slac-features.settings.php /var/sites/slac-ext/sites/default/settings.php`

###Site Initialization###

Slac-Features includes some PHP scripts that build slac-features profile - preparing them with default demo content and settings.  

They reside in `/var/sites/_sitename_/rebuild`

- slac_ext_org.php  | _builds/rebuilds the SLAC External Profile_ 
- slac_int_org.php  | _builds/rebuilds the SLAC Internal Profile_
- slac_misc.php     | _builds/rebuilds the SLAC Misc Profile_
- slac_people.php   | _builds/rebuilds the SLAC People Profile_
- slac_project.php  | _builds/rebuilds the SLAC Project Profile_

Invoking one of these files, in the website directory will build the database and configure the website. In that process, it disables Webauth and slac_login to enable local development.

We invoke that file by doing the following:

```
$ cd /var/sites/slac-ext/rebuild
$ /usr/local/bin/php slac_ext_org.php
```

You may see some errors concerning `Date()`, these are safe to ignore, on a local development environment.
If you encounter warnings, disregard them.
If the build fails, re-run it again.

You will know it has been successful when your browser initializes - either with a new window or new tab, and shows the current site you're building, and logs you in.

## Summary ##

This guide is by no means exhaustive. There are several places that this process can encounter errors. This document is given as a primer, and distributed with a larger package that builds a local development environment, design to get newer and less experienced Drupal Devlopers started.  If you encounter errors, please file an issue on github. 