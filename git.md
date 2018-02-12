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