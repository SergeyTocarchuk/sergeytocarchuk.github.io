---
layout: post
title: "Setup Online Code Repo with GitHub"
author: "Serhii T."
categories: journal
tags: [github]
image: github_logo.jpeg
---

### Setup Github

Upon download and installation in your local machine, first time setup steps are required (only one time) for your git installation:
```
git config --global user.name "Your name"
git config --global user.email youremail@example.com
```
Replace "Your name" and youremail@example.com above with your actual name and email address which you want shown on your repos.

To display git config settings, use the following command:
```
git config --list
```

First of all please sign-up for a [GitHub account](https://github.com/).

To display your public SSH key:
```
cat ~/.ssh/id_rsa.pub
```
If you don't have an SSH public key or are not sure, checkout the instructions [here]( https://help.github.com/en/github/authenticating-to-github/checking-for-existing-ssh-keys)

### Push to Repositary

When creating a GitHub repo for your application, you can click on the SSH button, then push existing repo:

```
git remote add origin git@github.com:yourgithubaccountname.git
```
To add a new remote Git repository as a shortname you can reference easily, run:

```
git remote add <shortname> <url>:
```

To view remotes setup in your environment (from your app directory):
```
git remote -v
```

And if you'd like to push a branch to another repository, you need to execute the “git push” command, and specify the correct remote name as well as the branch to be pushed:

```
git push <remote> <branch>
```

To check current state of file updates with already tracked/committed code in repo, check git status with the following command:
```
git status
```

To add/track all files, use the following command:
```
git add -A
```

To commit changes/updates/additions to repository, use the following command:

```
git commit -m "A useful message to help remember details of commit"
```

To push changes/updates/additions to repository use this command (remember you only need use it the first time):
```
git push -u origin master
```

For future pushes to repository:
```
git push origin master
```

To reject latest changes, you can use the following command:
```
git checkout -f
```

### Branches

- to make a new branch and switch to it with the command: 
```
git checkout -b branchName
```

- to check list of branches run _git branch_

- commit all your changes to your feature-branch.

- if you don't want to push changes to feature-branch, switch to your main (master) branch:
```
git checkout main (or master)
```

- merge changes to our _main_ branch (first switch to the branch you want to merge INTO (_main_ or _master_):
```
git merge branchName
```

Push your changes to remote repo and that's it!

To delete the branch:
```
// from our local repo with:
git branch -d branchName

// from the remote repo on Github with 
git push --delete origin branchName
```

### Update local branch from remote one

```
git fetch
```

- Git gathers any commits from the remote branch that do not exist in your current branch and stores them in your local repository. However, it does not merge them with your current branch. This is particularly useful if you need to keep your repository up to date, but are working on something that might break if you update your files. 
- To integrate the commits into your current branch, you must run _git merge_ afterwards.

Shorthand for _git fetch_ and _git merge_ is:

```
git pull
```

- Git tries to automatically merge. It automatically merges the commits without letting you review them first. If you don’t carefully manage your branches, you may run into frequent conflicts.

### Some useful git commands:

- If you'd like to see all the commits you've made:
```
git log
```

- Stash the changes in a dirty working directory away
```
git stash
```

### Some useful resources:

[Free online Pro Git book](https://git-scm.com/book/en/v2)

[Reference manual](https://git-scm.com/docs)
