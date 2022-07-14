<hr>
<p align="center">
    <img alt="Git" src="git-logo.png" height="190" width="455">
</p>
<hr>

# Git-Cheatsheet

- ```git init``` = to **initialise**(create) a repository(.git file is added)
- ```git status``` = to see the the status(commits, changes) of your repository
- ```rm -rf .git``` = to delete your created git repository(just deletes the .git file)
- ```git clone repository_link your_name``` = will clone a repository and give it your_name  
- ```git clone repository_link``` = will clone a repository with default name
- ```ls``` = will list the items present in the current directory
- ```pwd``` = will show you the present working directory
- ```cd``` = to chage directory(eg- for folder = cd folder_name/ , for a drive = cd drive_name: , for a file = cd file_name etc)
- ```cd ..``` = to move back in the directory
- ```git add .``` = to add all the changes in staging area
- ```git add file_name``` = to add a specific file in staging area 
- ```git rm --cached Book1.xlsx``` = will remove Book1.xlsx from tracking 

- ```git diff``` = differentiates between working directory and staging area.
- ```git diff --staged (or you can use --cached)``` = differentiates previous commit and staging area.
- ```git rm file``` = to delete a file

- ```git mv file file_rename``` = to rename a file (will change name of file to file_rename)
     > In linux , renaming and moving a file is same

<br> 

### GIT LOG

- ```git log``` = will show all the commits made by an user with his/her name,date,email,time
- ```git log -p``` = will show the log and the files added or deleted by someone.
- ```git log -p -m(Where m is a number)``` = will show the log and the files added or deleted by m people(commits)
- ```git log --stat``` = will give a short summary about commits of different people
- ```git log --pretty=oneline``` = will show all commits in one line
- ```git log --pretty=short``` = will show all commits in short(will not show the date)
- ```git log --pretty=full``` = will show author name his full commits without date
- ```git log --since=2.days``` = will show the commits done in 2 days (you can use .weeks, .years, .months, .hours)

### Placeholder that expand to information extracted from the commit :
<hr>
<br>

> %H -
commit hash

> %h - 
abbreviated commit hash

> %T -
tree hash

> %t -
abbreviated tree hash

> %P -
parent hashes

> %p -
abbreviated parent hashes

> %an -
author name

> %aN -
author name

> %ae -
author email

> %aE -
author email

- ```git log --pretty=format:"%h -- %an"``` = will show abbreviated commit hash with (two --) in between and then author name

