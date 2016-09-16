Process:
--------

  **requirements**
     - ssh-keys
     - Github account
     - Mac or Linux computer
     - sudo or 'administrator' privileges
     - 20 GB of free Hard Disk space


  **General Steps**

-      Setup your local machine to develop in the MAMP 'stack' - Mac Apache MySQL PHP (One time process) Document forthcoming, or use Grail if OS-X
-      Get code location - Github Repository URL
-      Pull code to your machine - Git Pull
-      Create 'sandbox' - Git branch
-      Modify your code
-      Stage your code - Git add
-      Push your code to Github - Git push
-      Request Deployment - Service Now
-      Test
-      Request Merge via Pull Request - Github Interface
-      Fetch all Changes, Switch branch back to master - Git fetch

**ssh keys**

- Generate your Key: https://help.github.com/articles/generating-an-ssh-key/
- Install your Pub Key in github:https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/

**Github Account**

- Obtain a github account by signing up, it is free.
- Via Service Now - request having your user added to SLAC-OCIO Github
- Ensure that your ssh public key is configured in Github

**Obtain the repository url eg: (git@github.com/SLAC-OCIO/slac-features.git)**

- Log into Github.
- Open the SLAC-OCIO organization from the Org Dropdown. Located in the upper left of the webpage, under the picture of the "Octokitty"
- Browse through the available repositories until you find the one you want.  You can use the Search Bar, located above the Organization dropdown and next to the "Octokitty"
- Click on the title of the Github repository you wish to work on.
- Click the green "Clone or Download" button in the upper right area of the webpage.
- Select "SSH" by clicking on the word
- Copy the URL to your clipboard

**Pull code to your machine**

- Open the terminal application (command+space, type terminal, enter)
	On OS X, the Terminal application can be found in /Applications/Utilities. Open a Finder window and go to Applications, then Utilities. Then double click on Terminal. (Or, click the spotlight icon in the upper right hand corner of your screen and type Terminal – you should see Terminal under Applications.)
- Change directories to your sandbox website [cd ~/sites/]
- Clone your repository: `git clone git@github.com:SLAC-OCIO/slac-features.git`

- Change directory to your new codebase: cd  ~/sites/slac-features

**Create your Sandbox**

- Create a branch of the main tree to change code in: ```git checkout -b yourbranchname```
- Ensure you're on the correct branch ```git status```

**Modify your code**
Code, Create!, Be happy, Don't forget the semi-colon!

**Stage your code**

- Open the terminal application (command+space, type terminal, or type iTerm, hit enter)
- Change directories to your sandbox website [cd ~/sites/slac-features]
- Look at the needed changes: `git status`  Likely, you'll see a listing of files, some will be added, some deleted, some modified. Some will be in the "Untracked Files" section, we do not want to add these.
- Add everything in the list above untracked files.  You may add an entire folder, like:
    - `git add sites/all/themes/slac/_sass/`
- Once your files are staged for upload, you'll create a commit message
    - `git commit -m "I added padding to the new news block"`

** Push your code to Github **

- Open the terminal application (command+space, type terminal, enter)
- Change directories to your sandbox website [cd ~/sites/slac-features]
- Ensure you're on the correct branch: `git status -v -a`
- Push your code to the central repository in the cloud: `git push origin yourbranchname`
- Ensure you have the latest changes in your local filesystem: `git fetch` then `git pull master`

***Request Deployment to Staging***

- Open Service now, select Service Catalog
- Select Other Request, in the title, preface with [github staging]
- Submit

***Request merge via pull request***

- Log into Github.
- Open the SLAC-OCIO organization from the Org select list. Located in the upper left of the webpage, under the picture of the "Octokitty"
- Browse through the available repositories until you find the one you want.  You can use the Search Bar, located above the Organization dropdown and next to the "Octokitty"
- Click on the title of the Github repository you wish to work on.
- Click the "Branch" select menu
- Chose the branch you're working with, click it.
- In the branch commit status bar (blue background) select 'Pull request"
- In the comment field, write short synopsis of the changes you have made to the code
- Click on 'Create Pull Request' button, when finished with your synopsis

***Fetch all changes to your local filesystem***

- Open the terminal application (command+space, type terminal, or type iTerm, hit enter)
	On OS X, the Terminal application can be found in /Applications/Utilities. Open a Finder window and go to Applications, then Utilities. Then double click on Terminal. (Or, click the spotlight icon in the upper right hand corner of your screen and type Terminal – you should see Terminal under Applications.)
- Change directories to your sandbox website [cd ~/sites/slac-features]
- Fetch the changes: ```git fetch```
