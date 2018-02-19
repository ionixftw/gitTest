# Git
>"Git is one of the most beautiful command line tools that I have ever used!"

## Config
### user.name
```sh
git config --global user.name "name goes here"
```
### user.email
```sh
git config --global user.email "email goes here"
```
## Initialization
```sh
git init
```
## Status to check current condition of the working directory
```sh 
git status
```
## Add a specific file for staging
```sh
git add fileName.fileextension
```
## Add all files for staging
```sh
 git add .
```
## Commit staged files
```sh
 git commit -m "Commit message goes here"
```

* Commit message must be short but descriptive
* Always use present tense for commit messages
* Ex: "Fix: some bug in someFile" , "Add missing } in file.js", "Change user authentication to use Blowfish"

## Add and commit modified files with a single command

* Note: Does not work well with new or removed files

```sh
git commit -am "Commit message goes here"
```

## View commit log
```sh
git log
```
## View specified number of commit logs
```sh
git log -n 3
```
## View commit log since,until,author,grep
```sh
git log --since=2018-02-09
git log --until=2018-02-11
git log --author="Author name goes here"
git log --grep="Commit message goes here"
```
## Git has three-tree-architecture
1. repository
2. staging index
3. working directory

#### Tips

* git add command moves files from working directory to staging index
* git commit command moves files from staging index to repository
* But we do not do things the other way!
* Usually we pull files directly from repository to working directory skipping staging index
* Git generates a checksum for each change set
* Checksums(40 character hexadecimal string) are calculated based on data
* Changing data would change checksum
* Git uses checksums to track commits

## Git HEAD pointer

* Points to the last commit of the current branch in repository
* Points to the latest commit if git checkout command is used to switch branches
* Git stores HEAD value in .git/HEAD file

## Viewing changes with diff

* Modified but not staged files are different than the ones in the repository.
* To see the modifications use the git diff

```sh
git diff <file>
```
* To see modifications made to several files use git diff without specifying the file

```sh
git diff
```
* Note: git diff command compares changed files between working directory and repository
* To see difference between staged files and repository use the git diff --staged
 
```sh
git diff --staged
git diff --cached
```
## Deleting files
* To delete files use the git rm 
* git rm command removes the file and puts it in the staging index

```sh
git rm <file>
```
## Renaming files

* To rename files use git mv
* Renames and adds files to staging index
```sh
git mv <file> <renamedFile>
```
## Unstaging files

* git reset HEAD  unstages staged files
* It works by resetting HEAD pointer to the last commit

```sh
git reset HEAD <file>
```
## Editing latest commit

* We can edit the most recent commit with the --amend flag
* To retain data integrity previous commits can not be amended

```sh
git commit --amend -m "Commit message goes here"
```
## Undoing changes

* git checkout command is used for switching branches and undoing changes
* So in order to only undo changes and not switch branches '--' flag is needed

```sh
git checkout -- <file>
```
## Retrieving old versions of a file

* To retrieve the old version of a file use git checkout with the commits sha-1 value
* It also puts the retrieved file in the staging index

```sh
git checkout <commit> -- <file>
```
## Reverting a whole commit

* Reverting a commit undos the changes made in that specific commit 
* To revert a commit use

```sh
git revert <commit>
```
* It also commits changes simultaneously

## Resetting multiple commits

#### Tip: Before using git reset, it is always a good idea to copy commit history from git log in a new text file
* git reset
    * --soft
        * resets the HEAD pointer to the specified commit
        * stages the modified files that were modified in the later commits

    * --mixed(default)
        * resets the HEAD pointer to the specified commit
        * matches the staging index with repository(Empty staging index)
        * does not stage modified files that were modified in the later commits and leaves them in working directory
    * --hard
        * resets the HEAD pointer to the specified commit
        * resets everything to match that commit repository

```sh
git reset --soft <commit>
git reset --mixed <commit>
git reset --hard <commit>
```
## Cleaning git repository

* If there are untracked files present in the repository to clean them use the git clean command
    * -n flag shows which files would be cleaned
    * -f flag cleans those files shown by -n flag

```sh
git clean -n
git clean -f
```
## Using .gitignore to untrack files

