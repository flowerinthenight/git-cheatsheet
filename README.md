# Personal GIT cheatsheet

### Reset a file

```
git checkout HEAD -- my-file.txt
```

### Delete last commit

```
git reset --hard HEAD~1
```

### Delete local branch

```
git branch -d <branch-name>
```

or force delete with

```
git branch -D <branch-name>
```

### Delete branch from remote repository

```
git push origin --delete <remote-branch-name>
```

### Search for the merge commit from a specific commit

```
git log <SHA>..master --ancestry-path --merges
```

### Search for a commit message

```
git log | grep <pattern>
```

### List commits on range line of codes for one file

```
git blame -L<line#>,+<offset> -- <filename>
```

For example, three lines starting from line 257 of main.cpp

```
git blame -L257,+3 -- main.cpp
```

### History of a line (or lines) in a file

```
git log --topo-order --graph -u -L <line-start>,<line-end>:<file>
```

For example, history of line 155 of main.cpp

```
git log --topo-order --graph -u -L 155,155:main.cpp
```

### Compare (diff) a file from the current branch to another branch

```
git diff ..<target-branch> <path-to-file>
```

or if difftool is configured

```
git difftool ..<target-branch> <path-to-file>
```

### Rebase/squash all branch commits

```
git checkout -b new-branch
modify...
commit...
...
git rebase -i master
(sometimes, I branch out of master for a clean branch and do a git rebase -i clean-branch)
```

### Combine all branch commits to one before merging to master (sort of like the one above)

```
git checkout master
git checkout -b clean
git merge --squash branch_to_merge_to_one_commit
git commit
(add commit message)
git checkout master
git merge clean
```

### Revert a file or directory to a previous commit

```
git checkout <commit_id> -- file/or/directory
```

### Custom format for log

Add to global `.gitconfig` using `git config --global alias.logp "..."`

```
git log --pretty=format:'%Cred%h %C(yellow)%d%Creset %s %Cgreen(%cr|%ci) %C(bold blue)[%an]%Creset'
```

# License

[The MIT License](./LICENSE.md)
