## CLI Cheat Sheet

### Git

Clear all unstaged changes, including ignored files:

`> git clean -dfx`

Find removed file:

`> git log --all --full-history -- **/thefile.*`

## Powershell

[`$ Get-ChildItem -Filter “*current*” -Recurse | Rename-Item -NewName {$_.name -replace ‘current’,’old’ }`](https://blogs.technet.microsoft.com/heyscriptingguy/2013/11/22/use-powershell-to-rename-files-in-bulk/)
