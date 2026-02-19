# Commands

Before we begin with commands we first have install git on our system and then we need to create a git repository and then clone the repository on our local system.

***Note:** we once we install git on local pc, we will need to configure it with user name and email we can do it using these command `git config --global user.name <your_github_user_name>` and `git config --global user.email <your_github_email>`.*

## Creating Repository

There are two ways we can create a repository, the simplest way is to create a repository on github and it will show how we can work on it on our local pc, we basically clone the repository on our local system using the `git clone <repo url>` command.

The second way is to create a repository on our local system and initialize it git using `git init` command, then we push(basically update) the repository to our cloud i.e github, if we have already configured git then we can run this commnad `git push origin main`.

## Basic Commands - add, commit, push

Once we have cloned our repo, we can do our work i.e create file, makes changes in our files, etc. And once we have made the changes we can update it to our remote repo.

We do this by first adding the chagned file to *staging area*, then commiting the changes and then finally pushing all the commits to our remote repository.

**Add** -  we can add out files to *Staging Area* using `git add <file_name>` command, we can also use `git add --a` to stage all the changed files (not recommended).

**Staging Area** - this is the area before commit, we can review the files here before commiting on to them.

**Commit** - using the command `git commit -m "<commit message i.e descripton of the changes made>"`, once we commit the changes they are ready to be pushed to the remote repo.
***Note** : Commit message is mandatory and it has to be added within quotes("").*

**Push** - The command `git push` will update the changes to the remote repository which in on the github and everyone with access to that repo will be able to see the chagnes.
