### Creating a New Project and a New Repo on GitHub

3. Create a new Project
4. Add a `.gitignore` from a previous project.
5. Go into your project folder on the command line
6. Run the following commands

         git init
         git branch -m master main
         git add .
         git commit -m "initial commit"

7. Create a repository on GitHub
8. Add the repository as a remote with the SSH url (it should start with git@github)

         git remote add origin git@github...
         git push origin main