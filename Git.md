### Create a new branch with git and manage branches

> Before creating a new branch, pull the changes from upstream. Your master needs to be up to date


Create the branch on your local machine and switch in this branch :

    $ git checkout -b [name_of_your_new_branch]

Push the branch on github :

    $ git push origin [name_of_your_new_branch]

You can see all the branches created by using :

    $ git branch -a

Add a new remote for your branch :

    $ git remote add [name_of_your_remote] [name_of_your_new_branch]

Push changes from your commit into your branch :

    $ git push [name_of_your_new_remote] [url]

Update your branch when the original branch from official repository has been updated :

    $ git fetch [name_of_your_remote]

Then you need to apply to merge changes if your branch is derivated from develop you need to do :

    $ git merge [name_of_your_remote]/develop

Delete a branch on your local filesystem :

    $ git branch -d [name_of_your_new_branch]

To force the deletion of local branch on your filesystem :

    $ git branch -D [name_of_your_new_branch]

Delete the branch on github :

    $ git push origin :[name_of_your_new_branch]

If you want create a new branch:

    $ git branch <name_of_your_new_branch>
