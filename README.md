# gitcheat

## Config

    git config --global user.name udhos
    git config --global user.email udhos
    git config -l

## Commit

git commit "records changes to the repository".

![commit](img/commit.png)

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
