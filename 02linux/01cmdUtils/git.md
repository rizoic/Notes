### GIT

Git is a system for doing version control on your files

#### Temporarily igonore mode changes for commands
Sometimes when you copy a git folder the mode changes for all the copied files. This is especially true for NTFS filesystems on which it is difficult to keep track of the user permissions. In this git can show all files as changed which may not be desirable. In such cases you can use the following command to temporarily ignore mode changes

``` bash
git -c core.fileMode=false diff
```
[Source](https://stackoverflow.com/a/1580644)

You can check the above source for details on how to disable it if required globaly or for current repository.

#### Configure user.name and user.email for current repository
If you use different user.name and user.email for different repositories then it is ofter convinient to configure it individually for each repository and not have a global setting. You can use the following two commands to do this configuration for current repository

```bash
git config user.name "FirstName SecondName"
git config user.email "someemail@example.com"
```
