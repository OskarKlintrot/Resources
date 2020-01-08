# Powershell

## Powershell

[`> Get-ChildItem -Filter “*current*” -Recurse | Rename-Item -NewName {$_.name -replace ‘current’,’old’ }`](https://blogs.technet.microsoft.com/heyscriptingguy/2013/11/22/use-powershell-to-rename-files-in-bulk/)

Listen to new lines in a log fil containing a specific regex:

```text
> Get-Content .\application_2017-05-30.log -Wait -Tail 0 | Select-String '.+(UserRepository).+'
```

Run first line only of a script:

```text
> Get-Content <script> -First 1 | Invoke-Expression
```

