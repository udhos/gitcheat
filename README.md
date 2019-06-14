# gitcheat

![commit](img/commit.png)

## Config

    git config --global user.name udhos
    git config --global user.email udhos
    git config --global credential.helper 'cache --timeout 3600'
    git config -l

## Clone

    git clone <url>

"by default, the git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called) on the server you cloned from. Running git pull generally fetches data from the server you originally cloned from and automatically tries to merge it into the code you’re currently working on."

Git clone by default creates a remote called origin: "you should at least see origin - that is the default name Git gives to the server you cloned from"

## Index / Staging Area

"Staged means that you have marked a modified file in its current version to go into your next commit snapshot."

    git add <files> ;# "add this content to staging area". The staging area is the full content for the next commit.

## Add

    git add <files> ;# "add precisely this content to the next commit"

"Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part"

## Rm

    git rm          ;# remove file from working directory and also from staging area

    git rm --cached ;# keep file in working directory but remove it from staging area

## Diff

    git diff          ;# to see what is still unstaged

    git diff --cached ;# to see what you’ve staged so far (--staged and --cached are synonyms)

## Commit

    git commit ;# "records changes to the repository"

"Git thinks about its data more like a stream of snapshots."

git commit appends a new snapshot into the stream.

"Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part"

    git commit --amend ;# redo the last commit

    git commit -m 'message'
    git add forgotten_file
    git commit --amend

## Log

    git log ;# "lists the commits made in that repository in reverse chronological order"

## Unstage

    git add CONTRIBUTING.md        ;# add CONTRIBUTING.md to stage/index
    git reset HEAD CONTRIBUTING.md ;# remove CONTRIBUTING.md from stage/index

## Discard changes in working directory

    git checkout -- CONTRIBUTING.md ;# retrieve file from last commit, discarding changes in the working directory

## Remote

Remote is a pointer to a remote repository URL.

    git remote add <shortname> <url>

"you should at least see origin - that is the default name Git gives to the server you cloned from"

    $ git remote -v
    origin  https://github.com/udhos/gitcheat (fetch)
    origin  https://github.com/udhos/gitcheat (push)

"git remote add origin git@github.com:peter/first_app.git creates a new remote called origin located at git@github.com:peter/first_app.git. Once you do this, in your push commands, you can push to origin instead of typing out the whole URL"

https://stackoverflow.com/questions/5617211/what-is-git-remote-add-and-git-push-origin-master/5617350#5617350

    git push origin master
    # push the commits in the local branch named master to the remote named origin

Example:

    git remote add pb https://github.com/paulboone/ticgit
    git fetch pb = fetch all the information that Paul has but that you don’t yet have in your repository
    Paul’s master branch is now accessible locally as pb/master

### Inspecting remote

    git remote show <remote>

### Renaming remote

    git remote rename <old> <new>

### Deleting remote

    git remote rm <remote>

## Remote branch

"It’s important to note that when you do a fetch that brings down new remote-tracking branches, you don’t automatically have local, editable copies of them. In other words, in this case, you don’t have a new serverfix branch - you only have an origin/serverfix pointer that you can’t modify. To merge this work into your current working branch, you can run git merge origin/serverfix. If you want your own serverfix branch that you can work on, you can base it off your remote-tracking branch:"

    $ git fetch origin
     * [new branch]      serverfix    -> origin/serverfix

    $ git checkout -b serverfix origin/serverfix

### Tracking branches

"When you clone a repository, it generally automatically creates a master branch that tracks origin/master."

    git checkout -b serverfix origin/serverfix ;# set branch serverfix tracking remote branch serverfix from origin

    git checkout --track origin/serverfix      ;# shortcut for doing the same

    git checkout serverfix                     ;# even shorter

    git checkout -b sf origin/serverfix        ;# set branch sf tracking remote branch serverfix from origin

    git branch -u origin/serverfix             ;# set remote branch for a local branch

    git fetch --all ;#  fetch from all your remotes 

    git branch -vv ;# show remote tracking

### Deleting remote branch

    git branch -d serverfix            ;# delete branch locally

    git push origin --delete serverfix ;# delete branch from remote origin

## Fetch

    git fetch <remote>

"The command goes out to that remote project and pulls down all the data from that remote project that you don’t have yet. After you do this, you should have references to all the branches from that remote, which you can merge in or inspect at any time."

"git fetch command only downloads the data to your local repository - it doesn’t automatically merge it with any of your work or modify what you’re currently working on."

## Push

Push your work upstream.

    git push <remote> <branch>

## Tag

"A lightweight tag is very much like a branch that doesn’t change - it’s just a pointer to a specific commit."

"Annotated tags are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG)."

List tags:

    git tag

Show tag:

    git show v1.4

Annotated tag:

    git tag -a v1.4 -m "my version 1.4"

Lightweight tag:

    git tag v1.4-lw

Tagging specific commit:

    git tag -a v1.2 9fceb02

Sharing specific tag:

    git push origin <tagname>

Sharing all tags:

    git push origin --tags

Delete tag:

    git tag --delete <tagname>         ;# delete locally
    git push --delete origin <tagname> ;# delete tag from remote

### Checking out tag

    git checkout v2.0.0 ;# Puts repository in "detached HEAD" state

    git checkout -b version2 v2.0.0 ;# Create branch version2 based on tag v2.0.0

## Branch

"A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master."

"The master branch in Git is not a special branch. It is exactly like any other branch. The only reason nearly every repository has one is that the git init command creates it by default and most people don’t bother to change it."

See where branch pointers are pointing:

    git log --oneline --decorate

Show branches:

    git branch -a

Show last commit from every branch:

    git branch -vv

Create branch:

    git branch testing

Switch to branch: Switching branches changes files in your working directory

    git checkout testing

Create and switch to branch:

    git checkout -b <branch>

Delete branch:

    git branch -d <branch>

Show divergent history:

    git log --oneline --decorate --graph --all

## Merge

Basic merge:

    git checkout master
    git merge <branch>

"The useful --merged and --no-merged options can filter this list to branches that you have or have not yet merged into the branch you’re currently on."

    git branch --merged    ;# which branches are already merged into the branch you’re on
    git branch --no-merged ;# branches that contain work you haven’t yet merged in

## Pull

    git fetch <url> ;# get all changes from server, don't modify the working dir

    git pull ;# look up what server and branch your current branch is tracking, fetch from that server and then try to merge in that remote branch.

"Generally it’s better to simply use the fetch and merge commands explicitly as the magic of git pull can often be confusing."

## Rebase

Basic rebase:

    git checkout experiment
    git rebase master
    # replayed experiment on top of master

    git checkout master
    git merge experiment
    # master fast-forwarded to experiment

Merge vs Rebase: "In general the way to get the best of both worlds is to rebase local changes you’ve made but haven’t shared yet before you push them in order to clean up your story, but never rebase anything you’ve pushed somewhere."

## Head

A head is simply a reference to a commit object.
“HEAD” (uppercase) refers exclusively to the currently active head.

    $ cat .git/HEAD
    ref: refs/heads/master

"Notice the * character that prefixes the master branch: it indicates the branch that you currently have checked out (i.e., the branch that HEAD points to). This means that if you commit at this point, the master branch will be moved forward with your new work."

    git branch
    * master

# References

http://marklodato.github.io/visual-git-guide/index-en.html

http://onlywei.github.io/explain-git-with-d3/

https://blog.osteele.com/2008/05/my-git-workflow/

https://git-scm.com/book/en/v2
