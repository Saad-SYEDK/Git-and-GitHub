# Commands

Before we begin with commands we first have install git on our system and then we need to create a git repository and then clone the repository on our local system.

***Note:** we once we install git on local pc, we will need to configure it with user name and email we can do it using these command `git config --global user.name <your_github_user_name>` and `git config --global user.email <your_github_email>`.*

## Creating Repository

There are two ways we can create a repository, the simplest way is to create a repository on github and it will show how we can work on it on our local pc, we basically clone the repository on our local system using the `git clone <repo url>` command.

The second way is to create a repository on our local system and initialize it git using `git init` command, then we push(basically update) the repository to our cloud i.e github, if we have already configured git then we can run this commnad `git push origin main`.

## Basic Commands - add, commit, push

Once we have cloned our repo, we can do our work i.e create file, makes changes in our files, etc. And once we have made the changes we can update it to our remote repo.

We do this by first adding the chagned file to *staging area*, then commiting the changes and then finally pushing all the commits to our remote repository.

- **Add** -  we can add out files to *Staging Area* using `git add <file_name>` command, we can also use `git add --a` to stage all the changed files (not recommended).

- **Staging Area** - this is the area before commit, we can review the files here before commiting them.

- **Commit** - using the command `git commit -m "<commit message i.e descripton of the changes made>"`, will commit all the files in staging area, files not in the staging araea will not be commited. Once we commit the changes they are ready to be pushed to the remote repo.

    *Note : Commit message is mandatory and it has to be added within quotes("").*

- **Push** - The command `git push` will update the changes to the remote repository which in on the github and everyone with access to that repo will be able to see the chagnes.

## Status

The command `git status` is used to display the current status of our working directory and staging area. We have follwing statuses:

- **Untracked** - New file that git doesn’t track yet
- **Modified -**  Changed
- **Staged -**  Ready to Commit (after **add**, before **Commit**)
- **Unmodified -**  Not changed

## Undoing Changes

We have 4 different cases:

- **Staged Changes :**

    These are the changes that we have added to staging area(using **add**) but have not been committed (using **commit**). Basically we **unstage** changes. To undo this we use `git reset file_name` for particular file, if we want to reset all the files we have added to staging area, we can use `git reset`. We can also use `git checkout --` or `git restore`.
- **Single Commit :**

    If we have committed any changes and now we want to undo it we use `git reset HEAD~1`.
    HEAD~1 means we are moving our head one step back. (consider each commits as heads that are linearly connected)

- **Multilple Commits :**

    If we want to undo changes and go back to any particular commits we can use `git reset <commit_hash>`. We can find commit_hash by looking at out commit log using `git log` (enter q to quit)

    `git reset <commit_hash>` will unstage all the changes made till the commit hash, but it will keep the changes made in code editor which were made before `add`, if we want to undo all the changes and return our project as it was in the previous commit we can use `git reset --hard <commit_hash>`

- **Pushed Changes :**

    If we have pushed into remote, we can undo it by using `git revert <commit_hash>` command, this creates a new commit that does the opposite of bad commit.

| Scenario | Command | Effect |
| --- | --- | --- |
| Unstaged changes | `git restore <file>` | Discards local edits to a file |
| Staged changes | `git restore --staged <file>` | Keeps edits but removes from staging |
| Last local commit | `git reset --soft HEAD~1` | Deletes commit; changes stay staged |
| multiple local commit | `git reset <commit_has>` | Deletes commit; changes stay staged |
| Bad public commit | `git revert <commit-hash`> | New commit that "un-does" the old one |

## Branches

