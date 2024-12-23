# file_event_win_creation_new_shim_database

## Title
New Custom Shim Database Created

## ID
ee63c85c-6d51-4d12-ad09-04e25877a947

## Author
frack113, Nasreddine Bencherchali (Nextron Systems)

## Date
2021-12-29

## Tags
attack.persistence, attack.t1547.009

## Description
Adversaries may establish persistence and/or elevate privileges by executing malicious content triggered by application shims.
The Microsoft Windows Application Compatibility Infrastructure/Framework (Application Shim) was created to allow for backward compatibility of software as the operating system codebase changes over time.


## References
https://github.com/redcanaryco/atomic-red-team/blob/f339e7da7d05f6057fdfcdd3742bfcf365fee2a9/atomics/T1546.011/T1546.011.md#atomic-test-2---new-shim-database-files-created-in-the-default-shim-database-directory
https://www.mandiant.com/resources/blog/fin7-shim-databases-persistence
https://liberty-shell.com/sec/2020/02/25/shim-persistence/
https://andreafortuna.org/2018/11/12/process-injection-and-persistence-using-application-shimming/

## False Positives
Legitimate custom SHIM installations will also trigger this rule

## SentinelOne Query
```
ObjectType = "File" AND (EndpointOS = "windows" AND (TgtFilePath containsCIS ":\Windows\apppatch\Custom\" OR TgtFilePath containsCIS ":\Windows\apppatch\CustomSDB\"))

```