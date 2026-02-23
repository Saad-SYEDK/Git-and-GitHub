# Commands

Before we begin with commands we first have install git on our system and then we need to create a git repository and then clone the repository on our local system.

***Note:** we once we install git on local pc, we will need to configure it with user name and email we can do it using these command `git config --global user.name <your_github_user_name>` and `git config --global user.email <your_github_email>`.*

## Creating Repository

There are two ways we can create a repository, the simplest way is to create a repository on github and it will show how we can work on it on our local pc, we basically clone the repository on our local system using the `git clone <repo url>` command.

The second way is to create a repository on our local system and initialize it git using `git init` command, then we push(basically update) the repository to our cloud i.e github, if we have already configured git then we can run this commnad `git push origin main`.

## Basic Commands - add, commit, push, pull

Once we have cloned our repo, we can do our work i.e create file, makes changes in our files, etc. And once we have made the changes we can update it to our remote repo.

We do this by first adding the chagned file to *staging area*, then commiting the changes and then finally pushing all the commits to our remote repository.

- **Add** -  we can add out files to *Staging Area* using `git add <file_name>` command, we can also use `git add --a` to stage all the changed files (not recommended).

- **Staging Area** - this is the area before commit, we can review the files here before commiting them.

- **Commit** - using the command `git commit -m "<commit message i.e descripton of the changes made>"`, will commit all the files in staging area, files not in the staging araea will not be commited. Once we commit the changes they are ready to be pushed to the remote repo.

    *Note : Commit message is mandatory and it has to be added within quotes("").*

- **Push** - The command `git push` will update the changes to the remote repository which in on the github and everyone with access to that repo will be able to see the chagnes.

- **Pull** - `git pull` Fetches content from the remote repo into your local system, basically used to sync our local repo with the remote repo.

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

    ***Head is a pointer to our most recent commit, when we commit a change our head pointer moves forward, we can use head~2 to point to the commit that was 2 commits before the head***

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

Suppose two persons are working on a same applicaton and person 1 in assgined with feature A and person 2 is assigned with feature B. If both of them work together on the same file they will be disturbing each other, to fix this we have the concept of **Branches**.

Branch allows users to work in isolation without affecting the main branch.

We have following branch commandsL:

- **Creating a Branch :**

    Create a branch using the command `git branch <name_of_branch>`  
- **Switch to a Branch :**

    Switch to an existing branch using `git switch <branch_name>`  

    Create and switch directly using `git switch -c <new_brach_name>`
- **List all Branches :** `git branch` or `git -a branch` to list remote branches also
- **Merge a Branch :**

    To merge current branch with another branch `git merge <name_of_branch_to_merge>`, it will integrate the other branch with current branch.
- **Rename a Branch :** `git branch -m <old_name> <new_name>`.
- **Delete a Branch :** `git branch -d <branch_name>`.

    once you delete a brach locally you must update it to your remote repo in order to reflect the deleted branch, else the branch will not be removed from the github.
    `git push origin --delete <deleted_branch_name>`

Tips:

- Create a seprate branch for every feature, avoids failure in main program.
- Commit each small successful progress - Snapshot
- Once the new feature has been tested, merge it with main.
- Delete branch after it has been merged - Cleanup.

## Diff

The diff command is a powerful feature that allows use to compare between diffent stages of a file.

- `git diff` - It shows the difference between the latest commit vs current changes before adding to staging area.

- `git diff --staged` - Shows changes in staging area that are not yet commited.

- `git diff HEAD` - Shows local changes vs commited changes.

- `git diff <commit 1> <commit 2>` - Shows the difference between two commits identified by their commit_hash.

- `git diff <branch 1> <branch 2>` - Shows difference both branches identified by their branch_names.

- `git diff <file_name>` - similar to first command but only displays the changes of file_name.

**Checkout about tools like meld, difftools, etc.**

## Fork

Fork is a fearture of github that allows a user to create a personal copy of someone's repo and host it on cloud.

It is similar to clone but the difference is that when you clone you store the repo in your local machine.

*Fork is not a git command, it is a freature of github.*

Fork vs. Clone

| Feature | Fork | Clone |
| --- | --- | --- |
| Location | Created on the server (e.g., GitHub.com) | Created on your local machine |
| Ownership | You own the forked copy | You usually do not own the target |
| Write Access | Full control over your fork | Limited by original permissions |

## Pull Request

Suppose you are working on someone's project, you created a seprate branch or fork the repo to work on a specific feature. Once your feature is ready now you want to merge this changes with the main file/branch/repo, since you're not the admin/owner of that repo you will make a **Pull Request** to the owner. If the owner accepts that request your code/branch will be merged with the main branch.

***A Pull Request (PR) is a proposal to merge changes from one code branch into another.***

## Other

In GitHub a user can create following things:

- **Issues** - Primary unit of work, used to track, assign tasks, raise bugs, feature requests, etc

- **Labels** - Baiscally tags that are used to categorize issues, pull requests.
Common categories include - high priority, good first issues, help wanted, etc. users can also create custom labels.

- **Milestones** - Used for progress tracking, like deployment, v1, v3 release, etc. Milestones also group issues and pull requestes into a bundle with options to add deadlines.