- ```git log --amend``` = we can now merge our modified file into another author commit and change his message
(this will then open vim editor and you can start editing by pressing 'i' on your keyboard then after writing press ESC 
 button and then write ':wq' to exit ) [**For more info you can go to -** https://www.atlassian.com/git/tutorials/rewriting-history]
 
- ```git restore  --staged <file name>``` = will unstage the given file

<br>

## CHECKOUT

- ```git checkout``` = (can be used to change the current state of your repository (to move among) 1.branch 2.commit 3.tag)
- ```git checkout <commit hash>``` = will move to the state of that commit
- ```git checkout HEAD``` = will move to the state of latest commit.
- ```git checkout --<file_name>``` = will restore to the state when previous commit was done
- ```git checkout -f``` = will restore your whole working directory

<br>

## UNDO

- ```git reset``` = will remove all the files from the staging area
- ```git reset --soft [hash of the commit upto which you want to delete the commit]``` = will not undo the changes but will 
delete the commits above the specified hash of the commit.
- ```git revert [hash of the commit]``` = will undo the changes **with a new commit** [Revert (the commit message)]

<br>

## Working with git Server
- ```git remote``` = will show if you are connected to a server(Github etc..) or not 
- ```git remote add origin <Your repo link>``` = set the repository name to origin on git server.
- ```git remote -v``` = will tell you from where are you pushing and pulling a file
- ```git push -u origin master``` = to push your repository from local device to the server

<br>

## Adding SSH key to your github account 
- **Step1**: ssh-keygen -t ed25519 -C "your_email@example.com" <br>

    > (here we are using ed25519 algorithm which is latest otherwise
       you can use the tranditional method using rsa but not recommended , for reference you can go to 
	   https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

- **Step2**: Then click enter , then enter.

- **Step3**: Now go to C:/Users/*your user_name*/.ssh/id_rsa.pub and open it through notepad.

- **Step4**: Now copy the contents present in it (This is your ssh key)

- **Step5**: Then go to your github account click on the topmost right corner , go to settings then
       SSH and GPG keys , now click on newSSH_key AND paste the key 
Then add your key and you are good to go.
<!-- <Then write git push -u origin master> -->

## Setting aliases in Git

<br>

- ```git config --global alias.st status``` = will set alias for **git status** as **git st** globally. (You can create your own shortcuts according to your convenience)

<br>

## BRANCH

<br>

- ```git restore file_name``` = will switch to the state where your file was earlier when commited(all changes discarded)
- ```git branch newbranchname``` = will create a new branch with name **newbranchname**
- ```git checkout -b newbranchname``` = will create and switch to the new branch
- ```git checkout master``` = to switch again to master branch
- ```git commit -a -m "message"``` = to skip the staging area and directly commit
> Each commit has a unique SHA-1 hash and is 160bits or (20bytes).
- ```git commit --amend``` = now we can add the changes done in the previous commit without adding a new commit.
- ```git branch``` = to list all the branches in your git repository
- ```git merge branch_name``` = will merge branch in master branch
> <<< = conflict resolution marker 
- ```git add file_name``` = this is used to add a file in staging area but also is used to mark a merge conflict
- ```git branch -v``` = will show the no. of branches and show last commit hash and commit message on the local device
- ```git branch -av``` = will show all the branches in the repository
- ```git branch --merged``` = will show all the branches that has already merged 
- ```git branch --no-merged``` = will show all the branches that has not merged 
- ```git branch -d branch_name``` = will delete branch that has already merged , and will give error if branch has not merged to overcome the error write ```git branch -D branch_name```
- ```git push origin --delete [name of the deleted branch]``` = to delete the branch on the server
- ```git branch --list``` = will show the no. of branches(condition: there should be some content in the branch and are commited)
- ```touch file_name``` = will create a file with name file_name

> Types of branching workflow = 1.Long Running Branches 2.Short Running Branches

- ```git push origin bugfix``` = will push a branch named bugfix in the master branch origin
[NOTE: Always remember to be in the same branch which you want to push]

- ```git push origin bugfix:mybugfix``` = will change bugfix to mybugfix in remote(Github etc)
- ```git pull remote_name``` = will download(pull) all the changes done by someone who had made the repo that you cloned.
- ```git pull``` = will download and apply all the changes done online
- ```git fetch remote_name(eg- origin)``` = will download but not apply the changes done by someone who had made the repo that you cloned.
- ```git fetch --all``` = will download all the changes from all the remotes.
- ```git branch --show-current``` = will show the current branch you are on

<br>

## GIT STASH

<br>

- ```git stash``` = will store the code in a temporary location(procedure followed is LIFO(last in first out))
- ```git stash list``` = will show all the things that are stored in the stash.
- ```git stash -u``` = will store untracked files too with the changes done recently in the files that are staged .
- ```git stash``` = will stash only the changes in tracked and unstaged files.
- ```git stash pop``` = will reapply the stashed item
- ```git stash show``` = will show the no. of files present in the stashed item
- ```git stash show -p``` = will give the detailed information about the stash items  (where -p is patch , it is a type of format)
- ```git stash drop``` = will delete the stash present

<br>

## TAG

<br>

- ```git tag v1.0``` = [soft tag]will store the current state (version) of your repository as verison v1.0 [Mostly used in production]
- ```git tag --list``` = will show all the tags created
git tag -a v1.1 = [to create a tag properly we use -a](here vim editor will open and you have to write the metadata also)
- ```git checkout <tag name>``` = to switch to the state of given tag name

<br>

## SHOW

<br>

- ```git show <commit ID>``` = will show the information about repo at given <commit ID> if we do not mention the commit ID then will 
                       show information about the last commit.
					   
- ```cat <file>``` = will show the contents present a file

<br>

## RENAMING GIT BRANCH

- To rename a branch while pointed to any branch:
```git branch -m <oldname> <newname>```

- To rename the current branch:
```git branch -m <newname>```

- To push the local branch and reset the upstream branch:
```git push origin -u <newname>```

- To delete the remote branch:
```git push origin --delete <oldname>```
<br>

# Commands Overview

More information on git commands.

## Basic Git
1. **git config** (http://www.kernel.org/pub/software/scm/git/docs/git-config.html) - Sets configuration values for things like your user name, email, andgpg key, your  preferred diff algorithm, file formats to use, proxies,remotes and tons of other stuff. For a full list, see the git-config docs (http://www.kernel.org/pub/software/scm/git/docs/git-config.html)

2. **git init** (http://www.kernel.org/pub/software/scm/git/docs/git-init.html) - Initializes a git repository – creates the initial ‘.git’ directory in a newor existing project.

3. **git clone** (http://www.kernel.org/pub/software/scm/git/docs/git-clone.html) - Copies a Git repository from another place and adds the originallocation as a remote you can fetch from again and possibly push to if you have permission.

4. **git add** (http://www.kernel.org/pub/software/scm/git/docs/git-add.html) - Adds changes in files in your working directory to your index, orstaging area.

5. **git rm** (http://www.kernel.org/pub/software/scm/git/docs/git-rm.html) - Removes files from your index and your working directory so they willstopped being tracked.

6. **git commit** (http://www.kernel.org/pub/software/scm/git/docs/git-commit.html) - Takes all of the changes staged in the index (that have been ‘gitadd’ed), creates a new commit object pointing to it, and advances the branch to point to that new commit.

7. **git status** (http://www.kernel.org/pub/software/scm/git/docs/git-status.html) - Shows you the status of files in your index versus your workingdirectory. It will list out files that are untracked (only in your working directory), modified (tracked but not yet updated in your index), andstaged (added to your index and ready for committing).

8. **git branch** (http://www.kernel.org/pub/software/scm/git/docs/git-branch.html) - Lists existing branches, including remote branches if ‘-a’ is provided.Creates a new branch if a branch name is provided. Branches can also be created with ‘-b’ option to ‘git checkout’.

9. **git checkout** (http://www.kernel.org/pub/software/scm/git/docs/git-checkout.html) - Checks out a different branch – makes your working directory looklike the tree of the commit that branch points to and updates your HEAD to point to this branch now, so your next commit will modify it.

10. **git merge** (http://www.kernel.org/pub/software/scm/git/docs/git-merge.html) - Merges one or more branches into your current branch and auto-matically creates anew commit if there are no conflicts.

11. **git reset** (http://www.kernel.org/pub/software/scm/git/docs/git-reset.html) - Resets your index and working directory to the state of your lastcommit, in the event that something screwed up and you just want to go back.

12. **git rebase** (http://www.kernel.org/pub/software/scm/git/docs/git-rebase.html) - An alternative to merge that rewrites your commit history to move commits since you branched off to apply to the current head instead. A bit dangerous as it discards existing commit objects.

13. **git stash** (http://www.kernel.org/pub/software/scm/git/docs/git-stash.html) - Temporarily saves changes that you don’t want to commit immediately for later. Can re-apply the saved changes at any time.

14. **git tag** (http://www.kernel.org/pub/software/scm/git/docs/git-tag.html) - Tags a specific commit with a simple, human readable handle that never moves.

15. **git fetch** (http://www.kernel.org/pub/software/scm/git/docs/git-fetch.html) - Fetches all the objects that a remote version of your repository has that you do not yet so you can merge them into yours or simply inspect them.

16. **git pull** (http://www.kernel.org/pub/software/scm/git/docs/git-pull.html) - Runs a ‘git fetch’ then a ‘git merge’.

17. **git push** (http://www.kernel.org/pub/software/scm/git/docs/git-push.html) - Pushes all the objects that you have that a remote version does not yet have to that repository and advances its branches.

18. **git remote** (http://www.kernel.org/pub/software/scm/git/docs/git-remote.html) - Lists all the remote versions of your repository, or can be used to addand delete them.

## Inspecting Repositories

1. **git log** (http://www.kernel.org/pub/software/scm/git/docs/git-log.html) - Shows a listing of commits on a branch or involving a specific file and optionally details about what changed between it and its parents.

2. **git show** (http://www.kernel.org/pub/software/scm/git/docs/git-show.html) - Shows information about a git object, normally used to view commit information.

3. **git ls-tree** (http://www.kernel.org/pub/software/scm/git/docs/git-ls-tree.html) - Shows a tree object, including the mode and name of each node andthe SHA-1 value of the blob or tree that it points to. Can also be run recursively to see all subtrees as well.

4. **git cat-file** (http://www.kernel.org/pub/software/scm/git/docs/git-cat-file.html) - Used to view the type of an object if you only have the SHA-1 value,or used to redirect contents of files or view raw information about any object.

5. **git grep** (http://www.kernel.org/pub/software/scm/git/docs/git-grep.html) - Lets you search through your trees of content for words and phrases  without having to actually check them out.

6. **git diff** (http://www.kernel.org/pub/software/scm/git/docs/git-diff.html) - Generates patch files or statistics of differences between paths orfiles in your git repository, or your index or your working directory.

7. **gitk** (http://www.kernel.org/pub/software/scm/git/docs/gitk.html) - Graphical Tcl/Tk based interface to a local Git repository.

8. **git instaweb** (http://www.kernel.org/pub/software/scm/git/docs/git-instaweb.html) - Wrapper script to quickly run a web server with an interface into your repository and automatically directs a web browser to it.

## Extra Tools

1. **git archive** (http://www.kernel.org/pub/software/scm/git/docs/git-archive.html) - Creates a tar or zip file of the contents of a single tree from your repository. Easiest way to export a snapshot of content from your repository.

2. **git gc** (http://www.kernel.org/pub/software/scm/git/docs/git-gc.html) - Garbage collector for your repository. Packs all your loose objects for space and speed efficiency and optionally removes unreachable objects as well. Should be run occasionally on each of your repos.

3. **git fsck** (http://www.kernel.org/pub/software/scm/git/docs/git-fsck.html) - Does an integrity check of the Git “filesystem”, identifying dangling pointers and corrupted objects.

4. **git prune** (http://www.kernel.org/pub/software/scm/git/docs/git-prune.html) - Removes objects that are no longer pointed to by any object in any reachable branch.

5. **git-daemon** (http://www.kernel.org/pub/software/scm/git/docs/git-daemon.html) - Runs a simple, unauthenticated wrapper on the git-upload-pack program, used toprovide efficient, anonymous and unencrypted fetch access to a Git repository.


### To test your Knowlege you can go to - https://git-school.github.io/visualizing-git/

