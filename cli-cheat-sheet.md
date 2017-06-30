## CLI Cheat Sheet

### Git

Clear all unstaged changes, including ignored files:

`> git clean -dfx`

Find removed file:

`> git log --all --full-history -- **/thefile.*`

Git pull and rebase:

`> git pull --rebase`

[Undo latest unpushed commit:](http://stackoverflow.com/questions/927358/how-to-undo-last-commits-in-git)

```
> git commit -m "Something terribly misguided"              (1)
> git reset HEAD~                                           (2)
<< edit files as necessary >>                               (3)
> git add ...                                               (4)
> git commit -c ORIG_HEAD                                   (5)
```

[Find and restore a deleted file:](https://stackoverflow.com/questions/953481/find-and-restore-a-deleted-file-in-a-git-repository)

```
> git rev-list -n 1 HEAD -- <file_path>                     (1)
> git checkout <deleting_commit>^ -- <file_path>            (2)
```

## Powershell

[`> Get-ChildItem -Filter “*current*” -Recurse | Rename-Item -NewName {$_.name -replace ‘current’,’old’ }`](https://blogs.technet.microsoft.com/heyscriptingguy/2013/11/22/use-powershell-to-rename-files-in-bulk/)

Listen to new lines in a log fil containing a specific regex:

`> Get-Content .\application_2017-05-30.log -Wait -Tail 0 | Select-String '.+(UserRepository).+'`

## Docker for Windows

Run a docker container (in this case ruby), mount current directory to `/app` and open bash:

`> docker run -v ${pwd}:/app -it ruby /bin/bash`

## Dotnet core

Clear the package cache:

`> dotnet nuget locals all --clear`
