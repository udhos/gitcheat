# gitcheat

![commit](img/commit.png)

## Config

    git config --global user.name udhos
    git config --global user.email udhos
    git config -l

## Clone

    git clone <url>

"by default, the git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called) on the server you cloned from. Running git pull generally fetches data from the server you originally cloned from and automatically tries to merge it into the code you’re currently working on."

Git clone by default creates a remote called origin: "you should at least see origin - that is the default name Git gives to the server you cloned from"

## Index / Staging Area

"Staged means that you have marked a modified file in its current version to go into your next commit snapshot."

git add - "add this content to staging area". The staging area is the full content for the next commit.

## Add

git add - "add precisely this content to the next commit"

"Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part"

## Rm

git rm - remove file from working directory and also from staging area

git rm --cached - keep file in working directory but remove it from staging area

## Diff

git diff: to see what is still unstaged

git diff --cached: to see what you’ve staged so far (--staged and --cached are synonyms)

## Commit

git commit "records changes to the repository".

"Git thinks about its data more like a stream of snapshots."

git commit appends a new snapshot into the stream.

"Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part"

git commit --amend: redo the last commit

    git commit -m 'message'
    git add forgotten_file
    git commit --amend

## Log

git log "lists the commits made in that repository in reverse chronological order"

## Unstage

git add CONTRIBUTING.md - add CONTRIBUTING.md to stage/index
git reset HEAD CONTRIBUTING.md - remove CONTRIBUTING.md from stage/index

## Discard changes in working directory

git checkout -- CONTRIBUTING.md - retrieve file from last commit, discarding changes in the working directory

## Remote

Remote is a pointer to a remote repository URL.

    git remote add <shortname> <url>

"you should at least see origin - that is the default name Git gives to the server you cloned from"

    $ git remote -v
    origin  https://github.com/udhos/gitcheat (fetch)
    origin  https://github.com/udhos/gitcheat (push)

"git remote add origin git@github.com:peter/first_app.gitcreates a new remote called origin located at git@github.com:peter/first_app.git. Once you do this, in your push commands, you can push to origin instead of typing out the whole URL"
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

## Fetch

    git fetch <remote>

"The command goes out to that remote project and pulls down all the data from that remote project that you don’t have yet. After you do this, you should have references to all the branches from that remote, which you can merge in or inspect at any time."

"git fetch command only downloads the data to your local repository - it doesn’t automatically merge it with any of your work or modify what you’re currently working on."

## Push

Push your work upstream.

    git push <remote> <branch>

## Tag

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

### Checking out tag

    git checkout v2.0.0 ;# Puts repository in "detached HEAD" state

    git checkout -b version2 v2.0.0 ;# Create branch version2 based on tag v2.0.0

## Head

A head is simply a reference to a commit object.
“HEAD” (uppercase) refers exclusively to the currently active head.

    $ cat .git/HEAD
    ref: refs/heads/master

# References

http://marklodato.github.io/visual-git-guide/index-en.html

https://blog.osteele.com/2008/05/my-git-workflow/

https://git-scm.com/book/en/v2
