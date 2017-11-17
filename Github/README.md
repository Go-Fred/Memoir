# Git & Github

## Index

1. Getting started with Git & Github
2. Commits
3. Branches
4. Remotes

## 1. Getting started with Git & Github

### Educational guides

Two very good educational guides on Git:
- A guide on Youtube with simple words and analogies - [Git For Ages 4 And Up](https://www.youtube.com/watch?v=1ffBJ4sVUb4)
- Git Basic - [Guide by Atlassian](https://www.atlassian.com/git/tutorials/setting-up-a-repository)

### Github

Github is the most popular platform for storing and managing git repositories online. On its free plan, all repositories are public.

### Repositories

A repository is a directory where you can store your project files. It can be online (called remote) or local in a folder of your computer. Everyone working on the project has their own local copy of the repository.

Repo is a common abbreviation of repository.

### [Creating a new repository](https://help.github.com/articles/creating-a-new-repository/)

1. Create a repository on Github
2. Create a folder on your computer
`mkdir project`
3. Initialize git in your folder
`git cd project
git init`
4. Copy your files in the folder (or at least add a readme 😉)
```shell
echo "# test12" >> README.md
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:your-remote.git
git push -u origin master
```

### Cloning and forking on Github

Cloning is the action of copying an online repository to a local folder of your computer.

Forking is the action of copying someone's repository on Github (in its current state) in your own list of online repositories.

### Branching

To make sure projects members don't alter the remote with their changes, it's common to _branch off_ of the main project to make their change and then push their branch to the remote and finally open a pull request to merge the changes to the main project.

## 2. Commits

### How to make a nice commit?

1. Check what files have changed
`git status`

2. Prepare your files to be committed (also called staging)

a. Add all files to the future commit
`git add .`

b. Add a file entirely if you want to commit the entire file
`git add <file>`

c. If you want to commit some parts of a file and not others
`git add -p`

3. Commit your changes (put an id on the changes you just add)
`git commit -m "your commit description"`

It's good to commit only one thing at a time. So you usually do b) or c) then commit then re b) or c) and re-commit

### What changes was made for commit xx?

1. Retrieve the logs > to get out of vim :q
`git log` or `glog`

2. Retrieve the commit id

3. Check the commitId
`git show <commitId>``

### Delete a commit

1) Check what changes were made
2) Reset the head
a) If you hadn't pushed (changes are kept)
`git reset HEAD~1 // ~1 for 1 commit back`

Or (no mercy)
`git reset --hard HEAD~1`

b) If you had pushed
`git reset HEAD~1`

Overwrite the remote branch with the local branch one step before
`git push origin +nombranche`
and then

```shell
git add
git commit
git push
```

## 3. Branches

Nice branch
`git checkout -b new-branch master`

### Rename a branch

[Rename local branch](https://stackoverflow.com/questions/6591213/how-do-i-rename-a-local-git-branch)
`git checkout <old-branch>`
`git branch -m <new-name>`

[Rename local and remote branch in git](https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git/)
1. Delete the old-name remote branch and push the new-name local branch.
`git push origin :old-name new-name`

2. Reset the upstream branch for the new-name local branch.
Switch to the branch and then:
`git push origin -u new-name`

### Delete a branch

Delete a branch locally:
`git branch -d <local-branch>`

Force deletion:
`git branch -D <local-branch>`

[Delete a remote branch](http://stackoverflow.com/questions/2003505/how-to-delete-a-git-branch-both-locally-and-remotely)
`git push origin --delete <remote-branch>`

## 4. Remotes

Where does my remote point?
`git config`
