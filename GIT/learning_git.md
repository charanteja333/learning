#Learning git

* `git config --local` -> Will set the git variables local to repo
* `git config --global` -> Will set the git variables to a user account
* `git config --system` -> Will set the git variables to a system
* ``git config --list`` -> Will list all the git configurations
* ``git config --global user.name "fullname" , git config --global user.email "email"`` -> to configure the user and email associated to github account
* `git config --global core.editor "vim"` -> Will set the default text editor to vim
* `git config --global core.autocrlf` -> It handles new line as per the git
* ``git config --global push.default simple`` --> This is for  pushing only the current branch to git repository if it is set to `simple` else if set to `matching` will push all branches 
* ``git clone 'url'`` -> Make a local copy of the repo
* `git pull` -> fetches the latest changes done in all branches of repo and merges with the corresponding local branch if any
* `git pull --rebase` -- Will fetch the remote changes and and changes  done locally are available on top of it if there are no merge conflicts
* `git rebase` -- Will fetch the remote changes and changes  done locally are available on top of it if there are no merge conflicts
*  `git fetch` -> Similar to git pull but wont merge the local brances with the remote. It is a best practise to fetch and merge the git branches
* `git branch` -> Gives the current working branch
* `git branch -a` -> Will give all the branches of a repo
* `git checkout '-branchname-'` -> Will switch to the branch given
* `git add '-filenames-'` -> Will add the modified/untracked files to staging area
* `git add .` -> will add all the modified/untracked files to staging area
* `git commit -m '-commitmessage-'` -> Submit all the changes to current branch along with commit message
* `git push` -> Will push the changes to the branch on git hub repository if default push behaviour is set to simple
* `git status` -> Will give the current status if any files are to be comiited etc
* `git branch '-newbranchname-'` -> Will create a new branch locally for a repo
* `git push -u origin '-newbranchname-'` -> Will create a new branch on the github and push the changes
* `git push origin --delete '-oldbranchname-'` -> Will delete the remote branch
* `git checkout -b '-localbranchname-' origin/'remotebranchname'` -> Will create a local branch from remote branch
* `git checkout -b -branchname-` -> Will create a new local branch and switch to the branch to stage the changes 
* `git branch -d -branchname-` -> Will delete the local branch
* `git diff` -> Gives the changes made in the working directory with staged version of the file
* `git diff --staged` -> Gives the changes made in the working directory with latest commit of the file
* `git diff HEAD`	-> Combines the changes made in untracked and staged and display
* `git diff --color-words` -> Gives the changes in colours made word by word
* `git merge '-branchname-'` -> To merge the current branch with the branch given as argument
* `git log` -> Provides the list of all commits made to branch
* `git log --oneline` -> Gives only commmit ids and commit message
* `git log --oneline --graph --decorate --all` -> Gives output mentioned earlier with a graph
* `git log --stat` -> Will give the files changed in the commit
* `git log --patch` -> Will give the content changes in the files
* `git init '-repo name-'` -> Will create a local repo
*  > .git file in a repo contains all the git internals 
*  `git mv '-oldfilename-' '-newfilename-'` -> This will rename the file and move it to the staging area for commiting
*  `git mv '-oldfilepath-' '-newfilepath-'` -> This will move the file to new path and add it to the staging area
*  `git revert '-commit id-'` -> Will revert the commit and add a comment to it
*  `git commit --amend` -> Can be used to modify a commit previous commit message or add more changes to commit after adding them to staging area
*  `git reset HEAD <staged file>` -> Can be used to remove a file from staging area and put it back in working directory
*  `git reset --soft HEAD~2` -> To change the working directory to 2 commits before.All files to be committed are present in staging area.This is useful in adding group commits for a cleaner commit history
*  `git reset HEAD~2` -> This is default mixed mode .To change the working directory to 2 commits before.All files to be committed are present in working area
*  `git reset --hard '-commitid-'` -> This remove all the commits after given commit and cleans the working directory
*  `git checkout -- 'filename'` -> This will revert the modified changes to content with the last commit only for files in working area. Staging area files will not revert
*  `git rm 'filename'` -> This will remove the file and add the change to staging area for commiting
*  `git config --global alias.lol "log --oneline --graph --decorate --all" `-- This will create a alias named lol which can be used as 'git lol' to make the git log command easier

*  `git tag -a 'tagname' -m 'tagmessage'` -> To mark releases or tag specific points . This is annotated tag
*  `git show 'tagname'` -> Show the tag details along with the commit
*  `git tag 'tagname'-lw` -> This creates a light weight tag 
* `git checkout -b '-branchname-' '-tagname'` -> Will create a new local branch from the tag
* `git push origin '-tagname-'` -> Will create a remote tag will the local tags
* `git push origin --tags` -> Will create remote tags for all the local tags which are not present in remote
 
 