* Git uses .gitignore file to learn about files that should not be tracked
* Create a .gitignore file in the root of the working directory
* Wildcard symbol '*' represents all characters
* But negations symbol '!' negates the ignoring and tells git to track those files
* Ex: *.html ignores all files ending with .html extension. But !index.html tracks index.html
* Directory names with a trailing backslash ignores all files in that directory
* Ex: builds/ ignores all files in builds directory
* Comments start with a '#' symbol
* Gitignore repo: [Gitignore](https://github.com/github/gitignore)

## Ignoring tracked files

```sh
git rm --cached <file>
```

## Listing trees

```sh
git ls-tree <commit>
```

## More with git log

* One line log with partial SHA-1

```sh
git log --oneline
```
* One line log with fill SHA-1

```sh
git log --format=oneline
```
* Graph view of commits

```sh
git log --graph
```
* A useful collection of flags for git log

```sh
git log --oneline --graph --all --decorate
```
* Log of a branch

```sh
git log <branch> --oneline -3
```

* Limit the number of previous commits to output

```sh
git log --oneline -4
```
* To check every commits additions or deletions use the -p flag

``sh
git log -p
```
* View one commits full summary

```sh
git show <commit>
```

* Limit the range 

```sh
git log <commit>..<commit> --oneline
```

* To check a certain file's history add the filename after the range
* Leaving the second commit blank means all the way to the latest commit 

```sh
git log -p <commit>.. <file>
```
* Statistics and summary view

```sh
git log --stat --summary
```
## More with git diff

* To see changes between the working directory and a previous commit use git diff command

```sh
git diff <commit>
```
* To see changes between two or more commits pass the commit range
* To see changes made to a single file pass the file after commit range
* The -b flag removes space changes
* The -w flag removes all space changes
```sh
git diff <commit>..<commit>
git diff -w <commit>..<commit> <file>
```
## Branches

* The HEAD pointer always points to the last commit of the checked out branch
* To see all branches use git branch

```sh
git branch
```
* To create a new branch pass the name with git branch

```sh
git branch <branchName>
```
* Git stores branches in .git/refs/heads folder
* Git stores HEAD pointer value in .git/HEAD
* To switch branches use the git checkout command

```sh
git checkout <branchName>
```
* New branches does not contain any commits
* So the HEAD pointer does not move until new commits are added to that branch

* Creating and switching a branch at the same time

```sh
git checkout -b <branchName>
```
* Git won't checkout other branches if there are modified files (tracked) present in the working directory. So you have to commit those changes or discard those changes first.
* However if there are untracked files git will checkout other braches with no problem.

* Comparing branches

```sh
git diff <branchName>..<branchName>
```
* To see which branch contains all the commits

```sh
git branch --merged
```
* Renaming branches with -m (short for --move)

```sh
git branch -m <oldBranchName> <newBranchName>
```
* Deleting branches
* To delete a branch first checkout another branch
* Then delete the branch using -d (short for --delete)

```sh 
git branch -d <branchName>
```
## Merging

* At first make sure the working directory is clean in both the receiving branch and the sending branch
* Then checkout the receiving branch
* Use the git merge command

```sh
git merge <branchToMergeWith>
```
* Fast forward merges happen when there are no commits on the receiving branch
* Recursive merge happens when there are no conflicts between the branches
* If there are conflicts git does not automatically merge rather it asks you to solve them
* Git marks the conflicts usually by the following pattern in the respective files

```sh
<<<<< <branch>
some conflicts
=====
```
* When solving merge conflicts you have the option to abort the merge entirely

```sh
git merge --abort
```
* After solving the conflicts commit those changes to put an end to merging.

## Stash

* To put changes into stash use the git stash save command

```sh
git stash save "Stash message goes here"
```
* List things saved in stash

```sh
git stash list
```
* Show the changes made in a specific stash

```sh
git stash show -p stash@{0}
```
* Retrieving stashed files

* Git stash pop removes the copy in the stash

```sh
git stash pop stash@{0}
```
* Git stash apply just copies the files fromt the stash to the working directory

```sh
git stash apply stash@{0}
```
* Deleting a single stashe

```sh
git stash drop stash@{0}
```
* Deleting all stashes

```sh
git stash clear
```
## Remote repositories

* To see all remote repostories use git remote command
* If there is no remopte repo git remote will show nothing

```sh
git remote
```
* A little bit more information

```sh
git remote -v
```
* Viewing remote branches with git branch

```sh
git branch -r
```
* Viewing local and remote branches with git branch

```sh
git branch -a
```

* Add a remote repo to a local git repo using git remote add 

```sh
git remote add <alias> <url>
git remote add origin http://github.com/ionixftw/testingLab.git
```
* Remove a remote

```sh
git remote rm <alias>
git remote rm origin
```
* Pushing changes to remote repositories
* -u flag tracks the remote branch
```sh
git push -u <alias> <branchToPush>
git push -u origin master
```
* Cloning a remote repository

```sh
git clone <repositoryUrl> <folderToCloneTo>
git clone http://github.com/ionixftw/testingLab.git test
```
* Fetching changes from remote repository
* git fetch only syncs origin/master with remote repository
* it does not affect the local master branch
* remote branches can not be checked out

```sh
git fetch
```
* If you need those changes from origin/master branch to your local master branch you need to merge them
* git pull however does the fetching and merging in single command
* so git pull = git fetch + git merge

```sh
git pull
```
* Though you can not check out remote branches you can however create a new tracking branch to match the remote branch

```sh
git branch new_Branch origin/new_Branch
git checkout -b new_Branch origin/new_Branch
```

* Deleting remote branches

```sh
git push origin --delete new_Branch
```