# gitcheat

![commit](img/commit.png)

## Config

    git config --global user.name udhos
    git config --global user.email udhos
    git config -l

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

## Remote

Remote is a pointer to a remote repository URL.

    $ git remote -v
    origin  https://github.com/udhos/gitcheat (fetch)
    origin  https://github.com/udhos/gitcheat (push)

"git remote add origin git@github.com:peter/first_app.gitcreates a new remote called origin located at git@github.com:peter/first_app.git. Once you do this, in your push commands, you can push to origin instead of typing out the whole URL"
https://stackoverflow.com/questions/5617211/what-is-git-remote-add-and-git-push-origin-master/5617350#5617350

    git push origin master
    # push the commits in the local branch named master to the remote named origin

## Head

A head is simply a reference to a commit object.
“HEAD” (uppercase) refers exclusively to the currently active head.

    $ cat .git/HEAD
    ref: refs/heads/master

# References

http://marklodato.github.io/visual-git-guide/index-en.html

https://blog.osteele.com/2008/05/my-git-workflow/

https://git-scm.com/book/en/v2
