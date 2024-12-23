# registry_set_amsi_com_hijack

## Title
Potential AMSI COM Server Hijacking

## ID
160d2780-31f7-4922-8b3a-efce30e63e96

## Author
Nasreddine Bencherchali (Nextron Systems)

## Date
2023-01-04

## Tags
attack.defense-evasion, attack.t1562.001

## Description
Detects changes to the AMSI come server registry key in order disable AMSI scanning functionalities. When AMSI attempts to starts its COM component, it will query its registered CLSID and return a non-existent COM server. This causes a load failure and prevents any scanning methods from being accessed, ultimately rendering AMSI useless

## References
https://enigma0x3.net/2017/07/19/bypassing-amsi-via-com-server-hijacking/
https://github.com/r00t-3xp10it/hacking-material-books/blob/43cb1e1932c16ff1f58b755bc9ab6b096046853f/obfuscation/simple_obfuscation.md#amsi-comreg-bypass

## False Positives
Unknown

## SentinelOne Query
```
ObjectType = "Registry" AND (EndpointOS = "windows" AND (RegistryKeyPath endswithCIS "\CLSID\{fdb00e52-a214-4aa1-8fba-4357bb0072ec}\InProcServer32\(Default)" AND (NOT RegistryValue = "%windir%\system32\amsi.dll")))

```