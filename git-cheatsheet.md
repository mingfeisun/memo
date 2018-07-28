## Git commands
* Mingfei Sun
* Created at: 2018-07-23
* Modified at: 2018-07-25

### Branch operations
* Create a new branch from current branch
``` bash
git checkout -b <new_name> 
```
* Checkout to the new branch
``` bash 
git checkout <new_name>
```
* Delete a branch
``` bash
git branch -d <new_name>
```
* Delete dead files in history
``` bash
git gc --prune=now --aggressive
```
* List large file
``` bash 
git rev-list --objects --all \
| git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' \
| sed -n 's/^blob //p' \
| sort --numeric-sort --key=2 \
| cut -c 1-12,41- \
| numfmt --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
```
* merge
 ```bash
 # under current branch
 git merge <new_branch>
 ```
