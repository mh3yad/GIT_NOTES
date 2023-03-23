# GIT_NOTES
## init
```
git init -> create .git file
git add . | * | file.txt | *.php -> add files to staging and create blob in .git dir
git commit -m "message" -> from index to repo create commit and tree objects
git remote add name url|location
git push remote(origin) branch
```
# configs
```
git config --global (/etc/gitconfig) user.name || user.email
git config --system (~/.gitconfig) user.name || user.email
git config  (.git/config) user.name || user.email
git config --global core.ediotr (specify default editor)
git config --list
```
## scan files
```
ls                         -> list working tree
git ls-files -s(sha1)     -> list index
find .git/objects -type f  -> list repo
"HEAD:     $(git cat-file -p(content) -s(size) -t(type) HEAD:myfile)"
"Stage:    $(git cat-file -p :myfile)"
"Worktree: $(cat myfile)"
```
## log
```
git log --oneline -2(last 2) --all(from all branches) --graph 
git reflog -> log brnaches tips updates
```
## diff
```
git diff commit1 commit2 | branch1 branch2 
git diff                          -> View difference between Stage and Working Directory
git diff --staged                 ->  View difference between HEAD and Stage
git diff HEAD                     -> View difference between HEAD and Working Directory
```
## Undo
```
git rm --cashed file              -> untrack

git restore file                  -> discard mofification
git checkout file                 -> discard mofification

git restore --staged file         -> unstage  
git reset file                    -> unstage
![mine](https://user-images.githubusercontent.com/55093384/227140805-0f374889-d0cd-42e3-9a6f-d0a897ae8206.png)



git reset --hard HEAD             -> unstage and discard modification (copy from HEAD to index and w.t)
git checkout HEAD file

git reset HEAD~1 | HEAD@{1} (from reflog)
git revert HEAD~3                 -> Revert the changes specified by the fourth last commit in HEAD and create a new commit with the reverted changes.
git commit --amend                -> modify last commit msg and compined  staged changes with last commit content
```
## Tags
```
lightweight tags
git tag v1                        -> piointer, no commit created
git show v1
annotated tags -a
git tag -a v2                     -> create object on .git/object
```
## Branching
```
is a linear layout of commits
git branch
git branch new_branch
git switch branch
git checkout -b branch
git branch -d name
git branch --merged
```
## Merge
```
Fast forward -> when current commit is direct ancestor of the branch we are merging in
3-way merge -> when current commit is not a direct ancestor of the branch we are merging in 
```
## Rebase
```
keep clean history and remove dianmond shape from divergent branches, after we make fast-forward
replays commits from current branch to another
performing several cherry-picks
$(feature) git rebase main
$(main)    git merge feature
```
## conflict
```
when merging 2 branch that made commits on same lines in a file
```
## Remotes
```
git remote -v -vv 
git remote add name url|location
git pull = git fetch + git merge remote/branch
git push origin branch
```

