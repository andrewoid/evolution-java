# Git commands

Before reading this you should complete the interactive walkthrough [here](https://try.github.io/levels/1/challenges/1).

A good explination of git commands can be found [here](http://gitref.org/)

A quick reference PDF for github can be found [here](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)

## How to push our code to github

1. Open up a Command Prompt (or Terminal on Mac) 

2. "cd" into the directory that our code is in. If your code is located on a flash drive you may need to change to a different drive.

3. Initialize the directory as a git repo. To do this type 

> git init

4. See a list of files in the current directory (and sub directories) that can be added to git.

> git status

5. By default, git will allow you to add all files


> git add

> git commit

> git commit -m "commit message goes here"

> git reset

> git reset --HARD

> git remote add origin GITHUB_REPO_URL

> git push -u origin master