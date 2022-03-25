### Creating a new project and a new repo on GitHub

3. Create your project in IntelliJ
4. Add a .gitignore
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