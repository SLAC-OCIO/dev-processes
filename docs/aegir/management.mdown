Managing Aegir
==================

## AFS Folder Issues
If a site is having issues with images not appearing, the symlinks may be missing.

Our system is configured to utilize AFS as decentralized storage. Drupal sites require a ```sites/<sitename>/files``` and ```sites/<sitename>/private``` directories.
We store those directories in AFS volumes. Drupal's AFS directory is: ```/afs/slac.stanford.edu/g/web/drupal/``` The directories follow a numbered pattern, where the directory is in the form of a quartet of integers, which matches with the node id of site in the Aegir management system.

For example: Given the site ```assurance.slac.stanford.edu``` which in the aegir management system has the url of ```https://aegir.slac.stanford.edu/hosting/c/assurance.slac.stanford.edu``` and the node id of ```6567```. The AFS path will be ```/afs/slac.stanford.edu/g/web/drupal/6567```

The common directory structure for a drupal site is 

    --- siteroot
    	includes
    	logs
    	misc
    	modules
    	profiles
    	rebuild
    	scripts
    	sites
    		/<sitename>
    			/files #symlink to AFS volume
    				/tmp
    			    /images
    			    /pictures
    			    /css
    			    /js
    			    /ctools
    			    /imagecache
    			    /locations
    			    /files
    			    /temp
    			/private #symlink to AFS volume
    	themes
	

Sometimes the files or private directories are actual local file system directories and not symlinks.  This prevents files from being uploaded as well as causing login failures on the site. Many times no images will show, as the files needed are in AFS, not in the local file system.

### Overview of steps
To rectify this, the following things need to be done.

- Discern your sites - node id from the aegir interface. 
- log into drupal-admin01.slac.stanford, and both servers that house the site
- remove the local file system `files` and `private` directories
- create symlinks for `files` and `private` directories to their AFS counterparts.

If the AFS volume is empty you will need to:

- Locate the backup on `drupal-admin01.slac.stanford.edu`
- Move the backup to `/var/aegir/backup-exports
- Extract the Archive
- Copy the files directory to the proper AFS volume


#### Discern node id

- Log into Aegir
- Click on the platform
- Click on the sitename
- In the left sidebar is the AFS path which contains the node ID

#### Login to drupal-admin and each platform server

- Each platform has, at the minimum two servers. Since the `sites\<site>\files` directory is created by Aegir you must perform the symlink operations on both of them.

#### Local Filesystem Directories

- `cd /var/aegir/platforms/<platform>/sites/<site>`
- `rm -Rf files private`

#### Create the proper symlinks

- From anywhere in the filesystem: `ln -s /afs/slac.stanford.edu/g/web/drupal/<nid>/files /var/aegir/platforms/<platform>/sites/<sitename>/files`
- From anywhere in the filesystem: `ln -s /afs/slac.stanford.edu/g/web/drupal/<nid>/private /var/aegir/platforms/<platform>/sites/<sitename>/private`

#### Backup Location
- On the `drupal-admin01.slac.stanford.edu` server, in the `/var/aegir/backups` directory there will be several backups for your site. They can be located by: `ls /var/aegir/backups/ | grep '<sitename>'
	- Choose the most recent backup, copy the file name.
#### Backup copy
- For various reasons, chief among them the importance of not affecting the other backup files, you want to move the backup to `/var/aegir/backup-export` by doing: `cp /var/aegir/backups/<backup file> /var/aegir/backup-export`

#### Backup Extraction
- Change to the proper directory `cd /var/aegir/backup-exports`. 
- Decompress the archive file `tar -xvzf <archive file> ./`
#### Copy to Destination
- `cp -R /var/aegir/backup-exports/<decompressed folder>/files /afs/slac.stanford.edu/g/web/drupal/<nid>/files` Take care to leave the slashes off the end of the paths. The -R means recursively copy, respecting directory structure.
- Verify the files are in the correct location - `ls /afs/slac.stanford.edu/g/web/drupal/<nid>/files`

#### Cleanup
- Remove any archives involved in the files restoration. `rm -Rf /var/aegir/backup-export/<archive folder>`
- `rm -Rf /var/aegir/backup-export/<archive.tgz>`
- Verify the site in the Aegir interface.  This will ensure that the permissions of the files you restored are correct.