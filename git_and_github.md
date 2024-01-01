### Working on a new feature

``` shell
    # Switch to the main branch
    git checkout main
    
    # Make sure you have all the current changes
    git pull origin main
    
    # Create a new branch
    git checkout -b branchName
    
    # Do some work
    
    # look over the changes you made
    git status
    
    # Add *all* your changes to git
    # or add each file manually
    git add .
    
    # Save all the changes you added locally
    git commit -m "commit message that describes changes"
    
    # Save all your commits to GitHub
    git push origin branchName
```
