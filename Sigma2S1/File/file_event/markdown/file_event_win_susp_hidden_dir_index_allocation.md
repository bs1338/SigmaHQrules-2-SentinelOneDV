# file_event_win_susp_hidden_dir_index_allocation

## Title
Potential Hidden Directory Creation Via NTFS INDEX_ALLOCATION Stream

## ID
a8f866e1-bdd4-425e-a27a-37619238d9c7

## Author
Scoubi (@ScoubiMtl)

## Date
2023-10-09

## Tags
attack.defense-evasion, attack.t1564.004

## Description
Detects the creation of hidden file/folder with the "::$index_allocation" stream. Which can be used as a technique to prevent access to folder and files from tooling such as "explorer.exe" and "powershell.exe"


## References
https://twitter.com/pfiatde/status/1681977680688738305
https://soroush.me/blog/2010/12/a-dotty-salty-directory-a-secret-place-in-ntfs-for-secret-files/
https://sec-consult.com/blog/detail/pentesters-windows-ntfs-tricks-collection/
https://github.com/redcanaryco/atomic-red-team/blob/5c3b23002d2bbede3c07e7307165fc2a235a427d/atomics/T1564.004/T1564.004.md#atomic-test-5---create-hidden-directory-via-index_allocation
https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/c54dec26-1551-4d3a-a0ea-4fa40f848eb3

## False Positives
Unlikely

## SentinelOne Query
```
ObjectType = "File" AND (EndpointOS = "windows" AND TgtFilePath containsCIS "::$index_allocation")

```