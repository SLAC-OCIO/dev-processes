Meta Documentation 
===================

Documentation about the Documentation
-------------------------------------

:laughing:  



This set of documentation exists to promote a transparent and always available set of guides for developing, editing and improving the development of software in OCIO. This documentations' source code is available at
https://github.com/SLAC-OCIO/dev-processes

If you're a member of the SLAC-OCIO Github organization, you can access and edit this documentation. We welcome all pull requests, subject to review.  

----------


Organization
-------------

The documentation set (dset) is organized according to subject. The syntax of the documentation is Markdown, particularly [Github Markdown](https://guides.github.com/features/mastering-markdown/).

> **Note:**

> - Location of the code repository: [SLAC OCIO Github](https://github.com/SLAC-OCIO) 
> - Request Access: [Service Now](https://slacprod.service-now.com/navpage.do)

#### <i class="icon-folder-open"></i> Repository Structure
In the [documentation repository](https://github.com/SLAC-OCIO/dev-processes) there is a folder labeled 'Docs'
This is the primary folder for storing documentation files. In that folder are several others.  Each folder refers to a high-level topic or team.

> <i class="icon-folder-open"></i> - docs
> ><i class="icon-folder-open"></i> core-team
	>>> <i class="icon-file"></i> - DRUPAL_UPGRADE_PROCESS.md
	>>> <i class="icon-file"></i> - VENDOR_DEPLOY.md
	>>> <i class="icon-file"></i> - VENDOR_PR.md
	>>> <i class="icon-file"></i> - overview.md
	
> > <i class="icon-folder-open"></i> drupal

>>> <i class="icon-file"></i> - COMS_GIT.md
>>> <i class="icon-file"></i> - drupal-overview.md
>>> <i class="icon-file"></i> - grail.md
>>> <i class="icon-file"></i> - mamp-linux.md
>>> <i class="icon-file"></i> - slac_sites.md

Documentation Creation and Editing Process
--------------------

#### <i class="icon-file"></i> Create a document

 1. Clone the repository, locally.
 2. Create a new branch with the appropriate branch name. and switch to it.
 3. If you are adding a new subject, or team, create a new directory in the `docs` folder
 5. If you are adding a new page to the current dset, be sure to create the page in the appropriate folder, and that the file suffix is `.md` and the file is written with proper Markdown syntax.

Once you have finished editing, create a commit message with a summary of your changes and push your changes remotely.


#### <i class="icon-pencil"></i> Edit  existing document

If you find mistakes, errors or something missing, you can edit any document in the repository.

 1. Clone the repository, locally.
 2. Create a new branch with the appropriate branch name. and switch to it.
 3. Open the document in your preferred editor.
 4. Make appropriate edits using Markdown syntax.
 5. Save your document
 6. Stage your changes
 7. Commit your changes, with a summary of the changes you made, or the subject you edited.
 8. Push your branch to GitHub
 9. Login to Github, and issue a pull request.

#### <i class="icon-pencil"></i> Rename a document

Generally, the name doesn't matter - since we're using readthedocs.io, the structure is maintained via the yaml file in the root directory of the repository. If you do rename follow the steps in Edit existing document.

#### <i class="icon-trash"></i> Delete a document

You can delete documents but it is generally advised to restructure or edit them instead. If documents are deleted that should be there, OCIO-Leads will restore it.



----------


Tools
-------------------

At the very least the following tools are needed:

 - [git](https://git-scm.com/) installed locally 
 - A text editor, in ascii mode. 
 - A modern web browser

> **Note:**

> - A great Git UI application called [GitKraken](https://www.gitkraken.com/) is available.  It has a pleasant and intuitive UI, simplifies most operations and can perform pull request through Github. There is a no-cost version and a pro version.
> - For assistance with Git installation please see [Githubs Article on Git installation](https://help.github.com/articles/set-up-git/)
> - Most code editors can edit markdown. Popular text editors include [Atom](https://atom.io/), [Sublime Text](https://www.sublimetext.com/), [Notepad++](https://notepad-plus-plus.org/)
> Through implication - that you're reading this document - denotes you have a web browser.



Publication
-------------

Once you are happy with your document, and have saved it - you will need to insert it in the navigation tree of the [ReadTheDocs.io](http://slac-ocio-dev-processes.readthedocs.io/) site.

#### <i class="icon-upload"></i> Editing mkdocs.yml

Open the `mkdocs.yml` file in the root directory of the repository you cloned.

Ignore (don't change) anything above the following:
```
pages:
  - Home: index.md
  - Drupal: 
    - 'Overview of Drupal at SLAC': 'drupal/drupal-overview.md'
    - 'Local Development of Drupal': 'drupal/mamp-linux.md'
    - 'OS-X Development Machine Configuration': 'drupal/grail.md'
    - 'Communications <---> Dev Processes': 'drupal/COMS_GIT.md'
    - 'Up and Running with SLAC Sites': 'drupal/slac_sites.md'
  - Core Team:
    - 'Overview of Drupal for DevOps Team':  'core-team/overview.md'
    - 'Deployment of Vendor Pull Request': 'core-team/VENDOR_PR.md'
    - 'Deployment of Production from Vendor': 'core-team/VENDOR_DEPLOY.md'
```
----------

###New Team/Project
Assuming you created a new folder (you should have) in the `docs` directory, create a new second level list item:

```
- Core Team:
    - 'Overview of Drupal for DevOps Team':  'core-team/overview.md'
    - 'Deployment of Vendor Pull Request': 'core-team/VENDOR_PR.md'
    - 'Deployment of Production from Vendor': 'core-team/VENDOR_DEPLOY.md'
- My New Project:
	- 'Overview of My New Project': 'new-project/overview.md'
	- 'Other interesting stuff': 'new-project/other.md'
```
You will see that I added ```- My New Project:``` as well as two 'pages' below the second level list item, and indented fours spaces, adding a `-`.
> ####Note:
> - There is never any reason for creating a top level list item. Please retain the structure already created
> - The syntax used in the yml or Yaml file can be further understood in [this article](http://docs.ansible.com/ansible/YAMLSyntax.html#yaml-basics)
> - This file is very syntax sensitive, so please follow the examples, we suggest cutting and pasting - then editing to suit your update.

The structure of the navigation is very simple, yet elegant. The top level list item: `pages` creates a list object for parsing. Second level items (home, drupal, core-team) are akin to main navigation items - these are subject to re-organization as time progresses and more projects are ported here. 

The secondary level items should follow this convention: `- Section Name : `
Tertiary level items should follow this convention: ```- 'Subject of SubSection': 'second-level-label/file-name.md'```

That's it - the yml file looks intimidating to a non-developer/non-coder, but is very simple and elegant.


[TOC]


