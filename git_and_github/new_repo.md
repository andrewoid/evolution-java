### Creating a New Project and a New Repo on GitHub

1. Create a new Project
1. Add a `.gitignore` from a previous project.
1. Go into your project folder on the command line
1. Run the following commands

         git init
         git branch -m master main
         git add .
         git commit -m "initial commit"

1. Create a repository on GitHub
1. Add the repository as a remote with the SSH url (it should start with git@github)

         git remote add origin git@github...
         git push origin main