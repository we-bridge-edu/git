Git exercises
====

Those exercises aim at helping you understand the basic Git operations and the various cases you might encounter in work environment.
The topics will include in order:

1. Cloning a repository
2. Changing branch (checkout and branch)
3. Making changes (commit)
4. Merging
5. Deleting a branch
6. Resolving merge conflicts
7. Oops I forgot... (--amend)

Exercise 1: Clone
===

* Clone this repository using the SSH Clone URL
* The URL is `git@github.com:we-bridge-edu/git.git`
* To clone use the `git clone <url> <path>` command

Your local repository (files on your computer) are now the same as the remote (github) one.
By default the remote will be called `origin`,It is possible to have multiple remotes with different names, but let's keep that for later.

Exercise 2: Changing branch
===

After cloning the repository you should be on the `master` branch

* Get an updated view of the remote using the `git fetch` command
* Switch to the `dev` branch using the `git checkout <branch_name>`

Exercise 3: Making changes
===

When adding new feature or correcting bug we do it in a new branch for a better organization and code maintenance. (You could then remove one feature easily)

* Be sure you are on the dev branch
* Be sure your dev branch is up to date with the remote using `git pull <remote_name> <branch_name>`
* Create a new branch named `add_water` based on the dev one using `git checkout`

**Not working?** That's because the branch does not exists yet, it needs to be created the first time by adding the `-b` parameter:
`git checkout -b <branch_name>`


* Modify the `shopping.csv` to add 3 bottles of water to the shopping list
* Commit your changes

Exercise 4: Merging
===

You now have your changes ready to be merged into the `dev` branch:

* Checkout the `dev` branch
* Don't forget to `pull` your branch before merging in case it's not up to date
* Merge using the `git merge <branch_name>` to merge a branch into the current one
* Commit the changes

You should now have water in you `dev` branch!
Note that in good development environments, a developer won't merge its code by himself but will do a request that will be reviwed by someone else (usually senior member of the team) who will decide if it's really ok to be merged

Exercise 5: Deleting a branch
===

Your feature is now merged, you no longer require the branch `add_water` on your local repository, let's delete it!

* List your branches using the `git branch --list` command
* Delete the `add_water` branch using the `git branch -d <branch_name>` command
* List your branches again to be sure it was deleted properly

Exercise 6: Resolving merge conflicts
===

Most of the time git will try to merge by itself but sometimes it has no way to know how to merge 2 files.
This happens usually when the same lines you modified were modified after your latest `pull`

The branch `add_honey` added honey to the end of the list.

* Checkout the latest `dev`
* Try to merge it with the `add_honey` branch

Conflicts! Why?
You added water at the end, and it added honey at the end: Git do not know wich one should come before the other.
On a shopping list it does not matter but for many cases like software code the order is very important, that's why you have conflicts to resolve.

* Resolve the conflict by putting the honey first and the water at the end
* Commit your changes

Exercise 7
===

Oops, you just realized you merged those honey and water in the wrong order, it should be honey at the end!

Two Cases:

1. You did other modifications / commit before you realized your mistake, in that case it's best to do the changes and commit
2. You realized just after your commit

In this last case you can "rework" on the latest commit to either change the commit message or add missing files (or both). To do this:

* Do the modifications (invert the order of Honey and Water in your list)
* When committing, add the `--amend` option, this will rework your latest commit rather than creating a new one
* E.g. `git commit --amend`

If you specify a commit message it will overwrite the previous one (you can use that to quickly change/fix your latest commit message),
else the message will remain the same.
