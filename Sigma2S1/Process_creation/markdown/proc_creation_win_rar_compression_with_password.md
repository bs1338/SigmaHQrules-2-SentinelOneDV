# proc_creation_win_rar_compression_with_password

## Title
Rar Usage with Password and Compression Level

## ID
faa48cae-6b25-4f00-a094-08947fef582f

## Author
@ROxPinTeddy

## Date
2020-05-12

## Tags
attack.collection, attack.t1560.001

## Description
Detects the use of rar.exe, on the command line, to create an archive with password protection or with a specific compression level. This is pretty indicative of malicious actions.

## References
https://labs.sentinelone.com/the-anatomy-of-an-apt-attack-and-cobaltstrike-beacons-encoded-configuration/
https://ss64.com/bash/rar.html
https://github.com/redcanaryco/atomic-red-team/blob/f339e7da7d05f6057fdfcdd3742bfcf365fee2a9/atomics/T1560.001/T1560.001.md

## False Positives
Legitimate use of Winrar command line version
Other command line tools, that use these flags

## SentinelOne Query
```
EventType = "Process Creation" AND (EndpointOS = "windows" AND (TgtProcCmdLine containsCIS " -hp" AND (TgtProcCmdLine containsCIS " -m" OR TgtProcCmdLine containsCIS " a ")))

```