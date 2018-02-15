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
## Using .gitignore files

* Git uses .gitignore file to learn about files that should not be tracked
* Create a .gitignore file in the root of the working directory
* Wildcard symbol '*' represents all characters
* But negations symbol '!' negates the ignoring and tells git to track those files
* Ex: *.html ignores all files ending with .html extension. But !index.html tracks index.html
* Directory names with a trailing backslash ignores all files in that directory
* Ex: builds/ ignores all files in builds directory
* Comments start with a '#' symbol
* Gitignore repo: [Gitignore](https://github.com/github/gitignore)
