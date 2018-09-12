# GIT

Git is a system for doing version control on your files

## Temporarily igonore mode changes for commands
Sometimes when you copy a git folder the mode changes for all the copied files. This is especially true for NTFS filesystems on which it is difficult to keep track of the user permissions. In this git can show all files as changed which may not be desirable. In such cases you can use the following command to temporarily ignore mode changes

``` bash
git -c core.fileMode=false diff
```
[Source](https://stackoverflow.com/a/1580644)

You can check the above source for details on how to disable it if required globaly or for current repository.

## Configure user.name and user.email for current repository
If you use different user.name and user.email for different repositories then it is ofter convinient to configure it individually for each repository and not have a global setting. You can use the following two commands to do this configuration for current repository

```bash
git config user.name "FirstName SecondName"
git config user.email "someemail@example.com"
```

## Use two different github accounts on same machine with ssh-keys.
ssh-keys are a conviinent way to interact with github. However you may run into errors incase you want to use multiple accounts on the same machine as you cannot reuse ssh keys for two accounts. The correct way to handle this thing is to create two different ssh keys for each account and confiure them to be used in the following way

This assumes you have created two different keys for each of your accounts. For details on how to create keys see this [page](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)

```bash
#activehacker account
Host github.com-activehacker
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_activehacker

#jexchan account
Host github.com-jexchan
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_jexchan
```
[Source](https://gist.github.com/jexchan/2351996)

You may also have to change you remote url to be of the format `git@github.com-{username}:{repo-url}.git` e.g. git@github.com-activehacker:activehacker/gfs.git

## Merge a branch into master

You can merge a branch in the master using the command line as follows

``` bash
git checkout master
git pull origin master
git merge test
git push origin master
```

The flow is basically doing this:-

1. Setting up the current branch to master
2. Pulling changes if any in the remote into master. This is preventing any conflicts later
3. Then you do the merge. If you have not made any changes to master this a fairly straigt forward things and should happen automatically without any intervention
4. Then you push the merged change to master on remote.

[Source](https://stackoverflow.com/a/5602109)

## Delete a branch from local/remote

You can delete the branch from local and remote using the following commands

``` bash
git branch -d <branchname>
# e.g. git branch -d tempbranch

git push --delete origin <branchname>
# e.g. git push --delete origin tempbranch
# Do change from origin if you remote name is different
```
[Source](https://stackoverflow.com/a/2003515)

