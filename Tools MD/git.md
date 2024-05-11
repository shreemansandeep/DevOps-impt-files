git init

git config --global user.name "Polarapu Prasad"
git config --global user.email "devopstraining2015@gmail.com"

git config --list

Paheses:


1) Workspace
2) Staging  / Index
3) Local repo

touch file1
ls
git status
git add file1
git status
git commit -m "label" file1
git status
git log
git show cid

touch file2 file3 file4 file5
git status
git add file2 file4
or
git add *
or
git add .
or
git add -A
git status
git commit -m "label"


git reset --soft cid  (local to staging)
git reset HEAD file-name  (staging to workspace)
git reset --mixed cid  (local to workspace)     /cid-1
git stash (This command temporarily stores all the modified tracked files.)

git commit -m "label" file  (workspace to local *only modiified files) 


git clone https://github.com/polarapu/batch59.git
ls
cd batch59
touch prasad
git status
git add .
git commit -m "label" prasad
git push

-------------------------------------------------------------
git clone https://github.com/polarapu/batch59.git
ls
cd batch59
ls
touch name
git status
git add *
git commit -m "label" 
git status
git log
git push
git pull --rebase (used to update your local branch with the latest changes from the remote branch, but instead of merging the changes)
git push
git pull --rebase
git push

log's
--------
git log
git log -n
git log --oneline
git log --oneline -n
git log --author=Pratap
git log --author=Pratap -n
git log --author=Pratap --oneline
git log --author=Pratap --oneline -n
git log --since=yy-mm-dd
or
git log --after=yy-mm-dd

git log --until=yy-mm-dd
or
git log --before=yy-mm-dd

git log --since=yy-mm-dd --until=yy-mm-dd
or
git log --after=yy-mm-dd --before=yy-mm-dd

git log --after="yy-mm-dd hh:mm" --before="yy-mm-dd hh:mm"

git log -- file-name
git log --grep="label"

BRANCH
-----------

git branch
git branch branch-name
git branch
git checkout branch-name 
git merge branch-name  (all changes)
git cherry-pick cid   (only one commit) (git cherry-pick in git means choosing a commit from one branch and applying it to another branch.)

git push origin branch-name 
or
git push path/of/c-repo branch-name
git branch -d branch-name  (local)
git push origin -d branch-name  (central)

git branch 
git branch -r (lists all of the remote branches that are associated with the current repository.)
git checkout -b origin/branch
git checkout -b origin/branch
git branch

git revert cid (This is useful if you have made a mistake in a commit and you need to revert to the previous state.)



TOUCH, CAT, VI
-----------------------
touch
--------
touch file1
ls
touch file2 file3 file4


CAT
-----
cat > file5
....
....
ctrl+d

cat file5

cat >> file5
...
...
ctrl+d

VI
---

vi file6
---------
esc i
........
.........
esc :w
esc :q
or
esc :wq!

git status
git config --global alias.s "status"
git s

git config --list
git config --global alias.cl "config --list"
git cl

git log --oneline
git config --global alias.l1 "log --oneline"
git l1

git config --list

To remove Alias and user-email
-------------------------------------------
git config --global --unset alias.l1
git config --global --unset user.name
git config --global --unset user.email

git checkout -b branch  (creating branch & checkout to branch)

CONFLICTS:
==========
1)Abort
2)Manual
3) Auto merging

git merge --abort

TAG
------
git tag
git tag tag-name
git show tag-name
or
git log
git tag tag-name cid

git push origin tag-name
or
git push --tags
Delete
-------
git tag -d tag-name  (local)
git push origin -d tag-name  (central)

amend
---------
git commit --amend -m "label" 

ignorfiles
-------------

vi .gitignore
-----------------
file1
file2
file3


Q: what is a merge conflict in git and how can it be resolved 
A: when two developers are updating code on same file and same lines then we getting this issue. To resolve this issue following developers should work together and they should update valid code and commit.
