# Uploading to Github

Once we have a repo locally on our machine we should hook it up with a repo on the Github website. 

First, if you haven't already create a Github account.

Next, create a repo with the green "+ New Repository" button. The repository name should be the name of the application you are writing or the name of the class you are taking. 

**DO NOT CLICK THE CHECKBOX TO CREATE A README AND DON'T SELECT A GITIGNORE OR LICENSE.** If you do it will make things more difficult later on.

Once the repository is created you will see a https URL on the right side. Copy this URL.

To hook up our local repository to the Github repository type 

> git remote add origin [URL]

To upload your code to Github type

> git push origin master

If you refresh the page on Github you should now see all your code.


The [source code](https://github.com/andrewoid/evolution-java) for this book is also on Github.