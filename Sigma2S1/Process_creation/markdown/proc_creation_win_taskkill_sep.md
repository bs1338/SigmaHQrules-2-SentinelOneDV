# proc_creation_win_taskkill_sep

## Title
Taskkill Symantec Endpoint Protection

## ID
4a6713f6-3331-11ed-a261-0242ac120002

## Author
Ilya Krestinichev, Florian Roth (Nextron Systems)

## Date
2022-09-13

## Tags
attack.defense-evasion, attack.t1562.001

## Description
Detects one of the possible scenarios for disabling Symantec Endpoint Protection.
Symantec Endpoint Protection antivirus software services incorrectly implement the protected service mechanism.
As a result, the NT AUTHORITY/SYSTEM user can execute the taskkill /im command several times ccSvcHst.exe /f, thereby killing the process belonging to the service, and thus shutting down the service.


## References
https://www.exploit-db.com/exploits/37525
https://community.spiceworks.com/topic/2195015-batch-script-to-uninstall-symantec-endpoint-protection
https://community.broadcom.com/symantecenterprise/communities/community-home/digestviewer/viewthread?MessageKey=6ce94b67-74e1-4333-b16f-000b7fd874f0&CommunityKey=1ecf5f55-9545-44d6-b0f4-4e4a7f5f5e68&tab=digestviewer

## False Positives
Unknown

## SentinelOne Query
```
EventType = "Process Creation" AND (EndpointOS = "windows" AND (TgtProcCmdLine containsCIS "taskkill" AND TgtProcCmdLine containsCIS " /F " AND TgtProcCmdLine containsCIS " /IM " AND TgtProcCmdLine containsCIS "ccSvcHst.exe"))

```