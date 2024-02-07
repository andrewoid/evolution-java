# Git commands

Before reading this you should complete the interactive walkthrough [here](https://try.github.io/levels/1/challenges/1).

A good explanation of git commands can be found [here](http://gitref.org/)

A quick reference PDF for github can be
found [here](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)

## How to push our code to github

1. Open up a Command Prompt (or Terminal on Mac)

2. "cd" into the directory that our code is in. If your code is located on a flash drive you may need to change to a
   different drive.

3. Initialize the directory as a git repo. To do this type

   > git init

4. See a list of files in the current directory (and sub directories) that can be added to git.

   > git status

5. By default, git will allow you to add all files. However there are certain files that we don't want added to git. In
   order to tell git not to add these files we need to create a ".gitignore" file. A ".gitignore" file is just a text
   file with a list of file types to ignore. Create a text file called ".gitignore" (the . in the beginning is
   important) and inside put the following line.

   *.class

6. If you run "git status" again you should see less files. All java .class files will no longer appear on the list. The
   reason we ignore .class files is because they are automatically generated from source code so there isn't a reason to
   add them to git.

7. Now we want to add some files to git. We can add them one by one or we add multiples at a time.

   > git add src

   Add the source folder to git

   > git add .

   Add all files in the current directory to git

8. After adding files to git we should check "git status" to make sure we've added all the files. When we are finished
   adding files to git we need to commit those files. Committing files is when we tell git that we are finished with all
   the files we've added.

   > git commit -m "commit message goes here"

   The commit message should be something short that describes the work that had been done. If we do more work and run "
   git status" we would see a list of new files and a list of modified files. When we are finished, all the files should
   be added to git and another commit should be made.