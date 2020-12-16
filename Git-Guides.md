# Version Control: GIT

Created time: Dec 15, 2020 4:55 PM
Last edited time: Dec 15, 2020 5:05 PM
Tags: information

## Revert to a commit

```bash
#Replace <old-commit-id> which you desire to roll back 
git reset --hard <old-commit-id>

#Push to the remote server
git push -f <remote-name> <branch-name>
```

## Rename a branch name

```bash
#Checkout to the branch that you want to rename.
git checkout <branch_name>

#Rename your branch
git branch -m <new_name>

#Let the remote server to remove the old name, and push the new name as new branch.
git push origin :<old_name> <new_name>

#Let remote server to update the new branch
git push -u origin <new_name>
```
