# Git Version Control with Git

## Commands

* **git clone**: Create a local copy of a remote repository.
* **git add**: Stage changes for commit.
* **git commit**: Record changes to the repository.
* **git log**: Display commit history.
* **git push**: Push changes to a remote repository.
* **git pull**: Fetch changes from a remote repository and merge.
* **git init**: Initialize a new Git repository.
* **git remote add origin <remote_repo>**: Connect a local repository to a remote one.
* **git push --set-upstream origin master**: Create a local and remote connection for a new Git repository.
* **git checkout <branch>**: Switch to a different branch.
* **git checkout -b <branch>**: Create and switch to a new branch.
* **git branch**: List branches.
* **git status**: Display the status of changes.
* **git branch -d <branch>**: Delete a branch.
* **git rebase**: Avoid unnecessary merge commits in Git history.
* **git rm -r --cached <folder>**: Unstage a folder.
* **git rm --cached <file>**: Remove a file from the remote repository.
* **git stash**: Temporarily save unfinished changes.
* **git stash pop**: Apply the last stash and remove it.
* **git reset --hard HEAD~1**: Revert and discard changes to the last commit.
* **git reset HEAD~1**: Revert but keep changes from the last commit.
* **git commit --amend**: Merge changes into the last commit.
* **git reset --hard HEAD~1**: Revert and discard changes to the last commit.
* **git push --force**: Force push changes to a remote repository.
* **git revert <commit_hash>**: Create a new commit to revert changes from a previous commit.
* **git merge**: Merge branches.

## Remove Git

Remove local .git configuration:

```` bash

`rm -fr .git`
``````

## Best Practices

1. Use one branch per feature.
2. Establish a development branch as an intermediary master.
3. Utilize pull/merge requests for collaboration.
4. Delete branches after merging.
5. Include a .gitignore file to exclude unwanted files from version control.