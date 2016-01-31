# Note To Self - Web Development Cheatsheet

### GIT STEPS & COMMANDS
***

```
git init
```

```
git status
```
```
git add
```
```
git commit . -m “Message goes here”
```

To see which remote servers you have configured, you can run the

```
git remote -v
```

command. It lists the shortnames of each remote handle you’ve specified. If you’ve cloned your repository, you should at least see origin – that is the default name Git gives to the server you cloned from:

**Create a new repo on github.com and do the following:**

    git remote add origin https://github.com/timurcatakli/lucky_numbers.git

    git push -u origin master

    Delete an origin

    git remote rm origin


**Removing or disabling GIT**
All the data git uses info is stored in .git/ , so removing it should work just fine. Of course, make sure that your working copy is in the exact state that you want it, because everything else will be lost. From there, you can run git init to create a fresh repository. 

    rm -rf .git 
should suffice

### MY GIT WORKFLOW
***

CLONE THE REPO TO LOCAL HARDDRIVE

    git clone …github.repo.url

MASTER is already created - create a new branch called “dev” and switch into it

    git checkout -b “dev”

CONTINUE WORKING ON “DEV”, ONCE YOU MAKE A PROGRESS ADD-COMMIT

    git add .
    git commit . -m “A nice explanatory msg goes here”

switch to master and merge “dev” with “master

    git checkout master
    git merge dev

switch back to “dev” and continue working - this way you always have a working copy on master and if you make a mistake you may revert back - once you are done,  **push to origin** and **delete the branch 'dev'**
