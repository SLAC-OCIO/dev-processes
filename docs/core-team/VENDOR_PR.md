Processing a Github Pull Request
--------------------------------

> This document covers performing a pull request, this does not cover
> the code review as that is far beyond the purview of this limited
> document to cover all of the drupal framework and php. That knowledge
> is essential to understanding the steps the vendor took and the ways
> in which they altered our environment and sites. However, it may be
> necessary at times to process a pull request. Processing pull requests
> without code reviews is risky, in that we may find ourselves with
> security problems, or unable to comprehend how or what a vendor
> completed for us.
> 
> All pull requests are initiated from the github UI.

- The vendor/developer will issue a pull request.

  - The pull request will be present in github.  Github web UI is the safest place to process it, as they have automated tools that check if it can be automatically merged. If it can’t be automatically merged, refuse the pull request.
You can find notifications of pull requests either in email or the page you’re redirected to, after login to the github website.

- To merge click the button merge button.

- To decline, enter the reason for the declination and simply close the PR

- Once the merge is completed, login through the terminal to drupal-admin01.
  - Ensure you sudo as aegir. !!!!!DO NOT DO A PULL AS YOUR USER!!!!!  sudo -iu aegir
 Switch to the directory that contains the platform you’re updating with new code with.
run git status:  This will print the current branch you’re on.

  - Ensure you have sudo’d as aegir!

- `git pull origin yourbranchname`

- Switch to aegir UI (aegir.slac.stanford.edu)
  - Select the platform you’re updating and verify it.
  - Once that is successful, select the sites and verify them.

-  Once verify is complete, go back to the command line, in drupal-admin01

- In each site directory you will run the following commands utilizing the drush alias.
- ```updb -y
fra -y
fra -y
fl
cc all```
- *Preface each of those commands with ‘drush @sitealias ….`*

*When running the ‘fl’ command ensure that the state listed for each feature is empty. If it says overridden, then you must run fra (Features Revert All) until it no longer says overridden. If it keeps doing so, alert the vendor.*

- All of the code and features should be ready on the various sites.  Make sure to clear caches (drush @sitealias cc all) This effectively restarts the site.

- Test each site you have updated.
