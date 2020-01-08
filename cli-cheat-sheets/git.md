# Git

## Git

[Oh shit, git!](http://ohshitgit.com/)

Clear all unstaged changes, including ignored files:

```powershell
> git clean -dfx
```

Find removed file:

```powershell
> git log --all --full-history -- **/thefile.*
```

Git pull and rebase:

```powershell
> git pull --rebase
```

[Config Git to do a stash before pull and rebase automatically:](https://stackoverflow.com/a/30209750/4826084)

```powershell
# Once
> git pull --rebase --autostash
```

```powershell
# Permanent
> git config pull.rebase true
> git config rebase.autoStash true
```

[Undo latest unpushed commit:](http://stackoverflow.com/questions/927358/how-to-undo-last-commits-in-git)

```powershell
> git commit -m "Something terribly misguided"              (1)
> git reset HEAD~                                           (2)
<< edit files as necessary >>                               (3)
> git add ...                                               (4)
> git commit -c ORIG_HEAD                                   (5)
```

[Find and restore a deleted file:](https://stackoverflow.com/questions/953481/find-and-restore-a-deleted-file-in-a-git-repository)

```powershell
> git rev-list -n 1 HEAD -- <file_path>                     (1)
> git checkout <deleting_commit>^ -- <file_path>            (2)
```

[Remove all local branches that have been merged into the branch currently checked out:](https://stackoverflow.com/a/43334157/4826084)

```powershell
> git branch --merged | ? {$_[0] -ne '*'} | % {$_.trim()} | % {git branch -d $_}
```

[Remove untracked branches \(replace `-D` with `-d` to only remove fully merged branches:](https://stackoverflow.com/questions/13064613/how-to-prune-local-tracking-branches-that-do-not-exist-on-remote-anymore)

```powershell
> git fetch --prune
> bash
$ git branch -r | awk '{print $1}' | egrep -v -f /dev/fd/0 <(git branch -vv | grep origin) | awk '{print $1}' | xargs git branch -D
```

Staging Patches:

```powershell
> git add -i # Choose option "5" or "p" as in "patch"
```

Undo Patches:

```powershell
> git checkout -p <optional filename(s)>
```

Replace remote with local branch:

```powershell
> git checkout BranchToPushTo
> git reset --hard BranchToReplaceWith
> git push --force
```

